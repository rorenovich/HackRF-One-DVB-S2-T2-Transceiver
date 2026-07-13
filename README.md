# 📡 HackRF-One DVB-T / DVB-S2 SDR Transmitter

<p align="center">

Software Defined Radio implementation of DVB-T and DVB-S2 digital television transmitters using **HackRF One**, **GNU Radio**, and **gr-dtv**.

</p>

<p align="center">

![GNU Radio](https://img.shields.io/badge/GNU%20Radio-3.10-blue)
![HackRF](https://img.shields.io/badge/Hardware-HackRF%20One-green)
![Language](https://img.shields.io/badge/Python-GNU%20Radio-yellow)
![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux-lightgrey)
![License](https://img.shields.io/badge/License-MIT-success)

</p>

---

# Overview

This project implements complete SDR-based digital television transmitters for both **DVB-T** and **DVB-S2** standards.

Unlike simple SDR demonstrations that replay prerecorded IQ samples, this project generates **standards-compliant RF signals in real time** starting from an MPEG Transport Stream (MPEG-TS). The complete physical layer is implemented inside GNU Radio using the **gr-dtv** framework before being transmitted through **HackRF One**.

The project was developed to explore the architecture of modern digital broadcasting systems and gain practical experience with Software Defined Radio (SDR), Digital Signal Processing (DSP), and Forward Error Correction (FEC).

---

# ✨ Features

- ✔ DVB-T transmitter
- ✔ DVB-S2 transmitter
- ✔ GNU Radio Companion flowgraphs
- ✔ HackRF One support
- ✔ MPEG-TS transmission
- ✔ Real-time RF generation
- ✔ Configurable modulation and coding
- ✔ SDR-based architecture
- ✔ Compatible with commercial DVB receivers

---

# Project Architecture

```
               MPEG Transport Stream
                        │
                 Digital Processing
                        │
          Channel Coding / Interleaving
                        │
          Digital Modulation (QAM/APSK)
                        │
         Physical Layer Frame Generation
                        │
              IQ Sample Generation
                        │
                HackRF One SDR
                        │
                  RF Transmission
```

---

# DVB-S2 Flowgraph

The DVB-S2 transmitter implements the complete baseband processing chain.

```
File Source
      │
BB Header
      │
BB Scrambler
      │
BCH Encoder
      │
LDPC Encoder
      │
Bit Interleaver
      │
16APSK Modulator
      │
Physical Layer Framer
      │
Root Raised Cosine Filter
      │
HackRF One
```

### Configuration

| Parameter | Value |
|-----------|------:|
| Modulation | 16APSK |
| Code Rate | 9/10 |
| Roll-Off | 0.20 |
| Frame Type | Normal |
| Sample Rate | 10 MSPS |

---

# DVB-T Flowgraph

The DVB-T transmitter follows the ETSI EN 300 744 physical layer.

```
File Source
      │
Energy Dispersal
      │
Reed Solomon Encoder
      │
Convolutional Interleaver
      │
Inner Encoder
      │
Bit Interleaver
      │
Symbol Interleaver
      │
64-QAM Mapper
      │
Pilot Insertion
      │
OFDM Modulator
      │
Cyclic Prefix
      │
HackRF One
```

### Configuration

| Parameter | Value |
|-----------|------:|
| FFT Mode | 8K |
| Modulation | 64-QAM |
| Code Rate | 2/3 |
| Guard Interval | 1/32 |

---

# Technologies

| SDR | DSP | Broadcasting |
|-----|-----|--------------|
| HackRF One | GNU Radio | DVB-T |
| gr-osmosdr | DSP | DVB-S2 |
| gr-dtv | IQ Processing | MPEG-TS |
| Python | OFDM | APSK |

---

# Repository Structure

```
HackRF-One-DVB-S2-T2-Transceiver
│
├── dvbs2_tx.grc
├── dvbs2_rx.grc
├── dvbt_tx.grc
├── README.md
└── examples/
```

---

# Skills Demonstrated

- Software Defined Radio
- Digital Signal Processing
- GNU Radio
- RF Engineering
- DVB-T
- DVB-S2
- OFDM
- APSK
- QAM
- BCH Coding
- LDPC Coding
- Reed-Solomon Coding
- Convolutional Coding
- MPEG Transport Stream
- IQ Signal Processing
- Wireless Communications

---

# Hardware

- HackRF One
- GNU Radio 3.10
- gr-dtv
- gr-osmosdr
- Windows / Linux

---

# Future Improvements

- Live UDP MPEG-TS streaming
- Adaptive Coding and Modulation (ACM)
- DVB-S2X support
- PlutoSDR compatibility
- Automatic receiver synchronization

---

# License

This project is intended for research and educational purposes.

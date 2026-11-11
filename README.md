# Advanced Audio Coding & Psychoacoustic DSP Seminars

<div align="center">

[![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![DSP](https://img.shields.io/badge/Domain-Digital_Signal_Processing-15803d?style=for-the-badge)]()
[![University](https://img.shields.io/badge/TU_Ilmenau-Advanced_Audio_Coding-c026d3?style=for-the-badge)](https://www.tu-ilmenau.de/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)

**Technische Universität Ilmenau • Department of Electrical Engineering & Information Technology**  
*Graduate Course: Advanced Audio Coding (AAC / MP3 Signal Processing Architecture)*

</div>

---

## 📌 Overview

This repository contains the algorithmic implementations, mathematical derivations, and DSP pipelines developed across the four graduate seminars of the **Advanced Audio Coding** curriculum at TU Ilmenau (the historic birthplace of MP3 audio coding).

The work implements the end-to-end perceptual audio codec architecture: from time-frequency filter banks and Modified Discrete Cosine Transform (MDCT) to psychoacoustic masking models, non-uniform quantization, and bit allocation.

---

## 🎧 Perceptual Audio Codec Pipeline

```mermaid
graph LR
    classDef input fill:#eff6ff,stroke:#1e40af,stroke-width:2px;
    classDef filter fill:#f0fdf4,stroke:#15803d,stroke-width:2px;
    classDef psycho fill:#fefce8,stroke:#a16207,stroke-width:2px;
    classDef quant fill:#fdf2f8,stroke:#be185d,stroke-width:2px;

    PCM[Input PCM Audio<br/>44.1 kHz, 16-bit] --> FB[Polyphase Filter Bank /<br/>MDCT 50% Overlap]
    PCM --> PAM[Psychoacoustic Model<br/>ISO/IEC 11172-3]
    
    PAM --> SMR[Signal-to-Mask Ratio<br/>& Masking Thresholds]
    FB --> MDCT_COEFF[Spectral Frequency<br/>MDCT Coefficients]
    
    SMR & MDCT_COEFF --> QBA[Dynamic Bit Allocation &<br/>Non-Uniform Quantization]
    QBA --> BITSTREAM[Lossless Bitstream Packing<br/>Huffman / Entropy Encoding]

    class PCM input;
    class FB,MDCT_COEFF filter;
    class PAM,SMR psycho;
    class QBA,BITSTREAM quant;
```

---

## 📚 Seminar Curriculum Breakdown

### 🔬 Seminar 1: Quantization & Companding
- **Uniform vs. Non-Uniform Quantizers**: Implementation of mid-tread and mid-riser uniform quantizers.
- **Companding Laws ($\mu$-law / A-law)**: Logarithmic compression of high-dynamic range signals for telecommunications.
- **Signal-to-Quantization-Noise Ratio (SQNR)**: Empirical SQNR validation against theoretical limits ($6.02B + 1.76$ dB).

### 📡 Seminar 2: Sampling & Signal Reconstruction
- **Nyquist-Shannon Theorem**: Critical sampling, spectrum replication, and anti-aliasing filter design.
- **Interpolation & Decimation**: Multirate signal processing, polyphase decomposition, and spectral foldover elimination.

### 🎛️ Seminar 3: Filter Banks & Subband Coding
- **Quadrature Mirror Filters (QMF)**: Polyphase analysis and synthesis filter bank pairs.
- **Alias Cancellation**: Achieving Perfect Reconstruction (PR) under orthogonal and pseudo-QMF constraints.
- Code: [`Main.py`](audio-coding-seminars-master/Seminar%203/Main.py), [`functions.py`](audio-coding-seminars-master/Seminar%203/functions.py).

### 🎼 Seminar 4: MDCT & Psychoacoustic Masking
- **Modified Discrete Cosine Transform (MDCT)**: Overlapped block transform with 50% overlap.
- **Time-Domain Aliasing Cancellation (TDAC)**: Sine window and Kaiser-Bessel Derived (KBD) windows for critical subsampling.
- **Auditory Masking**: Simultaneous masking (tone-masking-noise and noise-masking-tone) and temporal masking.
- Code: [`MDCT.py`](audio-coding-seminars-master/Seminar%204%20/MDCT.py).

---

## 🚀 Getting Started

### Prerequisites
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scriptsctivate
pip install numpy scipy matplotlib
```

### Running Seminar 3 (Filter Banks):
```bash
cd "audio-coding-seminars-master/Seminar 3"
python Main.py
```

### Running Seminar 4 (MDCT & TDAC Analysis):
```bash
cd "audio-coding-seminars-master/Seminar 4 "
python MDCT.py
```

---

## 📬 Contact

- **Author**: Sayan Bhattacharya
- **Email**: [sayanpm17@gmail.com](mailto:sayanpm17@gmail.com)
- **LinkedIn**: [linkedin.com/in/snbhattacharya5](https://www.linkedin.com/in/snbhattacharya5/)

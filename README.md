# Ideal-Sampling

# VENKATESAN S (212223060296)

## Aim
The aim of this program is to demonstrate the concept of ideal sampling by discretizing a continuous signal at
regular intervals. It visualizes both the continuous signal and its corresponding discrete samples to illustrate the sampling process in signal processing.

## Tools required
Python: A versatile programming language used for scientific computing and signal processing. NumPy: A powerful numerical library in Python for performing array-based operations and mathematical computations. Matplotlib: A plotting library for generating high-quality graphs and visualizations of data, essentialfor demonstrating the sampling process.

## Program

#Impulse Sampling

import numpy as np

import matplotlib.pyplot as plt

from scipy.signal import resample

fs = 100

t = np.arange(0, 1, 1/fs) 

f = 5

signal = np.sin(2 * np.pi * f * t)

plt.figure(figsize=(10, 4))

plt.plot(t, signal, label='Continuous Signal')

plt.title('Continuous Signal (fs = 100 Hz)')

plt.xlabel('Time [s]')

plt.ylabel('Amplitude')

plt.grid(True)

plt.legend()

plt.show()

t_sampled = np.arange(0, 1, 1/fs)

signal_sampled = np.sin(2 * np.pi * f * t_sampled)

plt.figure(figsize=(10, 4))

plt.plot(t, signal, label='Continuous Signal', alpha=0.7)

plt.stem(t_sampled, signal_sampled, linefmt='r-', markerfmt='ro', basefmt='r-', label='Sampled Signal (fs = 100 Hz)')

plt.title('Sampling of Continuous Signal (fs = 100 Hz)')

plt.xlabel('Time [s]')

plt.ylabel('Amplitude')

plt.grid(True)

plt.legend()

plt.show()

reconstructed_signal = resample(signal_sampled, len(t))

plt.figure(figsize=(10, 4))

plt.plot(t, signal, label='Continuous Signal', alpha=0.7)

plt.plot(t, reconstructed_signal, 'r--', label='Reconstructed Signal (fs = 100 Hz)')

plt.title('Reconstruction of Sampled Signal (fs = 100 Hz)')

plt.xlabel('Time [s]')

plt.ylabel('Amplitude')

plt.grid(True)

plt.legend()

plt.show()

## Output Waveform

![image](https://github.com/user-attachments/assets/ea1267b7-d867-4a67-97d9-90861de85d29)

## Results
The results show two plots: the first displays a continuous sine wave with a 5 Hz frequency. The second plot illustrates the ideal sampling of the sine wave, where the samples (red dots) are taken at regular intervals (100 Hz sampling rate). The ideal samples perfectly match the continuous signal, with no distortion or aliasing, as the sampling rate is sufficiently high.

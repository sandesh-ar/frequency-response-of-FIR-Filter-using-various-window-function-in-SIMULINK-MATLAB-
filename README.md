# 📡 Frequency Response of FIR Filter using Various Window Functions in MATLAB  

## 📌 Overview  
This repository contains **MATLAB code and Simulink models** to analyze the **frequency response of FIR (Finite Impulse Response) filters** using different **windowing techniques**.  

The study explores how **different window functions** affect the performance of FIR filters in terms of **main lobe width and side lobe levels**, ultimately influencing the filter’s ability to remove **unwanted noise** and retain **essential signal components**.  

---

## 🎯 Objectives  
✅ **Design and analyze FIR filters** using different windowing techniques.  
✅ **Compare frequency responses** of various **low-pass and high-pass FIR filters**.  
✅ **Implement MATLAB scripts and Simulink models** to visualize filter behavior.  
✅ **Understand the impact of different window functions** on main and side lobes.  

---

## 🏗️ Methodology  

### 📌 **Filter Design in MATLAB**  
The project involves designing **FIR filters** using different **window functions** such as:  
✔ **Rectangular Window**  
✔ **Bartlett (Triangular) Window**  
✔ **Hamming Window**  
✔ **Hanning Window**  
✔ **Kaiser Window**  
---

## 📜 **MATLAB Code for FIR Filter Design**  
```matlab
clc;
clear all;
close all;
n=20; % Filter Order
fp=200; fs=600; f=1000;
wp=2*(fp/f);
ws=2*(fs/f);
wn=[wp,ws];

% Different Window Functions (Uncomment to choose)
% window=boxcar(n+1); % Rectangular Window
% window=bartlett(n+1);% Triangular Window
% window=hamming(n+1);% Hamming Window
% window=hanning(n+1);% Hanning Window
window=kaiser(n+1); % Kaiser Window

wn=2*(fp/fs);
b=fir1(n,wn,'high',window);
[H,w]=freqz(b,1);

subplot(2,1,1)
plot(w/pi, 20*log(abs(H)));
xlabel('Normalized Frequency');
ylabel('Magnitude (dB)');
title("Magnitude Response");

subplot(2,1,2)
plot(w/pi, angle(H));
xlabel('Normalized Frequency');
ylabel('Phase (Radians)');
title("Phase Response");
 ---
```
## 🎛️ Filter Types & Parameters  

### 🔹 High-Pass FIR Filter  
- **Response Type**: Highpass  
- **Design Method**: FIR, Equiripple  
- **Filter Order**: Minimum order  
- **Units**: Normalized (0 to 1)  
- **Stopband Edge Frequency**: `wstop = 0.2`  
- **Passband Edge Frequency**: `wpass = 0.5`  

### 🔹 Low-Pass FIR Filter  
- **Response Type**: Lowpass  
- **Design Method**: FIR, Equiripple  
- **Filter Order**: Minimum order  
- **Units**: Normalized (0 to 1)  
- **Passband Edge Frequency**: `wpass = 0.2`  
- **Stopband Edge Frequency**: `wstop = 0.5`  

---

## 🔬 Simulation in Simulink  

### 📊 Filtering High-Frequency Noise in Simulink  

#### 📌 **Signal Sources:**  
🔹 **Sine Wave Block**  
- **Frequency**: `75 Hz`  
- **Sample Time**: `1/1000`  
- **Samples Per Frame**: `50`  

🔹 **Random Source Block**  
- **Source Type**: `Uniform`  
- **Minimum**: `0`  
- **Maximum**: `4`  
- **Sample Time**: `1/1000`  
- **Samples Per Frame**: `50`  

🔹 **Add Block**  
- **Icon Shape**: `Rectangular`  
- **List of Signs**: `++`  

🔹 **Model Settings**  
- **Start Time**: `0 sec`  
- **Stop Time**: `5 sec`  
- **Type**: `Fixed-step`  
- **Solver**: `Discrete (No continuous states)`  

📷 **Simulink Model in Action**  
![Simulink Model](https://github.com/your-repo/FIR-Filter-MATLAB/blob/main/simulink_model.png?raw=true)  

---

## 📈 Results & Observations  

✔ **Kaiser window** provided the **best frequency response** with better **side lobe suppression**.  
✔ **Rectangular window** had the **largest side lobes**, causing **unwanted spectral leakage**.  
✔ **Hamming and Hanning windows** provided a good balance between **main lobe width and side lobe attenuation**.  
✔ **Simulink model effectively filtered high-frequency noise**, while retaining essential signal components.  

📷 **Comparison of Window Responses**  
![Comparison](https://github.com/your-repo/FIR-Filter-MATLAB/blob/main/comparison.png?raw=true)  

---

## ✅ Advantages of Different Window Functions  

| **Window Function** | **Main Lobe Width** | **Side Lobe Level** | **Use Case** |
|----------------|----------------|---------------|----------|
| **Rectangular** | Narrow | High | Basic Filtering |
| **Bartlett** | Wider than Rectangular | Moderate | Speech Processing |
| **Hamming** | Moderate | Low | Audio Signal Processing |
| **Hanning** | Moderate | Very Low | Image Processing |
| **Kaiser** | Adjustable | Very Low | Best for Noise Reduction |

---

## 🏁 Conclusion  

### 📌 **Key Takeaways:**  
🔹 **Kaiser Window** is ideal for **optimal filter performance** due to its adjustable **β (beta) parameter**.  
🔹 **Hamming and Hanning windows** provide a **good trade-off** between **main lobe width and side lobe suppression**.  
🔹 **Rectangular window** has the **worst side lobe attenuation**, making it unsuitable for high-precision filtering.  
🔹 **Simulink simulations confirm the effectiveness** of FIR filters in removing unwanted high-frequency noise.  

---

## 🚀 Future Work  

🔹 Implement **Adaptive FIR Filtering** for **real-time noise cancellation**.  
🔹 Explore **higher-order FIR designs** for **sharper frequency transitions**.  
🔹 Compare FIR filters with **IIR (Infinite Impulse Response) filters**.  

---
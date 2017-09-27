# IBM QX3

This document contains information about the IBM Q experience **ibmqx3** backend. 

## Contributors (alphabetical)
Baleegh Abdo, Vivekananda Adiga, Lev Bishop, Markus Brink, Nicholas Bronn, Jerry Chow, Antonio Córcoles, Andrew Cross, Jay M. Gambetta, Jose Chavez-Garcia, Jared Hertzberg, Oblesh Jinka, George Keefe, David McKay, Salvatore Olivadese, Jason Orcutt, Hanhee Paik, Jack Rohrs, Sami Rosenblatt, Jim Rozen, Martin Sandberg, Dongbing Shao, Sarah Sheldon, Firat Solgun, Maika Takita

## Status History 
This device went online June 2017.

## Device Specifications

The connectivity map for the CNOTS in this device is
```
coupling_map = {0:[1], 1: [2], 2: [3], 3: [14], 4: [3, 5], 6: [7, 11], 7: [10], 8: [7], 9: [8, 10], 11: [10], 12: [5, 11, 13], 13: [4, 14], 15: [0, 14]}
```
Where a: [b] means a CNOT with qubit a as control and b as target can be implemented.

The connectivity is provided by total 22 coplanar waveguide (CPW) "bus" resonators, each of which connects two qubits. The connectivity configuration is shown in the figure below; the colored dots indicate qubits, and the colored bars indicate CPW bus resonators. Three different resonant frequencies are used for the bus resonators. The white bars indicate the buses with a resonant frequency of 6.25 GHz, the grey bars 6.45 GHz, and the black bars 6.65 GHz.    

<img src="images/ibmqx3-bus.png?raw=true" width="750">

Each qubit has a dedicated CPW readout resonator attached (labeled as R) for control and readout. The following picture shows the chip layout.

<img src="images/ibmqx3-labeled.png?raw=true" width="320">

The following table shows some of the main experimental parameters for this device.

| Qubit| &omega;<sup>R</sup><sub>i</sub>/2&pi; (GHz)       | &omega;<sub>i</sub>/2&pi;  (GHz)| &delta;<sub>i</sub>/2&pi; (MHz) | &chi;/2&pi; (kHz)| &kappa;/2&pi; (kHz)|
|----|-------------|--------|-------|--------|-------|
| **Q0**  | 6.97422 | 5.2488 | -292.8    | 130 | 360 |
| **Q1**  | 6.86632 | 5.3795 | -291.0    | 155 | 520 |
| **Q2**  | 6.96126 | 5.2683 | -289.2    | 115 | 470 |
| **Q3**  | 6.87780 | 5.0665 | -294.0    | 100 | 410 |
| **Q4**  | 6.95389 | 4.9725 | -290.7    | 90  | 430 |
| **Q5**  | 6.85116 | 5.1427 | -286.0    | 100 | 520 |
| **Q6**  | 6.98277 | 5.2956 | -289.2    | 105 | 410 |
| **Q7**  | 6.85933 | 5.2490 | -298.4    | 135 | 540 |
| **Q8**  | 6.97074 | 5.0967 | -287.6    | 120 | 450 |
| **Q9**  | 6.87252 | 5.1463 | -297.6    | 135 | 480 |
| **Q10**  | 6.95874 | 5.0301 | -291.5   | 95  | 530 |
| **Q11**  | 6.87590 | 5.1068 | -290.7   | 105 | 620 |
| **Q12**  | 6.96597 | 4.9383 | -299.0   | 95  | 450 |
| **Q13**  | 6.86325 | 5.0807 | -289.8   | 115 | 480 |
| **Q14**  | 6.97800 | 4.8442 | -296.0   | 80  | 390 |
| **Q15**  | 6.85608 | 5.0842 | -289.8   | 135 | 430 |

where &omega;<sup>R</sup><sub>i</sub> is the resonance frequency of the readout resonator, &omega;<sub>i</sub> = (E<sub>i</sub> - E<sub>0</sub>)/&hbar; is the qubit frequency with i={0...1,0...10,...,01...0,1...0}.  The anharmonicity (&delta;<sub>i</sub>) is the difference between the frequency of the 1-2 transition and the 0-1 transition. That is, it is given by &delta;<sub>i</sub> = (E<sub>2i</sub> - 2E<sub>i</sub>+ E<sub>0</sub> )/&hbar;.  &chi; is the qubit-cavity coupling strength, and and &kappa; is the cavity coupling to the environment (&kappa;).

Crosstalk, which we parameterize by &zeta;<sub>ij</sub> = (E<sub>i+j</sub> - E<sub>i</sub> - E<sub>j</sub> + E<sub>0</sub>)/&hbar; is measured using a **J**oint **A**mplification of **ZZ** (JAZZ) experiment, which is a modified **BI**linear **R**otational **D**ecoupling (BIRD) [^fn1]. The standard BIRD sequence used in nuclear magnetic resonance (NMR) is a Ramsey experiment on one qubit, with echo pulses on both the measured qubit (Q<sub>i</sub>) and the coupled qubit (Q<sub>j</sub>).  In the JAZZ experiment, this sequence is performed twice for each initial state of the coupled qubit. Additionally, the phase of the final &pi;/2-rotation is varied in order to detect an oscillating signal. &zeta;<sub>ij</sub> is equal to the frequency difference found between the two experiments.  The JAZZ experiment is shown in the figure below, and the measurements of all &zeta;<sub>ij</sub> are in the following table.  The GD pulse notation is defined below in the Gate Specification section.

[^fn1]: J.R. Garbow, D.P. Weitekamp, A. Pines, Bilinear rotation decoupling of homonuclear scalar interactions, *Chemical Physics Letters*, Volume 93, Issue 5, 1982, Pages 504-509.

<img src="images/zz_sequence.png?raw=true" width="400">

In the crosstalk matrix, the error bar is less than 1 kHz for all &zeta;<sub>ij</sub> and a dash indicates an interaction strength for that pair < 5 kHz.

| &zeta;<sub>ij</sub>/2&pi; (kHz) | Q0 | Q1 | Q2 | Q3 | Q4 | Q5 | Q6 | Q7 | Q8 | Q9 | Q10 | Q11 | Q12 | Q13 | Q14 | Q15 |
|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|
| **Q0** | | -46 | - | - |	- | - | - | - | - | - | - | - | - | - | - | -62 |
| **Q1** | -46 | | -70 | - | - | - | - | - | - | - | - | - | - | - | - | - |
| **Q2** | - | -74 | | -101 | - | - | - | - | - | - | - | - | - | - | - | -52 |
| **Q3** | - | - | -98 | | -31 | - | - | - | - | - | - | - | - | - | -57 | - |
| **Q4** | - | - | - | -34 | | -59 | - | - | - | - | - | - | - | -25 | - | - |
| **Q5** | - | - | - | - | -62 | | -75 | - | - | - | - | - | -53 | - | - | - |
| **Q6** | - | - | - | - | - | -74 | | -60 | - | - | - | -63 | - | - | - | - |
| **Q7** | - | - | - | - | - | - | -60 | | -64 | - | -78 | - | - | - | - | - |
| **Q8** | - | - | - | - | - | - | - | -65 | | -22 | - | - | - | - | - | - |
| **Q9** | - | - | - | - | - | - | - | - | -22 | | -39 | - | - | - | - | - |
| **Q10** | - | - | - | - | - | - | - | -77 | - | -37 | | -43 | - | - | - | - |
| **Q11** | - | - | - | - | - | - | -63 | - | - | - | -41 | | -53 | - | - | - |
| **Q12** | - | - | - | - | - | -55 | - | - | - | - | - | -53 | | -46 | - | - |
| **Q13** | - | - | - | - | -26 | - | - | - | - | - | - | - | -46 | | -96 | - |
| **Q14** | - | - | - | -58 | - | - | - | - | - | - | - | - | - | -95 | | -109 |
| **Q15** | -66 | - | -53 | - | - | - | - | - | - | - | - | - | - | - | -111 | 


The relaxation (T<sub>1</sub>) and coherence (T<sub>2</sub>) times for each qubit are given in the following table. T<sub>1</sub> is measured with an inversion recovery experiment, and T<sub>2</sub> is measured with a Hahn echo experiment.  These values are averaged over 50 measurements each for T<sub>1</sub> and 30 measurements for T<sub>2</sub>, performed over one week. The numbers in parentheses are standard errors of the mean.

| Qubit | T<sub>1</sub> (&mu;s) | T<sub>2</sub> (&mu;s)|
|----|----|----|
| **Q0** | 39.85 (0.69) | 34.97 (0.55) |
| **Q1** | 33.03 (0.31) | 60.63 (1.61) |
| **Q2** | 44.58 (0.76) | 48.79 (1.05) |
| **Q3** | 52.9 (0.66) | 77.8 (2.05) |
| **Q4** | 42.44 (0.48) | 78.74 (1.18) |
| **Q5** | 46.4 (0.91) | 76.89 (2.07) |
| **Q6** | 42.8 (0.7) | 28.96 (0.46) |
| **Q7** | 33.07 (0.54) | 50.53 (1.16) |
| **Q8** | 45.99 (0.67) | 72.51 (1.41) |
| **Q9** | 43.59 (0.61) | 69.14 (1.59) |
| **Q10** | 51.7 (0.99) | 70.93 (2.4) |
| **Q11** | 47.52 (0.69) | 54.33 (1.02) |
| **Q12** | 25.24 (0.31) | 32.63 (1.09) |
| **Q13** | 45.94 (0.49) | 61.26 (0.99) |
| **Q14** | 49.78 (0.79) | 43.04 (0.94) |
| **Q15** | 36.93 (1.81) | 45.72 (1.86) |


## Experimental Setup
The following cartoon shows a depiction of the device I/O microwave setup. We acknowledge MIT-Lincoln lab for providing the traveling-wave parametric amplifiers (TWPA) for this system.   

<img src="images/ibmqx3-expsetup.png?raw=true" width="400">

## Gate Specification

 
<img src="images/gatedef_U1U2U3_CNOT.png?raw=true" width="320">

A frame change (FC) is equivalent to applying a virtual *Z*-gate in software, where *Z*(&theta;)=FC(-&theta;). Gaussian derivative (GD) and Gaussian flattop (GF) pulses are defined with amplitude and angle parameters.

All the GD have a gate time of 80 ns, and the gate times for all GF pulses used in CX gates are given in the table below. There is an additional buffer of 10 ns after each GD or GF pulse. 

| CX Gate | GF Gate Time (ns) |
|----|----|
| **CX0_1**   | 209 |
| **CX1_2**   | 260 |
| **CX2_3**   | 230 |
| **CX3_14**  | 348 |
| **CX4_3**   | 304 |
| **CX4_5**   | 310 |
| **CX6_7**   | 170 |
| **CX6_11**  | 174 |
| **CX7_10**  | 187 |
| **CX8_7**   | 265 |
| **CX9_8**   | 239 |
| **CX9_10**  | 283 |
| **CX11_10** | 196 |
| **CX12_5**  | 270 |
| **CX12_11** | 183 |
| **CX12_13** | 191 |
| **CX13_4**  | 240 |
| **CX13_14** | 205 |
| **CX15_0**  | 348 |
| **CX15_14** | 183 |


### Two-Qubit Gates

All currently calibrated two-qubit gates and their directions are defined in the coupling map, and are shown in the device picture below.  Generally, two-qubit gates are possible between neighboring qubits that are connected by a superconducting bus resonator.  The IBM Q experience uses the cross-resonance interaction as the basis for the CX-gate.  This interaction is stronger when choosing the qubit with higher frequency to be the control qubit and the lower frequency qubit to be the target, so the frequencies of the qubits determines the direction of the gate.  There are some exceptions to the rule of high frequency control/low frequency target: the gate direction must be reversed if the higher levels of the control qubit are degenerate with the target qubit, or if either qubit is coupled to a third (spectator) qubit that has the same frequency or a higher level with the same frequency as the target.  In two cases on the QX3, no gate is possible between neighboring qubits because of degeneracies with spectator qubits that prevent the gate from working in either direction.  

<img src="images/ibmqx3-connections.png?raw=true" height="600">

Reported gate errors are measured using simultaneous randomized benchmarking (RB)[^fn2]. RB gives the average error per Clifford gate, which we convert to error per gate according to the set of primitive gates used on QX3.

[^fn2]: Jay M. Gambetta, A. D. Córcoles, S. T. Merkel, B. R. Johnson, John A. Smolin, Jerry M. Chow, Colm A. Ryan, Chad Rigetti, S. Poletto, Thomas A. Ohki, Mark B. Ketchen, and M. Steffen, Characterization of Addressability by Simultaneous Randomized Benchmarking, Phys. Rev. Lett. 109, 240504.

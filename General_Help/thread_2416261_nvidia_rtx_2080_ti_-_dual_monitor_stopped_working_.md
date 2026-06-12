---
title: "nvidia rtx 2080 ti - dual monitor stopped working -  smi driver not loaded - ubuntu 1"
date: 2019-04-08
forum: General Help
---

### Post by gerdhe on 2019-04-08
One day booting my PC I noticed that only one out of two monitors  displayed the signal/data from the PC. Switching cable, ports and  rebooting I realized that every of the three display ports of my trx  2080 ti were working fine but not at the same time. At maximum one  port/display shows the PC's output data. Further when calling nvidia-smi  I had the following result: "NVIDIA-SMI has failed because it couldn't  communicate with the NVIDIA driver. Make sure that the latest NVIDIA  driver is installed and running."
Going to "settings"->about I found out that the Graphics are managed  by "llvmpipe (LLVM 7.0, 256 bits)". Seems to be the fallback variant of  the Mesa 3D graphics library when no GPU driver is available. Ubuntu  18.04.2 is currently installed on my machine.
Reinstalling the NVIDIA driver several times and using different  methods (e.g. by executing run_file {NVIDIA Driver, CUDA 10.0 including  driver installation}, using the graphics driver ppa from Ubuntu, .deb  packages for CUDA 10.0 and CUDA 10.1 including driver installation) did  not solve the problem. 
After removing the old driver and re-installing the latest versions of  the driver (418 and 410) I will get always the same message when  executing nvidia-smi:
"NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA  driver. Make sure that the latest NVIDIA driver is installed and  running." Further, only one monitor works while the other does not a  signal.
I also tried another GTX graphic card (different model) and got the same issue.
The strange thing is, that I did not change anything on my system when  problem has occurred the first time, besides some regular Ubuntu  updates. Could those have been affected the NVIDIA driver?

---

### Post by gerdhe on 2019-04-08
In meantime I have found out that my cc and c++ refer to clang-8 and clang++-8. I used the update alternatives in order to clang the default compiler. I thought that maybe that has caused the issue. I changed the update alternatives of cc and c++ to refer to gcc-7 and g++-7. Then I removed Cuda and Nvidia with purge and reinstalled Cuda 10.0 based on the network .deb file. Calling nvidia-smi after that lead to the correct result. I think the problem has been originally caused by cc and c++ referring to Clang.

---


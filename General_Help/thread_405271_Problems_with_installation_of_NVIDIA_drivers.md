---
title: "Problems with installation of NVIDIA drivers"
date: 2007-04-09
forum: General Help
---

### Post by Soopeli on 2007-04-09
I'm using Linux Mint 2.2 (Ubuntu 6.10) and I have M2N8-VMX motherboard with all kinds of not-working integrated peripherals :) This motherboard has an integrated GeForce 6100 GPU, which works only with Linux Mint.

I have followed tseliot's guide in UDSF for installing NVIDIA drivers, primarily Method 1 for offline installation, still with no result. When I restart X after all procedures, the screen stays blank. The installation is a bit tricky, because my PC can't be connected to the Internet because the integrated network adapter doesn't work (at least yet). I can download all necessary files with other computer though, and transfer them with a USB memory to the Linux computer. Is there a way to try Method 2 without direct connection to the Net? I have tried to install Nvidia's newest drivers, but the installer says that "No precompiled kernel interface was found to match your kernel; would you like the installer to download a kernel interface for your kernel from the NVIDIA ftp site? (Yes/No). I replied No, and then followed "You do not appear to have libc header files installed on your system. Please install your distribution's libc development package."

So what are these header files and how can I install them?

---

### Post by useResa on 2007-04-10
What I understand from you description is that you are missing the libc6-dev package.
You can install these by issuing the following command in the terminal (Applications --> Accessories --> Terminal) ```
sudo apt-get install libc6-dev
```
Or by using Synaptic and search for the libc6-dev package

---

### Post by jubjubrsx on 2007-04-10
considering you dont have internet access pop your ubuntu cd back in do a search for libc and u can isntall the .deb package there then try to install the nvidia drivers :D:KS

but in realistic terms...get your nic working before anything else is what i would say then you can just download automatix and have that do the work for you /cheers!

---

### Post by compiledkernel on 2007-04-10
Pop your CD back in, and Read away. 

[https://help.ubuntu.com/community/NvidiaTroubleshooting](https://help.ubuntu.com/community/NvidiaTroubleshooting)
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Automatix will likely not solve your problems, and could possibly cause your system to break further if your not careful.

---

### Post by Soopeli on 2007-04-11
Thanks very much for advice. I was wondering, how should I apply Method 2 (ie. installing Nvidia's newest drivers) without direct internet connection? Which files should I download, if I haven't installed anything else after Linux installation? If I'm using Linux Mint with kernel 2.6.17-10-generic, should I install the following files:

libc6
nvidia-glx_1.0.8776+2.6.17.7-11.2_i386.deb
nvidia-kernel-common_20051028+1ubuntu7_all.deb
linux-generic_2.6.17.11_i386.deb
linux-headers-2.6.17-10-generic_2.6.17.1-10.34_i386.deb
linux-restricted-modules-2.6.17-10-generic_2.6.17.7-10.1_i38.deb

Anything else?

Does it matter, that some files have 2.6.17.11, although my kernel is 2.6.17.10?

Thanks for help!

---


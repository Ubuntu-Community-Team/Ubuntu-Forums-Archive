---
title: "Nvidia drivers -- how to get, and keep"
date: 2024-01-27
forum: General Help
---

### Post by ericaltendorf on 2024-01-27
Background:  I have a threadripper workstation with dual Nvidia 3090's which have been running vLLM models in docker successfully for a few weeks now.  Today I noticed the clients calling the docker service were erroring out.  I went to the workstation and the screen was blank.  I ssh'd in and could see the vLLM processes and xorg were both at 100% CPU.  nvidia-smi couldn't communicate with the cards.  I could not stop the docker container so I force killed all the processes.  I figured a reboot would be in order, and so before doing that I did an apt update & upgrade.  Soft reboot didn't succeed so I did a hardware reset.

Upon reboot, graphics have fallen back to safe mode (1024x768), nvidia-smi still says "NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running."

At this point I'm primarily focused on getting the system up and running again, rather than debugging what caused it to seize up -- I can do that if it happens again.

Other system info:

$ inxi -G
Graphics:
  Device-1: NVIDIA GA102 [GeForce RTX 3090] driver: N/A
  Device-2: NVIDIA GA102 [GeForce RTX 3090] driver: N/A
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: nouveau,vesa
    unloaded: fbdev,modesetting gpu: N/A resolution: 1024x768~76Hz
  OpenGL: renderer: llvmpipe (LLVM 15.0.7 256 bits)
    v: 4.5 Mesa 23.0.4-0ubuntu1~22.04.1

$ apt list nvidia-driver-* --installed
Listing... Done
nvidia-driver-530/unknown,now 530.30.02-0ubuntu1 amd64 [installed,automatic]

$ uname -a
Linux ######## 6.5.0-15-generic #15~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Fri Jan 12 18:54:30 UTC 2 x86_64 x86_64 x86_64 GNU/Linux


I did see this thread: [https://ubuntuforums.org/showthread.php?t=2489174](https://ubuntuforums.org/showthread.php?t=2489174) and I can remove the apt drivers and reinstall them, but I don't quite understand why or what's going on here, or how to install the drivers such that they won't get borked on another apt upgrade.

thanks for any tips,

eric

---

### Post by MAFoElffen on 2024-01-27
I was the one that helped with that... Since then, some other things recently came into being challenges after that...

See where your kernel upgraded to the 6.5.0 series? And you are on Ubuntu 22.04.3 right?

Ubuntu 22.04.3 is on gcc and g++ version 11.4. The 6.5.0 kernel series was compiled with gcc-12. So when it goes to build the NVidia kernel modules, the modules fail to build, because they are different compiler versions.

First uninstall your nvidia driver so that dpkg starts working again...
```

sudo apt remove --purge nvidia-driver-530

```
Then follow the directions I wrote up here (top half of post) to install gcc-12 and g++-12:
[https://ubuntuforums.org/showthread.php?t=2494273&p=14175164#post14175164](https://ubuntuforums.org/showthread.php?t=2494273&p=14175164#post14175164)

Re-install your driver
```

sudo apt install --yes nvidia-driver-530
sudo reboot

```
HINT: What about nvidia-driver-535? It is considered as stable now...

Thinking out loud:
I came up with that work-around, but I guess I "should" really file a bug report at Launchpad recommending that they push through gcc-12 through updates as the new default compiler for 22.04.3. That would solve these issues hitting graphics drivers, VirtualBox, WiFi drivers, and others hitting this module build issue with the 6.5.0 series kernels we are using now... I need to get around to that.

---

### Post by ericaltendorf on 2024-01-27
Wow, thanks for all the info!

FWIW, I think that's a typo in your first code block (s/apt install remove/apt remove/)

And for me, I was stuck for a bit trying to install nvidia-driver-530 and getting error messages, but 535 worked.  So I'm not sure which driver versions match which compiler versions, but for me I got 535 working with gcc 12.3.0.

---

### Post by MAFoElffen on 2024-01-28
Thank you. Yes. (dang) Corrected my typo. LOL

---


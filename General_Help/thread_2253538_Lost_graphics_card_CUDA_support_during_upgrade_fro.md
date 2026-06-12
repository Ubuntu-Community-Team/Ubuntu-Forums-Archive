---
title: "Lost graphics card CUDA support during upgrade from 13.10 to 14.10"
date: 2014-11-20
forum: General Help
---

### Post by jdallara on 2014-11-20
Hello,

  Upgraded my system from Ubuntu 13.10 to 14.10 via 14.04 and my graphics card no longer shows as a usable GPU for my BOINC applications.  It was working fine when I was running 13.10.

Graphics: Nvidia GeForce 750Ti
Driver: 340.58
Ubuntu 14.10
Kernel: 3.16.0-24
M/B: ASUS Z97-M Plus

Thanks,
Jon.

---

### Post by jdallara on 2014-12-01
Need to install nvidia-modprobe,

---

### Post by quantumbb on 2015-09-28
I have the same problem. It occurred when updating the nvidia driver. legacy drivers (304.xx and earlier) work on some projects, but the latest one (346.xx) doesn't work on any of them.

---

### Post by jdallara on 2015-09-28
> **quantumbb said:**
> I have the same problem. It occurred when updating the nvidia driver. legacy drivers (304.xx and earlier) work on some projects, but the latest one (346.xx) doesn't work on any of them.

Some legacy cards won't work with the newer drivers.  Nvidia.com has a listing of which cards will work with which drivers.  I don't have the link right now but look under the drivers section for legacy support.

---

### Post by quantumbb on 2015-09-28
The legacy drivers will not work with the GPUgrid project. This is the project I wanted to run on my Linux PC. There may be a conflict somewhere among Ubuntu 14.10 and later, nvidia driver 346.xx, and BOINC 7.4.23.

---

### Post by jdallara on 2015-09-28
Sorry, through you were referring to legacy hardware.  I had problems with Ubuntu also.  Install the Nvidia driver via synaptic or your favorite manager.  Get the same driver from Nvidia.  Ctrl-Alt-F1 to get a terminal screen.  Shutdown the window manager.  Install the Nvidia driver that you downloaded.  Reboot.  There is a problem with the opencl library that is in the Ubuntu package in that it doesn't get installed or something like that and you can't install it after the fact (or something like that, can't remember right now).  You can't use the Nvidia driver installation on its own because Ubuntu doesn't like one of its libraries, but installing it afterwards installs the opencl library that Boinc needs.  After I switched to Linux Mint, I found I can install the drivers directly from Nvidia and bypass having to do the double install.  I'm running GPUGrid with driver 346.72 right at this moment.

---

### Post by quantumbb on 2015-09-29
thanks for the info

---

### Post by quantumbb on 2015-09-29
I am now running GPUgrid on my Ubuntu PC with the latest nvidia driver.

---


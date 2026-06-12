---
title: "Intel video card not installed during Distribution upgrade"
date: 2017-04-16
forum: General Help
---

### Post by checoimg on 2017-04-16
I upgraded my computer via TTY to 16.10 and now the XORG server has been kept back:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  xorg
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

I searched for xserver-xorg-video-intel and it is not installed. My login screen is with a smaller resolution than before the upgrade.

My basic question is if installing the _xserver__-__xorg__-video-intel_ package would solve the "kept back" of XORG and with it the Login screen resolution difference from the previous version of my system.

---

### Post by deadflowr on 2017-04-16
It would make sense if you installed 16.04 from the 16.04.2 point release.
It has the same xorg version as 16.10.
It's just named something else, something extra: something like xserver-xorg-video-intel-hwe-16.04

I'd run dpkg -l to see what xserver packages are installed, if any:
```
dpkg -l | grep xserver 
```

My two cents on it anyway...

---

### Post by checoimg on 2017-04-16
Hi, a question. What does the "hwe" stand for?

---

### Post by ajgreeny on 2017-04-16
hwe = Hardware enablement stack.
See [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) for details.

---

### Post by checoimg on 2017-04-17
I decided to manually install the package and the driver is in use. I checked with "lshw"

This is the output:

```
*-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 18
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:25 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:3050(size=8) memory:c0000-dffff
```

---


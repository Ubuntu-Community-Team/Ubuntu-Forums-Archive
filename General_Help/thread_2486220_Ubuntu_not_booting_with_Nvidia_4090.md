---
title: "Ubuntu not booting with Nvidia 4090"
date: 2023-04-23
forum: General Help
---

### Post by cdobrich on 2023-04-23
I cannot boot to Kubuntu Linux on USB, (or from disk) with my new installed Nvidia 4090 video card. Possibly related I am seeing weird boot-menu behavior?


Tried booting with a new USB bootable drive with Kubuntu 23.04. (Also tried loading from disk, but just loads blank screen, powered left on.)

Trying to boot from USB: From the BIOS boot-menu, I have tried several options. 1st I select the USB: UEFI, then my monitor display goes blank (but stays powered on). I am not prompted to "Try Kubuntu" or "Install Kubuntu". I am not able to edit the kernel mode settings. 


NOTE: I notice that one of my hard drives does not appear in the boot-menu options, except for a single time it randomly was listed on a power-off/re-try.



***That single time it appeared***, I selected USB: UEFI and I got some boot-up graphics. While trying to boot, I was prompted to enter my password the encrypted hard-drives. It flashed the Kubuntu logo, then went back to console text. It displayed this message:



```

nouveau 000:0a:00.0: unknown chipset (192000a1)
hid-generic 003:0D8C:0134.001: No inputs registered, leaving

```

It did nothing for a long time, and eventually I hit CTRL+ALT+DEL, which it responded to and reboot. After this single time, nothing else has worked. I am completely loss, please help?


System Info:
```

Processors: 24 × AMD Ryzen 9 5900X 12-Core Processor
Memory: 62.7 GiB of RAM
Graphics Processor / Video Card: MSI RTX 4090 GAMING TRIO 24G
Motherboard Manufacturer: Gigabyte Technology Co., Ltd.
Product Name: X570 AORUS ELITE WIFI

```

---

### Post by TheFu on 2023-04-25
Welcome to the bleeding edge.
Generally, nvidia has made it difficult for distros to directly include their drivers, so they don't.  That means people with really new GPUs, especially those that are expensive, are unlikely to have the F/LOSS driver support and they need to learn to work around the nvidia problems.  I think there are grub options to get passed the initial boot issues - nomemset?  Something like that. 

From a sub-optimal boot, at least some level of desktop should work (even if just VESA drivers are used), then it is possible to load the recommended nvidia drivers using the "Additional Drivers" tool - which should be in the menu somewhere.  

Back when I had nvidia GPUs, I always used 
```
sudo ubuntu-drivers autoinstall
```
to get the best drivers that Canonical had tested for the hardware and kernel on my machine.

I got tired of fighting with nvidia and switched to AMD GPUs, which do allow their proprietary drivers to be included with the kernel, just like intel has done for 10+ yrs.  Can't remember the last time I had any hassles since dumping nvidia.

---


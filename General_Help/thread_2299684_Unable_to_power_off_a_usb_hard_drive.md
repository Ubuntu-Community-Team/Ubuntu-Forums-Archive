---
title: "Unable to power off a usb hard drive"
date: 2015-10-20
forum: General Help
---

### Post by spacemen12 on 2015-10-20
Hi,
   I have a usb 3 external hard drive. Works great. It auto mount when I plug it in. There is two partition on the drive, one small fat 32, and the rest is a LUKS encrypted partition. I run 14.04 on 64 bits and unity interface.

   The problem is when I want to remove the drive it causes problem. If I "safely remove parent drive" or "Eject parent drive", they unmount, but  less  than a second later they auto mount again. Same behavior if  I "power off" the drive from disks program.

   I also try the remove the "auto mount" (from Disks, edit mount options), but I con only do it for the non encrypted partition. Even when the auto mount is off, it auto mounts after I shut it down or "safely remove parent drive".

   I  am reluctant to pull the plug while it is mounted, or trying to mount. The only solution I have is to shutdown the computer, unplug the drive and restart the computer. It should be simpler than that. Who knows the recipe?

Best regards,

---

### Post by tgalati4 on 2015-10-20
It's possible that there is a process that is trying to write to the drive.  Do you have any hard mounts in /etc/fstab?  It's possible that encryption causes this as well.  

There is a hot plug polling process that will automatically mount drives that runs every 2 seconds I believe.  It could be a firmware issue with the external drive.  You might need to modify the *udev* rules for that drive.  [http://askubuntu.com/questions/297412/how-do-i-make-udev-rules-work](http://askubuntu.com/questions/297412/how-do-i-make-udev-rules-work)

I have no clue as to what to set those rules to in your situation.

The other option is to use *acpitool* and shut down the power to that USB port during S3 sleep.  Put the machine to sleep then pull the drive.

---

### Post by stalkingwolf on 2015-10-20
try a different usb plug.  I have the same problem in mint13.   if i plug into the front plug it does the same thing.  i just wait til it reboots then shut it down again and it works .
the other thing is i plug into a hub that is plugged into the back of the computer.  it shuts right down.

---

### Post by spacemen12 on 2015-10-20
> **tgalati4 said:**
> 
It's possible that there is a process that is trying to write to the drive.

Unlikely, if it just automount, I can unmount it (usualy when it writes, it does not want to unmount until it is finished), and it will remount.

> **tgalati4 said:**
> 
Do you have any hard mounts in /etc/fstab?

No.

---

### Post by spacemen12 on 2015-10-20
> **stalkingwolf said:**
> try a different usb plug.  I have the same problem in mint13.   if i plug into the front plug it does the same thing.  i just wait til it reboots then shut it down again and it works .
the other thing is i plug into a hub that is plugged into the back of the computer.  it shuts right down.

Same behavior, irrespective of the plug in this case.

---

### Post by tgalati4 on 2015-10-21
Open a terminal:

```
sudo apt-get install acpitool
acpitool -w
```

---

### Post by mcduck on 2015-10-21
It could also be the drive itself. One of mine removable drives (out of 6) behaves this way. The only explanation I have is that the drive's controller itself is a bit overzealous about powering the drive & reconnecting again after being ejected. I've seen the same with some other drives over the years, always the ones with build-in fancy features (button for automatic backups, built-in encryption or anything like that.).

What I usually do is just eject the drive and unplug it during the short time when it's actually powered down and the power led on the drive is not lit. Seems to be fine this far, but you need to be quick.

---

### Post by spacemen12 on 2015-10-22
> **tgalati4 said:**
> Open a terminal:

```
sudo apt-get install acpitool
acpitool -w
```

   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. BR20	  S3	*disabled  pci:0000:00:1e.0
  2. EUSB	  S4	*enabled   pci:0000:00:1d.0
  3. USBE	  S4	*enabled   pci:0000:00:1a.0
  4. PEX0	  S4	*disabled  pci:0000:00:1c.0
  5. PEX1	  S4	*disabled  pci:0000:00:1c.1
  6. PEX2	  S4	*disabled  pci:0000:00:1c.2
  7. PEX3	  S4	*disabled
  8. PEX4	  S4	*disabled
  9. PEX5	  S4	*disabled
  10. PEX6	  S4	*disabled
  11. PEX7	  S4	*disabled
  12. GBE	  S4	*enabled   pci:0000:00:19.0
  13. NPE1	  S4	*disabled  pci:0000:00:01.0
  14. NPE2	  S4	*disabled
  15. NPE3	  S4	*disabled  pci:0000:00:02.0
  16. NPE4	  S4	*disabled
  17. NPE5	  S4	*disabled
  18. NPE6	  S4	*disabled
  19. NPE7	  S4	*disabled  pci:0000:00:03.0
  20. NPE8	  S4	*disabled
  21. NPE9	  S4	*disabled
  22. NPEA	  S4	*disabled
  23. PWRB	  S3	*enabled

---

### Post by tgalati4 on 2015-10-22
Plug in the drive and post:

```
lsusb
lspci
```

---

### Post by spacemen12 on 2015-10-23
Thanks, see below for the output (long)

> **tgalati4 said:**
> 

```
lsusb

```

Bus 002 Device 006: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 002 Device 005: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 004: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 0bc2:a0a1 Seagate RSS LLC 
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

> **tgalati4 said:**
> 
```

lspci
```

00:00.0 Host bridge: Intel Corporation Xeon E5/Core i7 DMI2 (rev 07)
00:01.0 PCI bridge: Intel Corporation Xeon E5/Core i7 IIO PCI Express Root Port 1a (rev 07)
00:02.0 PCI bridge: Intel Corporation Xeon E5/Core i7 IIO PCI Express Root Port 2a (rev 07)
00:03.0 PCI bridge: Intel Corporation Xeon E5/Core i7 IIO PCI Express Root Port 3a in PCI Express Mode (rev 07)
00:05.0 System peripheral: Intel Corporation Xeon E5/Core i7 Address Map, VTd_Misc, System Management (rev 07)
00:05.2 System peripheral: Intel Corporation Xeon E5/Core i7 Control Status and Global Errors (rev 07)
00:05.4 PIC: Intel Corporation Xeon E5/Core i7 I/O APIC (rev 07)
00:11.0 PCI bridge: Intel Corporation C600/X79 series chipset PCI Express Virtual Root Port (rev 06)
00:16.0 Communication controller: Intel Corporation C600/X79 series chipset MEI Controller #1 (rev 05)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 06)
00:1a.0 USB controller: Intel Corporation C600/X79 series chipset USB2 Enhanced Host Controller #2 (rev 06)
00:1b.0 Audio device: Intel Corporation C600/X79 series chipset High Definition Audio Controller (rev 06)
00:1c.0 PCI bridge: Intel Corporation C600/X79 series chipset PCI Express Root Port 1 (rev b6)
00:1c.1 PCI bridge: Intel Corporation C600/X79 series chipset PCI Express Root Port 2 (rev b6)
00:1c.2 PCI bridge: Intel Corporation C600/X79 series chipset PCI Express Root Port 3 (rev b6)
00:1d.0 USB controller: Intel Corporation C600/X79 series chipset USB2 Enhanced Host Controller #1 (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation C600/X79 series chipset LPC Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation C600/X79 series chipset 6-Port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation C600/X79 series chipset SMBus Host Controller (rev 06)
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
02:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio [Radeon HD 6400 Series]
06:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
07:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
ff:08.0 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link 0 (rev 07)
ff:08.3 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link Reut 0 (rev 07)
ff:08.4 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link Reut 0 (rev 07)
ff:09.0 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link 1 (rev 07)
ff:09.3 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link Reut 1 (rev 07)
ff:09.4 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link Reut 1 (rev 07)
ff:0a.0 System peripheral: Intel Corporation Xeon E5/Core i7 Power Control Unit 0 (rev 07)
ff:0a.1 System peripheral: Intel Corporation Xeon E5/Core i7 Power Control Unit 1 (rev 07)
ff:0a.2 System peripheral: Intel Corporation Xeon E5/Core i7 Power Control Unit 2 (rev 07)
ff:0a.3 System peripheral: Intel Corporation Xeon E5/Core i7 Power Control Unit 3 (rev 07)
ff:0b.0 System peripheral: Intel Corporation Xeon E5/Core i7 Interrupt Control Registers (rev 07)
ff:0b.3 System peripheral: Intel Corporation Xeon E5/Core i7 Semaphore and Scratchpad Configuration Registers (rev 07)
ff:0c.0 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 07)
ff:0c.1 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 07)
ff:0c.2 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 07)
ff:0c.6 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller System Address Decoder 0 (rev 07)
ff:0c.7 System peripheral: Intel Corporation Xeon E5/Core i7 System Address Decoder (rev 07)
ff:0d.0 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 07)
ff:0d.1 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 07)
ff:0d.2 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 07)
ff:0d.6 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller System Address Decoder 1 (rev 07)
ff:0e.0 System peripheral: Intel Corporation Xeon E5/Core i7 Processor Home Agent (rev 07)
ff:0e.1 Performance counters: Intel Corporation Xeon E5/Core i7 Processor Home Agent Performance Monitoring (rev 07)
ff:0f.0 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Registers (rev 07)
ff:0f.1 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller RAS Registers (rev 07)
ff:0f.2 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 0 (rev 07)
ff:0f.3 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 1 (rev 07)
ff:0f.4 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 2 (rev 07)
ff:0f.5 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 3 (rev 07)
ff:0f.6 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 4 (rev 07)
ff:10.0 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 0 (rev 07)
ff:10.1 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 1 (rev 07)
ff:10.2 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 0 (rev 07)
ff:10.3 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 1 (rev 07)
ff:10.4 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 2 (rev 07)
ff:10.5 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 3 (rev 07)
ff:10.6 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 2 (rev 07)
ff:10.7 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 3 (rev 07)
ff:11.0 System peripheral: Intel Corporation Xeon E5/Core i7 DDRIO (rev 07)
ff:13.0 System peripheral: Intel Corporation Xeon E5/Core i7 R2PCIe (rev 07)
ff:13.1 Performance counters: Intel Corporation Xeon E5/Core i7 Ring to PCI Express Performance Monitor (rev 07)
ff:13.4 Performance counters: Intel Corporation Xeon E5/Core i7 QuickPath Interconnect Agent Ring Registers (rev 07)
ff:13.5 Performance counters: Intel Corporation Xeon E5/Core i7 Ring to QuickPath Interconnect Link 0 Performance Monitor (rev 07)
ff:13.6 System peripheral: Intel Corporation Xeon E5/Core i7 Ring to QuickPath Interconnect Link 1 Performance Monitor (rev 07)

---

### Post by Skaperen on 2015-10-23
> **spacemen12 said:**
> I  am reluctant to pull the plug while it is mounted, or trying to mount. The only solution I have is to shutdown the computer, unplug the drive and restart the computer. It should be simpler than that. Who knows the recipe?

Best regards,

what i do is *re-mount* it in *read-only* mode, unplug it, then un-mount it. seems to work ok.

---

### Post by tgalati4 on 2015-10-23
Try removing power to device #2:

```
sudo acpitool -W 2
acpitool -w

```

Close any open applications, put the machine to sleep, pull the drive, wake up the machine.  To enable power during sleep, just repeat the command above--it is a toggle.

It could be a USB2 versus USB3 difference.  Perhaps put the disk drive in a USB2 enclosure and try it.

---

### Post by vanchope on 2015-12-14
I experience the same problem on Ubuntu 15.10. The issue with automatic reconnect of an external USB 3.0 drive could be related to the following long lasting bug which is still not fixed: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/792085](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/792085)

---

### Post by Yawanathan_Israel on 2015-12-16
Best thing to do is to unmount, once unmounted, Unplug the drive. This way you won't have any corruption issues.

Thanks
Yawanathan



> **spacemen12 said:**
> Hi,
   I have a usb 3 external hard drive. Works great. It auto mount when I plug it in. There is two partition on the drive, one small fat 32, and the rest is a LUKS encrypted partition. I run 14.04 on 64 bits and unity interface.

   The problem is when I want to remove the drive it causes problem. If I "safely remove parent drive" or "Eject parent drive", they unmount, but  less  than a second later they auto mount again. Same behavior if  I "power off" the drive from disks program.

   I also try the remove the "auto mount" (from Disks, edit mount options), but I con only do it for the non encrypted partition. Even when the auto mount is off, it auto mounts after I shut it down or "safely remove parent drive".

   I  am reluctant to pull the plug while it is mounted, or trying to mount. The only solution I have is to shutdown the computer, unplug the drive and restart the computer. It should be simpler than that. Who knows the recipe?

Best regards,

---


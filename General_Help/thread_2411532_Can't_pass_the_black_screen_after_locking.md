---
title: "Can't pass the black screen after locking"
date: 2019-01-31
forum: General Help
---

### Post by sebgondron on 2019-01-31
Hi everyone,

I have an issue since yesterday and I unfortunately don't see anything that could have caused it. After having locked the screen -- by myself or after 10 minutes of inactivity -- the screen stays completely black. There is not even a mouse icon. I cannot do anything and the login form is not appearing. The only thing I can do is to press the start button long enough to initiate a hard reboot.

Some information about my system.

```
uname -sa
Linux **** 4.15.0-44-generic #47-Ubuntu SMP Mon Jan 14 11:26:59 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
```

```
lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (rev 07)
00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 08)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 (rev 21)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #1 (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 9d13 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 (rev f1)
00:1d.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #9 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Device 9d4e (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (4) I219-V (rev 21)
01:00.0 Network controller: Intel Corporation Wireless 8265 / 8275 (rev 78)
3b:00.0 Non-Volatile memory controller: Toshiba America Info Systems Device 0116
```

Thanks a lot for helping me!

Best,
Seb

---

### Post by nickinrl on 2019-02-01
Sorry not a helpful reply but a also getting the same issue. After looking at the syslog I'm not seeing any errors at the time of lock or when I attempt to get back to the login screen. Are there any other logs that may help point to an issue?

```
Linux 4.15.0-44-generic #47-Ubuntu SMP Mon Jan 14 11:26:59 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
```

```
lshw -c video  *-display                 
       description: VGA compatible controller
       product: Iris Pro Graphics 580
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:125 memory:de000000-deffffff memory:c0000000-cfffffff ioport:f000(size=64) memory:c0000-dffff
```

```
lspci00:00.0 Host bridge: Intel Corporation Skylake Host Bridge/DRAM Registers (rev 0a)
00:02.0 VGA compatible controller: Intel Corporation Iris Pro Graphics 580 (rev 09)
00:08.0 System peripheral: Intel Corporation Skylake Gaussian Mixture Model
00:14.0 USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-H Thermal subsystem (rev 31)
00:16.0 Communication controller: Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
00:17.0 SATA controller: Intel Corporation Sunrise Point-H SATA Controller [AHCI mode] (rev 31)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #1 (rev f1)
00:1c.1 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #2 (rev f1)
00:1c.2 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #3 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-H LPC Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-H PMC (rev 31)
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
00:1f.4 SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (2) I219-LM (rev 31)
02:00.0 SD Host controller: O2 Micro, Inc. SD/MMC Card Reader Controller (rev 01)
03:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)
```

---

### Post by Impavidus on 2019-02-01
Have you tried switching back and forth between some virtual terminals? ctlr-alt-F3 then ctrl-alt-F7, or use some other function keys.

---

### Post by nickinrl on 2019-02-01
I have attempted that and did not get anything, had to hard shut down. Weird thing now is all is working and I'm not sure why.

---

### Post by sebgondron on 2019-02-05
Hi,

My problem was solved without me knowing really how. There has been an update for which I was needing to restart my computer. I had also read on the net that similar problems could be caused by a misconfiguration of gdm3 and that restarting the service and then hardrebooting solved it for some people. So I decided to took the opportunity of the update to run this command:

```
sudo service gdm3 restart
```

When I hardrebooted the computer, the problem was solved. I don't know what did the trick: the update, the restart of gdm3 or even something else.

Best regards,
Sébastien

---


---
title: "Workspace is not coming in full screen"
date: 2016-11-20
forum: General Help
---

### Post by albertspade on 2016-11-20
Hi my workspace is not coming in full screen. How to solve it?

---

### Post by oldrocker99 on 2016-11-20
Welcome to the forums!

What is your hardware? Please post the results of ```
lspci
```

---

### Post by Bucky Ball on 2016-11-21
Welcome. Solving it involves giving more detail than you have given. Did you just install? Have you installed a driver for your video card? Do you know what video card you are using? Have you updated the machine since install? Have you tried anything to fix this? Have you opened 'Display' and tried another resolution?

Try to include as much information as you can when posting for help else potential helpers will spend time which could be spent fixing your issue asking for basic information. :)

We don't need to know all of your hardware from the 'lspci' command and sift through your output to find the video (although the lspci output may come in useful at some point), so for the video, just post the output of this, please:

```
sudo lshw -C video
```

Use code tags. There is a (green) link for how in my signature at the bottom of this post.

---

### Post by albertspade on 2016-11-21
Here are my lspci results
adm@admin-desktop:~$ lspci
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:16.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset PT IDER Controller (rev 06)
00:16.3 Serial controller: Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82578DC Gigabit Network Connection (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
adm@admin-desktop:~$
```

---

### Post by albertspade on 2016-11-21
[COLOR=#000000]adm@admin-desktop:~$ [/COLOR]sudo lshw -C video
 ```
 *-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:fe000000-fe3fffff memory:d0000000-dfffffff ioport:f160(size=8)
```

---

### Post by wildmanne39 on 2016-11-21
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---


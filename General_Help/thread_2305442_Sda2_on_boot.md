---
title: "Sda2 on boot"
date: 2015-12-06
forum: General Help
---

### Post by Thugkitty on 2015-12-06
I was trying to install gpu drivers, and when i reset my computer i got this.. can this be fixed or do i need to reinstall the OS?

[ATTACH=CONFIG]265991[/ATTACH]

---

### Post by SlidingHorn on 2015-12-06
Not really somewhere I excel, however, I can get some information out of you that will help others...

To let them know about your hardware, please paste the output of the following in code tags in the thread (if you can't login, try going to a tty by pressing Ctrl+Alt+F1 and log in from there):

```
lspci -vnn | grep VGA -A 12
```

More info about the hardware:

```
sudo lshw -C display
```

Also, more information would be helpful in regard to which driver you installed, where you got it, etc.  Hopefully, with enough information, someone smarter than me will come by and be able to make heads or tails of your problem :)

---

### Post by grahammechanical on 2015-12-06
Does Ubuntu still load to a working desktop? Then what is the problem?

If you remove the proprietary video driver you will not see that file system check (fsck) message because it will be covered by a purple splash screen but the message will still be there. Linux is doing a file system check on the partition it is going to load Ubuntu from and then printing the result to the screen. That is all.

It seems that if we use an open source video driver we get a purple splash screen during loading and if we use a proprietary video driver we do not get the purple splash screen. And we see a few Linux messages. 

You might also see very briefly a Linux login prompt. It is for Ubuntu to log in so that it can load. Ubuntu runs on Linux.

I base my answer on my own experience by comparing the loading process of 2 installations of Xenial Xerus (16.04). One with an open source video driver and one with the proprietary Nvidia video driver.

Regards.

---

### Post by Thugkitty on 2015-12-06
> **SlidingHorn said:**
> Not really somewhere I excel, however, I can get some information out of you that will help others...

To let them know about your hardware, please paste the output of the following in code tags in the thread (if you can't login, try going to a tty by pressing Ctrl+Alt+F1 and log in from there):

```
lspci -vnn | grep VGA -A 12
```

More info about the hardware:

```
sudo lshw -C display
```

Also, more information would be helpful in regard to which driver you installed, where you got it, etc.  Hopefully, with enough information, someone smarter than me will come by and be able to make heads or tails of your problem :)


```
thugkitty@thugkitty-MS-7721:~$ lspci -vnn | grep VGA -A 12
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Richland [Radeon HD 8670D] [1002:990c] (prog-if 00 [VGA controller])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7721]
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at b0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=256]
    Memory at feb00000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci

00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller [1002:9902]
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7721]
    Flags: bus master, fast devsel, latency 0, IRQ 44
--
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=64

00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7809] (rev 11) (prog-if 10 [OHCI])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7721]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb4c000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 0 [1022:1400]
    Flags: fast devsel

00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 1 [1022:1401]
--
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Oland PRO [Radeon R7 240/340] [1002:6613] (prog-if 00 [VGA controller])
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:226b]
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at fea00000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at e000 [size=256]
    Expansion ROM at fea40000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci

01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series] [1002:aab0]
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:aab0]
    Flags: bus master, fast devsel, latency 0, IRQ 45


```



```
thugkitty@thugkitty-MS-7721:~$ sudo lshw -C display
[sudo] password for thugkitty: 
  *-display               
       description: VGA compatible controller
       product: Richland [Radeon HD 8670D]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:46 memory:b0000000-bfffffff ioport:f000(size=256) memory:feb00000-feb3ffff
  *-display
       description: VGA compatible controller
       product: Oland PRO [Radeon R7 240/340]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:47 memory:c0000000-cfffffff memory:fea00000-fea3ffff ioport:e000(size=256) memory:fea40000-fea5ffff


```

I got the driver from the the amd website. ```
 amd-driver-installer-15.30.1025-x86.x86_64.run 
```

The "Generate Distribution Specific Driver Package would not run, this is the error I was getting ```
 NOTE: If your system has logged the missing packages required for installation, install them in the order as per the log file to resolve package-dependency issues.
Check if system has the tools required for Packages Generation.
fglrx installation requires that the system have kernel headers.  /lib/modules/4.2.0-16-generic/build/include/linux/version.h cannot be found on this system.

To build RPM packages 'rpmbuild' software package is necessary. Please install it either from DVD or download from any website.
On Red Hat, please run commnad : sudo yum install rpm-build <we presume, you have RedHat registration. Otherwise create local repo from DVD> 
On SuSE, please run commnad: sudo zypper install rpm-build <we presume, you have DVD in CD drive>
Please look in to Installer Notes for further information

To build kernel modules of AMD, system needs Kernel-Development package to be installed
Please run command: sudo zypper install kernel-devel <we presume, you have DVD in the CD driver>

One or more tools required for Graphics Pacakges Generation are not found on the system. Recommended is to install the required tools for successful package generation.
Optionally, you can run commands to ignore these dependecies but end result may not be as expected. Not recommended

```

So i downloaded Synaptic Package Manager and downloaded ```
 Video driver for the AMD Radeon and FireGL graphics accelerators.

This package provides 2D display drivers
and hardware accelerated OpenGL for X11. 
```

Then i uninsatlled ```
 Video driver for the AMD Radeon and FireGL graphics accelerators 
``` so i could install ```
 Inastall Driver 15.30.1025 on X.Org 6.9 or later 64-bit 
```

Restarted my computer and then i got that error.

I can start Ubuntu but i need to use the Adcance start options.

---

### Post by Thugkitty on 2015-12-06
I have amd a-10 with a r7 240/340 and i was trying to get them to crossfire

---


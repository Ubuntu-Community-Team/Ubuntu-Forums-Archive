---
title: "I have to boot twice to get Ubuntu running"
date: 2015-04-24
forum: General Help
---

### Post by _sluimers_ on 2015-04-24
For some reason the first boot stopped working. I can't tell since when, because I did not have to boot for quite some time a while ago.

What happens is that for a brief moment the Ubuntu-orange square pops up (either grub's background or that of the unlock screen) and then my screen goes blank and my monitor turns off.

Booting up the second time works fine.

---

### Post by oldfred on 2015-04-24
With Vivid on my new system, it boots very fast, but it does turn off monitor, and just a few seconds later turns it back on. Something in the mode switching does not seem correct.

If not Vivid, does Ubuntu shutdown fully & normally?
Is system new UEFI with BIOS/CSM and system has to switch boot modes? Or default in UEFI is one and your install is the other?

---

### Post by _sluimers_ on 2015-04-27
I've had this problem since at least 14.10.
It shuts down fully.
This system has UEFI. Not sure it has BIOS/CSM? Not sure what you mean by the last question.

---

### Post by oldfred on 2015-04-27
If it is UEFI then it has CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

But depending on settings in UEFI and mode you have installed it may have to switch. 
UEFI & BIOS are not compatible and you have to totally reboot to change boot modes.

I would check UEFI settings. What brand/model computer, & what video chip?

---

### Post by _sluimers_ on 2015-05-03
Here's some screenshots of my UEFI

[http://i284.photobucket.com/albums/ll3/folatt/20150504_025913_zpskprgsdbd.jpg](http://i284.photobucket.com/albums/ll3/folatt/20150504_025913_zpskprgsdbd.jpg)
[http://i284.photobucket.com/albums/ll3/folatt/20150504_025952_zpssubecrdw.jpg](http://i284.photobucket.com/albums/ll3/folatt/20150504_025952_zpssubecrdw.jpg)
[http://i284.photobucket.com/albums/ll3/folatt/20150504_030017_zpsrp21loqw.jpg](http://i284.photobucket.com/albums/ll3/folatt/20150504_030017_zpsrp21loqw.jpg)

Output of ~$ sudo lshw -short

```

H/W path         Device     Class       Description
===================================================
                            system      Computer
/0                          bus         Motherboard
/0/0                        memory      9978MiB System memory
/0/1                        processor   AMD A8-3820 APU with Radeon(tm) HD Graphics
/0/100                      bridge      Family 12h Processor Root Complex
/0/100/2                    bridge      Family 12h Processor Root Port
/0/100/2/0                  display     GT218 [GeForce 210]
/0/100/2/0.1                multimedia  High Definition Audio Controller
/0/100/10                   bus         FCH USB XHCI Controller
/0/100/10/0      usb2       bus         xHCI Host Controller
/0/100/10/1      usb1       bus         xHCI Host Controller
/0/100/10/1/2               generic     LGE Android Phone
/0/100/10.1                 bus         FCH USB XHCI Controller
/0/100/10.1/0    usb4       bus         xHCI Host Controller
/0/100/10.1/1    usb3       bus         xHCI Host Controller
/0/100/10.1/1/1             input       USB Keyboard
/0/100/10.1/1/2             input       Wireless USB Device
/0/100/11                   storage     FCH SATA Controller [IDE mode]
/0/100/12                   bus         FCH USB OHCI Controller
/0/100/12/1      usb7       bus         OHCI PCI host controller
/0/100/12.2                 bus         FCH USB EHCI Controller
/0/100/12.2/1    usb5       bus         EHCI Host Controller
/0/100/13                   bus         FCH USB OHCI Controller
/0/100/13/1      usb8       bus         OHCI PCI host controller
/0/100/13.2                 bus         FCH USB EHCI Controller
/0/100/13.2/1    usb6       bus         EHCI Host Controller
/0/100/14                   bus         FCH SMBus Controller
/0/100/14.1                 storage     FCH IDE Controller
/0/100/14.2                 multimedia  FCH Azalia Controller
/0/100/14.3                 bridge      FCH LPC Bridge
/0/100/14.4                 bridge      FCH PCI Bridge
/0/100/14.5                 bus         FCH USB OHCI Controller
/0/100/14.5/1    usb9       bus         OHCI PCI host controller
/0/100/15                   bridge      Hudson PCI to PCI bridge (PCIE port 0)
/0/100/15.2                 bridge      Hudson PCI to PCI bridge (PCIE port 2)
/0/100/15.2/0               bus         VT6315 Series Firewire Controller
/0/100/15.3                 bridge      Hudson PCI to PCI bridge (PCIE port 3)
/0/100/15.3/0    eth0       network     RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
/0/101                      bridge      Family 12h/14h Processor Function 0
/0/102                      bridge      Family 12h/14h Processor Function 1
/0/103                      bridge      Family 12h/14h Processor Function 2
/0/104                      bridge      Family 12h/14h Processor Function 3
/0/105                      bridge      Family 12h/14h Processor Function 4
/0/106                      bridge      Family 12h/14h Processor Function 6
/0/107                      bridge      Family 12h/14h Processor Function 5
/0/108                      bridge      Family 12h/14h Processor Function 7
/0/2             scsi0      storage     
/0/2/0.0.0       /dev/sda   disk        250GB CT250BX100SSD1
/0/2/0.0.0/1     /dev/sda1  volume      243MiB Linux filesystem partition
/0/2/0.0.0/2     /dev/sda2  volume      232GiB Extended partition
/0/2/0.0.0/2/5   /dev/sda5  volume      232GiB Linux filesystem partition

```

Output of ~$inxi -Fx
```
System:    Host: rogier-desktop Kernel: 3.19.0-15-generic x86_64 (64 bit gcc: 4.9.2)
           Desktop: Unity 7.3.2 (Gtk 3.14.12-0ubuntu2) Distro: Ubuntu 15.04 vivid
Machine:   Mobo: ASRock model: A75 Pro4 Bios: American Megatrends v: P1.40 date: 06/21/2011
CPU:       Quad core AMD A8-3820 APU with Radeon HD Graphics (-MCP-) cache: 4096 KB
           flags: (lm nx sse sse2 sse3 sse4a svm) bmips: 19998
           clock speeds: max: 2500 MHz 1: 1200 MHz 2: 1200 MHz 3: 800 MHz 4: 1600 MHz
Graphics:  Card: NVIDIA GT218 [GeForce 210] bus-ID: 01:00.0
           Display Server: X.Org 1.17.1 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.0hz, 1920x1080@60.0hz
           GLX Renderer: Gallium 0.4 on NVA8 GLX Version: 3.0 Mesa 10.5.2 Direct Rendering: Yes
Audio:     Card-1 Advanced Micro Devices [AMD] FCH Azalia Controller driver: snd_hda_intel bus-ID: 00:14.2
           Card-2 NVIDIA High Definition Audio Controller driver: snd_hda_intel bus-ID: 01:00.1
           Sound: Advanced Linux Sound Architecture v: k3.19.0-15-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: c000 bus-ID: 05:00.0
           IF: eth0 state: up speed: 1000 Mbps duplex: full mac: 00:25:22:de:b5:09
Drives:    HDD Total Size: 250.1GB (30.9% used) ID-1: /dev/sda model: CT250BX100SSD1 size: 250.1GB temp: 26C
Partition: ID-1: / size: 220G used: 72G (35%) fs: ext4 dev: /dev/dm-1
           ID-2: /boot size: 236M used: 92M (42%) fs: ext2 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 32.9C mobo: N/A gpu: 45.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 205 Uptime: 34 min Memory: 1605.7/9978.3MB Init: systemd runlevel: 5 Gcc sys: 4.9.2
           Client: Shell (bash 4.3.301) inxi: 2.2.16 
```

---

### Post by oldfred on 2015-05-03
It looks like you only have legacy. As your UEFI setting says option ROM first which is the CSM or BIOS.

You also just show a /boot and this: /dev/dm-1
Is this a full drive LVM or LVM with encryption install?

With the option ROM first you may get it trying UEFI (even though you say CSM) and then it has to switch to the CSM mode?

Some other threads with Asrock.
 ASRock Z97
[http://www.phoronix.com/forums/showthread.php?102720-ASRock-Z97-Extreme6](http://www.phoronix.com/forums/showthread.php?102720-ASRock-Z97-Extreme6)
ubuntu 14.04 on asrock Z87 extreme 4 or pro 4 
[http://ubuntuforums.org/showthread.php?t=2216079](http://ubuntuforums.org/showthread.php?t=2216079)
Some have issues with Asrock and its asmedia ports
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)
AsRock Z77 Windows always reset to default
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order)

---

### Post by _sluimers_ on 2015-05-04
My /boot:
[http://i284.photobucket.com/albums/ll3/folatt/Screenshot%20from%202015-05-05%20033915_zpshcflkmnx.png](http://i284.photobucket.com/albums/ll3/folatt/Screenshot%20from%202015-05-05%20033915_zpshcflkmnx.png)

I don't know how to show /dev/dm-1.
It's LVM with encryption install.

---

### Post by oldfred on 2015-05-04
I still think somehow UEFI is trying to boot in UEFI mode and then has to reboot into BIOS boot mode?

UEFI and BIOS boot modes are not compatible and you have to totally reboot to switch boot modes.

---

### Post by tgalati4 on 2015-05-05
If it is an old hard disk, then the spindle will get sticky and require a couple of reboots to spin up to speed.  Post the SMART parameters of the disk drive.

```
sudo smartctl -a /dev/sda
```

---


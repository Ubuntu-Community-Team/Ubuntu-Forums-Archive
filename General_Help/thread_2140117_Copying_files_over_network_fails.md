---
title: "Copying files over network fails"
date: 2013-04-28
forum: General Help
---

### Post by Grand Puba on 2013-04-28
Hello,
I have a clean install of Ubuntu 13.04 on my PC. When I try to copy folders and files over my LAN from another PC running windows XP the copying process freezes randomly.
Sometimes it will copy a few KBs and sometimes a few MBs - completely random - but it always freezes. I tried all sorts of folders to make sure that the problem does not occur only in one specific folder. Also, say I have a 100 files in a folder, I mark all the files on the other computer (ctrl+a) and then ctril+c and ctrl+v on my PC, not all the files are copied! sometimes it copies 53 files, sometimes 89 but never all the files! These files are just word documents, nothing fancy. This problem did not exist on Ubuntu 12.10.

Please assist.
Thanks.

---

### Post by Mopar1973Man on 2013-04-28
Might be helpful to know what hardware there is in the machine. I'm a bit of noob too this all but I'm going to try and help the best I can. 

This should list out hardware on the machine.
```
sudo lshw
```

I'm sure someone else knows how to filter the results down better.

---

### Post by Grand Puba on 2013-04-28
Hi,

Here is the data from lshw -short:

H/W path        Device      Class          Description
======================================================
                            system         ()
/0                          bus            DP35DP
/0/0                        processor      Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
/0/0/1                      memory         4MiB L2 cache
/0/0/3                      memory         32KiB L1 cache
/0/2                        memory         32KiB L1 cache
/0/4                        memory         64KiB BIOS
/0/17                       memory         8GiB System Memory
/0/17/0                     memory         2GiB DIMM DDR2 Synchronous 800 MHz (1.2 ns)
/0/17/1                     memory         2GiB DIMM DDR2 Synchronous 800 MHz (1.2 ns)
/0/17/2                     memory         2GiB DIMM DDR2 Synchronous 800 MHz (1.2 ns)
/0/17/3                     memory         2GiB DIMM DDR2 Synchronous 800 MHz (1.2 ns)
/0/100                      bridge         82G33/G31/P35/P31 Express DRAM Controller
/0/100/1                    bridge         82G33/G31/P35/P31 Express PCI Express Root Port
/0/100/1/0                  display        G92 [GeForce 9800 GTX / 9800 GTX+]
/0/100/3                    communication  82G33/G31/P35/P31 Express MEI Controller
/0/100/19       eth0        network        82566DC-2 Gigabit Network Connection
/0/100/1a                   bus            82801I (ICH9 Family) USB UHCI Controller #4
/0/100/1a.1                 bus            82801I (ICH9 Family) USB UHCI Controller #5
/0/100/1a.2                 bus            82801I (ICH9 Family) USB UHCI Controller #6
/0/100/1a.7                 bus            82801I (ICH9 Family) USB2 EHCI Controller #2
/0/100/1b                   multimedia     82801I (ICH9 Family) HD Audio Controller
/0/100/1c                   bridge         82801I (ICH9 Family) PCI Express Port 1
/0/100/1c.1                 bridge         82801I (ICH9 Family) PCI Express Port 2
/0/100/1c.1/0               storage        88SE6101/6102 single-port PATA133 interface
/0/100/1c.2                 bridge         82801I (ICH9 Family) PCI Express Port 3
/0/100/1c.3                 bridge         82801I (ICH9 Family) PCI Express Port 4
/0/100/1c.4                 bridge         82801I (ICH9 Family) PCI Express Port 5
/0/100/1d                   bus            82801I (ICH9 Family) USB UHCI Controller #1
/0/100/1d.1                 bus            82801I (ICH9 Family) USB UHCI Controller #2
/0/100/1d.2                 bus            82801I (ICH9 Family) USB UHCI Controller #3
/0/100/1d.7                 bus            82801I (ICH9 Family) USB2 EHCI Controller #1
/0/100/1e                   bridge         82801 PCI Bridge
/0/100/1e/3                 bus            TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
/0/100/1f                   bridge         82801IR (ICH9R) LPC Interface Controller
/0/100/1f.2                 storage        82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA Controller [AHCI mode]
/0/100/1f.3                 bus            82801I (ICH9 Family) SMBus Controller
/0/1            scsi2       storage        
/0/1/0.0.0      /dev/sda    disk           320GB WDC WD3200AAKS-0
/0/1/0.0.0/1    /dev/sda1   volume         199MiB Windows FAT volume
/0/1/0.0.0/2    /dev/sda2   volume         297GiB Apple HFS+ partition
/0/3            scsi3       storage        
/0/3/0.0.0      /dev/sdb    disk           160GB WDC WD1600JS-61M
/0/3/0.0.0/1    /dev/sdb1   volume         141GiB EXT4 volume
/0/3/0.0.0/2    /dev/sdb2   volume         8120MiB Extended partition
/0/3/0.0.0/2/5  /dev/sdb5   volume         8120MiB Linux swap / Solaris partition
/0/5            scsi4       storage        
/0/5/0.0.0      /dev/sdc    disk           320GB WDC WD3200AAKS-0
/0/5/0.0.0/1    /dev/sdc1   volume         298GiB Windows NTFS volume
/0/6            scsi5       storage        
/0/6/0.0.0      /dev/cdrom  disk           DVDRAM GH24NS72



and data from lspci command as well:

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82G33/G31/P35/P31 Express MEI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G92 [GeForce 9800 GTX / 9800 GTX+] (rev a2)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101/6102 single-port PATA133 interface (rev b2)
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]


thanks.

---

### Post by Grand Puba on 2013-04-28
Bump.

Can anyone help with this issue?

Thanks.

---

### Post by Grand Puba on 2013-04-30
Does anyone have an idea of how to at least diagnose this issue?

Thanks.

---

### Post by Mopar1973Man on 2013-04-30
An idea is to research and see if there is a separate Linux driver for your WiFi hardware. I've had that same issue on my Toshiba Satellite Laptop then it corrected the problems on mine. But its a shot from the hip.

---

### Post by Grand Puba on 2013-05-01
Thanks for the reply Mopar.
I am connected through an ethernet cable not wifi but maybe the onboard LAN needs a new driver as well. Will try.

---

### Post by Grand Puba on 2013-05-01
Linux is crazy. I've downloaded the network driver from intel, compiled it, added it to the Kernel(!), assigned an IP address and IT WORKS!
For a power-user coming from Windows and Mac OS X, this was pretty radical... :D

MANY THANKS Mopar1973Man!

---


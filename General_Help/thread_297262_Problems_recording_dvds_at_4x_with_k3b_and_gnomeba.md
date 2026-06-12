---
title: "Problems recording dvds at 4x with k3b and gnomebaker"
date: 2006-11-10
forum: General Help
---

### Post by pedrofdmp on 2006-11-10
when i try to burn dvds at 4x with gnomebaker or k3b the recording speed ends up being 1x to 1.2x
during the recording the hdd led blinks from time to time (no heavy usage) and the cpu load goes from 20% to 60% (running some other applications at the same time)
i'm using Ubuntu 6.10
what can i do to burn at 4x ?

pedro@homepc:~$ cat /proc/ide/hda/model 
SAMSUNG SP0802N
pedro@homepc:~$ cat /proc/ide/hdb/model 
WDC WD80EB-28CGH2
pedro@homepc:~$ cat /proc/ide/hdc/model 
TSSTcorpDVD-ROM TS-H352A
pedro@homepc:~$ cat /proc/ide/hdd/model 
PLEXTOR DVDR PX-755A

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 156368016, start = 0
pedro@homepc:~$ sudo hdparm /dev/hdb

/dev/hdb:
 multcount    =  0 (off)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 15509/16/63, sectors = 15633072, start = 0
pedro@homepc:~$ sudo hdparm /dev/hdc

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
pedro@homepc:~$ sudo hdparm /dev/hdd

/dev/hdd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

00:00.0 Host bridge: VIA Technologies, Inc. KT880 Host Bridge (rev 80)
00:00.1 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:09.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x] (rev a1)

---

### Post by Zeroangel on 2007-01-18
I'm getting this problem as well and it's just started happening recently (K3B worked fine 3 days ago).

K3B outputs the IO Error message before burning, without supporting information.

When I run hdparm on the CD burner, it shows a few things like whether DMA is enabled. But also the error message:

HDIO_GETGEO failed: Inappropriate ioctl for device

I tried poking around on Google. And found a few things, but nothing has helped. For example I read that there might be a problem with readahead, so I tried disabling it using "sudo hdparm -A0 /dev/hdd" and I get an error message as well:

 setting drive read-lookahead to 0 (off)
 HDIO_DRIVE_CMD(setreadahead) failed: Input/output error


What's going on here?!

---------------
FYI: K3B "debugging output" says the following:

System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.5
QT Version:  3.3.6
Kernel:      2.6.17-10-generic
Devices
-----------------------
ATAPI DVD DD 2X16X4X16 G7Z9 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96R; RAW/R16; RAW/R96R; Restricted Overwrite]

HP CD-Writer+ 8200 1.0f (/dev/hdd, ) at  [CD-R; CD-RW; CD-ROM] [Error] [SAO; TAO; RAW; SAO/R96R; RAW/R96R]

---

### Post by Zeroangel on 2007-01-19
OK, I found a workaround, and that is to *not* use on the fly writing, but to have k3b write an image first.

Let me know if this works for you.

---


---
title: "Xubuntu DVD ISO burning problem"
date: 2007-03-10
forum: General Help
---

### Post by ohiopyle on 2007-03-10
I'm having some issues with xfburn and k3b in Xubuntu, I can get neither to burn an ISO to DVD. xfburn comes up with a generic error to use "cdrecord dev=help" .  k3b comes up with an error

```
:-( unable to WRITE@LBA=0h: Input/output error
:-( write failed: Input/output error
```

I'm not exactly sure where to go from here.  Any assistance would be appreciated.



```
ohiopyle@ohiopyle-desktop:~/Desktop$ cdrecord -scanbus dev=ATAPI
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.17-11-generic
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: 'ATAPI'
devname: 'ATAPI'
scsibus: -2 target: -2 lun: -2
Warning: Using ATA Packet interface.
Warning: The related Linux kernel interface code seems to be unmaintained.
Warning: There is absolutely NO DMA, operations thus are slow.
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus0:
        0,0,0     0) 'LITE-ON ' 'DVDRW LH-20A1H  ' 'LL05' Removable CD-ROM
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *

```

```
ohiopyle@ohiopyle-desktop:~/Desktop$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 11)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 11)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 11)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 11)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 11)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 11)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 11)
01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4600] (rev a3)
02:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
ohiopyle@ohiopyle-desktop:~/Desktop$ 

```

---

### Post by kerry_s on 2007-03-10
Looks like a permission problem, try launching as root->
press alt+F2 and type> gksu k3b

---

### Post by strabes on 2007-03-10
You have to be root when running any CD/DVD burning software. The command for KDE apps is "kdesu" not "gksu"

So you would run "kdesu k3b &" in a terminal. The "&" makes it run in the background e.g. allows you to keep working in the terminal.

---

### Post by kerry_s on 2007-03-10
> **strabes said:**
> You have to be root when running any CD/DVD burning software. The command for KDE apps is "kdesu" not "gksu"

So you would run "kdesu k3b &" in a terminal. The "&" makes it run in the background e.g. allows you to keep working in the terminal.

He's using Xubuntu, it might not have "kdesu", but i know for a fact it has "gksu" because it's part of GDM. I believe when i used k3b in xubuntu i had to change the /usr/share/applications/k3b.desktop to use "gksu" to run right. KDE apps usually don't take into account that they might be used in a different environment other than KDE.

---


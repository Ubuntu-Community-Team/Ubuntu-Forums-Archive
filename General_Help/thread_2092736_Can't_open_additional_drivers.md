---
title: "Can't open additional drivers"
date: 2012-12-08
forum: General Help
---

### Post by rafe101 on 2012-12-08
On my mythbuntu 12.04 I started getting choppy HD playback (separate issue) and I desperately want to try changing from the free video drivers to the proprietary ones to see if that helps me to be able to watch TV again, but I can't open the additional drivers menu.

I click on the link, watch it check for drivers as it always used to (and still does on the office computer), but then that finishes and . . . nothing.

Nothing happens after that. the actual window where I can see and pick the additional drivers never appears.

This is especially frustrating since HDTV has been unwatchable for about a month and no updates have either fixed that or allowed me to get back into the driver setup.

---

### Post by zenontherocks on 2012-12-15
Im having the same problem. For me it started when I tried installing wireless drivers through NDISWrapper using instructions from here: [http://undiff.com/2008/11/how-to-get-the-netgear-wn311t-to-work/](http://undiff.com/2008/11/how-to-get-the-netgear-wn311t-to-work/)

I followed the instructions to the letter but obviously something went wrong because my wireless drivers still don't work. So I tried opening the "additional drivers" program under System Settings, and it does exactly what is described in the OP.

It seems I need to undo the driver install and try again, but I have no idea how to do that and I can't seem to find instructions anywhere.

---

### Post by QIII on 2012-12-15
Can you give us some specs on your machine?

---

### Post by zenontherocks on 2012-12-17
I'm not sure specifically what you are asking for, as far as specs. Here is the output of "sudo lshw -short":

H/W path    Device       Class       Description
================================================
                         system      MS-7325 (To Be Filled By O.E.M.)
/0                       bus         MS-7325
/0/0                     memory      64KiB BIOS
/0/3                     processor   AMD Athlon(tm) 64 X2 Dual Core Processor 56
/0/3/5                   memory      128KiB L1 cache
/0/3/6                   memory      1MiB L2 cache
/0/2b                    memory      6GiB System Memory
/0/2b/0                  memory      2GiB DIMM DDR2 Synchronous
/0/2b/1                  memory      2GiB DIMM DDR2 Synchronous
/0/2b/2                  memory      DIMM [empty]
/0/2b/3                  memory      2GiB DIMM DDR2 Synchronous
/0/4                     memory      Memory controller
/0/1                     bridge      CK804 ISA Bridge
/0/1.1                   bus         CK804 SMBus
/0/2                     bus         CK804 USB Controller
/0/2.1                   bus         CK804 USB Controller
/0/5                     multimedia  CK804 AC'97 Audio Controller
/0/6                     storage     CK804 IDE
/0/7        scsi2        storage     CK804 Serial ATA Controller
/0/7/0      /dev/sda     disk        320GB ST3320613AS
/0/7/0/1    /dev/sda1    volume      298GiB Windows NTFS volume
/0/7/1      /dev/cdrom1  disk        CDDVDW SH-S203N
/0/8        scsi4        storage     CK804 Serial ATA Controller
/0/8/0      /dev/cdrom   disk        CDDVDW SH-S203N
/0/8/1      /dev/sdb     disk        320GB ST3320613AS
/0/8/1/1    /dev/sdb1    volume      476MiB EXT4 volume
/0/8/1/2    /dev/sdb2    volume      297GiB Extended partition
/0/8/1/2/5  /dev/sdb5    volume      13GiB Linux filesystem partition
/0/8/1/2/6  /dev/sdb6    volume      279GiB Linux filesystem partition
/0/8/1/2/7  /dev/sdb7    volume      3814MiB Linux swap / Solaris partition
/0/9                     bridge      CK804 PCI Bridge
/0/9/7                   network     88W8361 [TopDog] 802.11n Wireless
/0/a        eth0         bridge      CK804 Ethernet Controller
/0/b                     bridge      CK804 PCIE Bridge
/0/c                     bridge      CK804 PCIE Bridge
/0/d                     bridge      CK804 PCIE Bridge
/0/e                     bridge      CK804 PCIE Bridge
/0/e/0                   display     G94 [GeForce 9600 GT]
/0/100                   bridge      K8 [Athlon64/Opteron] HyperTransport Techno
/0/101                   bridge      K8 [Athlon64/Opteron] Address Map
/0/102                   bridge      K8 [Athlon64/Opteron] DRAM Controller
/0/103                   bridge      K8 [Athlon64/Opteron] Miscellaneous Control
/1          usb0         network     Ethernet interface

---

### Post by zenontherocks on 2012-12-17
Also, I am on plain Ubuntu. Not Mythbuntu like the OP. Not sure if that matters or not.

---

### Post by zenontherocks on 2012-12-18
Well I did a fresh format/install of Ubuntu 10.04, then retried the NDISWrapper and driver install, and everything appears to be functioning properly for me now. After messing around with 12.04 and 11.10 (to some extent), I really like 10.04 better anyway. It's simpler and it just works better.

Anyway, thought I'd follow up to say that I am no longer having this problem. Don't know about the OP though.

---


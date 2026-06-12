---
title: "Unable to burn CD since last kernel update ?"
date: 2005-08-21
forum: General Help
---

### Post by dovik on 2005-08-21
since few hours, i can't burn any CD.
(sorry for my poor english)

recently :

[list]
[*]burning CD : OK
[*]i decide to replace my CD burner (LG) by a DVD burner (Lite On)
[*]burning succed after hardware installation
[*]i install the "linux-386" update
[*]few hours after, HAL crash (no more CD auto mount)
[*]reboot
[*]UNABLE TO BURN CD !
[*]i install a better kernel for my AMD : "linux-k7"
[*]UNABLE TO BURN CD ANYWAY !
[/list]

i try to burn directly with cdrecord, and have some error like : *Cannot open SCSI driver*. 

i read */usr/share/doc/cdrecord/README.ATAPI.setup*.

and try this :

>     1. Become root, find out the virtual SCSI ID of your device, running:
    cdrecord dev=ATA: -scanbus

    2. Become root, setup cdrecord's environment - edit /etc/default/cdrecord:
    CDR_DEVICE=cdrw
    cdrw=ATA:3,0,0 12 30m
    (...)
    3. That's it, 'cdrecord -prcap' should find your writer.

this seem OK, 'cdrecord -prcap' list me some information about my DVD Burner.

but if i try to burn (or blank) a CD, then :

```
$ cdrecord -v -blank=fast
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
(...)
cdrecord: Warning: Running on Linux-2.6.10-5-k7
(...)
TOC Type: 1 = CD-ROM
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: 'ATA:1,0,0'
devname: 'ATA'
scsibus: 1 target: 0 lun: 0
Warning: Using badly designed ATAPI via /dev/hd* interface.
(...)
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
(...)
cdrecord: Device or resource busy. Cannot open '/dev/hdc'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
```

i'm lost ...

---

### Post by dovik on 2005-08-22
something strange : cdrecord tell me that i'm > Running on Linux-2.6.10-5-k7

but since the last update (begin of my problem), i'm using 2.6.10**-7** instead of 2.6.10**-5** !

EDIT : installing "linux-k7" version 2.6.10-7 put the linux-image-2.6.10-5-k7 on your computer (and Synaptic call this version "2.6.10-34.4" whenever it's named and installed as 2.6.10-5 ...)

the headache is near ...

---

### Post by elrohir_telperien on 2005-11-15
Hi,

regarding to the error "Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
(...)
cdrecord: Device or resource busy. Cannot open '/dev/hdc'. Cannot open SCSI driver."

have you tried unmounting /dev/hdc prior to burning?

cheers

---

### Post by dovik on 2005-11-15
thank's for your answer elrohir_telperien but i've installed the last Ubuntu on my computer and the problem is resolve.

---


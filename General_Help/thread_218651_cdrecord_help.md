---
title: "cdrecord help"
date: 2006-07-18
forum: General Help
---

### Post by skale on 2006-07-18
It doesn't work. I'm convinced it's either that I'm doing something stupid, or cdrecord does not like IDE burners. Both xcdroast and gnomebaker have the same problems, so I think the issue is with cdrecord. CDs mount fine.
here is the output of cdrecord scanbus
> sameer@ftbedroom:~$ cdrecord -scanbus
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-26-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

and when I try to burn something:

> sameer@ftbedroom:~$ cdrecord /dev/hdd /media/hda1/lfslivecd-x86-6.1.1-4.iso
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-26-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/cdrw'
devname: '/dev/cdrw'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
cdrecord: Device or resource busy. Cannot open '/dev/cdrw'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .


---

### Post by yopnono on 2006-07-19
> **skale said:**
> 
and when I try to burn something:

Try this for the burning issue, in terminal

```
sudo chown root:cdrom /dev/cdrw
```
then try to burn.
If this work then add this to the "/etc/rc.local" file.

```
chown root:cdrom /dev/cdrw
```
And reboot

---

### Post by jstaple on 2006-10-09
Try this...

1. Add yourself (Your user account) to the disk group (System->Administration->Users and Groups)
2. Goto System->Preferences->Removable Drives and Media and untick everything in the storage tab
3. Try and burn a CD again

You will have to put these ticks back when you want automount to work again.

This worked for me. Don't treat as a difintive answer give it a try and see if it works for you.

---


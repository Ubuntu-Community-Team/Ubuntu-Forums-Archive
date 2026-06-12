---
title: "Can't Erase CD-RW discs anymore"
date: 2007-01-29
forum: General Help
---

### Post by richardq on 2007-01-29
Recently I've been having a problem with CD-RW burning. I used to be able to use GnomeBaker to do a quick erase on a CD-RW disc and then re-burn files to it. However in the past 3 weeks every time I try to do the quick erase it fails. I've tried K3B and I get the same problem. I can write to a new CD-R or a new CD-RW, but it can't seem to do erases (quick or thorough) anymore. 

When I insert a previously written CD-RW disc, it reads the disc, automatically mounts it and opens a nautilus window showing the contents. It's always done that. But now the green light on my cd-drive stays lit and it seems that it won't let Gnomebaker access to the drive (shows it's in use). This is true even if I make sure to close the nautilus window before launching GnomeBaker.

Any clues? I haven't changed any settings that I know of. I have made modifications to my fstab recently for other reasons, but this problem was occurring before that time. I've shown my current fstab below anyway in case it helps. I'm running Edgy.


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2 -- converted during upgrade to edgy
UUID=23b7dbeb-e33f-49d6-b913-614dafe1bcf5 / ext3 defaults,errors=remount-ro 0 1
# /dev/hdb2 -- converted during upgrade to edgy
UUID=a0dd2e3f-788d-4342-95aa-a5f91fc01070 /home ext3 defaults 0 2
# /dev/hdb1 -- converted during upgrade to edgy
UUID=A67411EA7411BE4D /media/hdb1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=68F044B7F0448D6E /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda6 -- converted during upgrade to edgy
UUID=2573-6CC2 /osshare vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=fbdd0a57-3ddc-4c35-b8cd-c128d9e09655 none swap sw 0 0
# /dev/hdb5
UUID=f18debdc-7645-405c-b8be-ea577ef2b6d1 /home/richard/Photos ext3 defaults,errors=remount-ro 0 2
/dev/hda5       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by ahaslam on 2007-01-29
Does this work?
```
cdrecord -dev ATAPI:/dev/hdc -blank=fast
```
If not, sudo it.

Tony ;)

---

### Post by richardq on 2007-01-29
> **Anthony Haslam said:**
> Does this work?
```
cdrecord -dev ATAPI:/dev/hdc -blank=fast
```


I put in a CD-RW with data on it and tried it and got a result similar to what Gnomebaker displays in it's detailed output window. The output from my terminal is shown below. The thing that has me puzzled is that I can insert a new blank disc and write data to it no problem. 

```
richard@ubuntu:~$ sudo cdrecord -dev ATAPI:/dev/hda -blank=fast
Password:
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.17-10-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: 'ATAPI:/dev/hda'
devname: 'ATAPI:/dev/hda'
scsibus: -2 target: -2 lun: -2
Warning: Using ATA Packet interface.
Warning: The related Linux kernel interface code seems to be unmaintained.
Warning: There is absolutely NO DMA, operations thus are slow.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
cdrecord: Device or resource busy. Cannot open '/dev/hda'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord: 
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
richard@ubuntu:~$ 

```

---

### Post by ahaslam on 2007-01-30
> Cannot open '/dev/hda
**hda** :-k ... is that right?

Run ***sudo cdrecord -scanbus*** to view your drive(s) and their ID(s)

For more help, follow the suggestions at the end of your previous output & let us know how you're going ;)

Tony.

---

### Post by richardq on 2007-01-30
I think I might be getting in over my head here. I ran the 'cdrecord -scanbus' command but it only seems to show one hard drive and nothing else. I have two hard drives, hdb and sda. I don't see anything about the cd/dvd drive at all:

```
richard@ubuntu:/media/dvdrecorder$ sudo cdrecord -scanbus
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.17-10-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
Linux sg driver version: 3.5.33
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus0:
        0,0,0     0) 'ATA     ' 'WDC WD1600JD-22H' '08.0' Disk
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *
richard@ubuntu:/media/dvdrecorder$ 
```

My fstab (posted previously) shows the cdrom drive (hda5) to be mounted as /media/cdrom0, however the contents of the disc in the drive are actually mounted as /media/dvdrecorder. I can cd over to /media/dvdrecorder and view the files on the disc no problem.

The readme.ATAPI.setup.ubuntu file talks about checking the /etc/default/cdrecord file and the contents of that file show:

CDR_DEVICE=/dev/cdrw

So I tried changing it to:

CDR_DEVICE=/dev/hda5 (hda5 is what is used in the fstab file)

But there seems to be no difference to the behaviour of the drive. I still have no problems reading discs, or writing to blank discs. Only erasing the CD-RWs seems to be the problem.

I confirmed that it's not the discs yesterday when I blanked it on my XP machine at work no problem. 

Any good source for documentation on mount points and cdrw/dvd drives? I think I'm just getting more and more confused here. :(

---

### Post by juah on 2007-01-30
I noticed the same kind of problem (device busy).  A simple workout:

sudo eject
cdrecord blank=fast

The first command ejects the cdrw. Leave it on the tray. The second one loads it in again and starts to blank.

Or, you might skip the first command not loading the cdrw in in the first place. Let the cdrecord command do that. It worked for me, how's it for you?

-----
edited:

or even better:

cdrecord -eject blank=fast

ejecting the cdrw right away when finished

---

### Post by ahaslam on 2007-01-30
If your CD burner is mounted as hda5 (Edgy is weird), did you try: *sudo cdrecord -dev ATAPI:/dev/hda**5** -blank=fast*  [SIZE="3"]?[/SIZE]

If you want to ensure that's where it's mounted, issue: ***dmesg | grep 'hd'***
This is how it shows my drive -  * **hdc**: MATSHITAUJ-840D, ATAPI CD/DVD-ROM drive*

You may also want to consider reinstalling 'cdrtools' - it's very strange how you can read & write discs but not blank them.

> **juah said:**
> I noticed the same kind of problem (device busy).  A simple workout:

sudo eject
cdrecord blank=fast

Issuing the eject command may well help, but I'm sure extra parameters should be used when burning/blanking.

Tony.

---

### Post by richardq on 2007-01-30
Anthony, Juah,

Thanks to both of you for your help. I can now manage to get Gnomebaker (or cdrecord from the terminal) to do a fast blank IF I don't have the cd in the drive at the time (or it's sitting in the tray outside the computer). Basically, I run Gnomebaker and choose Blank CD-RW and press start. Then it opens the drawer and asks me to insert a disc. From that point on it works normally. 

Strange behaviour since it used to work no problem before. I haven't reinstalled the apps in the cdrecord suite but I may just do that and see if it helps.

Thanks again.

Richard

---


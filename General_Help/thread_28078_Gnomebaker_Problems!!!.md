---
title: "Gnomebaker Problems!!!"
date: 2005-04-18
forum: General Help
---

### Post by madzzoni on 2005-04-18
I have Gnomebaker installed in Hoary, but it will not make a copy of a audio-CD!

When i press the "copy audio-cd" butten, the proces starts ok and after 50% it ask for the "New disc", then i change the CD and hit OK-button, then nautilus opens in Burn-mode! and Gnomebaker gives this error:

cdrecord: Warning: Running on Linux-2.6.10-5-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Linux sg driver version: 3.5.27
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 0 = CD-DA
Using libscg version 'ubuntu-0.8ubuntu1'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'HL-DT-ST'
Identifikation : 'RW/DVD GCC-4480B'
Revision       : '1.00'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0009
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
Profile: 0x0002 (current)
Profile: 0x0010 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1621312 = 1583 KB

Can anyone help here??? (I dosn't have this problem in Warty.)

---

### Post by germ_e_1 on 2005-04-21
I had same issue, but didn't chase it.  I just installed K3B and cdrao and poof! like magic no problems there.  

I KNOW... not a GNOME solution!

---

### Post by madzzoni on 2005-04-21
[QUOTE=germ_e_1]I had same issue, but didn't chase it.  I just installed K3B and cdrao and poof! like magic no problems there.  

I KNOW... not a GNOME solution![/QUOTE]

How did you get cdrao? 
- it's not in my archieves....

---

### Post by DougInKY on 2005-04-21
I think he meant cdrdao. It is in universe.

Doug in Kentucky

---

### Post by goedson on 2005-04-22
[QUOTE=madzzoni]I have Gnomebaker installed in Hoary, but it will not make a copy of a audio-CD!

When i press the "copy audio-cd" butten, the proces starts ok and after 50% it ask for the "New disc", then i change the CD and hit OK-button, then nautilus opens in Burn-mode! and Gnomebaker gives this error:

cdrecord: Warning: Running on Linux-2.6.10-5-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Linux sg driver version: 3.5.27
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 0 = CD-DA
Using libscg version 'ubuntu-0.8ubuntu1'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'HL-DT-ST'
Identifikation : 'RW/DVD GCC-4480B'
Revision       : '1.00'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0009
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
Profile: 0x0002 (current)
Profile: 0x0010 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1621312 = 1583 KB

Can anyone help here??? (I dosn't have this problem in Warty.)[/QUOTE]
 Which version of the package are you using?

---

### Post by madzzoni on 2005-04-22
I use GnomeBaker 0.3 from the ubuntu-repos!

---

### Post by goedson on 2005-04-22
[QUOTE=madzzoni]I use GnomeBaker 0.3 from the ubuntu-repos![/QUOTE]
 Please, try the CVS snapshot available from my repository (see [http://www.ubuntulinux.org/wiki/GnomeBaker](http://www.ubuntulinux.org/wiki/GnomeBaker) for the URL) and let me know if you still experience this problem.

---

### Post by madzzoni on 2005-04-22
[QUOTE=goedson]Please, try the CVS snapshot available from my repository (see [http://www.ubuntulinux.org/wiki/GnomeBaker](http://www.ubuntulinux.org/wiki/GnomeBaker) for the URL) and let me know if you still experience this problem.[/QUOTE]
That's what i use in Hoary!
[COLOR=Red]Update[/COLOR]: Now i use the cvs-version (0.3+20050421) from your repository and this works for me.  O:) 

Only thing confusing, is that gnomebaker still opens the nautilus-burning window, when i insert the new blank CD-R in the drive when copy audio-CDs.

But now it does the job.... Thanks!

---

### Post by goedson on 2005-04-23
[QUOTE=madzzoni]That's what i use in Hoary!
[COLOR=Red]Update[/COLOR]: Now i use the cvs-version (0.3+20050421) from your repository and this works for me.  O:) 

Only thing confusing, is that gnomebaker still opens the nautilus-burning window, when i insert the new blank CD-R in the drive when copy audio-CDs.

But now it does the job.... Thanks![/QUOTE]

It's not gnomebaker that opens the nautilus-burning window. It's gnome-volume-manager that does it.

---

### Post by tread on 2005-04-23
Yep, you can get rid of it by going to System->Preferences->Removable Drives and Media, there is a box there you can uncheck for default action on a blank cd.

---

### Post by insulae on 2005-04-23
(my english is bad)

[SIZE=12][COLOR=Red]**goedson you are the best!!!**[/COLOR][/SIZE]

i am a ex-KDE user, with ubuntu i change my desktop and i like very much gnome, is very fast. I dont like use GTK applications and QT applications at the same time, i like use or GTK or QT applications, so i dont want now use K3B (is excellent app but is QT :P).

so i downloaded with apt-get gnomebaker is very very fast is beatiful, but this version (3.0) dont wont record a cd of 700MB and with this version 0.3+20050415-1ubuntu1 i can!!! and i can record cd of 650, yea baby!! you do a good job!!!.

---

### Post by madzzoni on 2005-04-26
[QUOTE=goedson]Please, try the CVS snapshot available from my repository (see [http://www.ubuntulinux.org/wiki/GnomeBaker](http://www.ubuntulinux.org/wiki/GnomeBaker) for the URL) and let me know if you still experience this problem.[/QUOTE]

Hey again!

Now i have another problem with Gnomebaker cvs-snapshot.

I can't burn ISO-image files! When trying i get an error saying "Gnomebaker is suddenly dead!"(Translated from DK) with options to inform developers (and i did).

Then i retried burn the image.. i get this info:

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.10-5-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
cdrecord: Device or resource busy. Cannot open '/dev/hdc'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord: 
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2

---------------------------------------------------------------

It seems like the "ubuntu-version" of gnomebaker burns ISO-images Okey!

---

### Post by ericsp on 2005-04-27
when installing the CVS, I get the following message:

Selecting previously deselected package gnomebaker.
 (Reading database ... 61716 files and directories currently installed.)
Unpacking gnomebaker (from gnomebaker_0.3+20050421-1_i386.deb) ...
dpkg: dependency problems prevent configuration of gnomebaker:
gnomebaker depends on libc6 (>= 2.3.2.ds1-21); however:
Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
gnomebaker depends on libvorbis0a (>= 1.1.0); however:
Version of libvorbis0a on system is 1.0.1-1.
gnomebaker depends on libvorbisfile3 (>= 1.1.0); however:
Version of libvorbisfile3 on system is 1.0.1-1.
dpkg: error processing gnomebaker (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing: gnomebaker

Gnomebaker can be started though (?)

---

### Post by goedson on 2005-04-27
[QUOTE=ericsp]when installing the CVS, I get the following message:

Selecting previously deselected package gnomebaker.
 (Reading database ... 61716 files and directories currently installed.)
Unpacking gnomebaker (from gnomebaker_0.3+20050421-1_i386.deb) ...
dpkg: dependency problems prevent configuration of gnomebaker:
gnomebaker depends on libc6 (>= 2.3.2.ds1-21); however:
Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
gnomebaker depends on libvorbis0a (>= 1.1.0); however:
Version of libvorbis0a on system is 1.0.1-1.
gnomebaker depends on libvorbisfile3 (>= 1.1.0); however:
Version of libvorbisfile3 on system is 1.0.1-1.
dpkg: error processing gnomebaker (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing: gnomebaker

Gnomebaker can be started though (?)[/QUOTE]

Are you using Warty? The package I've done for the CVS snapshot is compiled for Hoary.

---

### Post by goedson on 2005-04-27
[QUOTE=madzzoni]Hey again!

Now i have another problem with Gnomebaker cvs-snapshot.

I can't burn ISO-image files! When trying i get an error saying "Gnomebaker is suddenly dead!"(Translated from DK) with options to inform developers (and i did).

Then i retried burn the image.. i get this info:

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.10-5-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
cdrecord: Device or resource busy. Cannot open '/dev/hdc'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord: 
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2

---------------------------------------------------------------

It seems like the "ubuntu-version" of gnomebaker burns ISO-images Okey![/QUOTE]


The only thing I can imagine is that your device was busy when you were trying to write the CD. Maybe the CD was mounted? I've just tried writing a CD image, and it worked.

---

### Post by ericsp on 2005-04-27
[QUOTE=goedson]Are you using Warty? The package I've done for the CVS snapshot is compiled for Hoary.[/QUOTE]
 Nope. Fully on hoary

---

### Post by goedson on 2005-04-27
[QUOTE=ericsp]Nope. Fully on hoary[/QUOTE]

Looking at the dependencies not satisfied, it looks like you're using the package I've built for Debian SID and not Ubuntu Hoary. You should be using the one found at the [Ubuntu Hoary repository](http://people.debian.org/~goedson/packages/ubuntu/hoary/gnomebaker/snapshots/i386)

---

### Post by warjowuch on 2006-05-18
It is a user-problem, i recognize the problems, but as sudo gnomebaker it does work. Not that this is not silly, but that's the short-term solution.
Anyone knows how to use gnomebaker without root-privileges?

---

### Post by goedson on 2006-05-18
[QUOTE=warjowuch]It is a user-problem, i recognize the problems, but as sudo gnomebaker it does work. Not that this is not silly, but that's the short-term solution.
Anyone knows how to use gnomebaker without root-privileges?[/QUOTE]

Try this:

```

sudo dpkg-reconfigure cdrecord

```

And answer yes when asked " Do you want the cdrecord binaries to be installed SUID root?".
This should do it.


Another way of solving it would be giving read and write access to your CD writer device (usually some of the /dev/hdX) to a group your user is member of (cdrom).

---


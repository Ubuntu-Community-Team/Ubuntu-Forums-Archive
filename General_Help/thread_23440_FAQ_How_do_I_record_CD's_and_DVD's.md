---
title: "FAQ: How do I record CD's and DVD's?"
date: 2005-04-01
forum: General Help
---

### Post by Darrena on 2005-04-01
**[CENTER]How do I record CD's and DVD's in Ubuntu?[/CENTER] **

There are 4 popular applications to record CD's and DVD's in Ubuntu:

**Nautilus Burner: **
_Description_: This is the option to record to CD's and DVD's directly from the file manager in Gnome Nautilus.   It seems to only support basic recording like saving files to disc or recording ISO's.
_How to get it:_  It comes with a normal ubuntu/Gnome install.
_How to use it:_ To access this application open nautilus, select the Go menu and click CD/DVD Creator _or_ open Nautilus and type burn:/// in the location block.  Drag the files you would like to record to the window and click "Write to Disc".  To record an ISO right-click on the ISO file and select record.
[B]
Gnomebaker:[/B]
_Description:_ This is a GTK2 based CD Recording application that integrates nicely with Gnome.  It supports duplicating audio and data CD's, recording ISO's, and formating rewritable disks and recording audi CD's from MP3's.  A future version should have support for bin/cue's and many other requested features.  See [http://gnomebaker.sourceforge.net/](http://gnomebaker.sourceforge.net/) for more information
_How to get it: _ Enable the Universe repository and search for gnomebaker in synaptic or type the following in a terminal:
```
sudo apt-get install gnomebaker
```
_How to use it:_ The package creates a menu entry under Applications->Accessories->Gnomebaker.   The usage is similar to most other CD recording apps with a clean multi-paned interface interface for adding files to an image.  The closest comparison that I can think of in the Windows world would be the Older EZCD Creator.  


**Graveman:  **
_Description:_ Graveman is another GTK2 based CD Recording application that integrates nicely with Gnome.   It supports duplicating audio and data CD's, recording ISO's, creating audio CD's from MP3's/OGG, formating rewritable discs, overburning, and CD Fixation.  The application is being actively developed with new features.  See [http://graveman.tuxfamily.org/index-e.php](http://graveman.tuxfamily.org/index-e.php) for more information
_How to get it:_  Enable the Universe repository and search for graveman in synaptic or type the following in a terminal:
```
sudo apt-get install graveman
```
_How to use it:_ The package creates a menu entry under Applications->Accessories->Graveman.   The usage is similar to many "wizard" other CD recording apps and will be easy to use by anyone from a poweruser to your grandmother.

**K3B:**
_Description:_ K3B is one of the most popular, full-featured, and polished cd recording applications available on ANY platform.  It is written for KDE but runs fine under gnome after installing the KDE lib's.  It supports copying audio and data CD's, recording ISO's, recording Bin/cue's, recording MP3's to Audo CD's, formating CDRW's and DVDRW's and MUCH more.    See [http://www.k3b.org/](http://www.k3b.org/) for more information
_How to get it:_  It is available via synaptic, or:
```
sudo apt-get install k3b
```
_How to use it:_ The package creates a menu entry under Applications->Sound & Video->K3B.   The usage is similar NERO, is quite easy to use and very powerfull.


[U]
[B]
A 5th option for individuals who are uncomfortable with any of the above applications or would prefer a commercial product is NeroLinux:[/B][/U]

**Nerolinux:**
_Description:_ NeroLinux is a Linux port from ahead of the popular Nero recording suite from Windows and is the only application on this list that is not free.  See [http://www.nero.com/en/NeroLINUX.html](http://www.nero.com/en/NeroLINUX.html) for further information
_How to get it:_  NeroLinux is available for anyone who purchases "Nero 6 reloaded, register your key to download it at [http://www.nero.com/en/NeroLINUX.html](http://www.nero.com/en/NeroLINUX.html)
_How to use it:_ The package creates a menu entry under Applications->Accessories->Sound & Video->Nerolinux.  The interface is not exactly like the Windows version but it is close and users comfortable with Nero in Windows should have no problems with NeroLinux

[U][B]
Please let me know of any errors, corrections, or questions![/B][/U]

---

### Post by bored2k on 2005-04-02
That's hot right there [pardon my english right now, listening to 50 Cent right now :-P]. Good info for newcomers. You should add NeroLinux ;), and if possible address the k3bsetup2 problem ["not found"] . Still, off the chain.

---

### Post by Darrena on 2005-04-02
> **bored2k]That's hot right there [pardon my english right now, listening to 50 Cent right now :-P]. Good info for newcomers. You should add NeroLinux  said:**
>  . Still, off the chain.


Thanks!  :)

I forgot about Nerolinux, I have never used it but I can probably give a general synopsis of it.

Does the k3bsetup problem still happen with the current version available from the repositories?

---

### Post by bored2k on 2005-04-02
I'm not quite sure. But last time I tried it still gave me problems [go figure, kdelibs on my system AND it still didn't work.. grr].

About graveman , I think you missed some spots:
CD Duplication
CDRW Erasion
DVDRW Formatting
CD Fixation
Overburning

[IMO its much better than GBaker with its new upgrades].

Here is some NeroLinux info for [y'all](http://www.nero.com/en/NeroLINUX.html). I have used it and I like it. I think its the most feature featured burning application besides KDE. It's pretty [Nero is one of the 2 applications I love from another OS].

---

### Post by Darrena on 2005-04-02
[QUOTE=bored2k]I'm not quite sure. But last time I tried it still gave me problems [go figure, kdelibs on my system AND it still didn't work.. grr].

About graveman , I think you missed some spots:
CD Duplication
CDRW Erasion
DVDRW Formatting
CD Fixation
Overburning

[IMO its much better than GBaker with its new upgrades].

Here is some NeroLinux info for [y'all](http://www.nero.com/en/NeroLINUX.html). I have used it and I like it. I think its the most feature featured burning application besides KDE. It's pretty [Nero is one of the 2 applications I love from another OS].[/QUOTE]

Ok I added information about NeroLinux, changed the order so the GTK apps are first (I LOVE K3B, but it is probably best to stick with native gtk apps), made some misc syntax changes and updated graveman's description with the information you provided.  

Do you know if the new graveman that came out today supports burning bin/cue's?

I did a search for k3bsetup and everything related to that issue was pretty vague, is this the problem where people needed to run K3B using gksudo?

---

### Post by bored2k on 2005-04-02
That's why I started to dislike K3B, so ugly.
Graveman still doesn't support bin. I just tested it. All I see is .iso and iso only loading [at least the one on Hoary doesn't]. [http://graveman.tuxfamily.org/changelog-e.php](http://graveman.tuxfamily.org/changelog-e.php)

K3B problem is the following, at first boot it tells you that its good to configure with k3bsetup2, wich is not found in the system. If you try and opening it through the control panel, it won't open. You try it from a terminal, and you guessed it, won't open.

---

### Post by muzza on 2005-04-11
I'm having exactly the same problem.

I tried logging in temprorarily as root (sudo -s) then typed 'k3b' and the program ran without that root dialog box.  but it wouldn't let me run k3bsetup2 ' "not found"

When I later tried to run it from the applications menu, the same password box popped up.

---

### Post by kuleali on 2005-04-12
I have the same pro, any solution ?

---

### Post by Darrena on 2005-04-12
[QUOTE=kuleali]I have the same pro, any solution ?[/QUOTE]

Have you tried starting K3B with gksudo?  from run do gksudo k3b and enter your password and see if that works.

Is this Warty or Hoary?

---

### Post by Darrena on 2005-04-16
I updated the first post to show that gnomebaker is now available via the universe repository

---

### Post by madzzoni on 2005-04-19
**Gnomebaker won't copy audio-CDs!**
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
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
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
Device type : Removable CD-ROM
Version : 0
Response Format: 1
Vendor_info : 'HL-DT-ST'
Identifikation : 'RW/DVD GCC-4480B'
Revision : '1.00'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0009
Profile: 0x000A
Profile: 0x0009 (current)
Profile: 0x0008
Profile: 0x0002 (current)
Profile: 0x0010
Using generic SCSI-3/mmc CD-R/CD-RW driver (mmc_cdr).
Driver flags : MMC-2 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1621312 = 1583 KB

Can anyone help here??? (I dosn't have this problem in Warty.)

---

### Post by germ_e_1 on 2005-04-21
I got similar to above using Nautilis burning for an ISO.  I just installed K3B (used to use it a lot back when I used GenToo) and also required cdrao. 

After that everything just worked with K3B.  No sudo, no setup problem,  just worked !

(This system was upgraded from Warty to Hoary with only a few rough spots, not too bad though)

---

### Post by rykel on 2005-05-04
Hiz!!

Thanks for the list... really comes in handy, didn't know abt graveman before this...

Anyway, I LOVE the Gnome CD/DVD Creator and GnomeBaker... looks good, and do their jobs well... esp. CD/DVD Creator - it's sooo simple to burn files into a DVD-RW!

HOWEVER, Gnomebaker CANNOT deal with copying DVDs, so I ran K3B. (my favourite when I was still on MEPIS)

(Any idea why Gnomebaker cannot handle DVDs??)

K3B works like a charm... I dont remember having to "setup" anything except the CD-ROM speed... which btw, is strange, because on Fedora Core, K3B always detected the drive speed correctly.

I have attached a screenshot to show how I am right now copying a DVD using K3B.

Yeah, you are right ~ K3B looks out of place here in my Ubuntu GNOME world... Gnome is so cool that I cannot go back to KDE anymore!



Best Regards,

Rykel
Singapore

---

### Post by Darrena on 2005-05-04
Rykel,

The developer Gnomebaker plans to have DVD support as well as Bin/Cue in the next version.  I haven't seen an update on when...

---

### Post by rykel on 2005-06-07
Darrena,

I believe the reason GnomeBaker cannot work with DVDs currently is because of its underlying ubuntu cdrecord core. (no DVD support)

Unless there is a way to get cdrecord-proDVD into this system, I just have to wait for a while, until GnomeBaker 0.40.

Graveman! did no better at burning an iso image to a DVD+RW too.

As for k3b, it relies on growisofs, and I take that to be the rationale why it works with DVD+RW so well.


btw, I have a GnomeBaker 0.3 autopackage which was created by one of the GnomeBaker developers.

You will not find this on the official website yet, but if anybody wants it, simply GAIM me on MSN: lifestylediamond OR icq: 22768140.

I have used it, and found no installation problems with it so far. The program works exactly the same as it did when downloaded from Synaptic.

Best Regards,

Rykel
Singapore

---

### Post by psoleko on 2005-06-09
Odd. I have tried a few DVD-R's with GnomeBaker and it goes through everything just fine. When I try to read them they are unreadable even on other operating systems. Guess that explains it.

---

### Post by UbuWu on 2005-06-09
And there is serpentine for audio cd burning: [http://s1x.homelinux.net/projects/serpentine/](http://s1x.homelinux.net/projects/serpentine/)
It will be in main for breezy (I personally would have preferred gnomebaker).

---

### Post by Sav on 2005-06-10
On my laptop I have kubuntu.
K3b runs very well.

On my desktop I have installed Ubuntu, and I don't like messing with libs by different window managers.
Genomebaker is quite good, and I'll wait for new features.

---

### Post by steven_ellis on 2005-06-13
I have used k3b for quite some time even if my desktop is gnome or xfce as it just tends to work for both DVD and CD.

[QUOTE=Darrena]
**K3B:**
_Description:_ K3B is one of the most popular, full-featured, and polished cd recording applications available on ANY platform.  It is written for KDE but runs fine under gnome after installing the KDE lib's.  It supports copying audio and data CD's, recording ISO's, recording Bin/cue's, recording MP3's to Audo CD's, formating CDRW's and DVDRW's and MUCH more.    See [http://www.k3b.org/](http://www.k3b.org/) for more information
_How to get it:_  It is available via synaptic, or:
```
sudo apt-get install k3b
```
_How to use it:_ The package creates a menu entry under Applications->Sound & Video->K3B.   The usage is similar NERO, is quite easy to use and very powerfull.
[/QUOTE]

A tip for all gnome desktop users and k3b. If you have a notification area K3b will put up a notification icon that indicates the progress of the CD or DVD burn. I've found that this hammered both the window manager and Xorg on my Athlon XP 2800+. Also I couldn't burn DVDs at full speed because of the performance issues. This icon can easily be disabled by starting K3b and going

Settings ->
 Configure K3b ->
   Misc ->
    Show Progress in System Tray -> Disable

Now I can burn disks with almost no CPU load.

Steve

---

### Post by douglas_slac on 2005-08-11
For people having a problem with burning cd's, check the 'disk' group.  

I found that even though k3b checked use of /dev/cdrom, and /dev/sdc0 for write permission, cdrecord would use /dev/sg0 as the decive to write to.  This device had group setting of 'disk' group, and my username was not in the disk group.

I put my username in the disk group, and I was able to write.  Should users in ubuntu have their names added to the disk group?  The username was added to the audio, cdrom, video, scanner, and some other groups, why not disk?  Then again why is there a disk group?

---

### Post by MikePB on 2005-09-06
Forgive the noobness.... but how would you go about that?

---

### Post by douglas_slac on 2005-09-06
Well, there probably is some gui interface to managing users and groups for ubuntu, but I don't know what it is at this point.  I just put my username in the disk listing in the "/etc/group" file.  Next time you log in, then you are part of that group.

Also, if you don't want to edit a file, there is:

sudo adduser my_username disk

Just set my_username to the username you want, of course.  Then log and login again...

---

### Post by MikePB on 2005-09-06
Hmm... still no go... K3B only sees a complete CD-ROM.....

---

### Post by 0chiehchen on 2005-11-09
For Breezy, this problem seems to go away.  However, in some cases it still causes permission problem.  In my case, /dev/ got two sg devices.  (namely, /dev/sg0 and /dev/sg1).  sg1 is owned by group cdrom, but sg0 is not.  cdrecord seems to be accessing sg0 by default, so it shows permission error.  I did this:

[FONT="Courier New"]sudo chgrp cdrom /dev/sg*[/FONT]

and the problem goes away.


[QUOTE=douglas_slac]For people having a problem with burning cd's, check the 'disk' group.  

I found that even though k3b checked use of /dev/cdrom, and /dev/sdc0 for write permission, cdrecord would use /dev/sg0 as the decive to write to.  This device had group setting of 'disk' group, and my username was not in the disk group.

I put my username in the disk group, and I was able to write.  Should users in ubuntu have their names added to the disk group?  The username was added to the audio, cdrom, video, scanner, and some other groups, why not disk?  Then again why is there a disk group?[/QUOTE]

---

### Post by rory_fireshaper on 2006-02-18
[QUOTE=0chiehchen]

[FONT="Courier New"]sudo chgrp cdrom /dev/sg*[/FONT]

[/QUOTE]

For some reason I have to do this every time I want to burn a CD. Is there a way I can make this a script and run it at startup?

---

### Post by danish_demon on 2006-03-04
alright, i'm just trying to copy an audio cd.  i right click on the audio cd icon on my desktop and select "copy cd".  i then click "write" and get this pop-up window:

File image creation failed

Could not run sub process: Failed to execute child process "cdrdao" (No such file or directory).

if i try to install gnomebaker (just to try a different program) i get this after entering "sudo apt-get install gnomebaker" on the cli:
```
sudo apt-get install gnomebaker
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnomebaker: Depends: cdrdao but it is not going to be installed
E: Broken packages

```

any ideas on what is wrong?

thanks for your time.

edit:  just for more info, i can play audio cds with no problem.

---

### Post by rikai on 2006-03-04
Be sure you have universe enabled in your repositories.
cdrdao is available in universe.

---

### Post by danish_demon on 2006-03-06
when i try to install cdrdao i get this:

```

sudo apt-get install cdrdao
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  cdrdao: Depends: libgcc1 (>= 1:4.0.2) but 1:4.0.1-4ubuntu9 is to be installed
          Depends: libstdc++6 (>= 4.0.2-4) but 4.0.1-4ubuntu9 is to be installedE: Broken packages

```

edit:  NOTE: i am a breezy user, i didn't notice this was a hoary thread until just now

---

### Post by rikai on 2006-03-07
Very strange...
I can install cdrdao jsut fine on this box...

---

### Post by arcodelta on 2006-03-11
Hi everybody... 

I've found this thread searching for some clues recording under ubuntu 5.10.

I cannot record a cd, no matter which software I use. I think it's a more 'deep' problem. So I've tryed:

Q: How to blank CD-RW/DVD-RW?

   1. Read General Notes
   2. e.g. Assumed that /dev/cdrom is the location of CD/DVD-ROM
   3. sudo umount /dev/cdrom
      cdrecord dev=/dev/cdrom blank=fast
from:[http://ubuntuguide.org/#cddvdburning](http://ubuntuguide.org/#cddvdburning)

but I get errors also... 
luisito@ubuntu:~$ sudo umount /dev/cdrom
luisito@ubuntu:~$ cdrecord dev=/dev/cdrom blank=fast
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.12-10-686
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/cdrom'
devname: '/dev/cdrom'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c      1.91 04/06/17 C opyright 1988,1995,2000-2004 J. Schilling').
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   :
Vendor_info    : 'PIONEER '
Identifikation : 'DVD-RW  DVR-106D'
Revision       : '1.08'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Starting to write CD/DVD at speed 10 in real BLANK mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.
cdrecord: Success. blank unit: scsi sendcmd: no error
CDB:  A1 01 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 97 06 70 0E 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 9897584 (not valid)
cmd finished after 75.890s timeout 9600s
cdrecord: Cannot blank disk, aborting.
cdrecord: Some drives do not support all blank types.
cdrecord: Try again with cdrecord blank=all.

trying cd record blank=all, i get the same problem.

I've tryed different cd's, and brand and I've no success.

Any clue?

thanks in advance

---

### Post by rikai on 2006-03-11
Hm, is your user aded to the proper groups?

---

### Post by arcodelta on 2006-03-13
Sorry... I'm very new to this!

I know ther are groups, and users and I also Know about permissions, but which groups need I to be in... and more than that: How to know If I'm in this groups?

I've tryed to record a disk with sudo before cdrecord and no success. I think 'root' need to be in this groups by default.

?¿¿? I'm trying to get everything about this because is my last due to WinXP. After I could go away from MS.

waiting with my fingers on the keyboard ready to type!

---


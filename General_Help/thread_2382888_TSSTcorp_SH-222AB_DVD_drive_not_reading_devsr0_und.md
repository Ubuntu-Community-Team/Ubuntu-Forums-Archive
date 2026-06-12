---
title: "TSSTcorp SH-222AB DVD drive not reading /dev/sr0 under 16.04 LTS"
date: 2018-01-18
forum: General Help
---

### Post by MgFrobozz on 2018-01-18
I've recently upgraded to ubuntu 16.04.3.LTS from 14.04 LTS. My dvd drive was working ok under 14.04, and now it won't recognize any dvd, including pristine dvds that I created on it. When I insert a dvd and close the drive, it sounds like it seeks 3 times, with no following activity. After that, I'm unable to mount /dev/sr0. If I try to get information about the disk, I get a "no media mounted" error (see below, same error for /dev/sr0, /dev/dvd, /dev/dvdrw, /dev/cdrom, /dev/cdrw). I don't see any error messages in the log (dmesg).

I've found a few other instances of this problem in the forum for TSSTcorp (Toshiba Samsung Storage Technology) drives, but it was unclear that they were fixed by the last suggestion (cleaning the dvd lens). 

Any ideas about what's going on? 
Is there a way to turn on more logging for the device?

```

> dvd+rw-mediainfo /dev/sr0
INQUIRY:                [TSSTcorp][CDDVDW SH-222AB ][SB00]
GET [CURRENT] CONFIGURATION:
:-( no media mounted, exiting...

> lshw
    ...
     *-scsi
          physical id: 2
          logical name: scsi5
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SH-222AB
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: SB00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc


> cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.3 LTS"

> uname -srvm
Linux 4.4.0-104-generic #127-Ubuntu SMP Mon Dec 11 12:16:42 UTC 2017 x86_64

```

---

### Post by Cavsfan on 2018-01-18
I have the same DVD writer/player and it seems like it quit working a couple of years ago. I used to re-use DVD-RWs over and over.
But, now it fails to acknowledge there is even a DVD in it once formatted.

I did just put in an audio CD and it played it perfectly and this is on the development version of Xubuntu.
```
cavsfan@cavsfan-Le-Beast:~$ dvd+rw-mediainfo /dev/sr0INQUIRY:                [TSSTcorp][CDDVDW SH-S202J ][SB02]
GET [CURRENT] CONFIGURATION:
:-( no media mounted, exiting...

cavsfan@cavsfan-Le-Beast:~$ lshw
      ...
     *-scsi
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SH-S202J
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: SB02
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

cavsfan@cavsfan-Le-Beast:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu Bionic Beaver (development branch)"

cavsfan@cavsfan-Le-Beast:~$ uname -srvm
Linux 4.13.0-25-generic #29-Ubuntu SMP Mon Jan 8 21:14:41 UTC 2018 x86_64

```
I started using 8GB USB drives to install Ubuntu, etc. with, since I could not get the DVD burner to cooperate.

I did take it apart as best I could and used air to clean the heads, plus I found my old CD/DVD cleaner and used that a few times.

I successfully burned an installation DVD-R with 16.04.1 back a while ago but, it will not even recognize it is in the DVD player once it was formatted.

My system is almost 9 years old (April) so, I just chocked it up to being too old. But, it works on somethings and not on others.

---

### Post by MgFrobozz on 2018-01-18
My drive also plays audio cds without problems. I suppose the optics could *possibly* still be a problem (since dvd is recorded more "densely"), but playing the audio cd makes that much less likely.

Beginning to wonder whether a problem crept into the kernel driver. Anyone know which driver supports the TSSTcorp SH-222AB?

---

### Post by Cavsfan on 2018-01-18
But, this is on Bionic, Artful, Xenial and Arch Linux so a driver would not seem to be the problem.

---

### Post by mc4man on 2018-01-18
The 'specifics' of the laser beam used to read audio cd vs dvd are different. How any one drive accomplishes that may vary but they are different.
[http://www2.ensc.sfu.ca/~glennc/e894/e894l22k](http://www2.ensc.sfu.ca/~glennc/e894/e894l22k)
So having one media type fail before the other is quite common, more often than not it's dvd fails before audio cd. 
Add that to the fact that most Oem's supplied the cheapest drives available in sufficient quantities per point in time, they aren't going to last forever or even close.
If this is a desktop I'd just get a new drive, if a laptop usually easier to just get an external one..

---

### Post by Cavsfan on 2018-01-19
+1 what [COLOR=#000000]mc4man said.

But, I wanted to mention that I am now in Arch Linux and brought up Thunar (Xfce). I forgot the DVD was in the drive and when I clicked on it, it showed the contents of the 16.04 installation DVD.

It's probably hit or miss though. But, I was wrong when I said all my operating systems are the same.
I'm not going to bother replacing my DVD because I can install with USB drives and the BIOS is new enough to boot up on USB.

My PC has only 4GB memory and Windows 10 is the only one that has an issue with that. But, hopefully someday I'll get a screaming new PC with 64GB memory, a 1TB SSD and stuff...

I may give it another try the next time I need to install an ISO with a DVD as I haven't truly tried since I cleaned it.[/COLOR]

---

### Post by goofy864 on 2018-10-21
It's caused by a wrong BIOS-setting. Switch off the "Native SATA" support (maybe IDE is shown then) and the drive will work properly.

---


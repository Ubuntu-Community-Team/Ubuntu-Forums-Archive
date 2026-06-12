---
title: "Dual boot, problem with NTFS"
date: 2014-08-31
forum: General Help
---

### Post by cyberpunk3 on 2014-08-31
As per this page
[http://www.ubuntu.com/certification/hardware/201202-10627/](http://www.ubuntu.com/certification/hardware/201202-10627/)
my netbook (Asus EeePC 1001 PXD) is certified for Ubuntu. As the version on the link is 12.04, should I install that version (and maybe upgrade it later on), or can I go directly to the latest, 14.04.1? I suppose there's a reason for 12.04 on the certification page, which is either:
- the page just hasn't been updated;
- the download package linked on the page contains all "specific" drivers and settings for 1001PXD;
- or newer Ubuntu versions run poorly on this netbook.
(if it's #2, then 12.04 to 14.04.1 is probably the right path)

I tried 14.04.1 from a "live" USB on the netbook, and it seemed to work just fine (but then again, I didn't go into every single detail yet).

Also, the page has the 64-bit download, and I've read/heard that you don't gain anything if you run a 64-bit OS on this netbook. Is this only relevant for 64-bit Windows?

---

### Post by mörgæs on 2014-08-31
Hi, welcome to the fora.

> **cyberpunk3 said:**
> 
I tried 14.04.1 from a "live" USB on the netbook, and it seemed to work just fine (but then again, I didn't go into every single detail yet).


That is the way to go. Then I would install 14.04.1 and stick to it (since it's long term support).


> **cyberpunk3 said:**
> 
I tried 14.04.1 from a "live" USB on the netbook, and it seemed to work  just fine (but then again, I didn't go into every single detail yet).
 

What? Please post a link.

How much memory do you have?

---

### Post by cyberpunk3 on 2014-08-31
Which link? The one on the certification page I posted above points to "Ubuntu 12.04 LTS 64-bit" (the file is ubuntu-12.04-desktop-amd64.iso). The one I tried from a USB drive is "ubuntu-14.04.1-desktop-i386.iso".
The netbook has 2 GB of RAM.

---

### Post by mörgæs on 2014-08-31
Sorry, my second quote should have been *I've read/heard that you don't gain anything if you run a 64-bit OS on this netbook.* Sounds strange, and I am curious about who would have told you so.

Anyway, you have 2 GB so I recommend the 64 bit version.

---

### Post by cyberpunk3 on 2014-08-31
Well, it's been quite a while since I read that somewhere online when I was contemplating migrating from 32-bit Windows to 64-bit Windows on that machine. Unfortunately I don't have a link anymore. I vaguely remember it was something along the lines that the CPU is 64-bit, but other parts are too weak for a 64-bit system; and that 2 GB is the most RAM you can have on this system, whereas you should have at least 3 or 4 GB for a 64-bit one.
Like I said, that was for Windows; I don't know if it applies to Linux too.

If I put the "default" ubuntu-12.04-desktop-amd64.iso on it, can it be migrated to 14.x later on, while keeping all settings and customizations?

---

### Post by ajgreeny on 2014-08-31
Just for a bit of background to this 32bit vs 64bit situation, there are many users who suggest that with up to 2GB ram there is little to be gained from running 64bit OSs; with more than 2GB 64bit really starts to come into its own.
There is no hard and fast rule about this, however, and I suspect that the potential advantages of 64bit will be outweighed by the relatively slow cpu and other hardware in the netbook.

Your choice, I think, so why not try both as live USBs and see if you can notice any difference, either in the ram used, both at rest and with something like firefox open with several tabs, or the apparent speed of activity when running applications in both architectures.

You can check ram usage from the command free -m in terminal which will give output something like
```
~$ free -m
             total       used       free     shared    buffers     cached
Mem:          7682       1739       5942          0         57        707
-/+ buffers/cache:        974       6708
Swap:         8198          0       8198
```
with the **+- buffers/cache** line being the important one

---

### Post by mörgæs on 2014-08-31
> **cyberpunk3 said:**
> 
If I put the "default" ubuntu-12.04-desktop-amd64.iso on it, can it be migrated to 14.x later on, while keeping all settings and customizations?

You can see my opinion on upgrades in the link in my signature.

Why not install 14.04 right away?

---

### Post by cyberpunk3 on 2014-08-31
So I went straight to the 64-bit 14.04.1, as it worked more or less normally running "live" from USB, and 'free -m' didn't show anything weird (and it was about the same in both 32- and 64- bit versions when running the same applications).

I wanted dual boot with Windows 7 (which had already been there), so I chose the "Install Ubuntu alongside Windows 7" option. I had about 70 GB of unpartitioned space at the end of the (SSD) drive. The installation went on without a glitch; however, I've noticed that only one partition was created there (no swap even), with an additional 1.99 GB of unpartitioned space at the end (gparted says "unknown").

I also checked the starting offsets with msinfo32 in Windows, and noticed that the Ubuntu's partition starts with a number which doesn't equal a whole number when divided by 4096 -- which means incorrect alignment on SSD, as far as I know.

Is this normal, or should have I just used manual partitioning instead?

---

### Post by mörgæs on 2014-08-31
Please post the output from **sudo parted -l** in CODE tags.

---

### Post by cyberpunk3 on 2014-09-01
Below is the output. I guess the last partition is meant for swap, and the errors are related to "the disk drive for /dev/mapper/cryptswap1 is not ready yet or not present" which is displayed just before the system boots.

```
Model: ATA Crucial_CT256MX1 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  55,6GB  55,6GB  primary   ntfs         boot
 2      55,6GB  183GB   127GB   primary   ntfs
 3      183GB   256GB   73,4GB  extended
 5      183GB   254GB   71,3GB  logical   ext4
 6      254GB   256GB   2136MB  logical
```

The partitions are as follows: /dev/sda1, /dev/sda2, /dev/sda3, /dev/sda5, /dev/sda6.
The red circle with an exclamation mark in GParted is in front of sda1 and sda6.

---

### Post by mörgæs on 2014-09-01
Yes, 2 GB at the end of the disk sounds like a classical swap setup. I don't know why it's not used. I'm not on Buntu so can't dig any further right now. 

What does the red exclamation mark say?

---

### Post by cyberpunk3 on 2014-09-01
The exclamation mark at sda1 says:
```
Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ntfs file system support:  ntfsprogs / ntfs-3g.
```

The one at sda6 says:
```
Unable to detect file system! Possible reasons are:
- The file system is damaged
- The file system is unknown to GParted
- There is no file system available (unformatted)
- The device entry /dev/sda6 is missing
```

I also checked the partitions with "fdisk -lu /dev/sda". The output is as follows:
```
Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0004b62f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   108546047    54272000    7  HPFS/NTFS/exFAT
/dev/sda2       108546048   356757503   124105728    7  HPFS/NTFS/exFAT
/dev/sda3       356759550   500117503    71678977    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5       356759552   495943679    69592064   83  Linux
/dev/sda6       495945728   500117503     2085888   82  Linux swap / Solaris
```

This one is more detailed, and as far as I can see, there's 2047 bytes between sda2 and sda3, and 2049 between sda6 and sda5. At first sight it looks as some sort of misalignment, but then again, I'm not an expert at this. It was done automatically by the default Ubuntu installer, and maybe it's because extended partition is used in this case? Or should I use a tool to correct this?

---

### Post by mörgæs on 2014-09-02
I don't do double boots so I can't help you here, sorry.

Moved the thread to General Help and changed the title in order to attract some better advice. There's no reason to suspect a hardware problem.

---

### Post by dragonfly41 on 2014-09-02
The incorrect geometry might be fixed using testdisk utility ..

[http://ubuntuforums.org/showthread.php?t=2203661](http://ubuntuforums.org/showthread.php?t=2203661)

but check the testdisk web site and their forum.

---

### Post by fantab on 2014-09-02
EEE PC also has models that have 64bit cpu 'tweaked' to underperform in 32bit only...
I would recomend a lighter ubuntu like Xubuntu on that machine. I had one with xfce and fared qute well.
By the way, 12.04 is a good choice as well...

I think you have encrypted swap partition for some reason.
The output of:
```
sudo fdisk -l
```
should give more info on the first partition.

---

### Post by cyberpunk3 on 2014-09-02
I somehow manage to solve the issues with exclamation mark. Yes, the problems with the unknown/swap partition were encryption-related, that's been fixed as well.

The only unresolved question from this thread now remains -- should I or shouldn't I realign the partitions (as for the TRIMming, I suppose adding fstrim to crontab to be run daily/weekly should do the trick). The more I read various discussions on this topic around the internets, the less I know (the easiest was at the beginning, when all I knew was that the starting offset should be divisible by 4096...). :)

EDIT:
From what I can tell now, the extended partition is just a placeholder for logical partitions, and can thus be misaligned (as above), as it's read only on boot - only primary and logical partitions (which are those that contain actual data/files with which the system works) must be aligned correctly.

---


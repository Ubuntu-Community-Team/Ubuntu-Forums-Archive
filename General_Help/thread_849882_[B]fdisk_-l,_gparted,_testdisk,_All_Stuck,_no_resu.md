---
title: "[B]fdisk -l, gparted, testdisk, All Stuck, no results HELP [/B]"
date: 2008-07-05
forum: General Help
---

### Post by Keller on 2008-07-05
Neither of these programs is getting anywhere analyzing my disk, what can I do?
I thought the new Thread title was appropriate, as this is a more Ubuntu related problem than my previous post ([http://ubuntuforums.org/showthread.php?t=849854](http://ubuntuforums.org/showthread.php?t=849854))

Any Help would be amazing,
thanks

---

### Post by VMC on 2008-07-05
What do you mean no results. You mean no outputs? Are you booting up using Livecd or live system?

Clarify, please.

---

### Post by Keller on 2008-07-05
I'm booting from LiveDisk, and by no results I mean:
sudo fdisk  -ln is followed by about 15 minutes of nothing, than it just jumps to a command line again.

gparted stays stuck on "Scanning all Devices" The only outup in console is:
> ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 1.7.1
======================
Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only.
Unable to open /dev/scd0 - unrecognised disk label.



When I run Testdisk, I can click on Analyse, and the next screen says
> TestDisk 6.6, Data Recovery Utility, February 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
Checking current partition structure





*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted


And stays like that for about 30 minuts, nothing happening, eventually the window closes, or alternatively sometimes it gives me the option to quick scan after about that much time, again, with no results.

Thanks for taking the time to help me with this

---

### Post by VMC on 2008-07-05
> **Keller said:**
> :
sudo fdisk  -ln is followed by about 15 minutes of nothing, than it just jumps to a command line again.

Was that a typo: It should read

```
sudo fdisk -l
```

But if gparted can't scan then you have other issues. Does your BIOS reconize your hard drives okay? What info does it say.

---

### Post by Keller on 2008-07-05
yes, sorry, it was supposed to be -l

My bios does recognize the hard drive, from the bios everything looks fine as far as I can tell, it seems to be the partitioning that's messed up. I actually was able to see my volumes in gparted about 3 reboots ago, but I restarted to disable my (nonexistant) floppy drive to make it go faster, and since then it has been silent.

Testdisk just finished one more time and tells me "partition read error"

When I select "proceed" it stays at this and does not proceed:

> Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
Analyse cylinder     0/30400: 00%



---

### Post by cariboo on 2008-07-05
It looks like you are trying to partition your cd drive /dev/sd0.

Do you actually have a partition on drive /dev/sda? Try opening a terminal and at the prompt type:

```
fdisk /dev/sda
press m for help
```

this will list a lot of options including deleteing and create partitions, get familiar with all the functions and you should be able to partition your hard drive.

Jim

---

### Post by VMC on 2008-07-05
Maybe somethings wrong with the burn of the livecd. Did you do a media check first?

---

### Post by Keller on 2008-07-05
Well, I am not trying to partition my hard drive. I am trying to recover the partitions I already have. There should be:
dev/sda1 ext3 (general files)
dev/sda2 NTFS (Windows Partition
dev/sda3 ext3 (Linux files)
dev/sda5 swap

at least that is what was there last time gparted started. I just tried inserting my windows life disk, and it finds 3 partitions of which it recognizes none and says they are all empty.

The live CD should be fine, because I have used it for the past 3 months and just a couple of reboots ago it was all still showing results. So I am actually trying to recover some data and not just format over the entire disk, if possible.

Here is the result of fdisk:

> ubuntu@ubuntu:~$ fdisk /dev/sda

Unable to open /dev/sda


---


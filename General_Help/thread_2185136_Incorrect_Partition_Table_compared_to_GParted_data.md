---
title: "Incorrect Partition Table compared to GParted data"
date: 2013-11-01
forum: General Help
---

### Post by stuartmcfadyen on 2013-11-01
I had a major crash on my Ubuntu 9.04 system due to a battery failure at startup, half way through loading Linux. 

I was prompted to run **fsck ** a couple of times on re-start, with power supply connected, which, on completion enabled me to boot the system. However a large number of my programs would not run.

I decided to restore a old 40MB backup image to my current 250MB drive (GParted could resize the Partition later), but to my horror this failed with a file error. Despite this I was able to boot the system, presumably, as so little data had been written from the backup image.

I re-installed the non-working programs and in summary the system now appears to work normally .... HOWEVER ...

The HARDINFO Hardware Report shows a 40MB disk size.

GParted shows a 200MB+ Partiton with far more data content than I know to be true, (should be about 70MB in total).

**df** shows circa 40GB with free space of 18GB, which is the same as the free space shown on the 250GB GParted list.

What is going on ? Can anyone tell me how to correct this situation without having to re-install UBUNTU as clearly
my image backup is a failure !

I have posted images of relevant details below (CLICK them to see larger) ....

[ATTACH=CONFIG]247445[/ATTACH]
[ATTACH=CONFIG]247446[/ATTACH]
[ATTACH=CONFIG]247447[/ATTACH]
[ATTACH=CONFIG]247448[/ATTACH]

---

### Post by fantab on 2013-11-01
Post the output of:

```
sudo fdisk -l
```

You are using 9.04 which reached its 'end of life' [eol] on 23 October 2010. [See Here]("https://wiki.ubuntu.com/Releases").
Any special reason for this?
If I may suggest INSTALL latest Ubuntu which is 13.10. Backup all your Important DATA and Install latest Ubuntu.

---

### Post by stuartmcfadyen on 2013-11-01
Thanks for reply ... 9.04 up to now has been extremely stable for my aging Dell Laptop ! 
latest 13.10 and Mint etc will not load due to laptop not supporting **PAE** (Physical Adress Extension) for more than 2GB.

See below **fdisk -l** output

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29003   232966112+  83  Linux
/dev/sda2           29004       30401    11229435   82  Linux swap / Solaris

---

### Post by mörgæs on 2013-11-01
Here's more info about solving the [PAE]("https://help.ubuntu.com/community/PAE") problem. You could also try Bodhi mentioned in my signature.

As posted above a fresh install is recommended.

---

### Post by stuartmcfadyen on 2013-11-02
Thanks morgaes for the info. 
Question ... if I modify only the /proc/cpuinfo on my existing 9.04 system will I be able to test Live Distros for current releases, which I cannot at the moment ?

---

### Post by mörgæs on 2013-11-02
A live boot does not respond to any settings in the operative system on the hard disk. 

In stead of a live boot you could run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags. This will tell us how well your hardware works with the latest releases.

---


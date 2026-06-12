---
title: "error ----&gt;  SDB: assuming drive cache: write through"
date: 2007-06-06
forum: General Help
---

### Post by GPro44 on 2007-06-06
Hey running 7.04 (64bit version) on a 250gb Sata Harddrive,  I also got a 8800gts which is given me troubles but for now my problem seems like its with the hard drive.  When I hit Cntrl-Alt F2 or any other one, every three to four seconds I get an error message (really annoying, not letting me change my x11 files or anything else,  without screwing it up since it puts the error where ever my cursor isi) 

ERROR MESSAGE: [   123.23232] sdb: assuming drive cache: write through

heres some info 

hdparm /dev/sda
/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 30401/255/63, sectors = 488397168, start = 0

hdparm /dev/sdb
/dev/sdb:
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 1024/0/62, sectors = 0, start = 0

sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/sda2           16709       23082    51199155    7  HPFS/NTFS
/dev/sda3           23083       30096    56339955   83  Linux
/dev/sda4           30097       30401     2449912+   5  Extended
/dev/sda5           30097       30401     2449881   82  Linux swap / Solaris


Thanks for the Help

---

### Post by brallan on 2007-09-01
I've got the same problem:
On a fresh install of Feisty Fawn, after ```

sudo apt-get update
sudo apt-get upgrade

```I am getting this error in all of my six terminal windows (by pressing <CTRL><ALT><F1>, etc.) even before logging in, it's a scrolling error, repeating several lines such as:

```

[ 3455.843530] sdd: assuming drive cache: write through 
[ 3455.846700] sdb: assuming drive cache: write through 
[ 3456.129340] sdb: assuming drive cache: write through 
[ 3456.342509] sdc: assuming drive cache: write through 
[ 3456.424511] sdb: assuming drive cache: write through 
[ 3456.843530] sdd: assuming drive cache: write through 
```

after recieveing the error, i aborted (CTRL-C) but the error is persisting.

Anyone know what this means?

---

### Post by brallan on 2007-09-01
ugh,

i tried updating the system using the Update Manager, and when I rebooted, the system wouldn't let me past the login screen and the error message continued on all 6 terminal screens. I suspect either a RAM or a motherboard problem.

---


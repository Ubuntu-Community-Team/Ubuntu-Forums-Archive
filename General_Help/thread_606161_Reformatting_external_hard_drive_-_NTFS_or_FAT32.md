---
title: "Reformatting external hard drive - NTFS or FAT32?"
date: 2007-11-07
forum: General Help
---

### Post by bluepowder7 on 2007-11-07
i've got this 250Gig hard drive that i plan on using in a USB enclosure for backup and file storage purposes.  there's stuff on there now, but i'll move it over shortly, so that i can do a full clean format.  since i want this external hard drive to be usable by WinXP, Linux (most distros), and evetually FreeBSD, what's the best way to format it?  NTFS or FAT32 or ext2?  i'd rather format it once and just stick with what it is than have to shuffle stuff around to change formats later on.  i also want this thing to be as idiot-proof to hook up and read from / write to as humanly possible - the way pencil is inherently compatible with paper 99.99999999999% of the time.

NTFS?  FAT32?  ext2?  other?

considering there's only one flavour of WinXP and numerous flavours of Linux / BSD, would i get the best overall performance by formatting it to one of the other types (ext2 or jfs or whatnot), and then using a utility in WinXP to access it (rather than having an NTFS or FAT32 utility installed in every linux / bsd distro that i happen to be using)?

---

### Post by ofb on 2007-11-07
Take FAT32 off your list unless you'll be using an old Windows like w95/98/Me. It /used/ to be the most neutral until we got utlities for NTFS, but it's also old so quite a nuisance with a smaller character choice for filenames.

---

### Post by bluepowder7 on 2007-11-07
i don't intend on working with or having any computer with an OS more archaic than Win2k - just gonna stick with XP on my two machines for specific windows applications and games, and add on the linux / bsd stuff.

ok, so no point in dealing with FAT at all?  so, what's left - NTFS and the multitude of linux'ish file systems, like ext2 and jsf and reiser.  from what little i've learned so far, NTFS had to be reverse-engineered, so i'm a little bit hesitant in using it with linux / bsd.  are the other file systems like ext2 or whatnot more "open" such that there might be nicely written drivers for them for WinXP to use?

---

### Post by mahousaru on 2007-11-07
If you go down the ext route and use the IFS ext2 driver in Windows then be warned that currently the driver does not handle UTF8 file names properly.  So if you use different languages for your file names it will corrupt when you copy it over.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by NT4usB on 2007-11-07
I have a bunch formatted NTFS and they play well with Ubuntu. Don't know about other distros though.
I recently formatted a couple ext3 and shared them off the Ubuntu box, I write to them from 2K/XP no problem.
I haven't broken any of the NTFS drives, playing with them from Ubuntu. I've already broken (and quickly recovered using e2fsck) one of the ext3 formatted drives on Ubuntu.
Might have been an anomaly, or ext3 might not be as robust. Not enough data to say for sure.
I haven't tried to mount the ext3 drives on 2K/XP and don't know if it is possible.

---

### Post by bluepowder7 on 2007-11-07
UTF8 file names?  hmm...  is that something i can have some level of control over?  i never use non-ASCII characters in file names, not even the french "e" versions or anything unusual at all, so am i likely to have a problem?  much of what i will be storing will be audio and video files which i tend to rename myself anyways to keep the file name useful and descriptive.  the rest of the stored material would be work files: typical documents,  spreadsheets, presentation slides, etc (made from MS Office or OpenOffice).

---

### Post by Tekno_Cowboy on 2007-11-07
Go with FAT32. Some people may think its a little old, but if you're looking for the least problems going cross platform, it is your best bet. I've found the NTFS drivers in Ubuntu to be fairly buggy, at least with my setup, and the ext drivers in Windows tend to have problems too. FAT32 works without any extra work on most OS's.

---

### Post by 3rdalbum on 2007-11-07
If you're never going to be using files that are more than 4 gigabytes in size, then Fat32 is a good choice. (remember, a shrinked DVD ISO is more than 4 gigabytes).

NTFS is a good choice if you want to put large files on it. The driver for Linux is stable, if a little slow; the only gotcha is that you occasionally need to boot into Windows to run a filesystem check on NTFS. (this may change in the future). And of course, there's no 4 gigabyte file size limit like there is on Fat32.

I don't recommend installing an Ext2/Ext3 driver on Windows; I worry about cross-platform viruses being developed to take advantage of dual-booters to install themselves on Linux systems.

---

### Post by grim4593 on 2007-11-07
The problem with FAT32 is that it doesn't have large file support. So if you are trying to mess around with dvd isos or large archive files you can run into a problem.

NTFS runs fine in Ubuntu, but i find it's a bit slow when copying large files.

What I did was split my external drive into two partitions. One ext3 and the other fat32. Both operating systems can read/write to them (windows can access ext partitions with [http://www.fs-driver.org/](http://www.fs-driver.org/) ), and you don't have to worry about running into a problem if you deal with large files at any point.

---

### Post by Tekno_Cowboy on 2007-11-08
My results may not be typical, but with my Samsung 500GB drive, I only get a 4 M/s external transfer rate, and a 16 M/s internal transfer rate with NTFS. I get about 45 M/s for both with ext3, with higher bursts.

OOPS! hit the wrong button :(

I get somewhere near the same speed with FAT32 as I do with ext3.
This is all on Kubuntu. In Windows the rates are about even, but I get massive ext3 filesystem corruption.

---

### Post by timcredible on 2007-11-08
if you want windows to access it, use fat32.  if you want to do backups in linux, you'll need ext3 because fat32 doesn't have file permissions or ownerships.  so, what to do?  maybe you should do like i did and format part of your drive fat32 for windows and linux to use, and part of it ext3 for linux backups.  i have some info on doing backups and formatting drives for backup at [http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=50&Itemid=27](http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=50&Itemid=27)

---

### Post by bluepowder7 on 2007-11-08
hmm, good points on the file size limit in FAT32.  and ya, i also noticed that moving stuff from my FAT32 USB memory stick was WAY faster when going to (and from) the ext2 that's on my linux box than the NTFS on the winxp machine (very likely 4 times faster when moving a lot of medium size files).

ya, i'm beginning to think that making two partitions might be the way to go overall - do both FAT32 and ext2 partitions.  i'm avoiding ext3 because of the lack of an undelete function - something which bit me in the **** not long ago when i lost many of my work files that happened to be stored on an ext3 /home partition (ouch).



now, for making backups - how big should the ext2 partition on the external drive be?  is it some fraction of the /home partition that i use for all my docs and whatnot?  currently, my /home is around 60gigs, so how big of a partition should i allocate for backups?  same size?  a quarter?  the drive that's currently set aside for this purpose is a 250gig.

---

### Post by MCMcButtah on 2007-11-08
I started using the ntfs-3g driver since it was in beta with my 500 external and havn't had any problems and it has been more than a year i think. Its a little slow in transfers, but much quicker than it used to be. I needed ntfs because I have many files over 4 gig. Also the amount of wasted space with fat32 on a 500gig drive is substantial.

---

### Post by crjackson on 2008-01-16
> **bluepowder7 said:**
> i've got this 250Gig hard drive that i plan on using in a USB enclosure for backup and file storage purposes.  there's stuff on there now, but i'll move it over shortly, so that i can do a full clean format.  since i want this external hard drive to be usable by WinXP, Linux (most distros), and evetually FreeBSD, what's the best way to format it?  NTFS or FAT32 or ext2?  i'd rather format it once and just stick with what it is than have to shuffle stuff around to change formats later on.  i also want this thing to be as idiot-proof to hook up and read from / write to as humanly possible - the way pencil is inherently compatible with paper 99.99999999999% of the time.

NTFS?  FAT32?  ext2?  other?

considering there's only one flavour of WinXP and numerous flavours of Linux / BSD, would i get the best overall performance by formatting it to one of the other types (ext2 or jfs or whatnot), and then using a utility in WinXP to access it (rather than having an NTFS or FAT32 utility installed in every linux / bsd distro that i happen to be using)?

```
charles@MSI-K8N-Neo4-SLI-Platinum:~$ sudo apt-get install ntfsprogs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fftw3 libtunepimp5 python-qt3 python-sip4 libifp4 libofa0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libntfs9
The following NEW packages will be installed:
  libntfs9 ntfsprogs
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 400kB of archives.
After unpacking 1012kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com gutsy/main libntfs9 1.13.1-6 [125kB]
Get:2 http://us.archive.ubuntu.com gutsy/main ntfsprogs 1.13.1-6 [275kB]
Fetched 400kB in 1s (270kB/s)     
Selecting previously deselected package libntfs9.
(Reading database ... 133057 files and directories currently installed.)
Unpacking libntfs9 (from .../libntfs9_1.13.1-6_amd64.deb) ...
Selecting previously deselected package ntfsprogs.
Unpacking ntfsprogs (from .../ntfsprogs_1.13.1-6_amd64.deb) ...
Setting up libntfs9 (1.13.1-6) ...

Setting up ntfsprogs (1.13.1-6) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
charles@MSI-K8N-Neo4-SLI-Platinum:~$ mkntfs

Usage: mkntfs [options] device [number-of-sectors]

Basic options:
    -f, --fast                      Perform a quick format
    -Q, --quick                     Perform a quick format
    -L, --label STRING              Set the volume label
    -C, --enable-compression        Enable compression on the volume
    -c, --cluster-size BYTES        Specify the cluster size for the volume
    -I, --no-indexing               Disable indexing on the volume
    -n, --no-action                 Do not write to disk

Advanced options:
    -s, --sector-size BYTES         Specify the sector size for the device
    -p, --partition-start SECTOR    Specify the partition start sector
    -H, --heads NUM                 Specify the number of heads
    -S, --sectors-per-track NUM     Specify the number of sectors per track
    -z, --mft-zone-multiplier NUM   Set the MFT zone multiplier
    -T, --zero-time                 Fake the time to be 00:00 UTC, Jan 1, 1970
    -N, --ntfs-version VERSION      NTFS version: 3.1 (default) or 1.2 (old)
    -F, --force                     Force execution despite errors

Output options:
    -q, --quiet                     Quiet execution
    -v, --verbose                   Verbose execution
        --debug                     Very verbose execution

Help options:
    -V, --version                   Display version
    -l, --license                   Display licensing information
    -h, --help                      Display this help

Developers' email address: linux-ntfs-dev@lists.sf.net
Linux NTFS homepage: http://www.linux-ntfs.org

charles@MSI-K8N-Neo4-SLI-Platinum:~$ 
```

---


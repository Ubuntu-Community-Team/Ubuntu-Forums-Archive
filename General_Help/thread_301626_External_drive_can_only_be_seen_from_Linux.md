---
title: "External drive can only be seen from Linux"
date: 2006-11-17
forum: General Help
---

### Post by Scheater5 on 2006-11-17
Ok, so this is not exactly a Linux problem.  In many ways it's praise of Ubuntu.  I have a Seagate 140Gb harddrive.  For a year or so it worked perfectly with Windows, Mac and Linux.  I plugged it into my friend's Mac and it worked with no problem, transferred files to the Mac, even had write capability if I remember correctly.  Then the very next day, it wouldn't recognize the drive.  I believe the message was something akin to "Cannot open drive."  A few days later I tried it on my Windows PC, and a similar problem.  I have neither a PC nor a Mac on me, but just as soon as I get the chance I'll post the exact error messages.  But Linux, ironically, still has plug 'n' play read and write capability - never required any configuring or reformatting.  
If anyone has any idea why it would suddenly not be recognized, I'd appreciate the help.  Thanks guys.

---

### Post by taurus on 2006-11-17
You mean it's now suddenly both Windows and Mac don't recognize the harddrive anymore while Linux still does!  What filesystem does it use anyway?

---

### Post by Scheater5 on 2006-11-17
That's precisely what I mean.  I'll have more specs for you soon - don't have anything but my laptop on me now.  I want to say its FAT32...but I'm not certain.  It worked perfectly fine with Windows and Linux - both read/write - for almost 6 months.  It may have been the first time I used it with a Mac that it actually worked, and then the second it didn't.

---

### Post by Scheater5 on 2006-12-10
Ok, so I haven't responded to this in a while - first because of exams, and then because of a new problem.  I can't tell what filesystem the USB drive is.  Small problem - except that the reason I can't tell is because I can't access it.  Under any OS.  Tried plugging in and then turning on,  hotplugging, and booting the system while both on and off - nothing.  Tried mounting all sda's and hda's found under /dev on media, and in a directory created in /mnt.  Nothing.  Anyone have any ideas?

---

### Post by Scheater5 on 2006-12-10
Alright, booted into a LiveCD (I happened to have one of a Feisty snapshot handy) and Gnome Partition Editor lists it as sdb.  So I made a directory called seagate in /mnt.  

```
ubuntu@ubuntu:/mnt/seagate$ sudo mkdir /mnt/seagate
ubuntu@ubuntu:/mnt/seagate$ sudo mount /dev/sdb /mnt/seagate
mount: you must specify the filesystem type

```

How the ---???  The Gnome Partition Editor lists the filetype as unknown and the disklabel as msdos.  And I am confused.

---

### Post by Scheater5 on 2006-12-10
```
ubuntu@ubuntu:/mnt/seagate$ sudo mount -t msdos /dev/sdb /mnt/seagate
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
```
ubuntu@ubuntu:/mnt/seagate$ dmesg | tail
[ 1014.612000] cramfs: wrong magic
[ 1014.656000] Unable to identify CD-ROM format.
[ 1014.664000] SQUASHFS error: Can't find a SQUASHFS superblock on sdb
[ 1014.664000] VFS: Can't find ext3 filesystem on dev sdb.
[ 1461.132000] cramfs: wrong magic
[ 1461.176000] Unable to identify CD-ROM format.
[ 1461.184000] SQUASHFS error: Can't find a SQUASHFS superblock on sdb
[ 1461.184000] VFS: Can't find ext3 filesystem on dev sdb.
[ 2246.564000] FAT: invalid media value (0xb9)
[ 2246.564000] VFS: Can't find a valid FAT filesystem on dev sdb.

```

---

### Post by Scheater5 on 2006-12-10
```
ubuntu@ubuntu:/media$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3379    27141786   83  Linux
/dev/sda2   *        3380        4618     9952267+  83  Linux
/dev/sda3            4619        4864     1975995    5  Extended
/dev/sda5            4619        4676      465822   82  Linux swap / Solaris
/dev/sda6            4677        4864     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19455   156272256    c  W95 FAT32 (LBA)

```

Doesn't that mean it's a FAT32 filesystem?

```
ubuntu@ubuntu:/media$ sudo mount -t fat32 /dev/sdb /mnt/seagate
mount: unknown filesystem type 'fat32'
mount: maybe you meant 'vfat'?
```

---

### Post by Scheater5 on 2006-12-11
Alright, did some research and found that you can mount fat32 as vfat in Ubuntu.  But same problem

```
scheater5@scheater5-laptop:~$ sudo mount -t vfat /dev/sdb1 /mnt/seagate
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by Scheater5 on 2006-12-11
Testdisk yields this message

Disk /dev/sdb - 160 GB / 149 GiB - CHS 19457 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors
check_FAT: Bad jump in FAT partition
 1 * FAT32 LBA                0   1  1 19454 254 63  312544512
 1 * FAT32 LBA                0   1  1 19454 254 63  312544512


"Bad jump in FAT partition" - that sounds like the problem to me.  Anyone know how to correct such an error?

---

### Post by technodigifreak on 2006-12-11
> **Scheater5 said:**
> Testdisk yields this message

Disk /dev/sdb - 160 GB / 149 GiB - CHS 19457 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors
check_FAT: Bad jump in FAT partition
 1 * FAT32 LBA                0   1  1 19454 254 63  312544512
 1 * FAT32 LBA                0   1  1 19454 254 63  312544512


"Bad jump in FAT partition" - that sounds like the problem to me.  Anyone know how to correct such an error?

Have you tried running fsck on this partition?  I know it was designed for an ext2 fs, but I believe it is capable of checking other file systems, including vfat/fat32.  If not, you should be able to run a filesystem check on it from your XP machine.  This may be a case of screwed up partition table or (I really hate saying this...) bad sectors on the HDD.  Approximately how old is this drive?

---

### Post by Scheater5 on 2006-12-11
Thanx technodigifreak - but I figured it out, and it's the worst possible news.  I botched an attempt to turn a different computer into a Mac-intel, and I couldn't figure out where all the information was written to, since that computer still worked perfectly and it should have had a completely re-written harddrive.  I found it.
The external.  Not only did it erase all my backup date, but it didn't even work.  So now it's back to the drawing board.  The good news is that it's horrible, but not catastrophic.  I still have all I need to do my work on this computer.  I just have to replace my (rather extensive) music and video collection.  Joy.  I'm so buying another drive exclusively for backup after Christsmas...

---


---
title: "USB Transfer rate drops hard on large files"
date: 2019-05-24
forum: General Help
---

### Post by Drowz0r on 2019-05-24
Hello all

If I ever transfer a large file, the file transfer rate seems to bomb at around 1.2GB.

This happens with MP4s, or ISOs or anything really.

The file will shoot through on USB 2.0 or 3.0 speeds quite happily but upon reaching that 1.2GB mark the file rate drops, very quickly, down to about 2.2MB/sec.

I have tried on 320GB USB 2.0 external HDDs. 2.0GB USB 2.0 flash drives and 1T/2T USB 3.0 external HDDs as well all with the same result.

I have tried using different USB ports on my PC.

This is a reasonably recent development, in the last month or so I think.

If I do manage to get anything on the drive(s), once connected to another machine they function correctly.

I have tried on exFAT and FAT systems but it doesn't make any difference. NTFS I'm unable to copy to (I guess that's normal) and I need to transfer things around to windows and other machines to EXT# isn't an option.

The type of file doesn't make any difference.

Sometimes I'll just try and wait it out, moving the last 200MB at 2.2 MB/Sec and this will sometimes work - other times it will hang on something lke "1.4 GB og 1.4 GB  - 0 seconds left (2.2MB/sec).

Hope someone can help

---

### Post by TheFu on 2019-05-24
Try using NTFS. It doesn't have the limitations that all FAT file systems have on large file sizes and large disks. [http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)

```
$ more ~/bin/mnt-usb-ntfs
#!/bin/bash

LABEL1=PortMedia 
UID=1000
GID=1000
OPT1="big_writes,uid=$UID,gid=$GID"

 mkdir -p /mnt/$LABEL1  
 mount -o $OPT1 LABEL=$LABEL1 /mnt/$LABEL1
```
You'll need to use sudo with this script and change the LABEL1 to match whatever label your NTFS partition has. See the "big_writes" option? That is a work-around for NTFS slow performance that should help about 30%. You can use it anywhere mount options are supports, so in an fstab or in autofs config files are both fine.  The script assumes the main userid is accessing the partition. If not, change the UID/GID settings.

Have you considered that the data has to be written to disk/storage at some point and that after the disk buffers are full, slow write speeds are the likely issue?

NTFS is probably the best file system for your needs (cough, Windows), assuming the "write" is to spinning disks. Just be certain to mount it either in the fstab or with a mount command. Avoid using gvfs or gio for the best performance. Both of those GUI methods are known to have terrible performance, though performance fixes were supposed to have been made last year. I saw more planned for 2019.

You can watch the disk buffers use free RAM using the **free -h** command. As more RAM is used for programs and program data, the amount available for disk and network buffers is reduces.

---

### Post by HermanAB on 2019-05-24
Hmm, Windows has only two file systems: NTFS and ReFS.

Those other things that were mentioned aren't really file systems...
;)

---

### Post by Drowz0r on 2019-05-24
My issue is, FAT and exFAT or whatever should be able to handle the file sizes I'm moving without this issue. It only seems to happen on my ubuntu machine - other machines transfer the data without issue.

---

### Post by Drowz0r on 2019-05-24
FWIW I managed to format to NTFS and get it so it would let me copy over files.

The file copies to 1.4 of 1.4 and then the transfer rate slowly drops with "0 seconds left" remaining on the transfer.

Seems to be the same regardless of file system.

---

### Post by HermanAB on 2019-05-24
$ split -b 500M filename
$ cp filename* /whereeveritis/usbkey/.

C:\> copy file1+file2+file3 filename

---

### Post by Mark Phelps on 2019-05-25
Have run into the same problem transferring files between Linux filesystems -- so this is not just an NTFS problem.

---

### Post by HermanAB on 2019-05-25
You can also try ionice.  It helped with a previous USB bug.

---

### Post by TheFu on 2019-05-25
> **Drowz0r said:**
> FWIW I managed to format to NTFS and get it so it would let me copy over files.

The file copies to 1.4 of 1.4 and then the transfer rate slowly drops with "0 seconds left" remaining on the transfer.

Seems to be the same regardless of file system.

Dude, don't leave me hanging.

Did you use the mount with the big_writes option on the NTFS for higher performance xfers?  
Did that help or not?  We're guessing blind here without feedback.

I took some time this evening to test my copies 
FROM USB2 NTFS source (refurb WD Blue 250G)
TO  SATA3 EXT4 target (WD Blue 1TB) 
THRU USB3 port on the system.

Result was: **38 Mbps which turns into 4.75 MBps.**

Mount options are:```

 /dev/mapper/vg--hadar-lv--backups on /Backups type ext4 
     (rw,noatime,errors=remount-ro,data=ordered)
 /dev/sdb1 on /misc/250G type fuseblk 
     (rw,nosuid,nodev,noatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096)
```

The source file was 11423419785 bytes and took 4m45.776s clock time - that's a stopwatch-like time. I used the "time cp SOURCE TARGET" command.
Did 5 other files in series. Most were over 3G in size, 1 was only 1.4G.  They were all around 38 Mbps. Guess that's the limitation of this specific hardware.  With USB2 ports on a system, I typically see about 20-22 Mbps.

Nothing special about the setup. Cheap disks, USB2, just using good file system options already provided.

[https://superuser.com/questions/317217/whats-the-maximum-typical-speed-possible-with-a-usb2-0-drive/995350](https://superuser.com/questions/317217/whats-the-maximum-typical-speed-possible-with-a-usb2-0-drive/995350) suggests that 42Mbps would be towards the highest possible.

If you can, please test the big_writes option on your USB/NTFS mount.

If you are using a GUI to do the mounting, I don't know how to get that big_writes option. Plus, the GUI transfers are always slower than from a shell, IME.  Always.

---

### Post by Drowz0r on 2019-06-25
I honestly don't think this is that complicated tbh.

I don't opt to mount anything specific. I plug in a USB stick, or USB HDD, or anything into the PC and just copy files over.

Any files around 1.5GB or so just lag and hang. Even if the transfer does eventually complete the files are often corrupt.

What are you asking me to do? Because I don't really understand any of the above.

---

### Post by Drowz0r on 2019-06-25
> **HermanAB said:**
> You can also try ionice.  It helped with a previous USB bug.

Could you explain?

---

### Post by #&amp;thj^% on 2019-06-25
From the man page:
```
IONICE(1)                        User Commands                       IONICE(1)

NAME
       ionice - set or get process I/O scheduling class and priority

SYNOPSIS
       ionice [-c class] [-n level] [-t] -p PID...
       ionice [-c class] [-n level] [-t] -P PGID...
       ionice [-c class] [-n level] [-t] -u UID...
       ionice [-c class] [-n level] [-t] command [argument...]

DESCRIPTION
       This  program  sets or gets the I/O scheduling class and priority for a
       program.  If no arguments or just -p is given, ionice  will  query  the
       current I/O scheduling class and priority for that process.

       When  command is given, ionice will run this command with the given ar&#8208;
       guments.  If no class is specified, then command will be executed  with
       the "best-effort" scheduling class.  The default priority level is 4.
```
Your specs are about identical as mine, I don't see the slow speeds in transfers as you do though.
BTW I don't have  to use ionice though.;)

---


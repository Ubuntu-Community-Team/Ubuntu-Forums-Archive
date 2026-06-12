---
title: "[SOLVED] Mounting Windows Partition"
date: 2007-12-30
forum: General Help
---

### Post by dstein on 2007-12-30
On my other machine, I have two separate Hard Drives, one with Ubuntu and one with Windows XP. Upon installing Ubuntu on that machine, the operating system automatically recognized my Windows installation (and everything on the corresponding drive), and mounted the drive with an icon being placed on the desktop. I believe it says "Windows XP Desktop". It gives me direct access to the NTFS partition/drive that Windows is installed on.

I just installed Ubuntu on an older machine. The machine only had one drive, so I have a few partitions to allow for two operating systems, Windows and Ubuntu, Unfortunately, Ubuntu does not automatically recognize and mount the Windows partition. To access the drive, I must go to "Places", then "Computer", which opens a Nautilus window that lists all my drives (Floppy, 2 CD Drives, 'Filesystem', and 13.1GB Volume). The 'filesystem' icon gives access to the Linux files. When double-clicking the "13.1GB Volume" icon, I am asked for my password, then a window is opened briefly that says "opening ...". Then it opens my Windows partition, and I can access the files. At this point, an icon is also placed on the desktop that is labeled "disk", which allows access to that partition (no longer requiring a password). Please note that I referred to my Windows C:\ drive as a partition because it is not on a physically separate drive, unlike my other machine.

Can someone please guide me in setting up Ubuntu to automatically recognize and mount this partition everytime I boot.

Thanks for any help!!!

---

### Post by jken146 on 2007-12-30
[www.psychocats.net/ubuntu/mountwindows](www.psychocats.net/ubuntu/mountwindows)

---

### Post by dstein on 2007-12-30
Thank you. That seemed to work, although I have a few problems and questions.

First, I noticed that my drives are recognized as SCSI, and hence I had to add:
/dev/sda1       /Windows    ntfs nls=utf8,umask=0222 0 0

rather than:
/dev/hda1       /Windows    ntfs nls=utf8,umask=0222 0 0

Why does Ubuntu recognize my drive as SCSI, and associate all partitions with a SCSI drive? The drive is an old Western Digital IDE.

Also, this created a shortcut on my Desktop that reads '/Windows'. I would prefer that it didn't have the slash and read 'Windows'. How can I remove the '/' from all references to this partition (on my desktop, in nautilus, and in all other file browsing conditions)?

Lastly, I originally tried doing this with a directory called "Windows XP". I created this directory using "mkdir /Windows\ XP", which worked fine. However, the following entry caused errors when mounting:

/dev/sda1       /Windows\ XP    ntfs nls=utf8,umask=0222 0 0

Am I doing something wrong when creating files and directories that have spaces?

Thanks for all the help!!!

---

### Post by logos34 on 2007-12-30
> **dstein said:**
> 
Why does Ubuntu recognize my drive as SCSI, and associate all partitions with a SCSI drive? The drive is an old Western Digital IDE.

[https://launchpad.net/ubuntu/+spec/libata-for-all-ata-disks](https://launchpad.net/ubuntu/+spec/libata-for-all-ata-disks)

>  How can I remove the '/' from all references to this partition (on my desktop, in nautilus, and in all other file browsing conditions)?

Rename the drive in windows (right-click on volume in My Computer)

> Lastly, I originally tried doing this with a directory called "Windows XP". I created this directory using "mkdir /Windows\ XP", which worked fine. However, the following entry caused errors when mounting:

/dev/sda1       /Windows\ XP    ntfs nls=utf8,umask=0222 0 0

Am I doing something wrong when creating files and directories that have spaces?

try 

/dev/sda1 /"Windows XP" ...

---

### Post by dstein on 2007-12-31
In the psychocats tutorial, a mount point is created at the directory /Windows.
Suppose I wanted my system to mount to the same place it would mount by default, if I had double clicked the 'Windows XP' icon. I believe that it would mount it to /media/Windows\ XP by default.

How can I have it mount here by default? I know I have worded this strangely, but basically, in the fstab file, what would I but in the blank space below. I would like the partition to mount to a directory in the media folder, that automatically has the same name as what I have named the drive in Windows, as explained to me in a prior post. I named the drive 'Windows XP'.

# /dev/sda1       _________    ntfs nls=utf8,umask=0222 0 0


I am still not sure I explained myself properly. When I turn on my computer, my Windows partition does not mount by default. If I double click the icon in Nautilus, it will ask for my password and then mount the partition to some directory in /media, and it will have the same name as my partition.

How can I set my computer to do this automatically, such that it creates the same directory that matches the partitions name?


Thanks!!!

---

### Post by logos34 on 2007-12-31
I don't know why you're having such a problem.  Maybe it's the space...would 'WindowsXP' be acceptable?  Try that.  I know I can mount my ntfs partitions to mountpoints with same name as volume:

e.g. 

/dev/hda1  --> volume name 'C:_drive' 

I create a mountpoint /media/C:_drive and it mounts there. 

the drive icon shows up on desktop named 'C:_drive'

except I'm using ntfs-3g driver.  But I don't see how that affects things

---

### Post by dstein on 2007-12-31
logos, fortunately I am not having problems. My follow-up questions are from curiosity, not necessity. I have managed to have my system mount the drive fine. I was just wondering how to set it up in the most automated way possible, mostly out of curiosity. I still consider myself a newbie to Linux and I am just trying to learn as much as possible. Your responses have been very helpful. Thanks.

---


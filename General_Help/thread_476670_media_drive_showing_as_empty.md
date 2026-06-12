---
title: "media drive showing as empty"
date: 2007-06-17
forum: General Help
---

### Post by garymcgarrigle on 2007-06-17
my main media drive is showing as being completely empty  :(

i was away over the weekend at a stag and my girlfriend told me that while I was away there was a power outage (my PC was on at the time). Everything seems fine except my media drive (mounted as a fat drive) is now completely empty.

what can I do?

---

### Post by garymcgarrigle on 2007-06-17
tried running fsck but it didn't help. is there another syntax I should be trying?

gary@black:~$ sudo fsck -t vfat /dev/sdb1
Password:
fsck 1.40-WIP (14-Nov-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sdb1: 0 files, 1/30509102 clusters
gary@black:~$

---

### Post by garymcgarrigle on 2007-06-17
the drive/partition seem to be mounted ok but the data is gone (or at least inaccessible).

are there any apps I can use to scan the disk to see if my files are still there and recover them?

---

### Post by merlinus on 2007-06-17
Try booting from Knoppix -- [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)

-merlin

---

### Post by shadows85 on 2007-06-17
> **garymcgarrigle said:**
> the drive/partition seem to be mounted ok but the data is gone (or at least inaccessible).

are there any apps I can use to scan the disk to see if my files are still there and recover them?



If you didn't make a backup I doubt you can recover the files, but I'm not 100% sure.

---

### Post by garymcgarrigle on 2007-06-17
anyone know if recreating the partition table with gpart might help?

if it was a partition table problem would the drive be able to mount at all?

am I likely to do any damage (and make the situation worse) by recreating it?

---

### Post by garymcgarrigle on 2007-06-17
just used ADRC data recovery in Windows to scan the drive for deleted files.

it found deleted file (old data) but no sign of the data that should be there.

it's got to be somewhere. can anyone help?

---

### Post by garymcgarrigle on 2007-06-17
i'm logged back into Ubuntu and I can see some Windows directories (vol info and recycle folders) on the partition so it looks like I have a working partition..... but none of my data   :frown:

---

### Post by garymcgarrigle on 2007-06-17
TestDisk 6.5, Data Recovery Utility, October 2006
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

   * FAT32 LBA                0   1  1 60800 254 63  976768002
Use Right arrow to change directory, q to quit
Directory /

No file found, filesystem seems damaged.




------------------

any way to repair the filesystem?

---

### Post by garymcgarrigle on 2007-06-18
anyone on this morning that has any ideas to help me?

---

### Post by garymcgarrigle on 2007-06-18
at work now so won't be able to try anything for a while but is there any way to re-create the table of contents?

---

### Post by garymcgarrigle on 2007-06-18
can i re-create the file allocation table?

---

### Post by garymcgarrigle on 2007-06-18
just ran data doctor recovery. it took 4 hours to scan the drive and is only showing me actual deleted content, no sign of the current data (or at least what was the current data).

i'm at a loss to understand what could erase all traces of actual data and leave the deleted files alone.

---

### Post by AtleJo on 2007-08-14
First I will say that I am new to Ubuntu so my knowledge about this is limited. However I have used computers since 1986 so I have some experience.


Are you sure the files are deleted. I have a similar problem on a network drive. I have mounted all my networkdrives (actually folders on the drive) in fstab and created folders in media/ where they are 
mounted. 
Like this:

//XXnetdisk1/music  /media/music  cifs                                username=XX,password=XXXXX,iocharset=utf8,file_mode=0777,dir_mode=0777

I use 3 Synology network drives each have 2- 3 folders that are mounted as drives. I have 7 mounted drives, 6 works perfect and one give me problems. It happend after I had a shutdown while I had files from that drive open.


On the problem one I can not see the files from my Ubuntu machine if I copy a file to the drive it will show but as soon I reload the view it is gone. If I copy one more time it will ask me if I want to overwrite the file even if it looks like there is nothing there.

From my Windows machine I can see the full content so I know that the files are not deleted.

I have tried to mount and unmount to delete the line in fstab,  etc. nothing helps. The next move will be to make a new folder on the drive, move the files and mount it with a new name.

I can not help you with the solution but I wanted to let you know that this might be a bug or.........

---


---
title: "File modified times always 1 hour different from Ubuntu to Android phone"
date: 2012-11-01
forum: General Help
---

### Post by tk83 on 2012-11-01
I'm running Ubuntu 12.04 with all updates applied. I sync my music files across to my Android phone by plugging the phone into the computer in USB storage device mode and using a simple rsync command to sync the respective music folders.

The problem I'm having is that the files on the phone always seem to have a 1 hour time difference to those on the computer. 

For example on 24 October I let rsync do a full sync of all files from computer to phone. So in theory all files should be same on the two devices. However when I did the same sync today instead of just syncing what had changed (almost nothing) it started trying to copy over every single file.

Here's an example file:
Phone:
```
  File: `05 Black Eyed Peas - I Gotta Feeling.mp3'
  Size: 9298663         Blocks: 18176      IO Block: 32768  regular file
Device: 830h/2096d      Inode: 3474        Links: 1
Access: (0644/-rw-r--r--)  Uid: ( 1000/     tim)   Gid: ( 1000/     tim)
Access: 2012-10-24 01:00:00.000000000 +0100
Modify: 2009-12-10 15:49:46.000000000 +0000
Change: 2012-10-24 22:58:10.000000000 +0100
 Birth: -
```Computer:
```
  File: `05 Black Eyed Peas - I Gotta Feeling.mp3'
  Size: 9298663         Blocks: 18168      IO Block: 4096   regular file
Device: fc04h/64516d    Inode: 5769277     Links: 1
Access: (0640/-rw-r-----)  Uid: ( 1000/     tim)   Gid: ( 1000/     tim)
Access: 2012-10-24 21:58:08.268184322 +0100
Modify: 2009-12-10 14:49:47.000000000 +0000
Change: 2012-08-07 20:40:43.647993309 +0100
 Birth: -
```The phone is a Samsung Galaxy S2 running stock standard Android 2.3.5. The music files are stored on the SD card.

Does anyone have any ideas what could be causing the modified time to change?

---

### Post by papibe on 2012-11-01
Hi tk83.

What kind of filesystem is the phone being mounted as? fat32? ext3?

Are you sure your phone is set to the same time zone that your computer?

Regards.

---

### Post by tk83 on 2012-11-01
Hi,

The phone and the computer are both set to the same time zone - London which is currently GMT+0. 

The phone file systems show up as FAT32 and Ubuntu mounts them with the vfat module:
```
/dev/sdd on /media/PHONESD type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sdc on /media/409E-0G83 type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
tim@localhost:~$ date
Thu Nov  1 22:20:36 GMT 2012
```

---

### Post by papibe on 2012-11-01
I think the problem is this: FAT does not support time zones, then all times are saved on UTC. I imagine those files were transferred before Oct 28 when London time were one hour behind UTC (I believe now they are the same).

You may try to mount your phone using mtp instead of as a 'mass storage device'. That is what I used for my Nexus 7 and my wife's Galaxy Nexus.

Let us know how it goes.
Regards.

---

### Post by tk83 on 2012-11-02
Ok that actually makes sense. I was in Germany in early October so that's another 1 hour difference when I changed it back to London time before the 24th. And then of course the UK went out of daylight saving time on the 28th October so that's another hour.

Shows how crap FAT32 is though :( 

So I just have to get used to rsync re-syncing all my files if the timezone changes. Thanks for your help.

---


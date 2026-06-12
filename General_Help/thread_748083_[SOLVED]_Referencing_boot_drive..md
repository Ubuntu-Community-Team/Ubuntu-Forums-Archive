---
title: "[SOLVED] Referencing boot drive."
date: 2008-04-07
forum: General Help
---

### Post by Barriehie on 2008-04-07
Hello Everyone,

I'm currently running the below shell script to backup my boot drive to my backup drive.  This resides in the root dir. of the boot drive.  I would like to put this file on the backup drive and run it automatically.  So, the ? is how do I reference the boot drive in this command line???

[B]tar cvpzf /media/backup/bup$(date +%m%d%y).tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media /

[/B]Thank You,
Barrie

---

### Post by mixmaster on 2008-04-07
Maybe I am misunderstanding the question, but the command that you have quoted uses fully qualified paths throughout so should perform the same function no matter where it is invoked.

Remember that tar works on filesystems.  Presumably your boot drive has one or more filesystems which are mounted on '/' and possibly '/home' or other vital locations.  If you accepted the default "use whole disk" option on installation you have just the one fs mounted on '/'.

Given the way you are talking about drives in this context I am guessing you are comparatively new to linux, in which case the relationship between physical devices (drives) and addressable storage (mountable file systems) may be a bit new/confusing.  Very simply, except at the lowest levels, linux does not really know about drives (in the sense that windows knows about C;, D: etc).  Instead, each physical device has segments of storage defined which are mounted on some directory in the filesystem.  The storage mounted on '/' is generally used to boot from (not always).  If you add a new drive, you can mount it anywhere (as your backup drive is mounted on /media/backup).  I suggest you read some of the guides for more info on this topic, as it will come in useful later.

---

### Post by Barriehie on 2008-04-07
> **mixmaster said:**
> Maybe I am misunderstanding the question, but the command that you have quoted uses fully qualified paths throughout so should perform the same function no matter where it is invoked.

Remember that tar works on filesystems.  Presumably your boot drive has one or more filesystems which are mounted on '/' and possibly '/home' or other vital locations.  If you accepted the default "use whole disk" option on installation you have just the one fs mounted on '/'.

Given the way you are talking about drives in this context I am guessing you are comparatively new to linux, in which case the relationship between physical devices (drives) and addressable storage (mountable file systems) may be a bit new/confusing.  Very simply, except at the lowest levels, linux does not really know about drives (in the sense that windows knows about C;, D: etc).  Instead, each physical device has segments of storage defined which are mounted on some directory in the filesystem.  The storage mounted on '/' is generally used to boot from (not always).  If you add a new drive, you can mount it anywhere (as your backup drive is mounted on /media/backup).  I suggest you read some of the guides for more info on this topic, as it will come in useful later.

Thank you mixmaster!  You are correct on all points.  I was thinking that the / referred to the 'drive' the file is being invoked on.   I just moved the file onto the backup media and it works as anticipated!  I've a lot to learn about linux but still don't miss the 'other' program I had on here. :)

Barrie

---

### Post by Barriehie on 2008-04-08
Okay, this wasn't very quick by the guru standards but now I've managed to have the second 'drive' mounted at boot time and show on the desktop; it only took 4 hours... :)

Barrie

---


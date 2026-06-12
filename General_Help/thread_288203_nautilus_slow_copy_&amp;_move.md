---
title: "nautilus slow copy &amp; move"
date: 2006-10-29
forum: General Help
---

### Post by bassMonkey on 2006-10-29
Hi, just made a fresh edgy install. Everything else seems fine but nautilus file copying speed is just horrible, I can copy a dir containing 200mb of mp3:s in about 7 seconds using the terminal but when I try it in nautilus it takes about a **minute and a half!!**](*,)  I've tried both copying/moving files from one drive to another and on the same drive. Deleting files is no problem however. I'm using xfs, but that shouldn't matter since copying using the console works nicely! Anyone experiencing this?

---

### Post by Spano on 2006-10-29
I can confirm same behavior in nautilus and rox-filer as well.
Try copying across a LAN, then it's really slow.  I was putting the problem down to samba or ssh.
Just tried copying a large directory partition to partition as you have been doing - SLOW.
Really have no clue how to correct.

---

### Post by bassMonkey on 2006-10-29
Well, at least I'm glad I'm not alone on this one. Really frustrating!

Edit: also noticed that while copying with nautilus I hardly see a jump in usage of system resources.

---

### Post by coastdweller on 2006-10-29
[Anyone else think nautilus is slow?](http://www.ubuntuforums.org/showthread.php?t=276078&highlight=Nautilus+slow)
[Moving files with nautilus](http://www.ubuntuforums.org/showthread.php?t=240804&highlight=Nautilus+slow)
[SMB File copying *really* slow](http://www.ubuntuforums.org/showthread.php?t=271099&highlight=Nautilus+slow)

---

### Post by NNois on 2006-11-03
Yes here the same problem.
My disk is in XFS and another in FAT32

A temporary solution:
Using thunar the file tranfert are very good.

Also I've (tried) reported a gug in lauchpad for this. But I'm not sure i've done it good

---


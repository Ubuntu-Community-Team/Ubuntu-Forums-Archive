---
title: "fat32 and question marks"
date: 2006-11-16
forum: General Help
---

### Post by Folditron on 2006-11-16
I use a 300gb external drive formatted as fat32 to store all my music and movies. Unfortunately it seems that fat32 doesn't allow certain characters in file names(eg. question marks). Thus leaving me with many songs missing which is a tragedy for someone who likes his music collection obsessively and compulsively organized. So I'm wondering if there is a way to use a script or bash command to remove these unwanted characters from all the songs in my music directory before putting them on the fat32 drive?

---

### Post by rajasekhar.yeruva on 2006-11-17
edit the fat partition mounting entry in /etc/fstab and include iocharset=utf8. I read some where stating "iocharset=utf8" is not optimal for fat filesystems. But I am running it fine without any problems. This should solve your problem

Ex: /dev/hda4  /media/Fat  vfat **iocharset=utf8**,umask=000  0    0

---

### Post by Folditron on 2006-11-17
No luck. I didn't have an entry in fstab for the drive at all, so I created one using your options and my mount points. I still get this error when trying to put a file with a question mark on the drive 
Error "Invalid parameters" while copying "/home/bill...top/mnkbj?".

Help is much appreciated. It's you folks that answer questions in the forums that make this OS so awesome.

---

### Post by Folditron on 2006-11-20
anyone out there?

---


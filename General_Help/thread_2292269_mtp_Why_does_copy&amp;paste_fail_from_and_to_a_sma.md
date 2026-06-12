---
title: "mtp: Why does copy&amp;paste fail from and to a smarthphone's external sd-card (sdcard1)"
date: 2015-08-26
forum: General Help
---

### Post by ziegler-g on 2015-08-26
I am using Xubuntu 14.04 with Thunar 1.6.3. I cannot copy and paste folders and files from or to the SD-card of my Sony Xperia Z1 compact smartphone without some files or folders being "forgotten".

(Everything in the following is translated back from DE->EN.)

Say, I want to copy my Music folder from my laptop's desktop by copying and pasting it to my smartphone's sdcard1. I mean the target being mtp://[usb:002,004]/SD-Karte/. I mean the external card, not the built-in. 

I get the following:

```
Files are being copied to SD-Karte
libmpt-error - could not send object
Can't be seen.mp3
3.5 MB of 16.3 GB copied - 1 hour remaining.
Do you want to skip? [Yes](Copying continues)
After having copied 12 GB the same error with a whole Folder "DiWoDaSo"
After having copied 12.9 GB the same error with a whole Folder "Ludwig Van Beethoven"
After having copied 12.9 GB the same error with the song "Where do you go to my lovely"
After having copied 14.1 GB the same error with a whole Folder ""Never mind the bolloks"
```

Now the other way round. Trying to do a commplete backup of my sdcard1: I mean copying everything in mtp://[usb:002,004]/SD-Karte and pasting it into /home/ziegler/Schreibtisch/BackupSD

```
Collecting files
No valid file
Skip this one [Yes]

```
The copying process just stops instantaneously.

Let us try it the good old shell way:

```
ziegler[1]:~$ LANG="C" cp -a /run/user/1000/gvfs/mtp\:host\=%5Busb%3A002%2C004%5D/SD-Karte/* ~/Schreibtisch/BackupSD/
cp: error reading '/run/user/1000/gvfs/mtp:host=%5Busb%3A002%2C004%5D/SD-Karte/Android/data/cc.dict.dictcc/files/cc.dict.dictcc/dictcc-lp1.db': Input/output error
cp: failed to extend '/home/ziegler/Schreibtisch/BackupSD/Android/data/cc.dict.dictcc/files/cc.dict.dictcc/dictcc-lp1.db': Input/output error
cp: error reading '/run/user/1000/gvfs/mtp:host=%5Busb%3A002%2C004%5D/SD-Karte/Android/data/cc.dict.dictcc/files/cc.dict.dictcc/dictcc-lp4.db': Input/output error
cp: failed to extend '/home/ziegler/Schreibtisch/BackupSD/Android/data/cc.dict.dictcc/files/cc.dict.dictcc/dictcc-lp4.db': Input/output error
cp: error reading '/run/user/1000/gvfs/mtp:host=%5Busb%3A002%2C004%5D/SD-Karte/Android/data/cc.dict.dictcc/files/cc.dict.dictcc/dictcc-lp2.db': Input/output error
cp: failed to extend '/home/ziegler/Schreibtisch/BackupSD/Android/data/cc.dict.dictcc/files/cc.dict.dictcc/dictcc-lp2.db': Input/output error
cp: error reading '/run/user/1000/gvfs/mtp:host=%5Busb%3A002%2C004%5D/SD-Karte/Android/data/cc.dict.dictcc/files/cc.dict.dictcc/dictcc-lp6.db': Input/output error
cp: failed to extend '/home/ziegler/Schreibtisch/BackupSD/Android/data/cc.dict.dictcc/files/cc.dict.dictcc/dictcc-lp6.db': Input/output error
cp: error reading '/run/user/1000/gvfs/mtp:host=%5Busb%3A002%2C004%5D/SD-Karte/Android/data/cc.dict.dictcc/files/cc.dict.dictcc/dictcc-lp58.db': Input/output error
cp: failed to extend '/home/ziegler/Schreibtisch/BackupSD/Android/data/cc.dict.dictcc/files/cc.dict.dictcc/dictcc-lp58.db': Input/output error
cp: error reading '/run/user/1000/gvfs/mtp:host=%5Busb%3A002%2C004%5D/SD-Karte/Android/data/cc.dict.dictcc/files/cc.dict.dictcc/dictcc-lp8.db': Input/output error
cp: failed to extend '/home/ziegler/Schreibtisch/BackupSD/Android/data/cc.dict.dictcc/files/cc.dict.dictcc/dictcc-lp8.db': Input/output error
cp: error reading '/run/user/1000/gvfs/mtp:host=%5Busb%3A002%2C004%5D/SD-Karte/Android/data/cc.dict.dictcc/files/cc.dict.dictcc/dictcc-lp56.db': Input/output error
cp: failed to extend '/home/ziegler/Schreibtisch/BackupSD/Android/data/cc.dict.dictcc/files/cc.dict.dictcc/dictcc-lp56.db': Input/output error
^C
```

What is wrong here? How CAN I copy my files? Are there other, easy ways to transfer a music collection from a laptop or PC to an Android smartphone?

Thank you in advance. Greetings from Germany!

---

### Post by coffeecat on 2015-08-27
Ubuntu Phone and Tablet section is for portable devices running Ubuntu.

*Thread moved to **General Help**.*

---


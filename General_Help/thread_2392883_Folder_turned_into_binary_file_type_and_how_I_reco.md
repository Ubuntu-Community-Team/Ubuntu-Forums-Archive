---
title: "Folder turned into binary file type and how I recovered the files"
date: 2018-05-26
forum: General Help
---

### Post by aqtivator on 2018-05-26
Hello. 

**The problem:** a shared samba **folder** (about 1.1TB full of stuff) in Ubuntu, **turned into a binary file** (of 14.688.256 bytes)

**The story:**
I had a shared folder in ubuntu 16.04 named **NAS_D2**, on a disk formatted as **Ext4**, it had a bunch of subfolders.
One of the subfolders was a **Plex share**
One day I am trying to play a video located on that share through Plex player on an other PC, and it says *"problem with playback, file may be corrupt"* (or something like that I did not keep the screenshot)
So I go to look at the share and to my surpise the **folder** (NAS_D2) that was shared though **samba** somehow **turned into** a **binary file**
When I checked the drive, it was still filled with 1,1TB of data, so nothing was deleted.

**I just could not access it because the folder in question was turned into a file, and you cant open a file to access the the subfolders!**

**The solution**
[LIST=1]
[*]I removed the drive in question from the ubuntu machine
[*]Installed into a **windows 10** machine I have
[*]Installed **Ext2 Volume Manager** and mounted the drive (the drive was ext4 formatted)
[*]Installed **Recuva**
[*]Run a **Deep Recovery Scan** with recuva and **got most of the files back**.
[/LIST]


P.S.: I tried to recover the files with **testdisk**, but had no success, I am not that linux savy.
P.S.2: I am posting this, for anyone that maybe run into a similar problem and I hope you get everything back.

[ATTACH=CONFIG]279871[/ATTACH]

---


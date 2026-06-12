---
title: "Change Drive names?"
date: 2007-05-16
forum: General Help
---

### Post by wh33t on 2007-05-16
Ack, linux and its cursed security! damn you...

Anyhoo, I got a simple question. Why is it that I can't change the name of my Disks? Its currently appearing is 74.gb Volume, and FILE system. All I want to do is name the 74gb disk "Windows Xp" and the File System "Ubuntu Linux".

Even when I log in as root (yes i made that possible) I still can't do it... Jezuz! Any idea why i can't do this?

---

### Post by J0ris on 2007-05-16
The tools required to change the Volume or Device Name depends on the filesystem you have got installed on the given partition. As such you need to install following packages:
- ntfs fs: ntfsprogs, then use the ntfslabel tool
- vfat fs: mtools, not sure which command it was anymore
- ext2/3: tune2fs -L command (standardly installed I believe)

Have a look here too: [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by wh33t on 2007-05-16
Awesome, thanks.

I'll take a looksee into those.

---


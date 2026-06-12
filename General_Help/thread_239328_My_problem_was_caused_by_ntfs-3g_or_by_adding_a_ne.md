---
title: "My problem was caused by ntfs-3g or by adding a new drive in WINECFG?"
date: 2006-08-19
forum: General Help
---

### Post by DJRockoBobo on 2006-08-19
In order to install WoW I have done two tasks : the first one was to create a write support on 2 ntfs partitions because i hadn't got enough free space to install it on root partition. After that, I have created in WINECFG a sort of a new logical drive (a cd-rom drive) - more exactly : i've entered in:
winecfg-->drives-->add+
Now after using ntfs-3g and winecfg (drives) I can't install any programmes from ADD/REMOVE... or upgrade my computer through the announcing bubble.
And my question is: What caused my problem - ntfs-3g, winecfg....or might have been something else???
THANX IN ADVANCE

---

### Post by givré on 2006-08-19
I think more on neither of them,
What do you get when you do 
```
sudo apt-get updgrade
```
from the terminal.
Also, you should post your /etc/apt/sources.list

---


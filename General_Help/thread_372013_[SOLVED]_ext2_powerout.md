---
title: "[SOLVED] ext2 powerout"
date: 2007-02-27
forum: General Help
---

### Post by Zeotronic on 2007-02-27
My cat, which is responsible for property damage in my house, has managed to flip of my power strip during an installation on Xubuntu, now my Xubuntu wouln't go into GUI, before that it complains of a problem. I don't know how to fix this... My filesystem is ext2 and I'm running Xubuntu v6.10. If you need to know exactly what the error message says, I suppose I can get that information...

---

### Post by caldevil on 2007-02-27
Can't you reinstall  Xubuntu again?

---

### Post by HasratUSA on 2007-02-28
Lol

---

### Post by Zeotronic on 2007-02-28
Yea, I could reinstall Xubuntu, but the point is that I want to keep my data!

---

### Post by caldevil on 2007-02-28
Ohh, I thought you were doing a fresh install. Can you then post the actual error message?

---

### Post by Azakus on 2007-02-28
Download a livecd and run fsck from the terminal.
```
fsck -a -y /dev/partitionnumber
```
"partitionnumber" is the drive and partition giving you trouble, such as hda1 or sda3, etc.

---


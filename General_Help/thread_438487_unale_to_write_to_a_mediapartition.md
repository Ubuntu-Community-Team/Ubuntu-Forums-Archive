---
title: "unale to write to a /media/partition"
date: 2007-05-09
forum: General Help
---

### Post by loserboy on 2007-05-09
I just did a fresh install of feisty on my mom's comp, but this time I wanted to make an extra partition for backup and whatnot, so during install all i did was take a piece from the disk and call it /media/backup, that's always worked fine in other computers for me and it is mounting and showing on the desktop but it's showing as owned by root and I can't move stuff to it (haven't tried actually doing it with sudo). 

is there a way i can give it permission to be easily accessed without going root, and is there any reason why it did that? it's always been fine for me the only thing i did different this time was make it ext3 instead of fat32 cuz theres no reason for it to be fat32, she's completely windows free.

thanks in advance
mike

eta: tried it through term with sudo and it worked of course, but still I don't wanna go to terminal every time i wanna put something there

---

### Post by taurus on 2007-05-09
If it's an ext3 filesystem, then you just have to change ownership of the mount point, /media/backup, from root to her login name.  Then, she can write to it.  _Assuming_ her login name is **mom**, do

Applications -> Accessories -> Terminal
```
sudo chown -R **mom**:**mom** /media/backup
ls -la /media
```

---

### Post by loserboy on 2007-05-09
hey thanks a bunch, did it do that because I made it ext3?
im guessing fat32 doesn't automatically allow the same control over permissions

---


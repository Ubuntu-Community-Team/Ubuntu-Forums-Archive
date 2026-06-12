---
title: "[SOLVED] Ubuntu / Vista Ultimate"
date: 2008-06-18
forum: General Help
---

### Post by Dyffo on 2008-06-18
Some months ago I Installed UBUNTU alongside Windows Vista. All worked fine, at the boot start Ubuntu took priority, with the option to go to Vista if required. Today - Vista has dissappered off the start procedure - I do have the option of selecting another operating system. However when I select this the error message " Unrecognized Device String " appears.This is a set back because I have just a couple of programmes that I use that will only run on Windows. Any ideas - everything is still there - I just cannot get to it.

---

### Post by VMC on 2008-06-18
Output:
```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---


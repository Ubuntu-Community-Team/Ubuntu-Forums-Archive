---
title: "Please help.I installed Ubuntu and now i cant get to windows."
date: 2008-01-19
forum: General Help
---

### Post by zodiacdm on 2008-01-19
I have just recently switched over to ubuntu, since windows programs were taking up too much ram for what i wanted to do. i installed it on my second hard drive, but i chose the automatic installation, and now it doesn't give me the option to boot into windows. even if i just disconnect the hard drive, grub still comes up and give me an error. i am toying with different varieties and am going to give pc linux os a try, even though i like ubuntu (exept for the minor flaw in the wine freezing my system, different subject) i figured i should get it to recognize windows before i try to install a third os. thanks for yor help.

---

### Post by dabang on 2008-01-19
That's strange, Ubuntu adds Windows automatically to grub's menu... You may try adding it manually by editing /boot/grub/menu.lst

```
title           Windows
root            (hdX,X)
savedefault
makeactive
chainloader     +1
```

Replace hdX,X correctly, for example if Windows is on the first partition of your first harddrive it's
hd(0,0) -> first digit is HD, second is partition, start counting at 0

---

### Post by zodiacdm on 2008-01-19
sorry, but i'm still learning. i have edited the file and when i go to save it, it tells me i don't have the permission. yeah, i know, sudo. but how do i do this from the file?

---

### Post by Warpedflash on 2008-01-19
use
```
sudo /boot/grub/menu.lst
```
to edit your grub list. you have to be a superuser to edit it

---

### Post by ajgreeny on 2008-01-19
```
gksudo gedit /boot/grub/menu.lst
```will open the file as root and you will be able to save changes.  Be careful to only change the list at the bottom of the file, not anything else at this stage.

---

### Post by zodiacdm on 2008-01-19
> **ajgreeny said:**
> ```
gksudo gedit /boot/grub/menu.lst
```will open the file as root and you will be able to save changes.  Be careful to only change the list at the bottom of the file, not anything else at this stage.
This is the one i used, i could not get to the file in the super user terminal. i saved it. i am burning the new disc now, and i will let you know if i solved this as soon as i'm back up.

---

### Post by zodiacdm on 2008-01-19
This issue is solved, what they said worked beautifully. thanks guys.

---


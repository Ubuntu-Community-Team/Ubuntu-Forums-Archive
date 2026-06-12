---
title: "Dual Booting Options"
date: 2008-06-17
forum: General Help
---

### Post by us3rX on 2008-06-17
Everytime I update ubuntu I get more and more options when starting up the laptop.

When I installed ubuntu the first time it was

> 
Ubuntu 8.04. kernel 2.6.24-16-generic
Ubuntu 8.04. kernel 2.6.24-16-generic (recovery mode)

Ubuntu 8.04. memtest86+

Windows Vista Longhorn (loader)

Now it shows something like this...

> 
Ubuntu 8.04. kernel 2.6.24-19-generic
Ubuntu 8.04. kernel 2.6.24-19-generic (recovery mode)
Ubuntu 8.04. kernel 2.6.24-18-generic
Ubuntu 8.04. kernel 2.6.24-18-generic (recovery mode)
Ubuntu 8.04. kernel 2.6.24-16-generic
Ubuntu 8.04. kernel 2.6.24-16-generic (recovery mode)

Ubuntu 8.04. memtest86+

Windows Vista Longhorn (loader)

Was Just wondering if there is a way to change that? Cause I dont want to keep updating to the point where its going to flood the screen with options -.-

Thanks,
~us3rX :twisted:

---

### Post by Victormd on 2008-06-17
you can edit your menu.lst
```
sudo gedit /boot/grub/menu.lst
```
and scroll to the end of the file and either comment or remove the entries you don't want showing up.

On that note, it's always a good idea to keep the most up-to-date kernel and the one prior to that because if something goes wrong with the new kernel (bug or something) you can fall back on the previous one.

---

### Post by Victormd on 2008-06-17
If you want to you can also completetly remove the unwanted kernels from your system by searching for them in Synaptics and mark for removal.

Again, you may want to keep the last two (i.e., 2.6.24-18 and 2.6.24-19).

---

### Post by kalesh7 on 2008-06-17
edit the file /boot/grub/menu.lst
```
sudo gedit /boot/grub/menu.lst 
```
remove the parts you dont want(scroll down right through all the lines beginning with # then you will come to the options.)

---

### Post by us3rX on 2008-06-17
wow, thanks for the quick responces and thanks for the help =)

~us3rX :twisted:

---


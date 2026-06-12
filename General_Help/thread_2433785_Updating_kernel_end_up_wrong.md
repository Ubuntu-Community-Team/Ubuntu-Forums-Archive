---
title: "Updating kernel end up wrong"
date: 2019-12-25
forum: General Help
---

### Post by timufa123 on 2019-12-25
Hello Ubuntu Forum
Tried Ubuntu dual boot with Windows 7 and it's nice 

tried to update the kernel and it crashed my grub
using easybsd got my grub back and mounted Ubuntu 16.04 live cd  
tried to repair it but it is all read only
chroot didn’t worked for me too
mount remount commands didn't worked too
tried to install deb from there, nothing
mounted images nothing


every tutorial is mess
just want to delete kernels and leave one working generic
restore mode not working throwing me to the terminal (read only)

just want to rescue my files have the password and the user name

please help
thank you :)

---

### Post by mörgæs on 2019-12-25
> **timufa123 said:**
> 
just want to rescue my files have the password and the user name

From a live boot it should be possible to read the hard disk and copy the selected files to a USB drive.

When everything is saved you could consider a fresh install of a later release rather than salvaging 16.04.


> **timufa123 said:**
> 
just want to delete kernels and leave one working generic

When you have the new install running the command
```
sudo apt autoremove 
```
will delete all kernels but the two latest. It's a good habit to run it once a month.

---


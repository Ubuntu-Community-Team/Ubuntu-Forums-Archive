---
title: "QEmu help"
date: 2007-02-25
forum: General Help
---

### Post by Zilulil on 2007-02-25
EDITED: Running Feisty
ok i'm following the guide [WindowsXPUnderQemuHowTo]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo?highlight=%28QEmu%29") and I've ran into a few snags.
```
cd /usr/src/linux
make-kpkg debian
make-kpkg modules_image
module-assistant prepare kqemu 
dpkg -i /usr/src/kqemu-modules-''version''.dpkg
```
I couldn't get the last bit of this code to work, but I got around it by installing kqemu from the instructions on their site.
```
qemu -localtime -cdrom /dev/cdrom -m 384 -boot d windows.img
```
this bit of code is the one currently giving me troubles. it gives me the error or
```
qemu: could not open hard disk image '/dev/cdrom'
```
any help you could give would be greatly appriciated.

---

### Post by solar george on 2007-02-25
Try leaving out the -cdrom bit, you won't be able to access you cdrom through window$ though.

```
qemu -localtime  -m 384 -boot d windows.img
```

---

### Post by Tomy on 2007-03-02
> **Zilulil said:**
> 
```
qemu -localtime -cdrom /dev/cdrom -m 384 -boot d windows.img
```this bit of code is the one currently giving me troubles. it gives me the error or
```
qemu: could not open hard disk image '/dev/cdrom'
```any help you could give would be greatly appriciated.

Try putting a cd in the cdrom drive before you start qemu. This works for me.

---


---
title: "damaged filesystem"
date: 2007-03-25
forum: General Help
---

### Post by dbbolton on 2007-03-25
i had been dual booting windows and edgy. i booted a dapper livecd to use gparted- as i needed to create another partition to install 64 studio. in the middle of making my changes, gparted halted giving me the error that the device was busy. then, it froze, so i had to hard reboot.

i was welcomed with grub error 17. so, i booted the livecd again. here's what happened:
```
$ grub
grub> find /boot/grub/stage1

Error 15: File not found
```so, i ran gparted again. all of my filesystems are still there. however, /dev/hda2 (which had edgy installed) is now flagged as damaged.

is there anything i can do here, or do i need to wipe the disk ?

if so, how can i get rid of everything except /dev/hda1 (which has windows) and repair the MBR ?

---

### Post by dbbolton on 2007-03-25
well, i just erased my disk and reinstalled dapper. thanks, to the 8 people eho looked at this. i guess.

---


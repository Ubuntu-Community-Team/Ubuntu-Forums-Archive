---
title: "Grub wont find any of the disks, but they are there!"
date: 2008-02-13
forum: General Help
---

### Post by SpinningAround on 2008-02-13
I installed a new cooler to my NB today and started up the computer and when doing this I think I switched the ATA133 cable so now wont ubuntu find any of the disks, neither ubuntu or windows. 

Thing is that bios find the disks and when I use ubuntu live cd can I find the disk and read from them, so they are there they aren't broken grub simply wont boot them up. It stop at te grub menu, it's almost like the thing that grub is pointing at isn't there.

How do I fix this? Do I need to reinstall ubuntu (hope not!) or is the a better way around.

---

### Post by taurus on 2008-02-13
Sounds like you need to reinstall GRUB again.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
or
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

### Post by SpinningAround on 2008-02-13
Well i followed the RestoreGrub wiki and it guess worked fine, but thing is that grub still say the same thing, I did say something that /mnt/root/boot/grub isn't a XFS and for some reason have the hdd got the namne "hdc & hdd" they allways been "hda & hdb" (??) start to guess it would be easier to back everything up and do a complete reinstall :(

is there someway to change "hdc & hdd" back to "hda & hdb" ?

---


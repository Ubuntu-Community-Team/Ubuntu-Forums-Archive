---
title: "Grub problem with software raid1"
date: 2008-03-27
forum: General Help
---

### Post by SundaY82 on 2008-03-27
Hi,

I have a server running ubuntu 7.10 server and as os disk i run two 160gb in raid1. In the weekend when i did some maintenence on the box and tried to start it up again it froze just before "loading grub"(never got that far) with a black screen and a blinking curser. After a while i saw that one of the disks in my raid1 didnt have power so i connected the cable again and it booted up just fine. This makes me think that grub is only installed on one of the disks, the one that lost power. What i have read when searching the net on the matter is that you have to install grub on both disks with:
```
grub
root (hd0,0)
setup (hd0)
root (hd1,0)
setup (hd1)
quit
```
And change to the correct disks. In my case /dev/md0 consist of sdc1 and sdd1. But looking in /boot/grub/menu.1st it has "root (hd0,0)", how can that be when its sdc1 and sdd1?
Could it be that sda and sdb is arrays from my highpoint rocketraid card and modules for the card is proberly not loaded until linux boots up?
If so i guess sdc1 and sdd1 really becomes sda1 and sdb1 during bootup, but how do i fix grub when linux has loaded my highpoint arrays as sda and sdb?
I guess for it to boot i need to have (hd0,0) and (hd1,0), but if i try to fix grub with linux loaded wont it try to install grub on my highpoint arrays as they have become disk sda and sdb?

Anyone with an idea on how to solve this?
Maybe it simple, lets hope so :)

Thanks in advance!
Ola Ahlman

---


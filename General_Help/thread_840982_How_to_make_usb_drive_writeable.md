---
title: "How to make usb drive writeable?"
date: 2008-06-25
forum: General Help
---

### Post by Hashi on 2008-06-25
Hi,
  My installation is in a mess, I have posted to several threads seeking answers, and would like to try out some suggestions. Currently, I can only boot into Knoppix on a USB pen drive. (I won't go into why here, it doesn't belong here).
  I wqant to back up my entire home folder to anexternal 120GB USB drive before I start fooling around. However, Knoppix has mounted this drive as read only. I want to make it writeable (it is FAT32). It was writeable under Ubuntu.
  Can anyone tell me how to go about doing this?

PS Knoppix is Debian based, just like Ubuntu, as you probably know. I can read my original HDD OK, but I want to back up important stuff first, if that makes any sense?

Thanks
Jon

---

### Post by utsuprainfra on 2008-06-25
hmm, did you mount it with the mount command or fstab?

---

### Post by Hashi on 2008-06-25
Hi,
  Um, I don't know. The foreign operating system (Knoppix) just mounts all available drives as it sees fit. It seems to see fit to mount all drives as read only. There must be some way I can fix this? CHATTR or something?
Ta

EDIT: It obviously uses fstab, sorry, I wrote before I thunk.

---

### Post by mempman on 2008-06-26
if your usb driver is mounted onto /XXX, have you tried to change the permissio nof /XXX ?

you could change the permission by doing a :
sudo chmod a+rwx /XXX

try that

---


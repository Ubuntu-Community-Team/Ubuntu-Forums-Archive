---
title: "edit fstab for windows partition"
date: 2007-09-16
forum: General Help
---

### Post by mcfly2309 on 2007-09-16
Hi, my problem is i had installed windows on hda 1 and now i reinstalled it in the same partition as before (hda1) but ubuntu had added the previous installation to fstab and mounted it to /windows, so now i can't mount the new installation. In the fstab file it seems the UUID has changed so the windows partition can't be mounted automatically and i don't know how to mount it again with the new UUID. What is the UUID exactly and how do I change it? I want to keep the same options, ubuntu made by default during the installation (that step when it asks where to mount the different partitions)

---

### Post by rivalarrival on 2007-09-16
You don't strictly need the UUID - AFAIK, the UUID is a way of specifying the partition even if it isn't always at /dev/hda1. If, for instance, you plug the hard drive into a different IDE controller, the same partition might be called /dev/hdc1

Just read up on mounting NTFS drives in Ubuntu. Google will send you to a dozen how-tos for that.  Basically, though, you're probably going to change the UUID in fstab to /dev/hda1

---

### Post by mcfly2309 on 2007-09-16
hi, so i just wrote /dev/hda1 instead of UUID=%&$·&"Q$·% and with mount -a i got the windows partition. But i think it's not the same as when ubuntu did it, because now i can see the /windows mount on the desktop and before i couldn't, i think it was "safer" before. What is the difference between writing UUID or simply /dev/hdx in fstab?

---


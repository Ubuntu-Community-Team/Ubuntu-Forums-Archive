---
title: "Image/Backup Ubuntu"
date: 2008-03-19
forum: General Help
---

### Post by mawk1000 on 2008-03-19
Hi,
I am looking for a quick and reliable way of imaging an o/s so i can load it quickly onto another machine without hassle.

On Fedora/RH there is a very handy way where you can boot via the rescue cd, and then tar up each of the partitions (eg /boot / /var) and copy them to somewhere like the network. Then on a separate machine you can create partitions in the same formate (eg ext3) using a rescue cd and then just untar the saved tar files from the other machine into the correct locations. After that you can just run the grub-install (making sure the grub.conf matches) /dev/sda1 and reboot and the machine will use kudzu to change the differing hardware and the server will appear just as the previous server was. It is a handy way to image servers and important machines for quick recovery. Can you do something similar with Ubuntu/Debian?

Cheers
Nick

---

### Post by oskar2000 on 2008-03-19
I might have missed something... but I think you can do it exactly like that... It should recognize the hardware on boot-up and adjust itself.
I would use rsync rather than tar, but tar is fine of course.

---

### Post by housam on 2008-03-19
may this guide help you [[COLOR="Red"]_https://help.ubuntu.com/community/BackupYourSystem/TAR_[/COLOR]]("https://help.ubuntu.com/community/BackupYourSystem/TAR")

---


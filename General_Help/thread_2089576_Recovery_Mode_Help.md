---
title: "Recovery Mode Help"
date: 2012-11-29
forum: General Help
---

### Post by Legend1673 on 2012-11-29
I was recently given a Dell Laptop running Ubuntu. I am needing to reset the user password (he couldn't remember what it was). I have read the forums and it appears I need to do this in recovery mode. However, I cannot boot to recovery. I have tried esc and shift after bios and get a screen which says: "MBR 2FA:" and is unresponsive. Any help is appreciated.

---

### Post by thnewguy on 2012-11-29
If you can't get into recovery mode, grab a live CD, boot from that. Mount the local hard drive and reset the user's password. That will look something like this

sudo mkdir /media/disk
sudo mount /dev/sda1 /media/disk
sudo chroot /media/disk
passwd username
(enter new password)
exit
sudo umount /media/disk

---


---
title: "Grub 2.02 beta on 14.04 doesn't work properly"
date: 2015-12-24
forum: General Help
---

### Post by luca-dgh on 2015-12-24
I recently upgraded from 12.04 to 14.04, Gnome FlashBack, almost everything is ok, but Grub is a nightmare.
I have a separate partition for /boot (/dev/sda1) because I always have a partition with installed the system working (now /dev/sda2) and another partition with an experimental installation (now /dev/sda3), when I decide that the new installation is ok I simply change grub.cfg script and my family automatically use the new system without to sense the change.
Upgrading to 14.04 carried the new grub version 2.02-beta, but there is no way for me to put it to work. After a fresh install of Grub I reboot and the grub crash to a **grub rescue>** prompt.
The solution I found now is to mix the contents of old install of grub and the new install of grub, the system gives me some **error: file not found** messages, but boots.
Now, my questions:
1) how can I get a functioning install of Grub 2.02 ?
2) why I receive a message "Hit any key to continue " when booting the new kernels for 14.04?

I attach some info like grub.cfg file and a **ls **of boot partition, if more data are needed just ask me.
Thx a lot and Happy Christmas.

---

### Post by luca-dgh on 2015-12-29
wow. more than 200 views, but no one opinion.

---

### Post by luca-dgh on 2016-01-03
Ok, I solved the problem in Launchpad Answers [https://answers.launchpad.net/ubuntu/+question/280166](https://answers.launchpad.net/ubuntu/+question/280166)

---


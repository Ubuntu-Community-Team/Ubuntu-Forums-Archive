---
title: "Unable to eject external hard drives"
date: 2006-09-18
forum: General Help
---

### Post by Boomy on 2006-09-18
I'm trying to right click the drive and "eject".I used to be able to but now I get this error:

umount: only root can unmount /dev/sdc5 from /media/Storage1
eject: unmount of `/media/Storage1' failed

I have heard that just unpluggin external drives can cause corruption, so I'd rather unmount them before removing.

---

### Post by Ramses de Norre on 2006-09-18
```
sudo eject /dev/sdc5
```
Strange that it doesn't work through nautilus though..

---

### Post by Lapeth on 2006-09-23
Same happened to me today (remember to check that no programs are using data on the disk, such as open nautilus windows). I just turned the external drive off and then unplugged it, but I'll not guarantee that nothing bad will happen on your side.

Besides, my external drive is not automatically umounted when I shut down the computer, otherwise I can hear the drive turning off, which happens when I manually eject it, as you are trying to. Then I'll just hit the button on the external drive. Though the manual says you should always "unmount" the drive from the OS, I've never lost data on it by "being a little rougher". It's just good habit to do so.

---

### Post by dcstar on 2006-09-24
> **Boomy said:**
> I'm trying to right click the drive and "eject".I used to be able to but now I get this error:

umount: **only root can unmount** /dev/sdc5 from /media/Storage1
eject: unmount of `/media/Storage1' failed
.....

This means the drive was mounted without the "users" option (see "man mount" or "man fstab").

Have you altered your /etc/fstab file recently?

---


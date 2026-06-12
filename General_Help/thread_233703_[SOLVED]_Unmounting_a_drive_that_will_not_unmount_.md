---
title: "[SOLVED] Unmounting a drive that will not unmount completely!"
date: 2006-08-10
forum: General Help
---

### Post by RonB123123 on 2006-08-10
I know how to unmount a drive, but on my computer when I do this...
> umount /media/sda2/
It unmounts drive D successfully, but when I reboot, drive D is mounted again. Each time I have to unmount it using the above line in the terminal. Is there anyway to stop it from automatically mounting itself on restart? Thank you.

---

### Post by aysiu on 2006-08-10
```
sudo nano -B /etc/fstab
``` Find the line that has *media/sda2* in it and put a # sign in front of the line. For example, if you have a line that reads: ```
/dev/sda2 /media/sda2 ext3 defaults 0 0
``` change it to ```
#/dev/sda2 /media/sda2 ext3 defaults 0 0
``` Then save (Control-X, Y, Enter).

---

### Post by RonB123123 on 2006-08-10
Thank you, it worked perfectly! :D

---


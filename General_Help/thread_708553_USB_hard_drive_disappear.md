---
title: "USB hard drive disappear"
date: 2008-02-26
forum: General Help
---

### Post by venik212 on 2008-02-26
I have two (related?) problems:
1) When I reboot my kubuntu 7.10 on a Dell DImension 4550 it says that kinit cannot find a resume image, so it does a "normal" reboot, and I have to type "sudo kdm restart" in order to get into the usual KDE gui.
2) After I reboot, I cannot find my external 500 gb USB drive, which was working perfectly (as sdd1) before the rebooting.  The fstab file has a line for that drive, but when I try to manually mount it I am told that the drive does not exist.

What do I do?
 Both problems are annoying, but #2 is really terrible, since I have all my backups there!

---

### Post by taurus on 2008-02-26
Open a terminal and post the outputs of these commands here.

```
sudo fdisk -l
cat /etc/fstab
df -h
```

p.s.  Make sure the USB is plugged in and on before you run those commands.

---


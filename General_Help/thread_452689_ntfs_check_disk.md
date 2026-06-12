---
title: "ntfs check disk"
date: 2007-05-23
forum: General Help
---

### Post by blacksadness on 2007-05-23
Hey,
While was i was trying to mount my ntfs partition with ntfs-3g i got an error about the drive being scheduled for scan, well that used to be a normal thing and i would just reboot into windows before, but now i removed windows, what should i do? i was keeping this an ntfs partition till i manage to get my 70GB data of it, so my question is there a way to scan it from ubuntu? is there a way to convert it to ext3 on the fly?
Thank you in advance

---

### Post by taurus on 2007-05-23
You should use 0 as the last digit for ntfs entry in /etc/fstab.  And if you want to convert it from ntfs to ext3, then all data on that partition would be lost so back up before you convert it.

```
gksudo gedit /etc/fstab
```

---

### Post by blacksadness on 2007-05-23
hey, thx for the fast reply
i did add the 0 to fstab and also the force option it's mounting now but will this affect the drive? it's not going to be long before i back it up though i wouldn't want anything to happen before that, anyway is there an actually way to scan the disk from linux?
another option i thought of is running the windowsxp repair cd, but i'm not sure it will start if there is no windows installed, have anyone tried this?

---


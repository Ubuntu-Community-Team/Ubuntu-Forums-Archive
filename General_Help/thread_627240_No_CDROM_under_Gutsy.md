---
title: "No CDROM under Gutsy"
date: 2007-11-29
forum: General Help
---

### Post by fester225 on 2007-11-29
I just auto-upgraded (online) from feisty to gutsy. Now the CDROMs which I used to be able to read under Feisty can't be read under Gutsy.

Both Konqueror and Firefox find /media/cdrom0, but neither of them see anything on the drive. Looking at /media/cdrom0 through Konsole doesn't show anything either.

How do I get my CDROM working again?

---

### Post by -grubby on 2007-11-29
what model of CDROM DRIVE do you have?

---

### Post by p_quarles on 2007-11-29
> **fester225 said:**
> I just auto-upgraded (online) from feisty to gutsy. Now the CDROMs which I used to be able to read under Feisty can't be read under Gutsy.

Both Konqueror and Firefox find /media/cdrom0, but neither of them see anything on the drive. Looking at /media/cdrom0 through Konsole doesn't show anything either.

How do I get my CDROM working again?
/media/cdrom0 is a mountpoint, so the fact that it's there doesn't mean it's working properly (but you already knew that!)

In any case, after inserting a CD, try this:
```
mount /dev/scd0 /media/cdrom0
```
If that works, the CD-ROM should show up on your desktop. If it doesn't, check your file manager.

If that doesn't work, the output of the following two commands will be helpful for determing the problem:
```
cat /etc/fstab
```
and
```
sudo lshw
```

---


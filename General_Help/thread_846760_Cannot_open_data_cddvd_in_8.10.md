---
title: "Cannot open data cd/dvd in 8.10"
date: 2008-07-01
forum: General Help
---

### Post by LostAngel on 2008-07-01
Hello...since I have updated to 8.10, I cant access my DVD drive. I get the following error.

[mntent]: line 11 in /etc/fstab is bad
mount: cant find /media/cdrom0 in /etc/fstab  or /etc/mstab

---

### Post by drs305 on 2008-07-01
Make a backup of your fstab and open for editing:
```
sudo cp /etc/fstab /etc/fstab-bak1
gksudo gedit /etc/fstab
```

This is what my cdrom fstab entry looks like:
```
/dev/**scd0** /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
```

You should have something similar. If you aren't sure, post it here:
```
cat /etc/fstab
```

You might also check to see if you have a /media/cdrom0 folder. If you don't:
```

sudo mkdir /media/cdrom0

```

---

### Post by LostAngel on 2008-07-01
PERFECT! Thank you very much!!:):KS

---


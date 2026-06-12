---
title: "I found something quite weird. Anyone have any idea what's wrong?"
date: 2007-03-11
forum: General Help
---

### Post by ardchoille42 on 2007-03-11
I am using Ubuntu Dapper Drake. I found something quite weird.

```

[~ @ 04:08:19] whoami
ianmac
[~ @ 04:08:23] mount | grep /mnt/hdb1
/dev/hdb1 on /mnt/hdb1 type ext3 (rw)
[~ @ 04:08:33] sudo chown -R ianmac:ianmac /mnt/hdb1
[~ @ 04:08:47] ls -lha /mnt/hdb1
total 0
?--------- ? ? ? ?                ? /mnt/hdb1/.
?--------- ? ? ? ?                ? /mnt/hdb1/..
?--------- ? ? ? ?                ? /mnt/hdb1/backups
?--------- ? ? ? ?                ? /mnt/hdb1/dimages
?--------- ? ? ? ?                ? /mnt/hdb1/firefox
?--------- ? ? ? ?                ? /mnt/hdb1/initial
?--------- ? ? ? ?                ? /mnt/hdb1/lost+found
?--------- ? ? ? ?                ? /mnt/hdb1/music
?--------- ? ? ? ?                ? /mnt/hdb1/sysrescd
[~ @ 04:13:05] sudo ls -lha /mnt/hdb1
total 56K
drw-r-xr-x 9 ianmac ianmac 4.0K 2007-03-11 03:57 .
drwxr-xr-x 7 root   root   4.0K 2007-03-08 10:15 ..
drwxr-xr-x 2 ianmac ianmac 4.0K 2007-03-11 03:54 backups
drwxr-xr-x 2 ianmac ianmac 4.0K 2007-03-11 03:54 dimages
drwxr-xr-x 2 ianmac ianmac 4.0K 2007-03-11 03:55 firefox
drwxr-xr-x 2 ianmac ianmac 4.0K 2007-03-11 03:55 initial
drwx------ 2 ianmac ianmac  16K 2007-03-11 03:51 lost+found
drwxr-xr-x 2 ianmac ianmac  12K 2007-03-11 03:57 music
drwxr-xr-x 2 ianmac ianmac 4.0K 2007-03-11 03:57 sysrescd
[~ @ 04:19:06]

```

Does anyone have any idea what is wrong and how to correct it?

---

### Post by bernied on 2007-03-11
```
drw-r-xr-x 9 ianmac ianmac 4.0K 2007-03-11 03:57 .
```
Could it be that the execute bit (for owner) is not set on the base directory? So the owner cannot view the contents of the directory.
```
chmod 755 /mnt/hdb1
```should fix it.

---

### Post by ardchoille42 on 2007-03-11
> **bernied said:**
> ```
drw-r-xr-x 9 ianmac ianmac 4.0K 2007-03-11 03:57 .
```
Could it be that the execute bit (for owner) is not set on the base directory? So the owner cannot view the contents of the directory.
```
chmod 755 /mnt/hdb1
```should fix it.

That fixed it. I feel stupid now, hehe

Thank you for the heads up :D

---

### Post by bernied on 2007-03-11
No worries.
Watch [this](http://youtube.com/watch?v=Hp4iI59BfpQ), you won't feel so stupid.

---


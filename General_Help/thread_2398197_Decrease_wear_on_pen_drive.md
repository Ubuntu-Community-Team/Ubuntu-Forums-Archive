---
title: "Decrease wear on pen drive"
date: 2018-08-08
forum: General Help
---

### Post by raleigh3 on 2018-08-08
[B][SIZE=2]I want to decrease wear on my Clonezilla pen drive installation.

Final system tweaks
[/SIZE][/B]
**[SIZE=2]Decrease wear for a pendrive[/SIZE]**

[SIZE=2]**Add the mount option noatime in /etc/fstab** [/SIZE]

```
/dev/sdc1: UUID="2016-11-21-22-45-09-00" LABEL="2.5.0-5-amd64" TYPE="iso9660" PTUUID="1fae43d9" PTTYPE="dos" PARTUUID="1fae43d9-01"
/dev/sdc2: SEC_TYPE="msdos" LABEL="OCS-EFI" UUID="875C-F08F" TYPE="vfat" PARTUUID="1fae43d9-02"
```

How do I know which one to use for my UUID etc?

I have this in fstab.
UUID=2016-11-21-22-45-09-00                    /media/andy/2.5.0-5-amd64/   vfat noatime,errors=remount-ro 0  1

---

### Post by HermanAB on 2018-08-09
Err...  VFAT doesn't have atime anyway.

---


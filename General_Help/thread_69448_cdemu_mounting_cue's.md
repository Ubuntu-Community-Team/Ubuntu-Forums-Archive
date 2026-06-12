---
title: "cdemu mounting cue's"
date: 2005-09-26
forum: General Help
---

### Post by woofcat on 2005-09-26
Ok, Please someone make a detailed guide on this. I have tried to mount things many of times and have searched here and there to no clear solution. Could someone let me know how to mount a cue on Ubuntu.

This is currently what i do / get
```

root@Jims:/home/jim # mount /dev/cdemu/0 -t iso9660 /mnt/cdrom
mount: mount point /mnt/cdrom does not exist

```

---

### Post by seethru on 2005-09-26
does the directory /mnt/cdrom exist?

---

### Post by woofcat on 2005-09-27
Its not there. Nothing is in the /mnt

---

### Post by Gcool on 2005-09-27
First you have to create the directory.

mkdir /mnt/cdrom
mount /dev/cdemu/0 -t iso9660 /mnt/cdrom

---


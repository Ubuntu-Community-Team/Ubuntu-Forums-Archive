---
title: "New hard drive mounted on the first?"
date: 2014-05-20
forum: General Help
---

### Post by maazmahmood on 2014-05-20
I got a new hard drive, linux recognizes it as COMPAQ. and when I was looking at space left with "df -hk" I noticed that /dev/sda1 (COMPAQ) is mounted on /media/maaz/COMPAQ. Is this normal or should I be alarmed? Does this mean if I save something on Compaq it'll also be taking space up from my first hard drive. I know it sounds dumb but that's what I get from it. That COMPAQ is mounted on the first hard drive.

---

### Post by Bashing-om on 2014-05-20
maazmahmood; Hi !

The nomenclature 'sda' results as the 1st device recognized by the operating system.
To get a better idea of what the system sees and assigns compare the outputs of terminal commands:
```

sudo blkid
sudo fdisk -lu
sudo parted -l
cat /etc/fstab

```

thus
[INDENT][INDENT][INDENT]a tale is told
[/INDENT][/INDENT][/INDENT]

---


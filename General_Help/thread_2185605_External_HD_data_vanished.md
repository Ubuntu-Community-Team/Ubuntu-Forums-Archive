---
title: "External HD data vanished"
date: 2013-11-03
forum: General Help
---

### Post by ArchGabriel on 2013-11-03
Hi guys,

I have some serious problem here: I have a 500Gb Samsung external HD and I saved some important back up there. The problem is that some folders content just vanished! I don't know what happened and I tried almost every solution that I found on the internet (foremost, fidentify, testdisk, etc.) but none of them worked.
.
Is there anyway to recover my data?
.
Please, it is very important!
.
Thank you all in advance,

---

### Post by Bashing-om on 2013-11-03
ArchGabriel; Hi !

Have you tried to access your data from the command line ? Have you mounted the data disk manually and see what results ?

Show us what there is to work with, and we can try and mount/access from the command line.

```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print
sudo parted /dev/sda unit s print

```

If the hard disk is partitioned "GPT" then "fdisk" can not relate, we do the looking with "gdisk":
```

sudo gdisk -l /dev/sda
sudo gdisk -l /dev/sdb

```

If that data disk can not be mounted from the command line then indeed there is a serious problem.

[INDENT][INDENT]the longest journey starts with 1 step
[/INDENT][/INDENT]

---


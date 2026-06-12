---
title: "i get endless error messages upon login after a reboot (16.04lts)"
date: 2017-08-13
forum: General Help
---

### Post by ronjjjg8885 on 2017-08-13
seems that something is wrong with my os.

i don't know with which error to start.

take that for instance
[ATTACH=CONFIG]276387[/ATTACH]

can't believe there are so many hurdles with linux

---

### Post by cariboo on 2017-08-13
Once you learn hoe to use a Linux distribution, things get way easier, after all you've used Windows most of your life, and just recently started using Ubuntu. Restart in recovery mode and run the following command:

```
fsck /dev/sdxX
```

where /dev/sdXx = the partition you have Ubuntu mounted on. This command is basically equivalent to MS' chkdsk command.

If this doesn't help, make sure you submit the bug, as we all need to help with making Ubuntu better.

---

### Post by ronjjjg8885 on 2017-08-14
> [COLOR=#000000]where /dev/sdXx = the partition you have Ubuntu mounted on[/COLOR]
how to determine that?

---

### Post by Bashing-om on 2017-08-14
ronjjjg8885; Hey hey ;

> **ronjjjg8885 said:**
> how to determine that?

To see the drive partitioning :
Terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
where you are looking for the partition with the "boot" flag .

[INDENT][INDENT]careful is no accident
[/INDENT][/INDENT]

---


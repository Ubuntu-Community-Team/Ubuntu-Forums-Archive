---
title: "grub not lunching every time"
date: 2008-04-18
forum: General Help
---

### Post by koopah on 2008-04-18
hi,

sorry for my bad english,

i have gutsy on my new laptop (amilo pa 2548) and sometimes grub just don't work and my screen shows "operating system not found" instead of the grub menu.

the problem is that most of the time it works but sometimes (1/5 maybe) grub don't want to run and i must turn off my compter so it's kinda boring !

do you have any ideas of the reason of this problem?

thx guys

---

### Post by dstew on 2008-04-18
If it works sometimes, and sometimes not, it is usually a hardware problem. It could be a failing disk drive, or a bad ribbon cable. You can check the drive for errors using```
sudo fdisk
```EDIT: Wrong command. It should be```
fsck
```

---

### Post by bingoUV on 2008-04-18
How old is the hard drive? Do you frequently walk/travel with the laptop switched on i.e. so that there are mild to serious jerks to the laptop?

To check for bad blocks, boot from a live CD and run
```

sudo /sbin/fdisk -l

```

In the output, under the device column you will find /dev/hda1, /dev/hda2 etc. or /dev/sda1, /dev/sda2 .. or something like this. Accordingly, do like
```

sudo /sbin/e2fsck -cc /dev/hda1     
sudo /sbin/e2fsck -cc /dev/hda2

```
OR
```

sudo /sbin/e2fsck -cc /dev/sda1     
sudo /sbin/e2fsck -cc /dev/sda2

```

---

### Post by koopah on 2008-04-18
my laptop has 3 month and i don't travel with it so i assume the hard drive should be ok

thx for the advice i'll try these commands and tell you the results

i hope it's not my hard drive btw :(

---


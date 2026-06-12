---
title: "[SOLVED] I've got a mounted device that doesn't exist"
date: 2008-02-02
forum: General Help
---

### Post by init1 on 2008-02-02
I just install Xubuntu Gutsy today, and I was looking through my home folder with Thunar. I noticed that there was a 19M volume recognized as a disk, so out of curiosity, I clicked to mount it. The contents seem to be that of a distro's "/". When I did a "df" it told me that I had mounted "/dev/sda9". Both "fdisk -l" and gparted confirm that I don't **have** a "/dev/sda9"! What is this, and should I be concerned?

---

### Post by nemilar on 2008-02-02
Please post the contents of /proc/mounts:

```
cat /proc/mounts
```

Also, you might try seeing if

```
dmesg | grep sda9
```

says anything; if so, post that here, too.

---

### Post by init1 on 2008-02-02
> **nemilar said:**
> Please post the contents of /proc/mounts:

```
cat /proc/mounts
```

Also, you might try seeing if

```
dmesg | grep sda9
```

says anything; if so, post that here, too.
I did the dmesg, and it gave me
> 
[   12.900000]  sda3: <minix: sda9 sda10 sda11 >

Looks like /dev/sda9 is one of minix's subpartitions then. That would make sense.
Thanks I think that solved it. :D
Edit:
I checked the contents of "/dev" and indeed they are minix style devices. Thanks again :D

---


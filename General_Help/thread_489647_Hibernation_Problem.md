---
title: "Hibernation Problem"
date: 2007-07-01
forum: General Help
---

### Post by Di@blo on 2007-07-01
My system: Toshiba Satellite Pro 4600 [PIII @ 900MHz, 256MB RAM], runs perfect.

After upgrading from Dapper Drake (6.06 LTS) to Feisty Fawn [I reformatted and started over, guided partition], whenever I choose "Hibernate" from the exit menu, it goes fine for about 10 seconds, then this text comes up on the screen (just a tiny sample, because it's all pretty much the same):

```
[ 66.124000] usbdev2......(something)
[ 82.604000] Swap Error....
[ 82.784000] Buffer I/O error on device sda1, logical block 197804
[ 82.788000] Remounting File System Read-Only 
[ 82.936000] EXT3-fs error (device sda1): ext3_find_entry: reading directory #
995521 offset 0
```

Ok, so obviously this is an error with the drive. Can you recommend something besides reformating? [Although I really don't mind reformatting because I don't have anything of use on the HD, just the installation]

Also, I don't know if this has to do with it, but when I put in the 7.04 Live CD while 6.06 was on the drive, it would get stuck on 15% and lock up when I tried to reformat and install. But when I deleted the old partition with GParted (on the 7.04 live-cd) and then tried, it worked.

---

### Post by Di@blo on 2007-07-01
Anyone?

---

### Post by Cuppa-Chino on 2007-07-02
have you done a low level check on the drive? I mean for faulty blocks and sectors ?

---

### Post by Di@blo on 2007-07-02
Nope. What app(s) would you recommend for going about that?

---

### Post by CycleGeek on 2007-07-04
I've got the same issue - I also get swap errors when I try to hibernate.  Any help is definitely appreciated.

---

### Post by Cuppa-Chino on 2007-08-12
SOLVED - not enough memory to boot live cd

---


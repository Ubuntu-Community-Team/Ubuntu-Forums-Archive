---
title: "Ubuntu duel boot :|"
date: 2007-11-14
forum: General Help
---

### Post by darklight199 on 2007-11-14
I cannot select what OS I want to boot, it just loads right up to Ubuntu, I'm trying to load Windows XP.  Also, I tried to do a system restore but when I hit F10 for windows restore it did nothing...

---

### Post by HighSide on 2007-11-14
Have you gone into the Grub menu?

Hit ESC during boot, but you got to be quick, I think the default delay is 2 secs.

---

### Post by blop on 2007-11-14
I think you mean dual boot....a duel boot would probably mean loading two different OS that would battle to death somehow. They could not use swords or pistols....so likely it would be some buffer over flow fight.....

I digress

Whilst installing Ubuntu on top of your XP machine  (i assume thats the way you did it) where did you tell it to install?

---

### Post by darklight199 on 2007-11-14
I made a new partition for this.

---

### Post by blop on 2007-11-14
Did the installer recognise the windows partition?

---

### Post by Sef on 2007-11-14
Let's check that XP is there.

Applications > Accessories > Terminal

then type in this command:

```
sudo fdisk -l
```

copy and paste the results here.

---

### Post by darklight199 on 2007-11-14
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30048   241360528+  83  Linux
/dev/sda2           30049       30401     2835472+   5  Extended
/dev/sda5           30049       30401     2835441   82  Linux swap / Solaris

If I can't get this fixed I will have to buy a $200 cd to get windows back.

---

### Post by darklight199 on 2007-11-14
Bump:confused:

---

### Post by IcemanV9 on 2007-11-14
Uh-oh. XP is nowhere to be found on your HD.

For comparsion's sake (I have dual-boot [XP & Ubuntu] ) ...
```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2676    21494938+   7  HPFS/NTFS
/dev/sda2           11436       12161     5828760   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3            2677       11076    67473000   83  Linux
/dev/sda4           11077       11435     2883667+   5  Extended
/dev/sda5           11077       11435     2883636   82  Linux swap / Solaris

```

---

### Post by ronmarley1 on 2007-11-14
> **blop said:**
> I think you mean dual boot....a duel boot would probably mean loading two different OS that would battle to death somehow. They could not use swords or pistols....so likely it would be some buffer over flow fight.....

I digress



Now that's funny!

---


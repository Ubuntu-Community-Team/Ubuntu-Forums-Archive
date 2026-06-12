---
title: "Scanning Disk for errors"
date: 2006-08-12
forum: General Help
---

### Post by true_friend on 2006-08-12
some times here in Pakistan power fails and my system goes off. when i restars it then if thw o/s was windows it automatically check the hdd for error. while in ubuntu DD it checks after a lot of such failures. i experienced it scan dist while booting automatically but not every time when system goes off due to power failure. 
is it possible to configure ubuntu to check every time hard for errors after such power failure. 
This is my suggesstion also for Egy to make is automatic there. 
Regards
True_Friend

---

### Post by ifokkema on 2006-08-12
Well, you see, the Linux file system ext3 is much better at error recovery. The reason why it doesn't check the disk completely is because it's just not necessary. It checks the disk logs quickly and repairs any inode inconsistancies when booting up after a power failure, and that's just all it needs to do...

---

### Post by jordilin on 2006-08-12
Just type
```
tune2fs -c 1 /dev/hdaX
```
where X is the partition you wanna check at every boot

---

### Post by true_friend on 2006-08-12
but i have only one partiton with ext3
3 others are at fat32.

---

### Post by jordilin on 2006-08-12
> **true_friend said:**
> but i have only one partiton with ext3
3 others are at fat32.

Well, if I'm not wrong tune2fs only works for ext2 and ext3. Try typing
```
shutdown -rF now
```
and see if that checks your fat partitions as well

---

### Post by ifokkema on 2006-08-12
> **jordilin said:**
> Just type
```
tune2fs -c 1 /dev/hdaX
```
where X is the partition you wanna check at every boot
This will make the system fsck the drives **every time after boot** (or more precisely, every time it's mounted). I hope the power supply in Pakistan is not that bad that a fsck needs to be run every time you boot the PC... :???:

---

### Post by true_friend on 2006-08-12
ifokkema: u are right. it is not much bad situation here. but it should be automatic for other drives or any one which is in use and power fails. developers should see this idea in next release.

---

### Post by ifokkema on 2006-08-13
> **true_friend said:**
> but it should be automatic for other drives or any one which is in use and power fails. developers should see this idea in next release.
I think they will say it's just not necessary, as the journal is checked on mount time anyway, but you'll never know :)

---


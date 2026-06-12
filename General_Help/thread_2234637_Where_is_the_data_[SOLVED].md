---
title: "Where is the data? [SOLVED]"
date: 2014-07-15
forum: General Help
---

### Post by Bryant_Arrington on 2014-07-15
I installed a copy of Ubuntu 14.04 beside another copy of 14.04 that went wacko.  I do not know why.  This laptop is for a friend who only uses it for email so it really doesn't matter except that she had a few documents on the old copy.  I thought I would just copy them over, but realized I don't know where they are.

I went to the usr folder but do not see an obvious folder name in it.

Any help??

thanks!!!

---

### Post by ubudog on 2014-07-15
The files are probably on the old partition.  Can you post the output of:
```
sudo fdisk -l
```

---

### Post by oldos2er on 2014-07-15
If your friend is using Thunderbird, mail is stored in /home/user/.thunderbird/xxxxxxxx.default/Mail/
If you copy over the entire /home/user/.thunderbird/ folder plus its subfolders, to the current /home/user/ folder, Thunderbird will "see" and use it.

---

### Post by Bryant_Arrington on 2014-07-15
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000869ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   248277791   124137872   83  Linux
/dev/sda2       248279038   488396799   120058881    5  Extended
/dev/sda5       484732928   488396799     1831936   82  Linux swap / Solaris
/dev/sda6       248279040   484732927   118226944   83  Linux

Partition table entries are not in disk order

---

### Post by Bryant_Arrington on 2014-07-15
Thanks Ann.  I think I need to show hidden files too,.. right?

Edit:  I do not see the Home folder.  That is what I am looking for.

---

### Post by Bryant_Arrington on 2014-07-15
I did a search for "home" and found it.

Thanks all!!!

---

### Post by ubudog on 2014-07-15
Oh, my bad, I didn't realize you had mounted the partition already. #-o

---

### Post by bab1 on 2014-07-15
> **Bryant_Arrington said:**
> I installed a copy of Ubuntu 14.04 beside another copy of 14.04 that went wacko.  I do not know why.  This laptop is for a friend who only uses it for email so it really doesn't matter except that she had a few documents on the old copy.  I thought I would just copy them over, but realized I don't know where they are.

I went to the usr folder but do not see an obvious folder name in it.

Any help??

thanks!!!
FYI:  The /usr directory is really not NOT for users.  The name comes from **U**nix **S**ystem **R**esources.  This is where you store applications and unix type tools to manage the running system.

---


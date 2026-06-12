---
title: "LVM slow"
date: 2007-11-23
forum: General Help
---

### Post by marstein on 2007-11-23
After I successfully installed LVM and build a 3 disk array for backing up the other machines in the house things look pretty good. Except that deleting files on the LVM array is very slow:

```
Martin@momoputer:~/backup$ ll *TIB
-rwxr--r-- 1 Martin martin 6.1G 2007-11-16 23:47 2007_11_15_23_15_10_531D2.TIB
-rwxr--r-- 1 Martin martin 9.8G 2007-11-17 23:56 2007_11_15_23_15_10_531D3.TIB
-rwxr--r-- 1 Martin martin 9.7G 2007-11-18 23:51 2007_11_15_23_15_10_531D4.TIB
-rwxr--r-- 1 Martin martin 250G 2007-11-16 09:20 2007_11_15_23_15_10_531D.TIB
Martin@momoputer:~/backup$ time rm *TIB acronis_backup_place.cfg

real    6m27.788s
user    0m0.004s
sys     1m36.198s
```

6 minutes to delete 5 files?? What's going wrong? What information is needed to debug this problem?
I would be grateful for any hints. Thanks

---

### Post by Toet on 2007-11-23
There is a known bug where the read ahead of the lvm is default set at 256. This should be more like 8196.

workaround:

sudo blockdev --setra 8196 /dev/vg/lv

disappears after reboot.

Maybe it helps your delete, which I doubt.

---


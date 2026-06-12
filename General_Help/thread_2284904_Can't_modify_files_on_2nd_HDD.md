---
title: "Can't modify files on 2nd HDD"
date: 2015-07-02
forum: General Help
---

### Post by Andromendous on 2015-07-02
Hello all, New guy in town, have a little problem, I have a SSD which i dual boot win8 and Xubuntu 15.04, then I also have a 1TB HDD as storage also,

I used the program "Disks" to set it to auto mount the HDD on boot, I can copy files to the drive, but I cannot delete or modify any files on the drive, When i try to delete files, it says something like "cannot find trash bin" or something similar. 

If anyone has any ideas it would be much appreciated. 

Thank you.

---

### Post by tgalati4 on 2015-07-02
While in Ubuntu, open a terminal and post the output of:

```
cat /etc/fstab
cat /etc/mtab

```

---


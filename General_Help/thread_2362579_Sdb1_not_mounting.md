---
title: "Sdb1 not mounting"
date: 2017-05-30
forum: General Help
---

### Post by raleigh3 on 2017-05-30
Sdb1 is not mounting ?
```

  !/bin/bash

thunar /media/andy/MAXTOR_SDB1/Linux_Files/
```

----------------------------------------

Contents of fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation

UUID=ac6bf8cc-5bbc-44a6-a92f-0745372729f7 /               ext4    errors=remount-ro 0       1
UUID=b3b0f384-9e2e-45f5-8995-932f1113f59d      /SDB1_Mountpoint   ext3
Blkid
/dev/sda1: UUID="ac6bf8cc-5bbc-44a6-a92f-0745372729f7" TYPE="ext4" PARTUUID="cafc53cc-01"
/dev/sdb1: LABEL="MAXTOR_SDB1" UUID="b3b0f384-9e2e-45f5-8995-932f1113f59d" TYPE="ext3" PARTUUID="000f0791-01"
/dev/sdb2: LABEL="MAXTOR_SDB2" UUID="8adebdf0-6bc3-4eee-8363-3e9440688d42" TYPE="ext3" PARTUUID="000f0791-02"
/dev/sdb5: LABEL="MAXTOR_SDB5" UUID="fd00f2d7-d666-4614-885d-5ace942dd3f6" SEC_TYPE="ext2" TYPE="ext3" PARTUUID="000f0791-05"
```

---

### Post by yancek on 2017-05-30
At the beginning of your post you are trying to access sdb1 in the thunar filemanager at this location:

> **[SIZE=4]thunar /media/andy/MAXTOR_SDB1/Linux_Files/[/SIZE]**

Your fstab shows:  [SIZE=4]UUID=b3b0f384-9e2e-45f5-8995-932f1113f59d      /SDB1_Mountpoint   ext3[/SIZE]

If that's in your fstab it won't work as it needs to be the correct mount point which actually exists, the MAXTOR_SDB1 under /media/andy diretory created.   Do actually have the correct entry?  You also forgot to post what happens when you try to mount.  Does it fail to mount on boot, can you manually mount or does that fail?  And what happens when you try? 
Do you not have any other parameters for sdb1 in fstab?

---

### Post by vasa1 on 2017-05-31
Please use [CODE] tags to enclose material copied from the terminal or from log files and for scripts. Thanks.

---

### Post by raleigh3 on 2017-06-02
You are correct.

This fixed the problem.

```
UUID=b3b0f384-9e2e-45f5-8995-932f1113f59d      /media/andy/MAXTOR_SDB1   ext3
```

---


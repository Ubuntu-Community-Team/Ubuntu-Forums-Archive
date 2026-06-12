---
title: "fstab stopped working?"
date: 2019-02-22
forum: General Help
---

### Post by raleigh3 on 2019-02-22
Up till yesterday, this fstab mounted all my drives. Now, none of sdb mounts?
  ```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=a85421a7-db09-4922-ba41-8312a2f66556      /                   ext4    errors=remount-ro 0       1
UUID=b3b0f384-9e2e-45f5-8995-932f1113f59d      SDB1_Mountpoint     ext3     defaults         0       0
UUID=8adebdf0-6bc3-4eee-8363-3e9440688d42      SDB2_Mountpoint     ext3     defaults         0       0
UUID=8cdd0e0d-7714-4199-90ba-c6c20ff0ee1d      SDB5_Mountpoint     ext3     defaults         0       0

/swapfile                             none            swap    sw                         0       0

```

blkid

```
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/sda1: UUID="a85421a7-db09-4922-ba41-8312a2f66556" TYPE="ext4" PARTUUID="87fb6afb-01"
/dev/sdb1: LABEL="MAXTOR_SDB1" UUID="b3b0f384-9e2e-45f5-8995-932f1113f59d" SEC_TYPE="ext2" TYPE="ext3" PARTUUID="000f0791-01"
/dev/sdb2: LABEL="MAXTOR_SDB2" UUID="8adebdf0-6bc3-4eee-8363-3e9440688d42" SEC_TYPE="ext2" TYPE="ext3" PARTUUID="000f0791-02"
/dev/sdb5: LABEL="MAXTOR_SDB5" UUID="8cdd0e0d-7714-4199-90ba-c6c20ff0ee1d" SEC_TYPE="ext2" TYPE="ext3" PARTUUID="000f0791-05"
     

```

---

### Post by QIII on 2019-02-22
Hello!

Can you mount the device manually?

---

### Post by raleigh3 on 2019-02-22
```
mount: /SDB1_Mountpoint: /dev/sdb1 already mounted on /SDB1_Mountpoint.
```

But I still cannot see the drive.

---

### Post by QIII on 2019-02-22
OK.

I don't think fstab is the issue, then.  It's definitely mounted.

Where do you not see the drive when you expect to?  Can you navigate to any directories on the device in the terminal?

---

### Post by raleigh3 on 2019-02-22
I got this to work.

 ```
thunar  /SDB1_Mountpoint/Ubuntu_Mate_18.04
```

 Caja is set to show mounted volumes  but for some reason it is not working.

---

### Post by QIII on 2019-02-22
Ok.  You might want to go to your opening post and edit the title to get the right people looking.

"Edit Post" and then "Go Advanced"

---


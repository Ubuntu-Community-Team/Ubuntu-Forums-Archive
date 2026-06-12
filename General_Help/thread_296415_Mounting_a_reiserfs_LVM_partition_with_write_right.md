---
title: "Mounting a reiserfs LVM partition with write rights for a normal user"
date: 2006-11-09
forum: General Help
---

### Post by Jongi on 2006-11-09
The part of the fstab stands as:

```

/dev/Store/lvol0 /mnt/Store     reiserfs rw,defaults    1       2
```

I used **sudo mkdir /mnt/Store** to create the mountpoint.

I've done some searching and I've tried amongst others (after doing some searching):

```

/dev/Store/lvol0 /mnt/Store     reiserfs noatime    0       2
/dev/Store/lvol0 /mnt/Store     reiserfs defaults,user_xattr    1       2
/dev/Store/lvol0 /mnt/Store     reiserfs rw,user,defaults    1       2
```

EDIT: Here is what the /etc/mtab section looks like
```

/dev/mapper/Store-lvol0 /mnt/Store reiserfs rw 0 0
```

If there are any spelling mistakes, the error is here and not what was in the fstab at the time I tried the option.

---

### Post by Jongi on 2006-11-09
I share the LVM partition above between SUSE, FC5 and Kubuntu. So if an fstab entry is not possible, a Kubuntu startup script that will issue as a root user **chown jongi: /mnt/Store** after the drives are mounted will also do.

---

### Post by Jongi on 2006-11-11
I've seen that using chmod above means having to run it every time I load a different distro. I have since learned that using **chmod -R 777 Store/** removes that problem. I did try adding umask=777 or umask=0777 to the fstab entry but that rendered the partition unmounted.

---


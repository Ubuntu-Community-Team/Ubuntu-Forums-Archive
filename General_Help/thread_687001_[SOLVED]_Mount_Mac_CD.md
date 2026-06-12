---
title: "[SOLVED] Mount Mac CD"
date: 2008-02-03
forum: General Help
---

### Post by init1 on 2008-02-03
I've got an old Mac CD from 1995 that I would like to mount. I've tried
```

sudo mount /dev/cdrom /mnt
sudo mount -t hfs /dev/cdrom /mnt
sudo mount -t hfsplus /dev/cdrom /mnt
sudo mount -t iso9660 /dev/cdrom /mnt

```
And none of it worked. 
Anyone have any ideas?

---

### Post by pointone on 2008-02-04
What error message is displayed?

---

### Post by 3rdalbum on 2008-02-04
You might need to install the "hfsutils" and "hfsplus" packages and use them on the command-line. They won't actually mount the drive, but with their own versions of the basic file management tools they will let you view the drive and copy files from it.

You'll need to look at the man pages for these packages:

```
man hfsutils
man hfsplus
```

to learn how to use them.

---

### Post by init1 on 2008-02-04
> **3rdalbum said:**
> You might need to install the "hfsutils" and "hfsplus" packages and use them on the command-line. They won't actually mount the drive, but with their own versions of the basic file management tools they will let you view the drive and copy files from it.

You'll need to look at the man pages for these packages:

```
man hfsutils
man hfsplus
```

to learn how to use them.
Thanks, the hfsutils work fine for what I need :D

---


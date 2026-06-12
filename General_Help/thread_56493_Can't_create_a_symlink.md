---
title: "Can't create a symlink"
date: 2005-08-12
forum: General Help
---

### Post by cjoshuav on 2005-08-12
I'm trying to symlink my Thunderbird address book with the following:

```
$ sudo ln -s "/media/elysium/profiles/Thunderbird/Joshua-Win/abook.mab"
```

And I keep getting "Operation not permitted."

I just experimented with doing this in my /home directory and it works fine.  This is a folder on a different drive (Fat32).  Are there any permissions I need to set or change?

What am I doing wrong?

Joshua

---

### Post by amohanty on 2005-08-12
That depends on how the drive is mounted. Take a look at your fstab or type mount at  the command prompt and post the output.

AM

---

### Post by sir_mud on 2005-08-13
I'm having a similiar problem, here's the line from my fstab
/dev/hdb4       /media/www    vfat    umask=000       0       0
that's the default one ubuntu made on install

---

### Post by doclivingston on 2005-08-13
Fat32 doesn't support symbolic links (or hard links). You can create a symbolic links that points to something on a fat32 partition, but you can't create a link on one.

---


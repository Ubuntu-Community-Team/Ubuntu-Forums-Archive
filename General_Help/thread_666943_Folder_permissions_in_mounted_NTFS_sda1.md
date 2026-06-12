---
title: "Folder permissions in mounted NTFS sda1"
date: 2008-01-13
forum: General Help
---

### Post by brunods on 2008-01-13
Hey,

I have a mounted NTFS partition with Windows XP.
in fstab I set umask so that every user would have rx permissions and root would have wrx permissions.

Now I would like to know how to make a particular folder inside the mounted partition to be writtable by other users...
How can I do that?

Thanks a lot.

---

### Post by taurus on 2008-01-13
Maybe you can mount that ntfs partition with ntfs-3g driver instead of just ntfs driver in /etc/fstab.  Of course, you need to install ntfs-3g first.

```
sudo apt-get update
sudo apt-get install ntfs-3g
```

---


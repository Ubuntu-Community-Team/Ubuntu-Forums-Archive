---
title: "when I mount partitions a desktop link does not come up!! grr"
date: 2007-04-20
forum: General Help
---

### Post by billdotson on 2007-04-20
Ok say for instance I want to temporarily mount my Windows partition to copy some files to my ext3 partition.  Sounds like it wouldn't be so hard, right?

I have made the mount point /media/Windows, set the user to my default user (so not root)

and ran:

```

sudo mount /dev/sda1 /media/Windows/ -t ntfs -o nls=utf8,umask=0222

```

I get no error messages and if I go to the terminal and cd into /media/Windows I can see everything on that partition, but there is no link to it on the desktop, like there would be for something that automounts like a CD drive would (or partitions/ hard drives normally would)

This also happens if I go and edit my fstab to add a certain device to mount on a given mount point.  I do the normal  ```
 sudo umount -a 
``` and then ```
 sudo mount -a 
```
to get it to mount but it doesn't unless I reboot.  I can cd into it using the terminal fine, but there is no desktop link.

---

### Post by Compyx on 2007-04-20
See my last post in this thread: [http://ubuntuforums.org/showthread.php?t=414667]("http://ubuntuforums.org/showthread.php?t=414667"), the advice is for people wanting the reverse: to not see icons of mounted volumes, but the approach is the same. (Just check the box, not uncheck it).

---

### Post by billdotson on 2007-04-20
when doing manual mounts or adding new fstab entires desktop links do not come up.  With an fstab entry a ctrl-alt-backspace is required.

So... I got it.

---


---
title: "Conky if_mounted and autofs (automount)"
date: 2013-03-06
forum: General Help
---

### Post by tcsoft on 2013-03-06
I do have a problem with conky's if_mounted function to check if a device is mounted or not.
I have installed the package autofs, which automates the mount-process.

> **autofs** is a program for automatically mounting  directories on an as-needed basis. Auto-mounts are mounted only as they  are accessed, and are unmounted after a period of inactivity.
[http://help.ubuntu.com/community/Autofs]("https://help.ubuntu.com/community/Autofs")

In conky I use a template to check free space, only if a device is mounted:

```
template0 ${if_mounted \1}${fs_used \1}/${fs_size \1} (${fs_used_perc \1}%)${else}\1 not mounted${endif}
```

The problem:
Conky permanently checks for fs_used and autofs will not unmount the disks anymore.
Has anyone a solution to get around?

Thanks

---

### Post by dino99 on 2013-03-06
you might have several times packages doing dupe processes, as mountall already deal with mount/umount.

That conky thread is very documented:
[http://ubuntuforums.org/showthread.php?t=1771033](http://ubuntuforums.org/showthread.php?t=1771033)

---

### Post by tcsoft on 2013-03-06
mountall can not deal with mount/unmount in my situation, as my external harddisks are not listed in /etc/fstab ;)

---

### Post by tcsoft on 2013-03-06
situation: all autofs-disks are unmounted.
I start conky and autofs mounts the disks. Seems like the "if_mounted" statement is useless, or more likeley, it does some I/O operations and autofs mounts the disks (because of I/O access).
In my understanding, "if_mounted" should check the output of the "mount" command for the given "mountpoint" - and nothing else.

---


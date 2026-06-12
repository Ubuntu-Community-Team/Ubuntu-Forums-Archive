---
title: "copy files in live mode."
date: 2013-02-08
forum: General Help
---

### Post by ulao on 2013-02-08
I booted a liveCD of ubuntu on my windows box. All I want here is to move some backed up linux files ( currently on a windows partition ) to a linux drive. I can see both drives but when I copy I'm told I dont have permission to copy to the linux drive. How do I get permission.

---

### Post by sudodus on 2013-02-08
You probably do not own the target directory. One way is to copy with superuser privileges. I would do it in a terminal windows with ***cp*** (if simple) or ***rsync*** if more advanced. See ```
man rsync
```
```
sudo rsync -av /path/sourcedir/ /path/targetdir
```

If you prefer doing it with a file browser you can start it from a terminal window with
```
gksudo nautilus --no-desktop
```
*Beware, you can easily destroy your system* when the file browser has superuser privileges, so close it as soon as you have finished the copying.

---

### Post by ulao on 2013-02-08
Well I tried the rsync. Reading up on it afterword I dont think that is wise in my situation. I dont want update files I really need everything over written but the boot directories. I tried the rsync anyways just over writing the usr/etc/var/lib dirs and grub boots to the purple screen and then hangs. 

I guess I could try the same thing with a normal copy. Though I was wondering if unbuntu server has an in-place upgrade that will just fix up the OS and leave my installed software and settings?

ok CP:
using cp I tried with -afR seem to be doing the trick.

---

### Post by sudodus on 2013-02-09
> **ulao said:**
> Well I tried the rsync. Reading up on it afterword I dont think that is wise in my situation. I dont want update files I really need everything over written but the boot directories. I tried the rsync anyways just over writing the usr/etc/var/lib dirs and grub boots to the purple screen and then hangs. 

I guess I could try the same thing with a normal copy. Though I was wondering if unbuntu server has an in-place upgrade that will just fix up the OS and leave my installed software and settings?

ok CP:
using cp I tried with -afR seem to be doing the trick.
I'm glad cp 'seems to be doing the trick'. I guess you need -f to 'force copy' some stubborn file or directory.

Please confirm that it worked or come back and ask for other options :-)

---

### Post by ulao on 2013-02-09
I did the trick, thx!

---


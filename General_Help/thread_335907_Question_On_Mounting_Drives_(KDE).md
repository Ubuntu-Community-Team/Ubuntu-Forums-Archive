---
title: "Question On Mounting Drives (KDE)"
date: 2007-01-10
forum: General Help
---

### Post by jlacroix on 2007-01-10
I have mounted two more drives successfully in Kubuntu. (/mnt/windows and /mnt/storage). I can read the files in those drives through the terminal and they are automatically mounting through fstab and so far that part works.

What isn't working is that the drives aren't showing in my KDE System Menu. (The root "/" drive isn't there either, now that I think of it).

Is there a way to get those drives to appear in System for easy access?

fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=b4cbba8e-32f7-43bd-a418-37d35adba573 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=63a8ef0e-d32f-4421-a6b5-f6d7f82b7246 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1 /mnt/windows ntfs nls=utf8,umask=0222 0 0
/dev/hda2 /mnt/winstorage vfat iocharset=utf8,umask=000 0 0

```

---

### Post by aysiu on 2007-01-11
I don't know how to get them in the System menu (maybe right-click the menu and edit it, adding icons with the commands *konqueror /mnt/windows* and *konqueror /mnt/winstorage* to that submenu?).

You can, however, choose to display mounted partitions on your desktop (see attached image).

Or you could symlink them there: ```
sudo ln -s /mnt/windows ~/Desktop/windows
sudo ln -s /mnt/winstorage ~/Desktop/winstorage
```

---

### Post by jlacroix on 2007-01-11
I have already told KDE to show mounted hard drives on the desktop, but they do not appear there after setting that up. I made some links on my Desktop that seem to work, so I guess all that is left is sprucing up the system menu.

---


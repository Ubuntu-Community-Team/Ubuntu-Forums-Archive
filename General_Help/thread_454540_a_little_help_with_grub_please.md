---
title: "a little help with grub please"
date: 2007-05-25
forum: General Help
---

### Post by paranoiahax on 2007-05-25
Hi, I'm new to the forums, but I've had Ubuntu for about a year now. I've reinstalled windows 4 times within this year. Each time, windows has got rid of grub, and I've had to reinstall it, using :

```
find /boot/grub/stage1
root (hd0,0)
setup (hd0) 
quit
```

Also, when that update came out for Ubuntu that screwed up other partitions in the grub, I used the back up of menu.lst.

But now, I've tried both of the above methods, and it really DOES NOT work, i've tried over an over again :(

It's annoying, because I am really starting to miss Ubuntu now, even though it's only been gone for a few days lol.

Any help would be **greatly** appreciated. Thanks!

---

### Post by paranoiahax on 2007-05-25
anyone, please? :(

---

### Post by merlinus on 2007-05-25
Are you sure that your last re-install of windows did not hose your Ubuntu?

If you install ext2ifs from [http://www.fs-driver.org/](http://www.fs-driver.org/), you should then be able to look at your linux partitions.  At least that way you will know if they still exist.

-merlin

---

### Post by paranoiahax on 2007-05-25
I know they exist because I was browsing my own files on the live disk.

---

### Post by merlinus on 2007-05-25
Maybe this will help:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_restore_GRUB_menu_after_Windows_installation](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_restore_GRUB_menu_after_Windows_installation)

-merlin

---

### Post by merlinus on 2007-05-25
Here is another idea, in case the uuid of your linux partitions has been changed.

Enter the following in a terminal:

```

sudo fdisk -l

```

This will give you the linux partitions.

Then, for each (I am using /dev/sda7 as an example):

```

sudo vol_id -u /dev/sda7

```

This will give you the UUID for each partition.  Then compare this with the entries in your /etc/fstab

Be sure to look at the fstab for your installed system, NOT the one for the live cd.

hth....

-merlin

---


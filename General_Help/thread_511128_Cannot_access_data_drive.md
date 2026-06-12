---
title: "Cannot access data drive"
date: 2007-07-27
forum: General Help
---

### Post by Graham1 on 2007-07-27
Please help!!! Recently, I've been unable to access my data drive (fat32) in Ubuntu (which is also shared between Fedora and XP as well). When Ubuntu starts, it gets as far as "fschk..." or something similar and then halts (unless I press Ctrl+Alt+Del). Once I'm at the desktop, I get as far as /mnt/data but there are no folders/files within. 

:)

---

### Post by rillip on 2007-07-27
That's fsck that's running, file systems check.  It's best to let it complete, it can take a while though.  It's essentially the linux version of scandisk.  What's probably happening is that it tries to check, you interupt, when mounting it runs into an I/O error and so the mounting is aborted.  Let fsck run, say like overnight, and it should fix any issues on the disk.

---

### Post by Espreon on 2007-07-27
Hmmmmmm, try taking that data off the partion, put it on removable media. And do this in a terminal (if you don't have GParted installed):

```
sudo apt-get install gparted
```

And then repartion the partion and move the data back.
Or try defragging it.

Or Better yet do this:

Repartion it to an ext3 partion and on Windows goto this link: [http://e2fsprogs.sourceforge.net/ext2.html](http://e2fsprogs.sourceforge.net/ext2.html) or try this: [http://www.fs-driver.org/](http://www.fs-driver.org/)
download and install and enjoy! The links I provided are the websites of projects of ext3 drivers for Windows, I use the former and it works great for me.

---


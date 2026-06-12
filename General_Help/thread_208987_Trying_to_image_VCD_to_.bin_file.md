---
title: "Trying to image VCD to .bin file"
date: 2006-07-04
forum: General Help
---

### Post by maxillo on 2006-07-04
Hello,

I'm a total noob.  I know WinXP inside out, but feel totally useless with ubuntu.

I have a simple task.  I want to image my kids VCD movie to a .bin file on the hard-drive.

I'm using cdrdao with the following command.

$ cdrdao read-cd --device /dev/cdrom --datafile disc.bin toc 

and get an error saying

error trying to open /dev/cdrom exclusively (device or resource busy)...retrying...

What does this mean and how to I correct this error???[-( 

Thanks

---

### Post by evilghost on 2006-07-04
I've never used cdrdao but if I had to guess it would be because it's currently mounted (automount when disk is inserted).

I would unmount it first.

```

sudo umount /dev/cdrom
cdrdao read-cd --device /dev/cdrom --datafile disc.bin toc
eject /dev/cdrom

```

Hope this helped.

---

### Post by maxillo on 2006-07-04
Thanks so much...that did it!

---

### Post by evilghost on 2006-07-04
Glad to help.

---


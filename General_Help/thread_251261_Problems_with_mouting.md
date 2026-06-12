---
title: "Problems with mouting"
date: 2006-09-05
forum: General Help
---

### Post by Rhapsody on 2006-09-05
I've just reinstalled Kubuntu from scratch (root and /home both completely new) and I'm pretty happy overall, but I have a couple of problems with mounting disks.

First, the floppy drive. When I insert a disk, right click the Floppy Drive icon and select 'Mount', it seems to mount but the icon doesn't change to indicate this. Then, when I attempt to access the disk, I get a message saying:

```
Could not mount device.

The reported error was:

mount: dev/fd1 already mounted or /media/floppy0 busy

mount: according to mtab, dev/fd1 is already mounted on /media/floppy0
```

Sure enough, if I make my way to /media/floppy0, I find the contents of the disk. But why can't I access it through the drive icon?

Attempting to access hdb1 causes more worry though. Attempting to either mount or access the drive produces the following message:

```
Could not mount device.

The reported error was:

mount: can't find dev/hdb1 in /etc/fstab or /etc/mtab
```

A lot of my data (in fact, all of it) is on that partition, so I'd rather it be mounted when I boot actually, because I plan to use it a lot for various things.

---

### Post by gotgenes on 2006-09-05
> **Rhapsody said:**
> 
```
Could not mount device.

The reported error was:

mount: can't find dev/hdb1 in /etc/fstab or /etc/mtab
```

Shouldn't that be **/**dev/hdb1? The first / is missing in what you posted above.

Also, you should probably post your /etc/fstab file.

---


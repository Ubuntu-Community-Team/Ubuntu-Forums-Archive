---
title: "How to run a manual file system check?"
date: 2008-05-25
forum: General Help
---

### Post by tinker123 on 2008-05-25
Hi;

Something happened while I was booting my Ubuntu 8.04 box.  Now, every time I boot it tells me that a fcsk of my hard drive failed and that I need to run a manual file system check to make that message go away.

FWIW, I think it would helpful to include direction how to do that with that message.

Anyway, what do I need to do to make that message go away?

Thanks in advance

---

### Post by diablo75 on 2008-05-25
[http://ubuntuforums.org/showthread.php?t=618873](http://ubuntuforums.org/showthread.php?t=618873)

---

### Post by bingoUV on 2008-05-25
From a live CD, run 
```

sudo /sbin/fdisk -l

```

You will get a table, with first column "Device" and last column "System". For all devices that have System "Linux" (not "Linux swap" or something else), run the following after replacing <device>
```

sudo /sbin/e2fsck -c -f <device>

```

This will take quite long as I have included the -c option which will check the hard disk for bad blocks. I did this because some thing more than usual is wrong with your system, this is worthwhile for you.

---

### Post by ajgreeny on 2008-05-25
Or just before you shutdown or restart use ```
sudo touch /forcefsck
```At the next boot the system will do a check of all system partitions, including home if it is on a separate partition.

---

### Post by omababy on 2008-05-25
Nice tip there ajgreeny, I'll remember that one.

---

### Post by tinker123 on 2008-05-27
> **bingoUV said:**
> From a live CD, run 
```

sudo /sbin/fdisk -l

```

You will get a table, with first column "Device" and last column "System". For all devices that have System "Linux" (not "Linux swap" or something else), run the following after replacing <device>
```

sudo /sbin/e2fsck -c -f <device>

```

This will take quite long as I have included the -c option which will check the hard disk for bad blocks. I did this because some thing more than usual is wrong with your system, this is worthwhile for you.

Thanks much!

---


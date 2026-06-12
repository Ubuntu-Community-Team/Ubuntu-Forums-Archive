---
title: "how to change swap partition?"
date: 2004-11-16
forum: General Help
---

### Post by SVen2000 on 2004-11-16
how can I use another partition of my hard disk as swap? which utilities to use for this?

---

### Post by mrt on 2004-11-16
Have you considered not using one?  I don't use them, and I've never encountered a problem.  I have 512 megs of ram though...

---

### Post by jdong on 2004-11-16
Having some swap is never a bad idea! The Linux OOM (out-of-memory) handling techniques are quite harsh on desktops. Basically, when the system is completely out of RAM, Linux will pick the process using the most RAM, then kill it! Usually, this is X, and it'll zap your X session without warning!

To setup swap, I'm assuming you already have a free partition /dev/hda5 (or whatever), set to type 0x83 (Linux Swap). Use **cfdisk** to set the partition type if incorrect.

To create the swapspace: **mkswap /dev/hda5**. Should be common sense, but **MAKE SURE YOU TYPE IN THE CORRECT PARTITION!!!** Linux will not hesitate to zap any partition you specify, even one already in use!

To have Linux use it: **swapon /dev/hda5**.


To have Linux auto-use it on each startup, open up **/etc/fstab** with your favorite editor.

Add this line anywhere in the file:
```

/dev/hda2       none            swap    sw              0       0

```



-----

Note, you can also use a large file as a swapspace, so you don't have to create a separate partition. This approach does have a few downsides, such as lower performance and increased chance of fragmentation. Try to setup swap partitions if at all possible.

---

### Post by az on 2004-11-16
You can use parted to create partitions and move them around and such.  You must unmount the drive, though.  You can use the Ubuntu installer to play around with partitions - it uses parted.

You can also visit the gnu parted homepage and download boot and root images.  You boot the kernel then load a ramdisk which runs parted.

You can have several swap partitions, too, if you want.

---


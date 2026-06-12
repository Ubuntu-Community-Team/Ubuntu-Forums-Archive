---
title: "Unable to resize partitions - reported lack of free space when there is free space"
date: 2016-01-11
forum: General Help
---

### Post by jmunson-his on 2016-01-11
Greetings!

I've spent the better part of the morning attempting to get GParted to resize both the sda1 & sda4/sda5 partitions with no luck - searching for the answer to my particular problem has yielded no answer.

I'm still quite new to Linux in general (I'm using to run an internal web server for development reasons).

I have an older Dell once-Windows-Server-'03 box on which I've installed Ubuntu.  There were a bunch of updates this morning and upon approving them, found out there was no more space on /boot to perform the updates.

So began my search for 1) how to free up space, and 2) how to increase the partition size (hopefully without needing to reinstall).  /boot is a measely 243MiB, and /sda4 is ~79GiB.  /sda4 is only ~13% used, so there's lots of room to pull from.  Or so I thought.

I've booted into an Ubuntu LiveCD and run GParted from there.  However, GParted reports only 24MiB available as free space, not the GiB's I was expecting.

How do I resolve this problem?

I went this route after determining there seems to be nothing more to remove from /boot - having run the purge commands, etc.

Thanks!

---

### Post by sandyd on 2016-01-11
Hi, can you attach a screenshot of your GParted window please?

Thanks

---

### Post by jmunson-his on 2016-01-11
[IMG]http://i164.photobucket.com/albums/u9/jmunsonii/gparted_zps9u1spedg.jpg[/IMG]

---

### Post by sandyd on 2016-01-11
Ubuntu was installed with LVM (Logical Volume Manager). You will need to adjust partition sizes from the LVM utility.

To start with, please post the output of

```

lvdisplay
vgdisplay
pvdisplay
```

---

### Post by jmunson-his on 2016-01-11
LVDisplay:  [IMG]http://i164.photobucket.com/albums/u9/jmunsonii/lvdisplay_zpsijlycxy7.jpg[/IMG]

VGDisplay:  [IMG]http://i164.photobucket.com/albums/u9/jmunsonii/vgdisplay_zpscryj36ed.jpg[/IMG]

PGDisplay:  [IMG]http://i164.photobucket.com/albums/u9/jmunsonii/pvdisplay_zps0k90bpja.jpg[/IMG]

---

### Post by jmunson-his on 2016-01-11
Also, I could not install the graphical utility as there is no space to do so - this will all have to be done via command line... yay! :)

---

### Post by sandyd on 2016-01-11
Side Note: I highly do not recommend doing the below unless you absolutely are sure of this, and have backups. If you type something wrong, you can wipe out your disks. If Gparted fails, you may loose data. If you have actually cleaned up the boot partition (i.e., should have only one/two working kernels), it is much safer to simply move the boot partition to a external device such as a USB drive.

What you will have to do is the following:
1. Resize the LV you want to resize (In this case, /dev/ubuntu-kylin-vg/root
2. Rearrange/Defrag PV so that you can actually resize
3. Resize the PV (pvresize)

See [http://unix.stackexchange.com/a/193971](http://unix.stackexchange.com/a/193971) for direct instructions

The boot partition is at the start of the drive, you will have to move the partitions so that the free space appears on the left side of the extended partition. This will take a long time as you are basically copying the partitions from one place to another.

---

### Post by jmunson-his on 2016-01-11
Thanks for that, and no worries - this isn't a critical install and, honestly, aside from some desktops, I haven't done much with it so it is easily reinstalled. :)

---

### Post by jmunson-his on 2016-01-12
Alright - got it figured out. :)  

After following the thread  noted, I was left with unallocated space after sda5.  I wasn't sure what  to do with that (there seemed to be no way to move it), until I finally  realized that you have to shift that unallocated space around by  resizing/moving the partition(s) immediately next to it (which GParted  made really easy).  Once I figured that out 'twas a piece-of-cake to  complete (though, yes, it took quite a while).  All is good now. :)

Thanks for the help! :)

---


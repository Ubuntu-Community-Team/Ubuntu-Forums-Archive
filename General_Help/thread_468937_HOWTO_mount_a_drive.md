---
title: "HOWTO mount a drive"
date: 2007-06-09
forum: General Help
---

### Post by nami on 2007-06-09
I have 2x 250Gb drives and one of them I have ubuntu installed.

How do I mount the other drive without automating it.  I would like to only mount it when I want to using the terminal.

Help

---

### Post by taurus on 2007-06-09
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Or post the output of this command from a terminal.

```
sudo fdisk -l
```

---

### Post by nami on 2007-06-09
that seems to only be for fat32 or ntfs.  i would like to mount an ex3 drive manually.  the instructions in the link looked like it was setting up an automated mount on startup.

---

### Post by Bohlio on 2007-06-09
well, First you find the name of the drive, lets say this is your 2nd drive, 1st partition (hdb1), and you have your music on it.. Then you'd type in ```
mkdir /media/music
mount /dev/hdb1 /media/music
```

First you make the mount point, In this case, you have the drive mounted as /media/music.
then, you mount it. Replace /dev/hdb1 with the drive and partition that you want to mount, and change /media/music to wherever you want to mount it.

---

### Post by nami on 2007-06-09
Perfect thanks! :KS

---

### Post by Bohlio on 2007-06-09
I assume it worked?

---

### Post by nami on 2007-06-09
yes it worked perfectly, thanks :)

---


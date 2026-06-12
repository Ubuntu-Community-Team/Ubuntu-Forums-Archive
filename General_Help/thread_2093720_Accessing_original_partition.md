---
title: "Accessing original partition"
date: 2012-12-11
forum: General Help
---

### Post by wakkaa on 2012-12-11
I have ubuntu 9.04 on my desktop and installed the newest version of ubuntu 12.0 in a different partition on the same hard drive.  I'm using the 12.04 version and can't access the other partition data from the new partition.    I've tried using gparted and mounting the other partition and restarting computer but no matter what I do I can't access the old partition from the new partition.    Really I just want the old partition data on the new partition and delete the old version.  Any help would be awesome.  Thanks, Tim

---

### Post by deadflowr on 2012-12-11
Do either partition show up in the others home folder?
Look at the devices section in the left pane of the home folder(nautilus).

---

### Post by wakkaa on 2012-12-11
actually that helped.  It wasn't showing up from inside 12.0  but I booted into 9.04 and it showed the other then I copied the files over.  

Now I have a follow up problem.  I deleted the old partition and now I have half a hard drive worth of unallocated space.  how do I merge unallocated space with the other main partition?

---

### Post by Kirk Schnable on 2012-12-13
> **wakkaa said:**
> Now I have a follow up problem.  I deleted the old partition and now I have half a hard drive worth of unallocated space.  how do I merge unallocated space with the other main partition?

You could use GParted to achieve this.  You can't resize a partition while it's in use, but you could use a Ubuntu Live CD or a GParted Live CD ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)) to run GParted and resize your partition.

GParted is pretty straight-forward to use, but if you need any help, here's the official documentation on how to use it for resizing a partition:
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---


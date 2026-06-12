---
title: "QTparted vs Gparted...which is faster and more reliable?"
date: 2007-08-14
forum: General Help
---

### Post by Bart_D on 2007-08-14
Hello,

I was dwondering which partitioning package is faster...QTparted or Gparted?  I have Ubuntu on a single partition which I am hoping to split into 3 or 4 partitions (each around 20 GB) and install Zenwalk on one of them.  I was hoping for feedback on the two...opinions on which is faster and more reliable.  My video card is a crappy ATI Radeon 7000 and I am wondering if Zenwalk installed on a partition created through QTparted/Gparted would be faster in a dual boot system with Ubuntu than if it was installed with Gparted/QTparted respectively.

Your suggestions would be greatly appreciated
Bart_D

---

### Post by smoker on 2007-08-14
i've always used the 'gparted live-cd' for all my partitioning, it is pretty fast and has never let me down yet, info here:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

i don't think whatever you use to make the actual partitions will have any bearing on how fast the machine will dual boot.

---

### Post by rbmorse on 2007-08-14
I thought QTParted was old and no longer supported.

---

### Post by AlexThomson_NZ on 2007-08-14
> I am wondering if Zenwalk installed on a partition created through QTparted/Gparted would be faster in a dual boot system with Ubuntu than if it was installed with Gparted/QTparted respectively.

Whether the partition was created with gparted or qtparted will not affect the speed of the apps running on it.

Even the time spent doing the resizing/formatting, etc will likely not vary, as I believe they use the same backend, the only difference is Gparted uses gtk widgets (gnome) and QTparted uses QT widgets (KDE)

---

### Post by Bart_D on 2007-08-14
thanks for the replies.  I have ubuntu installed which I upgraded to xubuntu using synaptic.

Now, if Gparted uses gnome, will I have to d/l and install it using gnome or can I do everything from xfce?

---

### Post by merlinus on 2007-08-14
gparted live cd --  better with more features than the earlier version on the ubuntu live cd.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by smoker on 2007-08-14
use the gparted live cd, as i linked above, it will save you having the hassle of mounting and unmounting partitions you want to change, plus it is handy to have for backing up, copying  partitions, etc,

---

### Post by Bart_D on 2007-08-14
I have decided on GParted.

Anyone have an idea about my gnome/xfce question 3 posts above?
Bart_D

---

### Post by merlinus on 2007-08-14
If you use the gparted live cd, it will not even matter if you are running windows!

You boot from the cd.  No need to install the program.

-merlin

---

### Post by Bart_D on 2007-08-14
ok done.  I'll go with the Live-CD option.

Thanks for the QUICK replies.

---

### Post by Bart_D on 2007-08-14
Sorry one more question...are these partitions bootable?  I created one but was not asked if I want it to be bootable.  Is this done automatically, because it said "Boot" next to the one I shrunk while the other one said nothing?

---

### Post by merlinus on 2007-08-14
Generally the first partition on your hdd is marked bootable. especially if it is windows.  The others are not, but you can change the boot flag with gparted, if need be.

-merlin

---

### Post by Bart_D on 2007-08-14
Can you tell me how I would do this?  I am unable to select any boot option or flag option anywhere.

All I'v edone is shrink the only bootable partition on the HD, so there's now I think a lot of unpartitioned space....do I need to create a partition in this space and specify "boot" during THAT process, because I have done no such thing.:confused:

---

### Post by merlinus on 2007-08-14
Fine so far.  Exit, and boot from the ubuntu installation disk.  When you get to the partitioning menu, install in that free space.

It does not need to be bootable.

If you need further instructions, this may help:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

-merlin

---

### Post by Bart_D on 2007-08-14
I have ubuntu installed so I would do that for Zenwalk right?  Cause it's Zenwalk tgat I want to install on the other partittheion..

---

### Post by merlinus on 2007-08-14
Yes.  Pumalite is a very knowledgeable forum member who uses zenwalk, so he should be able to answer your questions about that distro.

-merlin

---

### Post by strabes on 2007-08-15
> **Bart_D said:**
> thanks for the replies.  I have ubuntu installed which I upgraded to xubuntu using synaptic.

Now, if Gparted uses gnome, will I have to d/l and install it using gnome or can I do everything from xfce?

Yes, it will simply load the gnome libraries, just like if you were to run a QT/KDE app inside gnome or xfce.

---

### Post by Bart_D on 2007-08-15
Alright, I have one last question:

Can I delete a partition with Gparted?  It has one of 2 Operating Systems installed and I don't want that OS anymore but instead want only the other of the two (want Xubuntu instead of Ubuntu.....:)).

If not with Gparted, then is there some other package with which this can be done?

Bart_D

---


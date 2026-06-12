---
title: "Can't boot Ubuntu from menu"
date: 2007-02-25
forum: General Help
---

### Post by WheelDawg on 2007-02-25
I recently had Windows die on me due to some Trojan horses (which I still don't know how they got there... heh)

So I re-formatted and re-installed Windows, however now my booting options are gone, and since Linux has a different filesystem, Windows doesn't even recognize that drive is there.

I'm pretty sure the way to fix it is a edit of the boot.ini or something similar, but I don't know what to edit in there.

Also, if it's possible (don't harass me from the forum for this, :lolflag: ) I'd like to keep Windows as the default OS, at least for now.

---

### Post by chewearn on 2007-02-25
You need to reinstall grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by LeslieL on 2007-02-25
That's a great link - in fact I bookmarked it for the next time I destroy everything. The last thing you need to do, once you're back in Ubuntu, is edit your /boot/grub/menu.lst file:

> gksudo gedit /boot/grub/menu.lst

or 

kdesu kate /boot/grub/menu.lst

Take some time to read through this file. It's full of interesting and useful information in the commented-out areas. 
Some way through the file you'll find a section starting
> ### BEGIN AUTOMAGIC KERNELS LIST

In this section (in mine) there are these lines:
> ## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)
In my case the default root device is hda1,3 (Linux starts counting from 0, so in Linuxese that changes to 0,2). Windows is on my hda1,1, so if I wanted to make that my default root device I'd change the line above to read
> # groot=(hd0,0)
Don't uncomment that line. Just change the numbers in it. 

I hope that's all a little clearer than mud. Good luck!

---

### Post by WheelDawg on 2007-02-25
Ok that sounds good.

One question though- If that line is commented why do the numbers in it matter? Is it only semi-commented? :P

I will probably try this out later on today, as lunch, church, and hangin out after church is kinda keeping me busy at the moment.

Thanks for the link!

---

### Post by LeslieL on 2007-02-25
They call it the Automagic section, so I think you're right, it's only semi-commented.  I guess grub doesn't use those lines, but whatever rewrites menu.lst when the kernel is upgraded does read them. It's all magic to me!

---


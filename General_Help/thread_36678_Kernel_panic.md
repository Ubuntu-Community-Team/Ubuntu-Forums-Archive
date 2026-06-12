---
title: "Kernel panic"
date: 2005-05-24
forum: General Help
---

### Post by Lunde on 2005-05-24
Kernel panic Not syncing: VFS: unable to mount root fs on unknown-block (0,0)

Ubuntu Hoary Hedgehog 5.04 

I belive that I'm not the only one who got this message today... I hope I am, but this all came after an update notified in my Gnome panel. I don't remember exactly which updates by name, but there were 4 of them.

something about kernel headers and lib06.

I installed the updates, everything worked fine after but when I did a reboot I'm not able to boot my system.

Anyone else out there who experienced the same? please post here if you have the same problem or any thoughts about it. I'm looking everywhere for a solution but can't seem to find it anywhere.

I'm running 2 identical ubuntu's on the same PC, so I'm able to edit any config files on the crashed system. 

Thanks.. Ubuntu rocks anyway n00b.001

---

### Post by Lunde on 2005-05-24
Here are the updates that I installed just before my system crashed

linux-headers-2.6.10-5 (version 2.6.10-34) will be upgraded to version 2.6.10-34.1
linux-headers-2.6.10-5-386 (version 2.6.10-34) will be upgraded to version 2.6.10-34.1
linux-image-2.6.10-5-386 (version 2.6.10-34) will be upgraded to version 2.6.10-34.1

still looking for an answere, if I'll find it, I'll post the solution here

---

### Post by salacious_crumb on 2005-05-25
I have the same problem you do.  I have checked /boot/grub/menu.lst and it seems to be ok.   What file system do you use for your root partition?  I'm using reiserfs....which I can only hope is compiled into the kernel.

---

### Post by Lunde on 2005-05-25
I'm using ext3, default from the ubuntu installer. 

I have two identical Ubuntu installations on my PC and I have compered the /boot/grub/menu.lst form both (The old one, that no longer works and from the fresh install) and there are no differences. I don't think the problem is there.

I'm a bit new to this, but I suspect it's got something to do with the kernel.

---

### Post by Lunde on 2005-05-26
OK.. I give up, copying my new system over the crashed one.. A bit scared this will happen to my fresh install fully configured to so I would like to have a fully functioning backup.

What i found searching on the net was, (and if I had the time I would go for it): 
...Boot from live CD and "chroot" to the crashed system to be able to run updates.   


DarkSilver:
------------------------------------------------------------------------
just for information:
to do a chroot from the LiveCD, you only need to do : sudo chroot /dev/hda1 /bin/bash 
--------------------------------------------------------------------------
Anyway... some more here: [http://www.ubuntuforums.org/showthread.php?t=36573](http://www.ubuntuforums.org/showthread.php?t=36573)

---


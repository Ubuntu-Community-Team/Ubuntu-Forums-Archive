---
title: "Funny GRUB behavior after replacing HD"
date: 2007-01-08
forum: General Help
---

### Post by cronholio on 2007-01-08
I've recently replaced my 80 GB IDE disk with a 400 GB SATA-II. I copied the contents of my ReiserFS root partition (previously hda1) to sda1 using dd and resized it using resize_reiserfs (to 380 GB). I removed the old drive, ran the Edgy Live CD, mounted the new root partition, chrooted into it and ran grub. root (hd0,0), setup (hd0) and off we go... time to reboot. Everything works well. The next reboot attempt, however, fails:

```
Error 18: Selected cylinder exceeds maximum supported by BIOS
```

Okay, I insert the Live CD, setup grub again, it works, I reboot again, it fails etc. etc. ad infinitum... Only the one reboot immediately after the grub setup will work. So I suspect the partition size is not really the problem here. It should be possible to boot from a 380 GB volume, right? I guess there is something happening to the grub config during boot or shutdown that confuses it, probably related to my old configuration (which is after all just cloned with dd).

Or do I really need to have a separate boot partition in this case?

---

### Post by cronholio on 2007-01-08
I just noticed that it seems to work when I connect the old HD, but it does boot off the new one. Wtf? :confused: 

By the way, I did change fstab as well.

---

### Post by harmegido on 2007-01-08
This may help: [http://ubuntuforums.org/archive/index.php/t-277374.html](http://ubuntuforums.org/archive/index.php/t-277374.html)

---

### Post by confused57 on 2007-01-08
Here's Herman's grub tutorial:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Maybe at the bootup grub menu, you could highlight the entry to boot Ubuntu, press "e" to edit, make sure root is set to (hd0,0) if it is on the 1st partition.  Then in the kernel line, you may need to change the root to something like:  root=/dev/sda1...try booting with the changes & if it works you can make it permanent in your /boot/grub/menu.lst.
In your old setup, it was probably set as hda1...you may also need to change your /etc/fstab from hda to sda.

You could always bootup the live cd, open a terminal:
```
sudo fdisk -l
```

---

### Post by az on 2007-01-08
> **cronholio said:**
> ... time to reboot. Everything works well. The next reboot attempt, however, fails:

```
Error 18: Selected cylinder exceeds maximum supported by BIOS
```

Okay, I insert the Live CD, setup grub again, it works, I reboot again, it fails etc. etc. ad infinitum... Only the one reboot immediately after the grub setup will work. So I suspect the partition size is not really the problem here. 

The problem is your BIOS, not grub.  I suspect it does not refresh itself after the first reboot, but does after the second.  It "remembers" where to look the first time, but not subsequent times.  It may be buggy or it may just be a limitation on the BIOS implementation.

Bios does not need to be able to find your whole hard disk to boot grub.  It just needs to find the second stage of grub as well as the kernel.  

> **cronholio said:**
> 
Or do I really need to have a separate boot partition in this case?

Yup.

---

### Post by cronholio on 2007-01-08
Thank you all for the replies. The thing is, I've done this a number of times already, minus the resizing thing and never on this machine, and this is the first time I ran into any problems. 

Now I was just about to start moving the partition and create a small boot partition, when I realized that my whole system becomes unstable after a while when the old HD is not plugged in (and neither will it boot, as said above). This really puzzles me. The old drive does not appear in fstab and is not mounted at all.

I noticed that grub will see my old drive as (hd0) when plugged in, so the new one becomes (hd1). The problem must be related to that:

Case 1: The old drive is not plugged in. System boots off the new one, something is missing/broken/lost/FUBAR'd.

Case 2: The old drive is plugged in. BIOS loads grub from new disk's MBR. Grub points to (hd0,0) which is the OLD drive and loads the kernel from there, but mounts the first partition of the new drive as root which in some way makes everything work.

Can you make any sense of that? :confused:

---

### Post by the.dark.lord on 2007-01-08
I got the same kind of problem. I installed Ubuntu on a HD, on a computer which has another HD running WinXP. When I remove the HD with Ubuntu, windoze doesn't log on by default, but instead grub loads up and shows 'Error 21'. Help please. 

Thanks.

---

### Post by orb9220 on 2007-01-08
The.dark.lord see my thread

[http://www.ubuntuforums.org/showthread.php?t=333238](http://www.ubuntuforums.org/showthread.php?t=333238)

---

### Post by confused57 on 2007-01-08
> **cronholio said:**
> 

I noticed that grub will see my old drive as (hd0) when plugged in, so the new one becomes (hd1). The problem must be related to that:

Case 1: The old drive is not plugged in. System boots off the new one, something is missing/broken/lost/FUBAR'd.

Case 2: The old drive is plugged in. BIOS loads grub from new disk's MBR. Grub points to (hd0,0) which is the OLD drive and loads the kernel from there, but mounts the first partition of the new drive as root which in some way makes everything work.

Can you make any sense of that? :confused:

What you might want to try is boot up with the live cd, with the IDE drive disconnected, and reinstall grub to the mbr of the SATA drive:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Then you can try booting to the SATA drive, if it doesn't boot properly, then try the "e" editing of your grub entry(as I mentioned in my previous reply) to boot Ubuntu.  If you're able to get your SATA to boot OK, then you'll need to change your bios hard drive boot order to boot the SATA drive before the IDE drive.
If none of this works, you may indeed need to create a separate boot partition, as suggested by azz.

---


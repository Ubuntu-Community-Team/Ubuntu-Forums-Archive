---
title: "mother of all problems"
date: 2007-10-12
forum: General Help
---

### Post by linux&gt;windows on 2007-10-12
Ok not really. I have a dell inspiron 4000, 800 MHz  and ive been using ubuntu for about a year and awhile ago uprading to feisty fawn. My problem is this recently i started it up and it all went fine till it said "dev/hda1 has been mounted 30 times without being checked, check forced " any way it gets to 20-21% and stops the hard drive makes a ticking noise but it still responds to key strokes so i rebooted and ran memtest with no problems. Is there a way to skip the check? Is my hard drive physically damaged? Any help is appreciated, thanks.

---

### Post by thomasaaron on 2007-10-12
Memtest checks your memory cards, not your hard drives. So that won't be much help.

Can you boot into recovery mode and run fsck? (I think it is the same thing as the computer is already trying to do, so it might not help.) 

At any rate, if it is sticking at 20% and not recovering on its own, I'd suspect a bad block or something.

---

### Post by linux&gt;windows on 2007-10-12
Yes i have tried recovery mode with the same results unfortunately:(

---

### Post by Lord Illidan on 2007-10-12
> **linux>windows said:**
> Ok not really. I have a dell inspiron 4000, 800 MHz  and ive been using ubuntu for about a year and awhile ago uprading to feisty fawn. My problem is this recently i started it up and it all went fine till it said "dev/hda1 has been mounted 30 times without being checked, check forced " any way it gets to 20-21% and stops the hard drive makes a ticking noise but it still responds to key strokes so i rebooted and ran memtest with no problems. Is there a way to skip the check? Is my hard drive physically damaged? Any help is appreciated, thanks.

It could be a sign of physical damage.

---

### Post by linux&gt;windows on 2007-10-12
Thats what i was thinking unfortunately
Is there a way to skip the check on bootup ?

---

### Post by waawaawee on 2007-10-12
shutdown -f for skipping fsck

---

### Post by DagMan on 2007-10-12
to disable future checking, from the live cd with the partitions **not** mounted, do this for each partition as root or sudo
```
tune2fs -c 0 -i 0 /dev/hdXY
```
where X and Y are drive number and partition number.  Change h to s if your disk comes up as sda instead of hda
so if you had 4 partitions, 2 primary and 2 on an extended, it might look like this
```
tune2fs -c 0 -i 0 /dev/sda1
tune2fs -c 0 -i 0 /dev/sda2
tune2fs -c 0 -i 0 /dev/sda5
tune2fs -c 0 -i 0 /dev/sda6
```
you don't need to do swap though it won't hurt it, nor will it hurt it.  Just don't have anything mounted.
You can also run checks from the live cd on unmounted partitions.
Here's my quick resource for this sort of thing btw [http://forums.gentoo.org/viewtopic-t-305871.html](http://forums.gentoo.org/viewtopic-t-305871.html)

---

### Post by Frak on 2007-10-12
Has your system recently crashed?

Ext3 FS doesn't conduct redundancy checks, therefore there is a chance that Ext3 called a "False Winner" and called a "bad block".

A patch is in the works for Ext3 on this problem.

---

### Post by jespdj on 2007-10-12
If a harddisk starts making strange noises like ticking, then that's a bad sign. It most likely means that the disk is dying. So make sure you backup any important data before it stops working! :(

---

### Post by linux&gt;windows on 2007-10-12
thanks ill try all that this weekend and report next week thanks

---

### Post by skipbarker on 2007-10-12
Save all your important stuff. Ticking from a hard drive is a bad sign.

---

### Post by HelixAgent on 2007-10-12
I had that problem and it was because I had a physical damage on my Hard Drive, maybe, according to your system it must be at least 4 years old so maybe your Hard Drive is a little bit damaged.

---


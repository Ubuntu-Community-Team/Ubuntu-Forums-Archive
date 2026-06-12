---
title: "Resize NTFS partition. (Picture included)."
date: 2007-01-12
forum: General Help
---

### Post by Seine on 2007-01-12
I would like to resize my NTFS partition to take advantage of some extra space there. See this screenshot from gparted for my situation.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=22798&stc=1&d=1168588428[/IMG]

If I try to unmount in gparted I'm told that the partition is in use and can't be unmounted. If I umount /dev/sda1 its successful, but (after refreshing gparted) resize is not an option!

Is there a way for me to resize this partition without destroying it?

Thank you
Seine

---

### Post by tito2502 on 2007-01-12
Its best to partition from a bootable CD.

---

### Post by Seine on 2007-01-12
I have the live CD to hand. Do you think my task will be possible if I boot into that?

---

### Post by logos34 on 2007-01-12
So, you did 
> sudo umount /dev/sda1

and it still won't let you resize?  Try closing gnome partition editor and reopening it after you umount sda1.  If that doesn't work use gparted on the ubuntu install livecd.

---

### Post by Seine on 2007-01-12
Yes, that's right. I still couldn't resize.

Now I'm running from the live CD and can resize. But I can't move sda2 leftwards to consume the freed up space. Is this something I wont be able to do without making an image of sda2?

---

### Post by logos34 on 2007-01-12
Try it in two steps...Shrink it/move sliders, then complete the operation.  Then come back (reboot if necessary) and expand sda2 into the unallocated space.  

Or download Gparted livecd.  It bills itself as 'industrial strength'...

---

### Post by Seine on 2007-01-12
sda1 is shrunk, but cannot expand sda2 'leftwards'. I'm happy to try gparted live cd. Unless someone confirms that what I want to do can't be done?

---

### Post by konst88 on 2007-01-12
I didnt use gparted, but i remember in partition magic you have first to move the partition to the left, which is a little long operation, after it the unallocated space will be on the right side, and then resize it to the right.

---

### Post by Seine on 2007-01-12
Other threads suggest the Ubuntu live CD version of gparted does not allow resizing at the start of partitions. I'm going to try the newest GParted LiveCD and report back.

---

### Post by Jongi on 2007-01-12
I've found that when it comes to NTFS resizing, using an XP based program is easiest.

---

### Post by Seine on 2007-01-13
The GParted live cd worked wonderfully. All is well again.

Thanks all.

---


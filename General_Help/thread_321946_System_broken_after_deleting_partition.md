---
title: "System broken after deleting partition"
date: 2006-12-19
forum: General Help
---

### Post by Steven_B on 2006-12-19
I had several partitions, two of which (hda6 and hda7) had copies of Ubuntu.  hda5 was a small empty partition left over from some previous re-arranging.  I booted a live CD and deleted hda5.  When I rebooted, the partitions were re-numbered, so partitions 6 and 7 are now 5 and 6.  When booting, it looks on hda6, runs the wrong copy of grub (which I thought only references hda7), but then boots from hda5.  I am able to log in, but the mouse doesn't work, and my splash screen and background don't appear (I think this is because they are on another partition).
When I try to mount hda3 or hda5, it gives me this error:
/dev/hda3(or 5) has wrong device number or fs type ext2 not supported
I attempted booting the live CD into recovery mode, but it gave me a kernel panic.
Any ideas?

---

### Post by bodhi.zazen on 2006-12-19
> **Steven_B said:**
> I had several partitions, two of which (hda6 and hda7) had copies of Ubuntu.  hda5 was a small empty partition left over from some previous re-arranging.  I booted a live CD and deleted hda5.  When I rebooted, the partitions were re-numbered, so partitions 6 and 7 are now 5 and 6.  When booting, it looks on hda6, runs the wrong copy of grub (which I thought only references hda7), but then boots from hda5.  I am able to log in, but the mouse doesn't work, and my splash screen and background don't appear (I think this is because they are on another partition).
When I try to mount hda3 or hda5, it gives me this error:
/dev/hda3(or 5) has wrong device number or fs type ext2 not supported
I attempted booting the live CD into recovery mode, but it gave me a kernel panic.
Any ideas?

LOL

boot to the live CD (almost any live CD will do).

sudo fdisk -l

to list your partitions

mount and edit your ubuntu root partitions, edit and update /boot/grub/menu.lst and /etc/fstab in each partition :p

---

### Post by Steven_B on 2006-12-19
That did the trick.  Thanks!
I'm assuming this problem is the point of the UUID thing in edgy?

---

### Post by Azakus on 2006-12-19
Yep. With UUID, each partition has a unique serial number so it will (nearly) always boot correctly (except, of course, if you delete the partition that has Edgy's root directory).

---


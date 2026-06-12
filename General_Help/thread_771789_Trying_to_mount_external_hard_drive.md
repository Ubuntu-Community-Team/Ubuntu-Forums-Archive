---
title: "Trying to mount external hard drive"
date: 2008-04-27
forum: General Help
---

### Post by AdrianStrays on 2008-04-27
So let me back up first.  Our old windows machine broke down (old age) and I gutted it, and turned its hard drive into an external hard drive.  Deleted most of the contents, except for the windows system, which it wouldn't let me delete (I was on a vista machine while doing this)

No big deal, flipped it off, plugged it into my Ubuntu Studio machine.  Can't mount it, need to force mount.  Fine, entered the following:

sudo mount -t ntfs-3g /dev/sdb1 /media/disk -o force 

Directory doesn't exist, I try this

sudo mount -t ntfs-3g /dev/sdb1 /media/windows -o force 

Drive mounts, contents empty.  That can't be right, as a large portion of it is unuse.  Flip it off, yet it still remains on the computer.  Weird.  Flip it back on, now "another" external drive appears.

How do I mount it properly, and remove the "ghost" external hard drive?

---

### Post by ryanhaigh on 2008-04-27
The problem is likely that you didn't unmount the drive before removing it. You may be able to 'unmount' now by doing ```
sudo umount /media/windows
```.

The journal on the device might not be clean which is probably why you had to force mount in the first place and may be why the windows install isn't showing up. Repair the partition in windows first.

---


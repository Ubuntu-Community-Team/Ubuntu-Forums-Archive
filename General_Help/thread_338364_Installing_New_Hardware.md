---
title: "Installing New Hardware"
date: 2007-01-14
forum: General Help
---

### Post by wireddad on 2007-01-14
I installed a new HD.  Ubuntu/linux did not recognize the new HD automatically.  Reloaded the OS and all fine.  What would have been a better way to get Ubuntu/linux to recognize the new HD instead of reloading.

The HD was formatted as FAT32. 

For that matter, what to do after installing new hardware.

---

### Post by crispy_420 on 2007-01-15
Assuming you have an already formatted hard drive. You'll want to mount it some where.

So you'll need to have a directory to mount to (eg. /home/music).

Then you'll tweak your fstab file to mount on boot.

You can always test by issuing the mount command. (mount /dev/hdb1 /home/music) *this is just an example*

Just search for some guides for a more detailed guide. This is just a simple howto to get you started in the right direction.

Good Luck!

---

### Post by wireddad on 2007-01-15
I am ok for now since I'd re-installed Kubuntu.  So there is really nothing in the OS as far as recognizing and automounting like it did the existing HD?  Or is there a command I can run to force linux to rescan for new hardware?

---


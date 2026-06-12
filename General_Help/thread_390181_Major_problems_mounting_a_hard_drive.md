---
title: "Major problems mounting a hard drive"
date: 2007-03-21
forum: General Help
---

### Post by Kazol on 2007-03-21
I have installed Ubuntu, and I can't even open the second hd, with an error message saying it cannot be mounted. I tried alternate commands, but it keeps saying the hd is in use and cannot be mounted\unmounted. The hd does contain another copy of Ubuntu (that I want to erase and setup RAID on), but is definitely not in use.

I tried putting the hd on the other channel, same problem. I also tried other hds, but they weren't even recognized! What do I do?

---

### Post by CocoAUS on 2007-03-21
What does gparted say when you tell it to look at/mount/unmout the disk?  You can probably boot from the live cd and erase the disk from there, since you said you wanted to erase it anyway.  Perhaps the problem has to do with the BIOS seeing it as a second OS?

Also, have you tried setting up your fstab to mount the drive on bootup?  You might try that.

---

### Post by Kazol on 2007-03-23
I tried booting the Ubuntu live CD, but I couldn't mount any hd.
When I tried to manually mount it, it gave an error message that it could not execute pmount.

---


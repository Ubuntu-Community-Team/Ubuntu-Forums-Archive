---
title: "Grub Error 22"
date: 2007-07-09
forum: General Help
---

### Post by MarshyTheKid on 2007-07-09
Yes, I know this has been posted many times. I've searched and have not found a solution for me.

First off. I'm dual booting with XP and Ubuntu. Yesterday I installed a new floppy drive and tried to mount it(With a floppy in it) in Ubuntu and it would not mount. I shut down to take a look at the connections and make sure it was tight. I tried to restart and had it go straight to XP, so I shut down again and I found that two of my three drives(NOT my OS' drive) came unplugged, so I plugged those back in and it still didn't work, no GRUB or anything. Those two drives are IDE and my drive where I have my XP and Linux partitions are on an SATA. I booted off of a live CD next and fixed my grub file. It still wouldn't work so I used Super Grub Disk ( [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) ) and fixed it. Now my grub comes up. I can boot to XP still which is (hd2,0). Ubuntu is set to (hd2,4) and will not work, nor (hd2,0-9)

I have been searching for a while, both on here and google, and have found little information that pertains to my problem. I appreciate any help. Thanks!



Edit: Sorry, I'm running Fiesty, doubt that helps in the least.

---

### Post by fredj on 2007-07-09
Maybe by reconnecting the drives that had become disconnected you have changed the order of the
partitions. Try disconnecting them again temporarily and see if you can boot in ubuntu again.

---

### Post by MarshyTheKid on 2007-07-09
That shouldn't change anything since I can boot into XP fine, which is on the same hard drive, but I'll try that.

---

### Post by MarshyTheKid on 2007-07-09
Well.. Hmm. It worked. I unplugged the other 2 hard drives and it booted up under (hd0,2) I think...

I guess the rest of the night will be me playing around, trying to figure out which is for what OS

---


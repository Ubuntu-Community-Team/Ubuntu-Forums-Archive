---
title: "system won't install."
date: 2006-09-29
forum: General Help
---

### Post by pentium on 2006-09-29
Recently I moved a WD 4 gig drive with ubuntu 6.06 to a more faster system and because i didn't know if ubuntu would reconfugure, i erased the drive. This meant I removed the partition holding ubuntu so that all that was left was the partitions that live made (locked). I then created a new partition which I could reinstall on and restarted the system.
The next time in I began to install. Everything went fine until i reached 99% and the system locked solid. I tried installing over and over again only to have it lock in the 90% range. I can rule out hardware problems due to I tried an install with the system gutted and all bios options disabled and it still locked.
On my last lockup, i restarted the system and removed the cd. Grub began to run and gave no error 22. it then loaded ubuntu and I thought everything was fine until i noticed that it was runnung off the partitions the live disc was suppost to remove. It makes no sense. is that partition giving me the problem?

---

### Post by pentium on 2006-09-29
okay, Just in case it was pissing the system off, I replaced the ribbon cable for the cd drives from 80 conductor to the older gray ribbon cable (40 conductor)
I also noticed that during install the following has to happen:
-partition 1 will be formatted and partitioned
-partition 5 will be formatted and partitioned

if /dev/hda5 stands for partition 5, then the system will be formatting the linux-swap from the live cd. would this explain the lockup? Because the swap was formatted, it can't find the rest of the data?

NOTE: currently the drive I am installing to has:
-3.62 gigs of allocated space
-400.06 mb extended partition (shows lock and is /dev/hda2)
   -196.05 mb allocated to linux-swap (locked and is /dev/hda6)
   -203.92 mb allocated to linux-swap (locked and is /dev/hda5)

I'm thinking that if i make the slave hard drive i have installed master (and vice versa for master), I can visually ensure that all partitions are removed and then just switch the drives back and try again. will that work?

---

### Post by pentium on 2006-09-30
nope, If I change the master to a slave, the live cd completely ignores the master (clean drive) and uses the slave! (has the partitions I want to remove!)
Is ubuntu stupid or something?!:mad:

---

### Post by morphodone on 2006-09-30
You might consider using the 'alternate' install cd.

[http://ubuntu-releases.cs.umn.edu//6.06/](http://ubuntu-releases.cs.umn.edu//6.06/)

Then just let ubuntu take over the entire drive if you have
nothing to lose.

---

### Post by pentium on 2006-09-30
I'll give it a try. Don't expect a reply tonight though.

---

### Post by pentium on 2006-09-30
yep, this will do exactly what I want....
Now If i can figure out how to make a non-corrupt cd!
I first used a cd-r and burned the cd with dvd decryptor. the result was a corrupt cd that won't work. I then tried a cd-rw and the result was that i discovered that the dvd drive can't read cd-rw's:(  I really ned help. i'm starting to think that linux is WORSE than windows when it comes to reliability.:mrgreen: :mrgreen: :mrgreen:

---

### Post by morphodone on 2006-09-30
Maybe your cdrom drive is going bad???

---

### Post by pentium on 2006-09-30
impossible, i have tried two drives.
am missing some setttings?

---

### Post by pentium on 2006-09-30
**THREAD CLOSED**
I got the booting problem fixed. A new thread has been created for another problem though involving the .iso ubuntu discs.

---


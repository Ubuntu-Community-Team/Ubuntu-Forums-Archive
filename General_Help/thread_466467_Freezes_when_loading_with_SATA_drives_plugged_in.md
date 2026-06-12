---
title: "Freezes when loading with SATA drives plugged in"
date: 2007-06-06
forum: General Help
---

### Post by Tyrun on 2007-06-06
Hey all, I've been toying with Ubuntu for a couple months, but have gotten serious about trying to make the transition to linux for good in the last couple of weeks.

I've had a couple of problems - and have been able to muddle through most of it (as I am fairly new to linux). 

However, after getting it to dualboot successfully, I've had a problem when I try to boot the machine with either of my two SATA drives plugged in.

Here's the breakdown:

P4, HT 3.00GHZ
1.5 GB RAM
Master 80gb PATA IDE drive (XP is loaded onto this)
Slave 160gb PATA IDE drive (Ubuntu is loaded onto this)

The two SATA drives are a 300gb and a 400gb. I installed ubuntu without them installed because out of fear of data corruption (Long story). After getting ubuntu up and running (and rebooting a couple times, so I know it was stable) I plugged in the SATA drives this morning, and it just hangs on the loading ubuntu screen at about the 2nd or 3rd bar.  

Is there any way to resolve this issue? Any help would be greatly appreciated!

---

### Post by exploder on 2007-06-06
You updated your kernel and it has issues with the Intel chipset. Boot your PC and at the prompt that says to hit esc for options press esc scroll to the original kernel and proceed.

---

### Post by screaminj3sus on 2007-06-06
Yes if you have upgraded to the latest kernel this will happen, you have pretty much the same hardware as me, I hd the same problem, you will have to use the old kernel until this is sorted out (I don't know Ubuntu let something like this through, TONS of people having problems)

---

### Post by Tyrun on 2007-06-06
I'm gonna try that, hopefully it'll work.

How long do you think it'll be before they release a kernel that works?

---


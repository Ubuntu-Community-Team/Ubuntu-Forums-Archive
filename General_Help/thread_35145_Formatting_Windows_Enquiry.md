---
title: "Formatting Windows Enquiry"
date: 2005-05-17
forum: General Help
---

### Post by AMCDeathKnight on 2005-05-17
I have 2 hard drives, a 10 gig and a 20 gig, Ubuntu is installed on the 10 gig and Windows Xp Pro, on the 20 gig, I use Grub bootup menu to boot into Ubuntu when startup so,and I believe grub is installed on the windows machine, as it is the Master and the ubuntu drive is set as slave. I need to format windows as it is really cluttered up. How can I do this, without bugging up Ubuntu, and the windows drive?
As I want grub back when it is formatted and ready.

How may I do this the easiest and yet the safest?

---

### Post by dave9191 on 2005-05-17
Formatting the windows driver should not make any changes to the MBR. But if you reinstall windows it will overwrite the MBR with its own boot info and you would have to reinstall grub. Best instruction I found for that are in the Gentoo installation handbook. Be sure to have a knoppix cd or some other live cd for you to boot into a linux OS to install grub again. Your grub config files are not stored on the MBR, they are stored on the boot partion, so you will also need to know which one that is for the grub install. 

Dave

---


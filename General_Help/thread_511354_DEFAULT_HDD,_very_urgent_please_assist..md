---
title: "DEFAULT HDD, very urgent please assist."
date: 2007-07-27
forum: General Help
---

### Post by Aesir09 on 2007-07-27
[B]OK, please help, today i was going to install Ubuntu, then decided not to, and i already made a partition using partition magic, by norton and once i made the 25gb partition, i said restart my computer i will install the operating system right away.,



so once i did this it restarted my computer and did the partitoning in a blueish screen.

this is when i said ok



once it was done i realized that i didnt want to and ill just return the memory later, but everytime i turned on my computer it would say cant load operating system.

that is becuase it thinks my new partition is my main hardrive!

so i used the cmd.exe thing from my disc and i ended up deleting the partition but the memory(25gb) was not returned to my regular HARDDRIVE

I NEED TO USE CMD.exe or in the BIOS or SOMEHTING!

SO THAT I CAN RETURN THE UNSPECIFIED MEMORY TO MY C DRIVE AND BOOT WINDOWS

HOW DO I TELL MY COMPUTER BOOT TO HERE.....? I WANT THE DEFAULT HDD TO BE THE ONE WITH WINDOWS INSTALLED!!!!!!!![/B]

---

### Post by ayoli on 2007-07-27
first, we all here can understand your distress but try to not use so much caps and bold text.
you may try to boot on a ubuntu (or any another dist) live CD then try to save your most important data (you should have done this before a sensible op like repartioning your hd).
then do a fresh install (windows before with saving space for a future linux part if needed).

---

### Post by Aesir09 on 2007-07-27
umm but yeah, this cant be to hard, all i need to do is tell my computer, boot at this part of the c drive....

ugh!

---

### Post by strabes on 2007-07-27
You can use a program like gparted to set the boot flag for that partition.

---

### Post by Fallen_62 on 2007-07-27
[http://ubuntuforums.org/showthread.php?t=511377](http://ubuntuforums.org/showthread.php?t=511377)

Read my reply there and see if that helps.  (Posting this in two places so you dont miss it)

---

### Post by russo.mic on 2007-07-28
Look, just boot up to a window xp cd, when it's done loading 40 different drivers which have NOTHING to do with installing an operating system, press R for recovery console, select your windows installation (probably the only one listed), and type

fixboot

hit enter,

fixmbr

Done and done.

Backup  backup backup!!!

Good luck,

Russo

---


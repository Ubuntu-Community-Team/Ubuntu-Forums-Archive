---
title: "Lubuntu is freezing causing a reboot, how can I see what's wrong?"
date: 2022-10-26
forum: General Help
---

### Post by homebrewdude on 2022-10-26
This is an older Intel NUC machine, basically headless.  But I do remote in.

Seems like everyday I cannot remote in, inforce a hard reboot and it's fine.

I dunno if hardware is failing?  Ubuntu issue?

Are there log files or anything I could be looking at?

---

### Post by Autodave on 2022-10-26
Generally, when I see a problem like that, it is memory failing.  Try running a RAM test and see what it tells you.

---

### Post by homebrewdude on 2022-10-27
With today's freeze, I noticed a bunch of I/O Error sda1 sector....

sda1 is the SSD drive.

I pulled the drive, checked in with CrystalDiskinfo and it shows no errors or problems.

Cleaned the NUC on the inside and re-seated the memory and SSD card.
Lets see what happens now.

I am thinking I need to order a new SSD...

---


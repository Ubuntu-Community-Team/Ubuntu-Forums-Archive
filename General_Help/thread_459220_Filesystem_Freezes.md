---
title: "Filesystem Freezes"
date: 2007-05-30
forum: General Help
---

### Post by SuperNatendo on 2007-05-30
Hi Everyone, I hope no one else has had this problem yet because I did search the forum and if this is addressed elsewhere I apologize.  

I am dual Booting Ubuntu and Windows xp on a dell optiplex gx260 with a 64mb ati rv200 qw [radeon 9500] AGP card.  1.5 GB Ram, 2.4 GHZ Pentium 4 Processor.

My problem is this, it seems everytime I try to access the filesystem, home folder, or mount an extenal hard drive my workstation freezes, I can't access the home folder or filesystem and I can't click on anything on the desktop or right- click or drag and drop on the desktop.  However, everything else still works properly!  I can run programs from the panel and everything.  I even downloaded the thunar file manager and that works fine!  I've noticed this problem since I ever tried using the desktop effects with the workstations on a cube option turned on, which I have since disabled all of those effects now, but am still having problems.

If anyone can tell me whats going on with my machine I'd really appreciate it!

---

### Post by MoLE on 2007-06-07
Sounds like you're describing a nautilus problem.  It might be worth restarting the xserver (Ctrl-Alt-Backspace) and relogin to see if the problem continues to happen.  

If so, filing a bug under nautilus for feisty in launchpad may get you somewhere.

---


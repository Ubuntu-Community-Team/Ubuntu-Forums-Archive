---
title: "Gutsy takes ages to load (way longer than Feisty or XP)"
date: 2007-10-18
forum: General Help
---

### Post by styxie on 2007-10-18
Hi, I've been using Feisty for a few months, and today I wanted to upgrade to Gutsy. However, the upgrade crapped out and my screen went black. Well, no worries, as I'm using Gutsy as a 'fun' OS, I loaded Windows, downloaded the Gutsy CD, and did a fresh install.

But now there's no Ubuntu loading screen (with the orange bar during the loading) and it takes Gutsy ages to load to GDM, much longer than Feisty. Can somebody help me please?

---

### Post by alextwo on 2007-10-18
Yep I'm having the same problems here. Any one esle?

---

### Post by Spenzer4Hire on 2007-10-18
Same issues here.  Blank loading screen and probably 4 or 5 times the loading time of Fiesty.  I followed instructions to fix the blank loading screen (has to do with an improperly set resolution).  It fixed the shutdown progress screen but not the startup one.

---

### Post by Whiffle on 2007-10-18
Try hitting "ctrl +alt +F1" while its booting.  It may show you some error messages.

On mine it did something similar, I had to add a command to the kernel loading line in grub and now it boots fine.

---

### Post by chrisccoulson on 2007-10-18
Also try installing bootchart, and post the bootchart images here (which can be found in /var/log/bootchart)

---


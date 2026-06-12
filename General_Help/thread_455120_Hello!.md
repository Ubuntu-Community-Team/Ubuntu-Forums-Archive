---
title: "Hello!"
date: 2007-05-26
forum: General Help
---

### Post by uranous on 2007-05-26
Hey, i am new to linux and I think I've done something stupid :p I was installing a program and i thought that it ''was stuck'' so I clicked on close during the installation, but it seems like the package installer never really closed, even though I restarted my pc twice, when I try to install again the following msg shows up: '' Only one software management tool is allowed to run at the same time.'' I tried to find the process in the system - administration - system monitor - processes but i couldn't find which it is and if this is the right way :) So, any ideas???
Thnx!

---

### Post by meng on 2007-05-26
Try opening a terminal and typing
sudo dpkg --configure -a
(you'll be asked to enter your USER password - make sure you type it and press Enter - the password will NOT echo to screen)
after this, try running package manager again.

Next time be sure to choose a more informative TITLE for your post.

---

### Post by uranous on 2007-05-26
Thnx for your FAST reply ;) and it worked :) 

> **meng said:**
> Next time be sure to choose a more informative TITLE for your post.
Yes, I'll try that next time!

---


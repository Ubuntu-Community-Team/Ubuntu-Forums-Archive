---
title: "Ubuntu 14.04 Not Booting From USB or DVD"
date: 2014-12-05
forum: General Help
---

### Post by Tyler_MacPherson on 2014-12-05
I've tried installing Ubuntu 14.04 from both a USB flash drive and a DVD, and no matter what it refuses to boot. I get to the boot menu for the Live DVD, where I can choose to Try Ubuntu Without Installing or Install Ubuntu. No matter what option I choose, it always freezes at exactly the same spot: "random: nonblocking pool is initialized". I've tried downloading the ISO several different times, and also verified the md5sum each time. I figured maybe it was just booting slowly, so I left the installation running overnight, and this morning it is still stuck at that same message. Any ideas on how to fix this? 

Thanks!

EDIT: I managed to get it to work! I hit F6 at the menu, and chose the "nomodeset" option. This installation then continued as normal.

---

### Post by mörgæs on 2014-12-05
Hi, welcome to the fora.
Please begin with a complete hardware description.

---

### Post by ajgreeny on 2014-12-05
Do you have an nvidia graphic card; that is the most usual cause of your problem.

Either way, well done!  I'm glad you found a solution.  Now please mark the thread as SOLVED from the **Thread Tools** menu at the top.

---


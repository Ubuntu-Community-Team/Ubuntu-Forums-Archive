---
title: "Wubi stuck in non-stop restart cycle solution  [HOWTO] [SOLVED]"
date: 2007-06-10
forum: General Help
---

### Post by kevinmedina on 2007-06-10
Hi,

I've posted a problem regarding a boot-up problem after a hard restart and wanted to share the solution.  Using  Wubi to install Ubuntu, the installation and boot-up process worked flawlessly until I gave my computer a hard reset.  My machine (Dell XPS M140 Laptop/Windows XP SP2) would then restart endlessly, never even reaching the boot menu.  I then booted my system using the Ubuntu live CD and, using gparted, found out that bad sectors existed on my NTFS partition.  To fix this I tried using a XP re-installation CD provided by Dell, but the boot would give me an error, not allowing me to access the recovery console.  Afterward I tried NTFS4DOS, which picked up my NTFS partition but did not allow me to run the chkdsk or scandisk command on the partition.  After mulling over the problem for another few hours I came across an ***original*** XP installation CD and decided to give it a shot.  It worked, allowing me to run the recovery console and, after running ***chkdsk /p /r*** my system booted right into the original boot sequence, with both Ubuntu and XP running seemlessly as they did before the hard reset.  

The solution is simple and has been suggested at various times, but I thought I would just share it since so many people like myself have run into similar troubles.  I hope I've helped :p

Thanks to Ago for helping me earlier.

---

### Post by ecology2007 on 2007-06-10
Thanks for sharing your solution.

---

### Post by Kemp on 2007-06-12
Awesome, I have exactly that problem from exactly that cause. Going to try your suggested solution and report back :D

---


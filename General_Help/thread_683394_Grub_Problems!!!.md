---
title: "Grub Problems!!!"
date: 2008-01-30
forum: General Help
---

### Post by Rdaneelolivaw on 2008-01-30
So i've searched the forum and found similar but not what my problem is questions/answers.  Basically everyone said get linux it's so much better than windows so i created a partition of my HD and installed ubuntu and then deleted that and installed kubuntu because of a wireless card problem.  Eventually i wiped off kubuntu (just deleted the partition) but so far no grub problems (i only tried loading windows) but i figured i'm not using that partition, so i re-expanded the shrunken windows partition and now when i load up my computer it says Grub loading...   Grub error 17 and then it just stays there and i can't do anything.  I've tried re-installing windows but it keeps freezing on me so anyone know what to do to uninstall/disable grub so i can load windows in peace and maybe eventually go back to linux once i've calmed down?

If this question has been answered can someone post the link to that forum topic, i didn't find one when searching the forum

---

### Post by Raccoon1400 on 2008-01-30
Boot from the installation CD and enter the recovery console, assuming your using xp, if you can get this far. The command "fixmbr" will rewrite the windows mbr.

---

### Post by Rdaneelolivaw on 2008-01-31
i use vista (it's a relatively new computer).  Is it the same thing with vista  or how different is it?

---


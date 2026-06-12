---
title: "Thunar crashes on cut-and-paste"
date: 2016-08-04
forum: General Help
---

### Post by MJae on 2016-08-04
Help!

As the title says, Thunar crashes on my system on cut-and-paste. This wasn't happening until I got to 16.04.

I don't really know what causes it. I've tried observing and, at first, I thought it happened when I cut-and-paste large files, but it also happens even if the files are smaller. Next, I tried checking if it was between drives, but it happens even if the transfer is only between partitions, even if the transfer was in the same drive and the same partition.

Please, what can I do?

I've been updating hoping it'll be fixed in the next one but it's still happening.

---

### Post by yoshii on 2016-08-04
This sounds very much related to the v16.04 issue with partial crashes during file renaming.  The files get renamed but the window displaying them crashes.  
What I ended up doing was using PCman File Manager instead of Thunar except for certain operations.  They both coexists peacefully together.  You can install PCman File Manager from Synaptic or Apt-Get.  It's what Lubuntu uses for it's file manager.  After it's installed you can use it anytime from a desktop shortcut or panel shortcut or if you want to use it as the default file manager, you set that in Preferred Programs from the (XFCE) Settings Manager.  

I actually kind of like PCmanFM slightly better for certain things.  It doesn't have custom folder emblems, but that's about the only drawback.  It has it's own preferences to be set also.  

Anyways, I recommend using that until the developers fix the bugs in 16.04.1 or .2

Maybe you should submit an official bug report.  I forget how that's done, but it's not via regular forum posts here.

---

### Post by MJae on 2016-08-11
PCManFM it is. To be honest, it was one of the things I didn't like about Lubuntu when I tried it out. Guess I have to work with it. For now. I still like Thunar better so I'll keep waiting for it.

I tried Nautilus, too. I used to like it. Now it's very different I didn't know what to do with it...

Thanks for the tip. I'll try and find the bug tool for Xubuntu so I can get this issue reported.

---


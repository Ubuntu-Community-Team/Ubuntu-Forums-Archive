---
title: "Thunar does not show my other internal partitions on the sidepanel"
date: 2008-05-14
forum: General Help
---

### Post by deformation on 2008-05-14
hello all

 I am having a small annoying problem, my windows partition and other internal partitions does not show in the side panel of thunar or in the panel places, it used to show there automatically in gutsy, but now whenever i want to access them i have to go to /media, anyone knows why and how to fix this?

thanks in advance

---

### Post by morgengenuss on 2008-05-14
well actually the solution is quite simple: you drag the folder you'd like to have (e.g. /media/sda3) to the sidepane and drop it there. that's it.

the point is that thunar's behavior concerning internal partitions changed from gutsy to hardy (from version 0.8 to 0.9) and a few users have complained about it, but i would say that this is really nothing to worry about.

---

### Post by deformation on 2008-05-14
Thanks for the reply, but its not GTK bookmarking that i want, i want the partitions to be listed among other external partitions, where i can right click and mount or unmount.

---

### Post by LavosPhoenix on 2008-06-16
This is exactly what I've been trying to find the answer to since Hardy came out. Yes, I realized you changed the behavior of Thunar, however, a link to a folder is still not an actual representation of a drive, which was shown in Gutsy. This is the functionality that more than just a few users want back, and has been stated, to be able to easily mount and unmount drives, especially removable drives.

Think about it. The upper half of the side pane is for special locations, the home directory, the desktop, the trash can, and the root. Why shouldn't this include MOUNTED FILESYSTEMS? The lower half is for shortcuts to directories located in those mounted filesystems, and shouldn't be for the link to the root of the filesystem itself.

Seriously, people want a fix. This is starting to be the beginnings of a pidgen-esque fiasco.

---


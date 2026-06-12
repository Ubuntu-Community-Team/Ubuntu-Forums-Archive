---
title: "Extra Hard Drives not automatically mounting?"
date: 2008-07-09
forum: General Help
---

### Post by MrMatt on 2008-07-09
Okay, running Ubuntu 8.04.1

I have edited the fstab file using:

  gksudo gedit /etc/fstab

however, when I boot, they do not appear on desktop, and I have to go to removable media and access them manually before they appear on the desktop (among other things this means that Rhythmbox needs to re-add my music every time I restart)

so far the fstab file reads as this (meaning what I added to it):

/dev/sda    	/media/System   ntfs    defaults   	0        2
/dev/sdb    	/media/Games  	ntfs    defaults   	0        2
/dev/sdc    	/media/Storage  ntfs    defaults   	0        2

any help appreciated, thanks for reading :)

---

### Post by iaculallad on 2008-07-09
> **MrMatt said:**
> Okay, running Ubuntu 8.04.1

I have edited the fstab file using:

  gksudo gedit /etc/fstab

however, when I boot, they do not appear on desktop, and I have to go to removable media and access them manually before they appear on the desktop (among other things this means that Rhythmbox needs to re-add my music every time I restart)

so far the fstab file reads as this (meaning what I added to it):

/dev/sda    	/media/System   ntfs    defaults   	0        2
/dev/sdb    	/media/Games  	ntfs    defaults   	0        2
/dev/sdc    	/media/Storage  ntfs    defaults   	0        2

any help appreciated, thanks for reading :)

The fstab file may not be your problem, it's your Nautilus settings. If you want your mounted drives to be displayed on Desktop, try following the procedures below:

Press Alt+F2, input "**gconf-editor**" (w/o double quotes) and press enter. Navigate to Apps->Nautilus->Desktop. On the right-pane window, place a check mark for the value "volumes_visible".

---

### Post by MrMatt on 2008-07-09
> **iaculallad said:**
> The fstab file may not be your problem, it's your Nautilus settings. If you want your mounted drives to be displayed on Desktop, try following the procedures below:

Press Alt+F2, input "**gconf-editor**" (w/o double quotes) and press enter. Navigate to Apps->Nautilus->Desktop. On the right-pane window, place a check mark for the value "volumes_visible".

I looked, and it was already checked.

Although a thought did occur to me, the hard drive the Ubuntu partition is on, (250gb Sata2 drive) already has 2 other partitions, and perhaps i need to add numbers to the drives i stated earlier?

as in:

/dev/sda1 /media/System ntfs defaults 0 2
/dev/sdb1 /media/Games ntfs defaults 0 2
/dev/sdc1 /media/Storage ntfs defaults 0 2

opinions? comments?

---


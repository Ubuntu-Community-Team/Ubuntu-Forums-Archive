---
title: "ATI driver headaches"
date: 2006-11-10
forum: General Help
---

### Post by Crazylikeafox on 2006-11-10
whenever i try to install the linux ati drivers from there site [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)
it will give me this thing saying 

"gedit has not been able to detect the character encoding, please check that your are not trying to open a binary file. select a chartcter enconding from the menu and try again"

then i select all 2 encondings and neither works, help! its really tough on the eyes at 60hz ;)

---

### Post by Crazylikeafox on 2006-11-10
anybidy? im using the newest version of ubuntu

---

### Post by igknighted on 2006-11-10
first of all, you are getting that error because you are probably just clicking the file you downloaded, and Ubuntu wants to open it with gedit (a text editor).  To install this file you need to right click and select properties.  Check the box that says 'make executable'.  Then open a terminal window and cd to the directory the file is in (if it is in your home folder you are already there, and if it is on your desktop you can use 'cd Desktop').  From there type ./(filename).

Having said all this, I strongly recomend NOT using the driver you downloaded.  The Ubuntu repositories have this driver available already.  Open Synaptic Package Manager from the System->Administration menu and search for 'fglrx'.  Mark this package for install, click apply, and once it is done you may need to open a terminal window and type 'aticonfig --initial', it will tell you if you do.  When all that is done, reboot your computer and the drivers should work.  If you run into any trouble there are many, many threads on getting the ATI drivers working, just search the forum.

PS: Search the forum before you post, there are millions of ATI driver how to's out there... and don't bump your thread unless it has been around 24hrs without a response... just some general forum advice

---


---
title: "desktop effects"
date: 2008-07-03
forum: General Help
---

### Post by omlx2 on 2008-07-03
i was trying to make the desktop effect works in ubuntu 08.4

and i got this msg form synptic package manager





desktop-effects:

Package desktop-effects has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

---

### Post by overdrank on 2008-07-03
> **omlx2 said:**
> i was trying to make the desktop effect works in ubuntu 08.4

and i got this msg form synptic package manager





desktop-effects:

Package desktop-effects has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

HI and have you seen the FAQ's sticky at the top of this forum
[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

:)

---

### Post by omlx2 on 2008-07-03
i didnt get what i need

i already install compiz and fusionc i con but it is not work
couse when i write in the terminal
compiz
and i got this
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
/home/omlx2/.themes/T-ish-Brushed-Overlaid/gtk-2.0/gtkrc:56: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/omlx2/.themes/T-ish-Brushed-Overlaid/gtk-2.0/gtkrc:57: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/omlx2/.themes/T-ish-Brushed-Overlaid/gtk-2.0/gtkrc:58: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/omlx2/.themes/T-ish-Brushed-Overlaid/gtk-2.0/gtkrc:59: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

and how can i know which type of card i have??

---

### Post by omlx2 on 2008-07-03
i run this command 

wget [http://blogage.de/files/4359/download](http://blogage.de/files/4359/download) -O compiz-check


chmod +x compiz-check

./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         i810
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

---

### Post by tuxxy on 2008-07-03
you need direct rendering check you graphix supports it, if not upgrade.

---

### Post by psyopper on 2008-07-03
Actually the i810 is blacklisted (if detected, prevents Compiz from running) I believe. It will work with most effects but is broken in some critical way. 

For instance, with the i810 if you actually do run Compiz you will not be able to see any video in any media player. It's bugs like these that keep chips like those blacklisted. The problem is not with Compiz. The problem is usually with either the drivers for the chipset, or a limitation of the chipset itself.

---


---
title: "wierd drive problem???"
date: 2007-10-04
forum: General Help
---

### Post by driectly3d on 2007-10-04
ok, i dont think this one should be too hard to fix, but its beyond me O.o

was trying to install build-essential package, it asks me to instert feisty amd64 cd, so i do.
For some reason it doesnt recognize the cd  (It keeps asking me to insert disk labeled........ in /cdrom/)  , so i exit terminal and check the computer and it says it's there, so i try the same thing again in synaptic package manager. the results are the same

I go back to the computer window, and it displays 2 cd drives, my computer has only one. The drive it's calling "cd-rom 1"  is:

unmountable
undeletable
contents=nothing
location=computer:///
volume=/
freespace=127.1 GB

The other cdrom (connected via IDE) is the one that is showing the feisty cd and is working just fine, but for some reason, the properties menu is seeing it as an ATA device and its not being recognized by the terminal or synaptic package manager as /cdrom/

Now Im really at a loss as to how ubuntu is recognizing my IDE cdrom drive as an ATA, or how the cdrom-1 drive is showing the hard drive capacity......... 

any help is greatly appreciated :)

---

### Post by driectly3d on 2007-10-04
alright, solved half the problem by going into terminal, and typing

sudo rm /media/cdrom/

then right clicking on cdrom in the computer window, going to properties, then the volume tab. Found the dropdown menu there that allowed me to set the mount point to 'cdrom'
 
But for some reason the other cdrom drive is still there in the computer window, still reading 127 GB

---


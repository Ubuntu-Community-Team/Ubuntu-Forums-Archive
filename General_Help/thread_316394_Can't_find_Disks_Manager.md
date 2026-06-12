---
title: "Can't find Disks Manager"
date: 2006-12-10
forum: General Help
---

### Post by glendavee on 2006-12-10
Can someone answer a very simple question :
I've just loaded Edgy onto a second hard disk, keeping the original for Windows XP. When I look for Disks Manager under System >Administration > Disks, it isn't there. Do I have to install it from a package in Synaptic Package Manager - I assumed it would be already available when I installed 6.10?
yours in confusion

---

### Post by Azakus on 2006-12-10
By disks manager, I'm assuming you mean a GUI like windows. Try this ```
sudo aptitude install gparted
``` That will install the Gnome Partition Editor, which you can use to manage partitions and disks in System->Administration->Gnome Partition Editor

---

### Post by mgmiller on 2006-12-10
The old disk management application had been orphaned and no one was supporting it any more.  That is why Gnome dropped it.

Another good application with a nice GUI is pysdm.

" Graphical Storage Device Manager
PySDM is a PyGTK Storage Device Manager that allows full customization of hard
disk mountpoints whithout manually accessing fstab.
It also allows the creation of udev rules for dynamic configuration of storage
devices"

```
sudo apt-get install pysdm
```

Then look under System-->Administration-->Storage Device Manager

---

### Post by glendavee on 2006-12-10
Thanks for advice. Tried to install gparted - no joy - aptitude install result is "no candidate version found, no packages will be installed"
Similar with pysdm - apt-get resulted in "couldn't find package pysdm"
I'm relying on packages that came with the install CD, as I can't access internet until I figure out how to configure my wireless card.

---

### Post by glendavee on 2006-12-11
Have now managed to install pysdm by downloading the package via my Windows internet connection. Thanks

---


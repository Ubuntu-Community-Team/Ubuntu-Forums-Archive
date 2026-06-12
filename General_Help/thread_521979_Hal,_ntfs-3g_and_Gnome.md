---
title: "Hal, ntfs-3g and Gnome"
date: 2007-08-10
forum: General Help
---

### Post by atmospherik on 2007-08-10
Hello everybody !


Since I installed ntfs-3g on my Feitsy, I can mount ntfs partitions in rw mode and automount them.

But, even if they are mounted in /media/xxx, they don't appear anymore on Gnome desktop.

I tried the same with the previously integrated "ntfs" driver and they don't appear anymore.

Some ideas ?

I suspect Hal config files but unfortunately, old ones (default ones before ntfs-3g adding) were not saved and I can't compare them to new ones.

---

### Post by TheExplorer on 2007-08-12
Install all of the following packages with Synaptic:

> libfuse2
fuse-utils
libntfs-3g
ntfs-3g
ntfs-config

Then go to **Applications -> System Tools -> NTFS Configuration**

If you can't cope with the Windows partition and the Apply button is greyed out there is a little trick:

Put a tick next to the desired partition, input 'Windows' or any other name and then click anywhere inside the list of available partitions.

The partitions would automount everytime you boot into Ubuntu.

---


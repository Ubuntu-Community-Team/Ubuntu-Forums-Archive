---
title: "How do I uninstall a vmware partition?"
date: 2007-08-28
forum: General Help
---

### Post by jsmidt on 2007-08-28
I made several vmware virtual partitions for different operating systems.  I don't want all of them.  How do I remove one of them while keeping the others?

---

### Post by OttifantSir on 2007-08-29
Right-click the one(s) you no longer wish to have. Towards the bottom there should be two choices: "Remove from inventory" and "Delete" (or similar)

The first will only remove it from the console, the other will delete the Virtual Machine altogether.

If I have understood you correctly. If you mean you have made too many partitions within a Virtual Machine, you have to use a partition tool made for that OS. fdisk is, if memory serves correctly, usable for both GNU/Linux and Windows, but non-graphical. At least for Ubuntu, you can also use GParted (Gnome Partition Editor), and for Windows, go to Download and find Portable Norton Partition Magic. (USB-version, free as in free beer) for graphical interfaces.

---

### Post by jsmidt on 2007-08-29
Thanks, your first suggestion worked.

---


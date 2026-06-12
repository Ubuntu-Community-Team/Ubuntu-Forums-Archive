---
title: "Wrong devices inserted into grub menu.lst"
date: 2007-01-26
forum: General Help
---

### Post by slithy on 2007-01-26
So I swapped out the hard drive in my laptop and changed my partitioning schema with the new drive.  I moved my ubuntu install over via tarballing and had to manually edit grub's menu.lst to reflect the change in device for the partition.

The problem is that everytime the menu.lst is automatically updated (ie when you install or remove a kernel) the old devices are put in, in place of the correct device.

Does anyone know how to fix this?

---

### Post by bernied on 2007-01-26
These settings are updated by a Debian scipt after any kernel upgrades. Look in menu.lst for the Automagic area, it has clear BEGIN and END markers. In the first part of this, anything with a single # is a command to the updater script. Like this:
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)
```
So that line with '# groot ...' tells the script where my root directory is.
There's more than one you need to change.

---

### Post by bernied on 2007-01-26
Read the bit at the start of this Automagic area - don't remove the # - just change the values of the options.

---

### Post by slithy on 2007-01-26
Yep that took care of it, thanks.

---


---
title: "uninstalled udev hosed system, can I copy a working install?"
date: 2014-05-08
forum: General Help
---

### Post by sdowney717 on 2014-05-08
I thought maybe I could but I tried using nautilus as sudo and get some errors about special privilege files that refuse to copy.

So If I have a separate boot partition on both PC's, both 64 bit,  can the contents be copied from working PC system partition into the now empty system partition and have it boot. How would you do this?

I have the broken system sitting in a usb ide drive.

I uninstalled udev because my hotplugging was broken. Uninstalling udev removed so many programs it left the system destroyed.

---

### Post by ian-weisser on 2014-05-08
> **sdowney717 said:**
> So If I have a separate boot partition on both PC's, both 64 bit,  can the contents be copied from working PC system partition into the now empty system partition and have it boot.

Sort of. Copying or cloning a /boot form one system to another will work...but may not be smooth:
As long as they use the same architecture.
Remember to correct the disk UUID in grub.

From the level of experience you seem to have, I recommend backing up your data using a LiveUSB before attempting to fix. You may wind up completely reinstalling.

---

### Post by sdowney717 on 2014-05-08
I certainly have messed up plenty in my history.
I have separate /home and /, so wont loose data.

I somehow have 10.7gb in the file system I was thinking of copying and only 10gb space in the other, so I will do a reinstall.

---


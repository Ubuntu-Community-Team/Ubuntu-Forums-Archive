---
title: "[SOLVED] How to uninstall other distros ?"
date: 2008-06-02
forum: General Help
---

### Post by thelugnut on 2008-06-02
I want to check out other distros and have formatted my hd into four partitions; one for Windows Xp, one for Ubuntu (8.04), one for common data, and the last for the different distro I desire to look at.

My question is this:
Is there a simple way to uninstall the other distro and remove it from the menu?

---

### Post by housam on 2008-06-02
Just format the partition, 
reinstall grub because the last system you install will overwrite the mbr.
You can edit the grub menu.lst to make the unwanted kernels from appearing in the grub menu by adding # in front of the lines of these kernels then save and reboot.

---

### Post by thelugnut on 2008-06-02
All right, housam, I will do that right after I run some errands. Thank you for the reply.

---

### Post by thelugnut on 2008-06-02
All right, housam ...

That worked just fine. 

Again, thanks for helping me out.

:guitar:

---

### Post by housam on 2008-06-02
Glad to hear that. have fun
cheers
housam

---


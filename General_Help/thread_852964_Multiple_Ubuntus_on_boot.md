---
title: "Multiple Ubuntus on boot?"
date: 2008-07-08
forum: General Help
---

### Post by edta on 2008-07-08
Hey guys
I'm having an minor, but irritating problem.
Because I hadn't used Ubuntu in awhile, I forgot my password (because it was exceedingly complex) and I reset it with jdong's password reset instructions. Now that I recovered my password, ever since, on boot there are now SIX ubuntu options on the OS selection screen (I'm dual booting Vista and Ubuntu).

Anyone know how to delete the selections on the boot screen?

Jdong's password recovery thread:
[http://ubuntuforums.org/archive/index.php/t-3609.html](http://ubuntuforums.org/archive/index.php/t-3609.html)

---

### Post by iaculallad on 2008-07-08
You can use the Synaptics Package Manager to fix that issue on having multiple Ubuntu boot options on your GRUB menu.

Open Synaptics and search for "linux-image" (w/o double quote). Right-click on the OLD kernel images present in your system and select "Mark for Complete Removal". Do the process of right-clicking on other OLD kernels and selecting it for complete removal. Once your done, click on "Apply". That process would leave only you're desired kernel in the GRUB menu list.

NOTE: Leave (1) OLD kernel just in case.

---


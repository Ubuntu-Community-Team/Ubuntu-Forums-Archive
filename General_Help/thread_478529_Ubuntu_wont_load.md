---
title: "Ubuntu wont load"
date: 2007-06-19
forum: General Help
---

### Post by Nu7a on 2007-06-19
I installed ubuntu on my dv9205ca laptop, but it wont load, it gets to this sorta splash screen, its white and black sorta takes over it. then nothing happens. It happened to me on the live CD and I changed the VGA settings to a lower res and it worked fine. But I can seem to figure out how to change the resolution so that i can actually get into ubuntu and actually load drivers for my card.

Thanks in advance, Tyler

---

### Post by scrooge_74 on 2007-06-19
if the system boots then from command line go to /etc/Xorg/xorg.conf and make changes so you can boot 

if it does not boot then you need to give options at start time like acpi=no

---

### Post by Nu7a on 2007-06-20
Ya, i cant boot, and that acpi=no didn't work, neither did acpi=OFF. Like it gets to the progress bar screen, does its thing, then right after that, the white fadeing into black screen comes up and nothing.

---

### Post by scrooge_74 on 2007-06-20
after the bios check there is a screen were you can press ESC, see if you can boot from recovery mode

---


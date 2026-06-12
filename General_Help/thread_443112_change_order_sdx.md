---
title: "change order sdx"
date: 2007-05-14
forum: General Help
---

### Post by DLGandalf on 2007-05-14
The problem is known by many, but what is the correct way to solve it:

when I installed a pci-ide controller my drives changed, my root formerly sda5 is now sdb5 and the attached ide-disk is now sda*

-should I just live with this and change the fstab etc

-or should I change /dev/sdb to /dev/sda and vice versa, if so how?
I read something on these fora that I 'd have to use udev but I think it's fairly complicated so if someone could give me a kickstart

-other options?

thanks

edit:
- in the past I also had that pci-ide installed but everything worked as expected
-grub still uses the 'old' configuration
-(just a thing I'd like to know 'df' still shows '/' mounted to /dev/sda5 with the correct usage, while sda5 doesn't even exist how is this possible?)

---


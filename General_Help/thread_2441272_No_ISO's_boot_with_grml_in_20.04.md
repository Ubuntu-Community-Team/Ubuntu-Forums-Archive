---
title: "No ISO's boot with grml in 20.04"
date: 2020-04-21
forum: General Help
---

### Post by maestrobwh1 on 2020-04-21
For 18.04, grml is a reat package for auto configuring the boot for any ubuntu based iso that is placed in the created /boot/grml folder.  Nothing put into that folder, including the Ubuntu 20.04 iso boots in 20.04.  They are added to the grub menu and can be selected, but only a black screen is offered after they are chosen to boot from, and no key touching/tapping works and only pressing and holding the power button gets out of it by turning off the computer.  Minor in the scheme of things, but the package no longer seems to be configuring correctly for the new version of grub, and I have no idea how to supply error information because my machine just locks right after iso selection from grub.

---

### Post by sudodus on 2020-04-21
It seems that [this bug](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1851311) is affecting you. You can click 'affects me too' and add heat to the bug report.

---

### Post by maestrobwh1 on 2020-04-21
Thanks, I just did that.  I read through it and nope, no iso will then boot with the setup it uses.

---


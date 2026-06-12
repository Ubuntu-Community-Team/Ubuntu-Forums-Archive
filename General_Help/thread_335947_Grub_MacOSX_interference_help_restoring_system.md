---
title: "Grub MacOSX interference help restoring system"
date: 2007-01-11
forum: General Help
---

### Post by pennyantics on 2007-01-11
During installation my mac powerbook grub installation messed up. I am trying to revert the system to how it was before attempting to debug the installation.

The powerbook had already been configured to dual boot OSX and windows. Upon booting up, post grub installation error, I am no longer presented with the windows boot option. I am fairly sure this is because of grub.

I am pretty inexperienced with the apples so I dont really understand how to use the bios or any equivalent. Any mac or linux relevant information will be helpful.

---

### Post by ajmorris on 2007-01-11
I am not sure i completely understand. You have grub installed to boot MacOSX and windows, is that right? Are you running linux? Can you access the grub console?
if so just run it and type "root (hd"hard disk number","partition number")

then "setup (hd0)"

e.g for me it is "(root hd0,5)" "enter" "setup (hd0)" "enter"

---


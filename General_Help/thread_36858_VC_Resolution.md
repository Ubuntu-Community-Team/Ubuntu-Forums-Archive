---
title: "VC Resolution?"
date: 2005-05-24
forum: General Help
---

### Post by sudo on 2005-05-24
How do I change the resolution in the virtual consoles (Ctrl-Alt-F1 thru F6).  It would be nice to go to 1280x1024.  Thanks.

---

### Post by sudo on 2005-05-27
To answer my own question, I edited the /boot/grub/menu.lst file and added vga=773 to the kernel line, like so:

kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 vga=773 ro quiet splash

Reference for this was found here:
[http://ruslug.rutgers.edu/~mcgrof/grub-images/configs/linux/menu.lst](http://ruslug.rutgers.edu/~mcgrof/grub-images/configs/linux/menu.lst)

 \\:D/ 

Cheers!

---


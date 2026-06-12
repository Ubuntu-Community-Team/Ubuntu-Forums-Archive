---
title: "Horizontally scroll Grub menu entries?"
date: 2015-05-26
forum: General Help
---

### Post by cogset on 2015-05-26
Is it possible to horizontally scroll  Grub menu entries? 
I'm talking about the actual Grub menu at boot, not the Grub command line: I have  a multiboot system which results in a crowded Grub menu with many lines that don't fit the screen and therefore end up with an arrow, in case I wish to read the entire line, how do I scroll these?

---

### Post by Dennis N on 2015-05-26
I think that the long entries extending to the right off the screen result from an older grub version unable to correctly parse a grub.cfg created by a newer grub version existing on another OS you have installed.

Two possible solutions:
1) use the newest version of grub to build the grub menu*. You get no such long lines.
2) use custom menu entries. 

As far as I know, there is no option to scroll the grub menu horozontally. You can view a 'wrapped' version of any entry line with the 'e' key, and return with 'Esc'. That is probably the best you can do.

* meaning you would install grub from the newest OS version of Ubuntu.

---

### Post by cogset on 2015-05-27
OK, thanks. That explains it: this is exactly an oldish Grub version that also manages newer releases (multi-boot).The 'e' key trick may be enough for my needs, I'd use this rather then going the trouble of making custom menu entries.

EDIT: BTW, when you say > meaning you would install grub from the newest OS version of Ubuntu.                 you probably mean downloading  the .deb package for a newer release and installing it with dpkg ?

---


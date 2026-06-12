---
title: "Cleaner Startup"
date: 2007-01-29
forum: General Help
---

### Post by th3gh05t on 2007-01-29
Hi,

When my Ubuntu computer starts up, it starts to load all of the required things, and has an 
[ ok ] when it had loaded successfully.

How do I change the look of this font? Are there any guides that show you how to do this?

Right now, the font is all big and sometimes goes off the screen so I can't read the whole line.

Thanks for your time!

---

### Post by taurus on 2007-01-29
Edit /boot/grub/menu.lst

```
gksudo gedit /boot/grub/menu.lst
```
and add this line to the end of the entry for the kernel.

```
vga=773
```
Save it and reboot and see if the font is a little smaller this time.  Otherwise, use vga=791 if you want.

---


---
title: "resolution in boot and outside xwindows"
date: 2005-03-22
forum: General Help
---

### Post by idn on 2005-03-22
Hi, im using hoary i386 and have just switched from suse desktop 9. In suse when you are working outside of xwindows and when the computer is booting, the resolution is in a nice 1280 1024 format, my native resolution for my monitor. However in ubuntu is uses a much smaller resoluton. Is there a way to change this, when i work i like lots of screen space, makes me feel less claustrophobic!

Anyhelp appeciated, 

and if you help me i might feel inclined to buy a nice ubuntu hoody in the shop and become all full time ubuntu.

thanks!

---

### Post by alastair on 2005-03-22
Set it up the way you want using the "vga=N" kernel arg. See :

[http://www.tldp.org/HOWTO/Framebuffer-HOWTO-5.html](http://www.tldp.org/HOWTO/Framebuffer-HOWTO-5.html)

I tend to use "vga=791" (0x317) which = 1024x768 at 16 bits.

This is a kernel arg (e.g. add to the GRUB line).

---

### Post by idn on 2005-03-23
Yeah cheers that worked fine.

---

### Post by maddox on 2005-03-28
hi
i´m a newbie on linux, i used mandrake for a while and i´m trying Ubuntu for the 1st time. I used to change the boot resolution with mandrake control center so i´m not quite used with Grub.

where i do change the boot resolution exactly? in /boot/grub/menu.lst ?? and do a "update-grub" after?
i dont want to mess to much with my boot config 

any help would be gratelly apreciatted

---

### Post by maddox on 2005-03-28
ok i got it

added vga=791 to the kernel line in menu.lst and it works perfectly :)

---

### Post by CouchMaster on 2005-04-01
System > Settings > Peripherals > Display

---

### Post by tomchuk on 2005-04-02
[QUOTE=maddox]ok i got it

added vga=791 to the kernel line in menu.lst and it works perfectly :)[/QUOTE]
 The best place to add it would be to the kopt line in /boot/grub/menu.lst that way it will be automagically added to newly installed kernels.

---


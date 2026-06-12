---
title: "PC won't shut down all the way?"
date: 2007-10-26
forum: General Help
---

### Post by haroldu on 2007-10-26
OK, I've looked at all the previous posts that I could find regarding the PC not shutting off after selecting shut down.  My PC shuts down gnome and goes to the plain ubuntu screen with the indicator line going down almost all the way then stops.  I'm new at this and need a visible example of adding the "apm=off" thing to the grub menu.lst kernel line?????  Or I need an easier way of telling the darn PC to shut down all the way when I select shut down.

Thanks,

Harold

---

### Post by Schalken on 2007-10-27
A friend of mine has the same problem. On his computer Ubuntu will shut down all the way but once it gets to "The system is going to reboot/halt now" it stops. Hitting the power switch is safe at this point because Ubuntu has shut itself down.

I dont know what apm=off does or if it will fix or break anything, but to add it to your grub, hold Alt+F2 and type "gksu gedit /boot/grub/menu.lst", then add apm=off to the lines that start with "kernel".

i would recommend you duplicate the entries in menu.lst (each group starting with the line "title") so that you have ones with apm=off and ones without apm=off, and you can boot into the latter if the former doesnt work.

---

### Post by haroldu on 2007-10-27
When I add the apm=off, do I just type a space after the other stuff on that line or do I put a comma, or what?

---

### Post by yabbadabbadont on 2007-10-27
Just a space.

Edit: It may or may not help.  There appears to be a regression in the ACPI/APM handling in the vanilla kernels starting with either 2.6.20 or 2.6.21.  There are open bugs on this at kernel.org.  My machine is one that does not power off, no matter what options are included/excluded from the kernel.  However, the 2.6.19 kernel works fine.  I just wait until it hangs and then hit the power button.  Note, you will likely see the keyboard LEDs flash just as it hangs.  This is when it tries to poweroff the system.  Once you see that, it should be safe to hit the powerbutton.  (I have to hold it for four seconds on my machine.)

---

### Post by haroldu on 2007-10-27
Thanks a bunch!  I finally figured out how and what to add.  When I read the kernel line, I didn't realize the line underneath was a continuation of that same line.  Many tries later it was fixed.  Boy there's quite a learning curve for this Linux stuff.  For the benefit of those who are really dense like me, I will put a copy of what mine ended up looking like:
----------
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=91b88452-0967-47e1-99b4-55d4ec84d445 ro quiet splash acpi=force
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=91b88452-0967-47e1-99b4-55d4ec84d445 ro single acpi=force
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=91b88452-0967-47e1-99b4-55d4ec84d445 ro quiet splash acpi=force
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=91b88452-0967-47e1-99b4-55d4ec84d445 ro single acpi=force
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin acpi=force
quiet
--------------
apm=off didn't work.  Of course I didn't realize that the kernel line was continued underneath because of text wrap and the size of my gedit window.  So when I finally added "acpi=force" to the end of the correct line and of each menu choice kernel line, then and only then did my PC shut off all the way.  

Thanks again for the help.  Remember what seems clear to one with experience is not necessarily clear to someone with less or no experience.

---


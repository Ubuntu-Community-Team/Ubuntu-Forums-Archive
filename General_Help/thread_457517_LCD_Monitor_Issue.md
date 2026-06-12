---
title: "LCD Monitor Issue"
date: 2007-05-28
forum: General Help
---

### Post by adamj on 2007-05-28
I am new to the land of Ubuntu....

When I run the Live CD my monitor flips out and shows error about non-compatabile screen Resolution.  I have run the the live CD on 2 different PC's (same monitor) with the same result so it appears to be an issue with the monitor...I have found away around this by removing the "splash" entry for the boot command (i think that is the correct terminology).  Once I do this it boots fine...I have a couple of questions here:

1. How to I permanently remove this once I have done the complete install?  As it still happens after I completed the install (I thought it may have fixed it).
2. What are the consequences for doing this?

Please help, can't seem to find any posts on this?

---

### Post by krismatth3 on 2007-05-28
You can edit /boot/grub/menu.lst as root, and remove the "splash" options as appropriate there. Then, reboot.

I am not aware of any negative consequences of doing so - other than the splash screen bit doesn't happen.

---

### Post by strabes on 2007-05-28
Two things. First, if you don't really want the bootsplash anyway, be sure to remove it from the "defoptions" section of your /boot/grub/menu.lst: > ## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet **splash**

But if you would like the bootsplash screen, like most people, you should try adding "splash vga=791" to the end of your kernel boot line. (the same line that you removed "splash" from earlier. For example, mine looks like this: > kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=03836559-7516-4199-a765-9ee6985a8708 ro quiet splash vga=791

Reboot. If the bootsplash screen works correctly, add it to the defoptions section like I mentioned above.

---


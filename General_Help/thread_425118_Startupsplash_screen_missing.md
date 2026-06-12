---
title: "Startup/splash screen missing"
date: 2007-04-27
forum: General Help
---

### Post by stuart_75 on 2007-04-27
Hi,

Just upgraded to Ubuntu 7.02, but Ive lost the startup screen that tells you the progress of the o/s starting up. The monitor goes blank and the TFT says "out of range". Then it reappears with the username and password screen.

Any ideas??

Thanks!

---

### Post by strabes on 2007-04-27
Try changing or adding a vga=xxx number onto the end of the kernel you use in /boot/grub/menu.lst:

[http://en.opensuse.org/SDB:Setting_up_Unsupported_Graphics_Cards_with_the_Framebuffer_Device_(GRUB](http://en.opensuse.org/SDB:Setting_up_Unsupported_Graphics_Cards_with_the_Framebuffer_Device_(GRUB))

For example, mine looks like this:
> 
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d0f0a4bf-dda5-466c-9037-01b3acbf1dfa ro quiet splash** vga=791**


---

### Post by lw5 on 2007-04-27
Post more info; are you working on a widescreen (laptop)? What is in your /etc/usplash.conf? Anything else that might be of importance; videocard for instance..

---


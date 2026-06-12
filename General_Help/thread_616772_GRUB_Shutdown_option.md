---
title: "GRUB Shutdown option"
date: 2007-11-18
forum: General Help
---

### Post by teryowen on 2007-11-18
Hey, I was wondering if it was possible to add a Shutdown or restart options to my grub menu.

Ive read somewhere else that i need to add the following to the menu.lst file
```
title halt!
halt
```

But that didn't work. So does anyone know how to create a shutdown option in GRUB?

---

### Post by V-600 on 2007-11-18
I know you can use grub to boot your computer to various runlevels.

I belive runlevel 0 is shutdown, and runlevel 6 is reboot. Runlevel 5 is the norm for ubuntu I believe. I am not sure you would do this from a grub entry, though I am sure if this is the right track someone else could.

You can also change within ubuntu using the command "telinit"  then whatever number you want.

Out of interest why do you want to reboot/shutdown from the grub menu

---

### Post by teryowen on 2007-11-18
Say i want to restart to run from a CD or i didnt get the opportunity to access BIOS or just to turn my computer off, maybe i turned it on but then had to go somewhere.

EDIT:
With that maybe ill add a boot from CD option would i just go about writing
```

title boot CD
root (cd0,0)

```

---


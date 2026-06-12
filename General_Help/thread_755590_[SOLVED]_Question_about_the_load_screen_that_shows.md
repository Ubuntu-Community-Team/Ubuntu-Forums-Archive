---
title: "[SOLVED] Question about the load screen that shows up on boot"
date: 2008-04-15
forum: General Help
---

### Post by max.goedjen on 2008-04-15
Question about screen with the progress bar/logo that shows up when I boot Ubuntu: what is this showing the progress of? I have my laptop set to boot to CLI only, is this loading assets that I'm not going to need/use?(My Ubuntu server does not display this screen, which is why I ask). If so, is there any way to disable this?

Also:
I'm trying to recall the way I set up my Ubuntu build to boot to CLI. I remember that it had something to do with changing permissions on a file to make it boot to CLI. I did see it on this forum, just can't seem to find it again. If anyone remembers, please chime in!

---

### Post by kutjara on 2008-04-15
> **max.goedjen said:**
> Question about screen with the progress bar/logo that shows up when I boot Ubuntu: what is this showing the progress of? I have my laptop set to boot to CLI only, is this loading assets that I'm not going to need/use?(My Ubuntu server does not display this screen, which is why I ask). If so, is there any way to disable this?

Also:
I'm trying to recall the way I set up my Ubuntu build to boot to CLI. I remember that it had something to do with changing permissions on a file to make it boot to CLI. I did see it on this forum, just can't seem to find it again. If anyone remembers, please chime in!

I prefer to see exactly what's loading when I boot, so I've edited my menu.lst to remove "splash" and "quiet" from my kernel's boot parameters. As a result, I get no splash screen, instead seeing a scrolling list of exactly what's going on during the boot process.

Type sudo gedit /boot/grub/menu.lst, then find the line for your kernel. remove quiet and splash, save, and you're good to go.

---

### Post by sekinto on 2008-04-15
I think to remove the bootsplash you remove "quiet splash" from the Ubuntu entry in your /boot/grub/menu.lst file.

---

### Post by max.goedjen on 2008-04-15
Brilliant, thanks guys.

---


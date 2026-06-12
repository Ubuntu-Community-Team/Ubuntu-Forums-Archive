---
title: "bootloader woes"
date: 2007-02-25
forum: General Help
---

### Post by drko on 2007-02-25
I just installed vista after I had already installed kubuntu, and now when I boot, it goes right to windows. Is there a way that I can reinstall GRUB from the kubuntu cd or a repair function that will fix it?

---

### Post by tgalati4 on 2007-02-25
Windows is excellent at clobbering other operating systems because they simply don't exist.  Windows automatically  rewrites the master boot partion, deleting the grub boot loader.  Let's us know how well vista works--we're all waiting to hear.

Boot from the live CD

In a terminal:

sudo grub-install              (which really should be named  Help-windows-screwed-up-my-new-Ubunut-install)


Welcome to the community and good luck.

---

### Post by sailingboarder on 2007-02-25
grub just froze on my comp
I haven't had any problems, nor changed anything, but just now it isn't working

when starting up, instead of saying grub loading or what ever and actually loading, it just says grub and stops

if i reinstall grub, will i loose anything?

right now i have dual boot xp and kubuntu edgy

---

### Post by Azakus on 2007-02-25
Reinstalling GRUB only rewrites the MBR (Master Boot Record) of the harddrive. This is the section that looks for a bootloader (GRUB) to boot from.
Try this guide: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by drko on 2007-02-25
> **tgalati4 said:**
> Windows is excellent at clobbering other operating systems because they simply don't exist.  Windows automatically  rewrites the master boot partion, deleting the grub boot loader.  Let's us know how well vista works--we're all waiting to hear.



Vista is just as bad as any other windows operating system, but I need it for LAN parties...

---

### Post by sailingboarder on 2007-02-25
that worked perfectly

now my comp starts up again

thanks

---


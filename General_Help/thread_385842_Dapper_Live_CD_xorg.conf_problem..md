---
title: "Dapper Live CD xorg.conf problem."
date: 2007-03-16
forum: General Help
---

### Post by kagashe on 2007-03-16
Hi,

While trying Dapper Drake Live CD on one PC I am getting error messages suggesting reconfiguration for video card driver and the resolution.

I am reconfiguring the display for vesa driver and 800x600 resolution which is suppossed to work since the machine is booting from Damn Small Linux (DSL) Live CD. I am doing the reconfiguration by using the commend:
> sudo dpkg-reconfigure xserver-xorg

After I finish the reconfiguration I have tried the command:
> gdm

but it says that GDM is already running.

Is it possible to get the GUI after reconfiguring xserver in Live CD environment?

If not

What is the command at boot: prompt to ask the Live CD to use the desired configuration i.e. vesa driver and 800x600 resolution.

kagashe

---

### Post by Kateikyoushi on 2007-03-16
You could try the way they change the driver before loading the gui. [LINK]("http://ubuntuforums.org/showthread.php?t=379807")
Or CTRL+ALT+Backspace restarts X, but I never tried it with the live cd.
Hope it helps.

---

### Post by kagashe on 2007-03-21
> **Kateikyoushi said:**
> You could try the way they change the driver before loading the gui. [LINK]("http://ubuntuforums.org/showthread.php?t=379807")
Or CTRL+ALT+Backspace restarts X, but I never tried it with the live cd.
Hope it helps.

xserver was not running due to bad configuration by Live CD. The problem was after reconfiguring xserver I could not restart GDM.

Your link certainly helped. I could reconfigure xserver for using vesa driver and it works. The monitor is "IBM" and vesa is the best available driver for it.

Thanks for your reply.

kagashe

---

### Post by kagashe on 2007-04-22
I could finally solve this problem by checking the frame buffer setting in the BIOS and changing it from 1024MB to 8192MB.

kagashe

---


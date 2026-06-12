---
title: "no signal at all after amdgpu-pro install"
date: 2018-01-31
forum: General Help
---

### Post by MGRT on 2018-01-31
[COLOR=#111111][FONT=Ubuntu]i've installed the drivers on this page[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][https://support.amd.com/en-us/kb-articles/Pages/Radeon-Software-for-Linux-Release-Notes.aspx](https://support.amd.com/en-us/kb-articles/Pages/Radeon-Software-for-Linux-Release-Notes.aspx)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]my system was running slower than when i had windows 10 so i tried this, but after install and reboot (i followed the instruction page on amd site, so i just did ./amdgpu-install -y i got boot info, violet screen, then lost signal.

the computer starded up and i could hear it boot normally, but no video. if i pressed the shutdown button it would take some seconds as normal to shut down.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]i tried entering recovery mode but the power in the house went down so i had to start up the pc again. this time no signal at all. 

something changed on boot too. i could not hear the computer boot as usual, but it just powered up, if i pressed the shutdown button it would shut down immediately.

i tried connecting the monitor to the motherboard videocard and still nothing. i tried disconnecting the hard disk and the radeon, after some time the pc booted from the usb drive with video signal from the mobo vga. i tried reconnecting the hard disk and after some tries i was able to get the system working but incredibly laggy. i logged in and uninstalled the amd drivers. after the reboot everything was smoother, so i tried reconnecting the radeon via DVI, and it finally woerked again.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]now 2 questions:

what happened? did i do something wrong with the installation, and can i use the radeon drivers or should i stick with the open source ones?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]as i said, the system is slow (even dragging windows isn't smooth)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]here are my specs:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Processor : AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ Memory : 4039MB (2966MB used) Machine Type : Desktop Operating System : Ubuntu 17.10[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]-Display- Resolution : 1280x1024 pixels OpenGL Renderer : AMD BONAIRE (DRM 2.50.0 / 4.13.0-32-generic, LLVM 5.0.0) X11 Vendor : The X.Org Foundation[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]thanks![/FONT][/COLOR]

---

### Post by ajgreeny on 2018-01-31
As far as I can make out your CPU, and therefore the integrated graphics are fairly old, ie, from around 2010 or maybe earlier than that.  I therefore suspect that the amdgpu-pro driver is not compatible with it.

As you are using 17.10, the system should have automatically set up the correct driver for that AMD chip when you installed the OS, and having now removed the amdgpu driver I think you will have to stick with the open source radeon driver you're now using.

---

### Post by MGRT on 2018-02-01
> **ajgreeny said:**
> As far as I can make out your CPU, and therefore the integrated graphics are fairly old, ie, from around 2010 or maybe earlier than that.  I therefore suspect that the amdgpu-pro driver is not compatible with it.

As you are using 17.10, the system should have automatically set up the correct driver for that AMD chip when you installed the OS, and having now removed the amdgpu driver I think you will have to stick with the open source radeon driver you're now using.

thanks, i noticed i didn't put the graphic card specs in here. i'm using a** sapphire radeon r7 260x**. it works with open source drivers, but it is slower than the same configuration on windows 10 (obvs with radeon drivers).
so it may be a cpu "problem"? sorry i'm a noob :)

---

### Post by MGRT on 2018-02-15
up just in case i could do something else. maybe the vga was just inputting to the wrong source? any way to control it? or i just can't do it with a **r7 260x? ****thanks**

---


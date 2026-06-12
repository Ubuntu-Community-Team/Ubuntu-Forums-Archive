---
title: "unload a module"
date: 2006-11-24
forum: General Help
---

### Post by dimkal on 2006-11-24
Hell, got sort of a newbie question here...

can anybody please tell me how to unload/remove a module once and for all?

my gdm only works when i run "sudo rmmod nvidia", so every time I login I get a followin xorg error:

(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly.
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

I initially installed newest nvidia drivers which didn't do the trick, now i followed the instructions on ubuntuguide and that did it.

I think there are two conflicting versions of the modules and one of them have to be unloaded.... 

Dima

---

### Post by mark_g on 2006-11-24
I think you could just search for 'nv' or 'nvidia' using Synaptic, remove all and then reinstall the correct driver. I've done this before myself and it worked for me.

---

### Post by dimkal on 2006-11-25
isn't there a way to permenately remove a module so I don't have to "sudo rmmmod nvidia" every time i boot up?

---


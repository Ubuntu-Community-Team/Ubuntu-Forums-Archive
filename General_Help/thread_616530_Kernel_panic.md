---
title: "Kernel panic?"
date: 2007-11-18
forum: General Help
---

### Post by davebridges on 2007-11-18
Hey all,

so i went to boot up this morning and got the following:

Starting up ...

[  23.437272] Kernel panic - not syncing: Attempted to kill init!

then nothing

I updated a few things yesterday via the autoupdate, but it had been working fine after a restart (i think).  Anyone got a fix for it?

---

### Post by davebridges on 2007-11-18
bump

---

### Post by davebridges on 2007-11-18
i tried loading recovery mode, same problem

i am running a memtest now... but i have no idea whats up

windows xp loads fine (through a usb boot disk)

---

### Post by davebridges on 2007-11-18
well the memtest didnt help... sorry to keep bumping this, but i sorta need this computer and would like some advice.  Should i just reinstall ubuntu?

---

### Post by teryowen on 2007-11-18
if your not worried about any files or stuff like that then ya just reinstall. or you can just back up the files and then reinstall ubuntu. This is what i would do, but perhaps there is a way to fix this and take less time but i dont know that way.

---

### Post by PhutterMan on 2007-11-18
Some PCMCIA wireless cards seem to trigger kernel panics...if you have one, try taking it out.  I went through the relatively inconvenient process of reinstalling Gutsy on a machine with no optical drive, no floppy drive, and that can't boot from USB only to have the kernel panic recur.  In my case, the machine boots fine with the wireless card out, and even works fine if you put it in after boot.

---


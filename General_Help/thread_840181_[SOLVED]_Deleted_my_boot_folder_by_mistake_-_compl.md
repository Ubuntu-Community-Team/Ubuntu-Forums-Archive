---
title: "[SOLVED] Deleted my /boot folder by mistake - complete reinstall?"
date: 2008-06-25
forum: General Help
---

### Post by breadbin on 2008-06-25
hi, i am having problems with my boot manager and it wasn't doing what I wanted but somewhere along the line i deleted the whole /boot folder which contains the images vmlinux-2.6.24 etc. can i copy these from the dvd or were they created by the install?

i'm using hardy heron 8.04 and next question if I can just copy them over or make new ones how do i install them? thanks

---

### Post by breadbin on 2008-06-25
well i sorted it out myself, it feels good. i made my own menu.lst file, copied the kernel off te cd into /boot and also the initrd file and edited the menu.lst to point to these. easy peasy not. now its dual booting perfectly. hope it stays that way

---

### Post by Zorael on 2008-06-25
> **breadbin said:**
> easy peasy not.
Do the same thing on an XP installation and you'll be greeted with a lovely text message explicitly telling you to reinstall. :>

Anyway, cheers to it working. Please tag thread as solved under thread tools.

---

### Post by sdennie on 2008-06-25
It may be worth it to re-install the original kernel packages so that your system is in a consistent state.  It might be easiest to do this in synaptic rather than the command line.  Within synaptic, search for "linux-image" and mark all the images that are installed for re-installation.

---

### Post by breadbin on 2008-06-25
> **vor said:**
> It may be worth it to re-install the original kernel packages so that your system is in a consistent state.  It might be easiest to do this in synaptic rather than the command line.  Within synaptic, search for "linux-image" and mark all the images that are installed for re-installation.

thanks for that cos I was wondering how to get the "real" kernel back and wasn't looking forward to compiling my own even though everyone says its so easy. Did it before with Mandriva and it kept crashing whatever I did wrong I don't know!

---


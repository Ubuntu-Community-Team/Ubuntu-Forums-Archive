---
title: "Sound/Volume Control issue with multiple sound cards"
date: 2006-11-01
forum: General Help
---

### Post by Cable on 2006-11-01
I have two sound cards:  one is an onboard and the other is an Audigy 2.  Obviously, I use the Audigy 2.  It works perfectly fine, I'm just having one small issue:  the volume control applet in the gnome-panel controls the volume of the Audigy 2, while the volume knob on my keyboard (volume level pops up on screen when turned) controls the volume of the onboard card.

It's *much* more convenient to be able to use the volume control on my keyboard.  How can I make it also control the volume of my Audigy 2?

Is there a way to completely disable a device like my onboard card so that it doesn't even show up in the system?

By the way...I did not have this issue in Dapper.  Other than this one small thing, Edgy is amazing!

---

### Post by Cable on 2006-11-01
I think I got it.  Just disabled the onboard card via the BIOS.  You would think I'd have thought of that sooner.  D'oh.

---

### Post by Cable on 2006-11-02
Nevermind, that didn't work.  It only worked after one reboot and now it's doing it again.  See first post for my question.

---

### Post by Cable on 2006-11-02
Bump.  Anyone know how to disable a device like onboard sound?

---

### Post by jkvv_1973 on 2006-11-02
I have the exact problem...I have an nforce2 mobo with onboard and an audigy...I have a cordless itouch logitech keyboard...

I will subscribe to this thread till its answered...Ive searched the forum and no luck...](*,)

---

### Post by Cable on 2006-11-03
New/better thread posted [here]("http://www.ubuntuforums.org/showthread.php?p=1707148#post1707148").

---

### Post by woedend on 2006-11-03
[http://www.ubuntuforums.org/showthread.php?t=291451](http://www.ubuntuforums.org/showthread.php?t=291451)

---

### Post by SC_Frank on 2006-12-19
Cable,

Did this ever get solved to your satisfaction?
I had the same problem - an onboard VIA, disabled in the BIOS and an Audigy 2 ZS.
Pretty obvious which one I want to use and until very recently the "used" sound card would jump around, so here is what I did.

I edited the alsa.base file in /etc/modprobe.d/alsa-base and commented out all references to loading any driver besides the the emu10k1 driver. Re-booted (could have reloaded the module, but I wanted to make sure it was clean) and whoopie! Works like a champ ---

Sound for me is the single biggest driver issue, though a fully functional beryl install is pretty damn cool if you ask me.

If you still need this fixed, hope it helps..........

Frank

---


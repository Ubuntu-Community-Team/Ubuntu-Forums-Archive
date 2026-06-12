---
title: "Laptop takes infinite screenshots -- crashes."
date: 2007-10-10
forum: General Help
---

### Post by bmeyer on 2007-10-10
I've got an HP Pavilion laptop.  I had openSUSE working just fine.  But now, after the desktop loads, it takes infinite screenshots and freezes up.

I tried booting Feisty Fawn from a CD.  90% of the time, it won't load the desktop (just stops partway through).  The times that it does reach the desktop, it also starts taking screenshots like crazy.

Is this a BIOS issue?  Drivers?  Something physically wrong with the Prt Scrn key on the keyboard?  Any suggestions on how to fix it?

---

### Post by FRuMMaGe on 2007-10-10
It sounds like your Print Screen button is either held down some way.  Try using compressed air to clean under the keyboard.

I know it probably isnt this, but you may as well give it a shot.

---

### Post by tgalati4 on 2007-10-10
That's a neat failure mode.  The computer has fallen in love with itself (after seeing its reflection in Linux) until it dies from lack of memory.

Find a spare keyboard.  Your machine probably as a spare PS/2 port in the back.  Otherwise find a USB keyboard.  You may have to set something in the BIOS to turn the internal keyboard off.  Normally, in Linux, both keyboards and mice/trackpads will be active.  Sometimes you can turn off the internal ones.

That will hopefully let you boot and examine /var/log for errors.  Dmesg may show a keyboard error.

Definitely sounds like dirt or a loose screw causing a short.  Anything rattling inside?

---

### Post by bmeyer on 2007-10-10
I have the key and some surrounding ones popped off and the rubber contacts pulled up.  The print screen loop continues.  Is there a way to disable a single key in the keymap or somewhere else?

---


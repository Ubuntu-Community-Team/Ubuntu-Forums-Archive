---
title: "Laptop mysteriously not booting into Grub"
date: 2013-02-17
forum: General Help
---

### Post by Thrashrokz33 on 2013-02-17
I just attempted to reboot my computer, and GRUB won't come up. I'm left with only a blinking cursor on a black screen.

I'm really not sure what I did to cause this. The only recent things I've done are install Steam and a few games. 

Also, I ran the command "sed 's/.^/U&/g'" attempting to uppercase some filenames, which didn't produce any output. I have a bad feeling that it did something harmful, as a bit of space seemed to have increased on my hard-drive.

Should I attempt to run update-grub from livecd and see what happens from there?

---

### Post by Thrashrokz33 on 2013-02-17
Anyone? I'm in the live-cd right now.

---

### Post by Thrashrokz33 on 2013-02-17
Disaster averted (I think).

I removed and re-added the boot menu entry using EasyBCD, and it booted without a hitch (and without a splash screen, oddly enough). Possibly just an update that messed with the boot menu I guess.

---


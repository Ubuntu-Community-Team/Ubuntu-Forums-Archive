---
title: "Ubuntu won't display of my monitor"
date: 2007-05-13
forum: General Help
---

### Post by flightrecorder on 2007-05-13
I installed everything ok, I booted linux up, got the ubuntu splash screen with load bar, but then the screen goes blank and a monitor notification says "video out of range.change display to 1600x1200"

My video card is NVIDIA GeForce 6800 on a Dell XPS 600. Any ideas on how to fix this?

---

### Post by ago on 2007-05-14
remove "splash" from c:\wubi\boot\grub\menu.lst, won't be as pretty but it should work. Then once in Ubuntu there shuould be some setting for changing usplash res, after which you regenerate the usplash initrd "sudo dpkg-reconfigure usplash" and put back splash into menu.lst.

---

### Post by flightrecorder on 2007-05-14
I tried what you said, but still no dice.  I booted into generic kernel, my screen goes blank for a few seconds, and then a screen of crazy coloured lines.

Maybe I should wait for the stable version, because I have had absolutely no liuck with this.

---


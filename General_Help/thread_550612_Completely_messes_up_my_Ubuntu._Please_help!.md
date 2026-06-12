---
title: "Completely messes up my Ubuntu. Please help!"
date: 2007-09-14
forum: General Help
---

### Post by DAE_JA_VOO on 2007-09-14
I have no isea what's going on guys. I've only been using ubuntu for a week now, and this morning i turned on my PC to find this nonsense:

[IMG]http://i29.photobucket.com/albums/c267/DAE_JA_VOO/more2/14092007952.jpg[/IMG]



If i say "yes", i get this:

[IMG]http://i29.photobucket.com/albums/c267/DAE_JA_VOO/more2/14092007953.jpg[/IMG]



And then get thrown here:

[IMG]http://i29.photobucket.com/albums/c267/DAE_JA_VOO/more2/14092007951.jpg[/IMG]



Any help, please guys :(

---

### Post by splintercellguy on 2007-09-14
Boot into Recovery Mode. At the console, type:

sudo dpkg-reconfigure -phigh xserver-xorg

Select the vesa driver, and stick with default settings, and pick desired screen resolutions. Reboot.

---

### Post by DAE_JA_VOO on 2007-09-14
Thanks! That worked! I had to reinstall my nvidia drivers and now it's fine again. But now my Compiz is broken. Any idea why? I tried reinstalling but it's still screwed :|

---

### Post by DAE_JA_VOO on 2007-09-14
Anyone? :(

---


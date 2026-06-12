---
title: "Installed fine - but brown screen, white cursor and that's it!"
date: 2005-10-17
forum: General Help
---

### Post by puppy on 2005-10-17
Hi folks, Breezy Badger installed fine but when I log in it just goes to a brown screen with a (moveable) white cursor (this is exactly the same problem I had when installing Hoary - thought they would have fixed this with the new distro :( ). Anyone got any ideas how I can fix it and get to the desktop?

Cheers

---

### Post by brentoboy on 2005-10-17
I'm guessing you hear the drums. but dont see any startup action - brown background after login. Mouse works, but nothing else.
--
I had the same problem.

restart, and use grub to boot to recovery mode - root console

# nano /etc/X11/xorg.conf

find your video driver module: "ati", "nv" whatever
change it to "vesa"

save, and restart.
# shutdown now -r

it should load. the vesa driver has no optimizations, but it works in almost any environment. Once you have it booting, you can look through the forums for help getting the "real" nvidia or ATI driver kicking - if you have a need for speed.

---

### Post by puppy on 2005-10-17
Superb that worked - now to install the nvidia driver and edit my xorg.conf file - doesn't look too scary :)

---

### Post by brentoboy on 2005-10-17
check this tread... it may save you some headache

[http://www.ubuntuforums.org/showthread.php?t=77131](http://www.ubuntuforums.org/showthread.php?t=77131)

---


---
title: "Need to recover xorg.conf...don't ask"
date: 2005-10-18
forum: General Help
---

### Post by Spyderizer on 2005-10-18
Ever have one of those moments where you've just realized about a second after typing something that you've just done something monumantally stupid?

In one foul swoop I managed to kill both my xorg.conf file and its backup. Umm, I need to know if there's a way to recover it, or if there's a way to generate a new one. The system is currently still running, if I shut it down right now X is not coming back.

Any help would be greatly appreciated, thanks in advance.

---

### Post by aclaunch on 2005-10-18
You can try "sudo dpkg-reconfigure xserver-xorg" and rebuild your xorg.conf.

Good Luck
Alan

---

### Post by Spyderizer on 2005-10-18
Thank you!

---


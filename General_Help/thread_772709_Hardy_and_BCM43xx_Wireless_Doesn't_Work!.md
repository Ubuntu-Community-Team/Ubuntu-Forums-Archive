---
title: "Hardy and BCM43xx Wireless Doesn't Work!"
date: 2008-04-28
forum: General Help
---

### Post by LinuxLovesMJ on 2008-04-28
I've noticed that after installing Hardy, it auto disabled and removed the bcm43xx firmware. My wireless does not work at all. I uploaded the bcm43xx deb file and wl_apsta firmware to the computer and tried to manually install it, but hardy still does not recognize it.

I blacklisted b43, b44, and ssb, enabled bcm43xx, and still no working wireless. 

Any solution to this? I have a linksys broadcom based card.

Thank you.

---

### Post by ghost_ryder35 on 2008-04-28
the new driver is b43, the b44 is your wired ethernet connection.
You will need to un black list the b43 for wireless and b44 if you want wired connection
you can do this through system, administration, hardware drivers - to do this you must enable third party repositories under system,administration,software sources
check my sig

---


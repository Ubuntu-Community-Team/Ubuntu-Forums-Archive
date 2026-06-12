---
title: "[SOLVED] How do I disable my graphics card?"
date: 2007-02-14
forum: General Help
---

### Post by nhmc on 2007-02-14
I have a laptop with dual boot Windows XP/Ubuntu Edgy, and I think my Nvidia graphics card has just died.  Neither Windows nor Ubuntu would boot up, but I am now able to boot Windows after disabling the graphics card in safe mode.

How do I disable my graphics card in Ubuntu?  I can log in as root on a command line in Ubuntu, it only fails when a GUI tries to load. 

Thanks!

---

### Post by dcstar on 2007-02-14
> **nhmc said:**
> I have a laptop with dual boot Windows XP/Ubuntu Edgy, and I think my Nvidia graphics card has just died.  Neither Windows nor Ubuntu would boot up, but I am now able to boot Windows after disabling the graphics card in safe mode.

How do I disable my graphics card in Ubuntu?  I can log in as root on a command line in Ubuntu, it only fails when a GUI tries to load. 

Thanks!

You will have to edit your xorg.conf file:
```
sudo nano /etc/xorg.conf
```
and change the driver from nvidia to VESA.

Save and exit, then:
```
/etc/init.d/gdm restart
```
and see if you get a basic X system working.

---

### Post by nhmc on 2007-02-15
Thanks for the reply!

VESA didn't work, but changing the video driver from 'nvidia' to 'nv' allowed me to start up the X system again.  However, even this was too much for my seriously wounded graphcis card to handle :-(   It looks like some serious hardware maintenance will be required.

---

### Post by dcstar on 2007-02-15
> **nhmc said:**
> Thanks for the reply!

VESA didn't work, but changing the video driver from 'nvidia' to 'nv' allowed me to start up the X system again.  However, even this was too much for my seriously wounded graphcis card to handle :-(   It looks like some serious hardware maintenance will be required.

I hope it's under warranty, most laptop video problems require a new motherboard.....   :(

---

### Post by nhmc on 2007-02-16
Aha.  I initially tried setting the driver to 'VESA' (upper case) and that didn't work.  I've now tried it in lower case, 'vesa' and that does work.  Ubuntu runs ok now, even with the dodgy card.

---


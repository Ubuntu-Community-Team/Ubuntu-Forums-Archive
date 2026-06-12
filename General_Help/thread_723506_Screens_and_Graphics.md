---
title: "Screens and Graphics"
date: 2008-03-13
forum: General Help
---

### Post by AntiHeroJoe on 2008-03-13
I've got some issues with my screen display. While trying to get my laptop to work with a projector for a presentation (it never worked, quite frustrating) I managed to mess up my main graphics settings.

If I try, through System > Admin > Screens and Graphics, to select a 1440x900 widescreen display, this setting will revert to 1024x768 on next start up.

Also, compiz/Advanced Desktop Effects is now telling me that I can no longer turn on these effects!

How can I fix this?

(CHALLENGE MODE: Without terminal, through a GUI interface)

---

### Post by zxscooby on 2008-03-13
maby reconfiguring the xserver?

[http://wiki.freespire.org/index.php/Reconfigure_a_Broken_Xorg_Server](http://wiki.freespire.org/index.php/Reconfigure_a_Broken_Xorg_Server)

---

### Post by AntiHeroJoe on 2008-03-13
> **zxscooby said:**
> maby reconfiguring the xserver?

[http://wiki.freespire.org/index.php/Reconfigure_a_Broken_Xorg_Server](http://wiki.freespire.org/index.php/Reconfigure_a_Broken_Xorg_Server)

Thanks man, that worked well. After that I just had a problem with missing title bars w/compiz, but a google search and xorg.conf edit fixed that. Kinda bums me out when I can't fix things with a GUI interface in Ubuntu. Thanks again, mate.

---


---
title: "xorg.conf how do i...."
date: 2007-04-27
forum: General Help
---

### Post by Loki-uk on 2007-04-27
Hi am I missing something but where is the setting for the screen resolution stored? I've had a look in /etc/X11/xorg.conf but it stores the colour depth and supported monitor modes but I can not see anywhere where it says actual current screen resolution? Is this stored in a different file somewhere?

Thanks

Loki

---

### Post by Pox on 2007-04-27
xorg.conf just handles the possible screen resolution - the actual one used is determined by your DE settings.  I'm guessing that's System -> Admin/Settings/Sometihing/ -> Display Settings or something similarin GNOME, I know it's Settings -> Display Settings in XFCE.

---

### Post by Loki-uk on 2007-04-27
Hi

But do you know where that data is stored as often I have changed the screen res and xserver dies or loops and I would like to know where it is so I change it back from a command line.

Thank You :)

---

### Post by Pox on 2007-04-27
I'm not sure, but it could be in a config file somewhere in ~/.gnome2/ or a key somewhere in gconf-editor.

---

### Post by Loki-uk on 2007-04-28
Thanks I think i'll have a root round (no pun intended) and see if I can find it :)

---


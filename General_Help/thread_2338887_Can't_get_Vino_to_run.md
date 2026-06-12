---
title: "Can't get Vino to run"
date: 2016-10-02
forum: General Help
---

### Post by dryan775 on 2016-10-02
Hello all.
I tried to upgrade from 14.04 to 16.04 and it crashed during installation (Windows EULA - ugh!). 
Anyway I finally got it working, but it was SLOW to boot and shutdown and couldn't find my printer.

I did a fresh install of Ubuntu Mate 16.04 but I can't seem to get Remote Desktop working.
i seem to have the software.
I have a vino-server file in /usr/lib/vino, it has execute bit set
ls -alF shows 
-rwxr-xr-x 1 root vino-servier*

I have "enabled" it in dconf-editor under org->gnome->desktop

I DON'T have a menu option to start the program

Going to the /usr/lib/vino and trying to run it gives me: command not found
If I start typing vino then hit tab (to auto complete) I get vino-p (which ISN'T listed in the ls

Any ideas?

nev.r.chk

---

### Post by steeldriver on 2016-10-02
It may be because the /etc/xdg/autostart/vino-server.desktop restricts it to certain desktop sessions e.g.

```

OnlyShowIn=unity;

```

---


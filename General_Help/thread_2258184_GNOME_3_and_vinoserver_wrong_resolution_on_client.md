---
title: "GNOME 3 and vinoserver wrong resolution on client"
date: 2014-12-25
forum: General Help
---

### Post by b666mg on 2014-12-25
Hi, 

I am having problems viewing my GNOME desktop on any VNC viewer.

I activated the VNC Server via alt+f2 "vino-preferences". 

the problem is that it always shows only half the resolution of the display which should be viewed. my GNOME session is running in 1920x1080 but all VNC Clients get only 960x540.

I guess it has something to do with GNOME's desktop settings (multiple virtual desktops) which lead to problems with vinoserver.

In dconf editor I can change the vino / remote access configuration but there's no option for setting the screen resolution.

I don't know if it's a bug in GNOME or vino - but i guess it should work because vino is the ubuntu GNOME built-in VNC Server application.

any ideas?
thanks in advance!

---

### Post by b666mg on 2014-12-26
can I provide further information that helps solving the problem?

---

### Post by b666mg on 2014-12-27
installed gnome-session-flashback and the client is viewing the full desktop with 1920 x 1080.

so there must be a problem with gnome3 and vino vnc server.

can anybody tell me how the (vino) vnc server gets the screen resolution it has to use?

---


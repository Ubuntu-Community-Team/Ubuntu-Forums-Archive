---
title: "[SOLVED] Is it possible to disable Gnome panels temporarily"
date: 2008-06-06
forum: General Help
---

### Post by bmwman on 2008-06-06
Is it possible to disable Gnome panels temporarily? I installed kiba-dock and like for now but it sucks having the 2 panels on top and the bottom. Can I disable the panels without removing them and how to disable/enable them again? Also can I add "Show Desktop" button adn Login/Shutdown menu on the kiba dock?

Thanks

---

### Post by klange on 2008-06-06
I'd set them to autohide and change the settings in gconf-editor to make them show only one pixel (default is like 4 or something).

---

### Post by bmwman on 2008-06-06
> **WindowsSucks said:**
> I'd set them to autohide and change the settings in gconf-editor to make them show only one pixel (default is like 4 or something).

I tried autohide but they're still quite visible. Couln't find where to change the size to 1 pixel

---

### Post by klange on 2008-06-06
/apps/panel/toplevels/[panel you want to set]/auto_hide_size
Set it to 1. And also, after looking, it appears the default is 6.

---

### Post by bmwman on 2008-06-06
Hmm, i don't have /apps/panel/toplevels/. Mine is /apps/panel/default_setup/toplevels/bottom_panel or top_panel. I changed it from 6 to 1 and enable auto hide but that didn't really change anything. I even restarted my X session.

---

### Post by bmwman on 2008-06-06
Are there any other ways to make my panels disappear and bring them back if I want to?

---

### Post by Forlong on 2008-06-07
> **bmwman said:**
> Hmm, i don't have /apps/panel/toplevels
Are you sure?
What's the output of
```
gconftool-2 --all-dirs /apps/panel/toplevels
```

---

### Post by bmwman on 2008-06-07
> **Forlong said:**
> Are you sure?
What's the output of
```
gconftool-2 --all-dirs /apps/panel/toplevels
```

@IBM-PC:~$ gconftool-2 --all-dirs /apps/panel/toplevels
 /apps/panel/toplevels/top_panel_screen0
 /apps/panel/toplevels/bottom_panel_screen0

---

### Post by bmwman on 2008-06-07
BTW when I make any changes, are they supposed to take effect after reboot or immediately?

---

### Post by bmwman on 2008-06-07
I figured it out :)

I opened the gconf-editor with sudo and maybe that's why it wasnt changinng anything since i'm not logged in with root. So much nicer now.

Thanks a lot.

---

### Post by Genius314 on 2008-06-07
If you're using Compiz-Fusion, another method would be to use the Widget Layer plugin. Just type *name=gnome-panel* in the "Widget Windows" box, and you can make the panel appear and disappear with a keyboard shortcut, mouse shortcut, or by moving to a certain edge of the screen.

---

### Post by bmwman on 2008-06-07
Dude, you are Genius :)

Thats even better solution. Awesome.

---


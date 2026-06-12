---
title: "Vlc, Movie player don't  work on Compiz"
date: 2008-05-12
forum: General Help
---

### Post by aurora_consurgens on 2008-05-12
I have problem with Vlc and Movie Player. Vlc, Movie Player don't work on Compiz. When I run Compiz and open file such as .mp3, .avi Vlc, Movie Player don't play. It will turn off automatically but I turn off Compiz Vlc, Movie Player can play. How I solve this problem?

Sorry, I'm not skillful English language because I'm a Thai. 

Thank you

---

### Post by aroch1 on 2008-05-16
For the video, sometimes the default video output module doesn't play nicely wit compiz.  You can fortunately change it easily though!  In VLC go to Settings->Preferences->Video->Output Modules.  Select the "Advanced options" option in the bottom right and try changing it to "X11 video output".  This has worked for me.

---

### Post by Whoo on 2009-02-08
You can try the magical variable:

> export XLIB_SKIP_ARGB_VISUALS=1 
vlc

Dominique

=====================
Gnome-session/Compiz/dock-cairo

---


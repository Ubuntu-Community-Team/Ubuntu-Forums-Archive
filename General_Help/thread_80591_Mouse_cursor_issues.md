---
title: "Mouse cursor issues"
date: 2005-10-22
forum: General Help
---

### Post by JensKue on 2005-10-22
My cursors look broken, like being displayed with only black and white. No fancy smooth colors ... So far I tried the kubuntu default cursor theme and PolarCursorTheme. The cursor looks good on logging in but changes/breaks when KDE desktop comes up. When logging out of KDE the cursor reverts to normal/good again.

If anyone happens to know how to take a screenshot with the cursor showing - please post, I will upload one then.

And something else: I managed to get the KDE-cursors working when using Gnome/GTK-apps like firefox by following some instructions from this board. However, the "busy"-cursor is still not right.

---

### Post by IronWolve on 2005-10-23
I'm having the reverse issue. It uses the default cursors on GDM and changes when logging into Gnome or KDE.

I noticed it would use the default x11 cursors. (The black buzy clock one). After I changed it under mouse options for humanity theme, it changed to the correct ones, but it only switchs after logging in.

Where is picking up the default x11 cursors before loading GDM/GNOME?

Where can I change the cursor before GDM so I can resolve this issue?

Thanks.

---

### Post by JensKue on 2005-10-23
... just found out that the cursors are only distorted as long as amaroK runs ... ?! Very strange. But when I close amaroK the corsors suddenly start looking good again. Similarly, they break when amaroK is started.

I never realised that because amaroK runs constantly on that pc :)

Any ideas?

---

### Post by IronWolve on 2005-10-23
I dont know the bootup proces for GDM and font selection, so after I figure that out I'll know where its loading the default mouse cursors.  I just dont like when it when Gnome loads and you see the old x11 default busy cursor, then it flips to the humanity cursor them.  Not broken, just not very professional looking.

Anyways, as just for the one application, nope.  

I do know KDE and Gnome defaults back to the generic x11 busy non-animated cursors if you play around with adding themes (edubuntu/gnome) additional art packages.  I had to go back in and set both to the Humanity theme, but it only fixes after login. Even if you dont manually select the themes, something triggers it to default. Its a bug somewhere...

Trying to google "GDM Busy cursors" isnt coming up with much hits.  I might just load a generic, small load onto a spare partition and try to find to find out.  Thats the only thing I dont like about x11, boot process has files spread all around, gets a little complicated when you go crazy and install too much stuff. (But whats the fun if you dont try to break stuff?)  :???: 

-IronWolve

---


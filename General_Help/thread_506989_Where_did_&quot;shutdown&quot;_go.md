---
title: "Where did &quot;shutdown&quot; go?"
date: 2007-07-22
forum: General Help
---

### Post by bcjtown on 2007-07-22
I've noticed that in my Feisty Fawn Server installation, under System, Quit, I no longer have the option of restarting or shutting down.  In order to do that, I have to log out and then restart from the login screen.  Is there a way to replace this functionality?

---

### Post by eggdeng on 2007-07-22
[http://www.ubuntux.org/lost-shutdown-option-in-exit-menu]("http://www.ubuntux.org/lost-shutdown-option-in-exit-menu")

---

### Post by UJoe4 on 2007-07-22
Sometimes this happens when you're using a different display manager and desktop environment. For instance, if you're using GNOME but logging in with KDM, GNOME won't show the shutdown/restart options.

---

### Post by geraldm on 2007-07-22
shutdown can "disappear" whenever env PATH variable changes. 
It helps to be able to bring up an xterm or any terminal and then access it directly
with /sbin/shutdown OPTIONS

Gerald

---

### Post by drs305 on 2007-07-22
I had a similar problem. I installed gtweakui and it restored the options once I set them via System, Prefs, gTweakUI - Session, Show logout menu. I don't use the server version but it's probably the same.

---

### Post by NilsE on 2007-07-22
Or just for the heck of it go into System/Administration/Login Window Preferences and select Show actions menu. This might just solve your problem.

---

### Post by drs305 on 2007-07-22
> **NilsE said:**
> Or just for the heck of it go into System/Administration/Login Window Preferences and select Show actions menu. This might just solve your problem.

In my case, I lost all references to logout at the above site and then discovered gTweakUI. Even after installing it I don't have any logout options displayed in the above location. I don't know how I lost them...

---

### Post by bcjtown on 2007-07-23
> **UJoe4 said:**
> Sometimes this happens when you're using a different display manager and desktop environment. For instance, if you're using GNOME but logging in with KDM, GNOME won't show the shutdown/restart options.

So how do I fix it?  I guess I need to switch to GDM but I don't know how to do it.

---

### Post by UJoe4 on 2007-07-24
Try:
> sudo dpkg-reconfigure gdm

---


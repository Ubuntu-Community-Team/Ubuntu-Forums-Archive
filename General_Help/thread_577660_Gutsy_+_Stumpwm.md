---
title: "Gutsy + Stumpwm"
date: 2007-10-16
forum: General Help
---

### Post by hebetude on 2007-10-16
I just discovered stumpwm, having used gnome for quite some time I wanted to test out mouse-less windows.  I found some inconsistencies with their howto install and my setup.  For one, it wants me to overwrite my .xsession file to execute their windows manager.

However, I do not have an .xsession file in my home directory nor do i have a .xinitrc.  I read through the global file /etc/X11/xinit/xinitrc and it indeed points to these locations.  Whats going on here?  If I create these files will I fubar my current gnome/compiz?  

I'd like to be able to preserve gnome+compiz, if stumpwm turns out to not be what Im looking for.

Thanks

---

### Post by tremby on 2007-12-16
afraid i can't answer your question -- i'm looking for the same answer. i've been using stumpwm on my Debian laptop for a few months now, and on that it's the only window manager so i had no problem overwriting the files. now i want to try stumpwm on my desktop machine, but would like it to appear on the sessions list along with KDE.

anyone know how to get this set up? i would have thought the stumpwm package would have sorted this all out automatically.

---

### Post by ~LoKe on 2007-12-16
Not necessary.  Just do this:

```
gksu nano /usr/share/xsessions/stumpwm.desktop
```
Paste this in:
> [Desktop Entry]
Encoding=UTF-8
Type=XSession
Exec=stumpwm
TryExec=stumpwm
Name=StumpWM
Comment=Stump window manager

I don't know if stumpwm is the executable, so check in /usr/bin to see if it's there.

It'll now appear in your session list.

That should do it.

---

### Post by lotus49 on 2008-06-03
That certainly did the trick for me.  Thanks for the post.

---


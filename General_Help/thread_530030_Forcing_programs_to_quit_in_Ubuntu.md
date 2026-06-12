---
title: "Forcing programs to quit in Ubuntu"
date: 2007-08-20
forum: General Help
---

### Post by dbsoundman on 2007-08-20
I would like to know if there's a way, preferably a keyboard command, that will allow me to force a program to quit in Ubuntu, much like ctrl-alt-delete works in Windows. I've had a couple occurances where I've had to shut the computer off manually because the whole thing froze up because of some stupid program.

Speaking of stupid programs...how can I uninstall a program from the command line? I don't know where the installation is actually placed, but I can't find it anywhere else, and this program just isn't working out well (slcreator), so I want to dump it.

-Dan

---

### Post by aysiu on 2007-08-20
Alt-F2 ```
xkill
``` will do it.

If you want to assign Control-Alt-Delete to ```
xkill
``` [you can do that, too.](http://72.14.253.104/search?q=cache:raKNorspTu0J:doc.gwos.org/index.php/GnomeKeyboardShortcut+site:gwos.org+gnome+keyboard+shortcut&hl=en&ct=clnk&cd=1&gl=us&lr=lang_en)

As for *slcreator*, how did you install it? How you uninstall it depends on how you installed it in the first place.

---

### Post by AlfaTrion on 2007-08-25
thanks for the xkill command.
when i logged back into kubuntu from xp gwenview was on for some reason and had stalled.

---

### Post by strabes on 2007-08-25
You probably have it set to save your session.

---

### Post by HermanAB on 2007-08-25
'Ctrl-Alt-Esc' should launch Xkill and change the mouse cursor to a skull and cross-bones.

Be careful what you click then!  You can cancel with 'Esc'.

Cheers,

Herman

---

### Post by maharbA on 2007-08-26
> **HermanAB said:**
> 'Ctrl-Alt-Esc' should launch Xkill and change the mouse cursor to a skull and cross-bones.

Be careful what you click then!  You can cancel with 'Esc'.

Cheers,

Herman

I believe that's only for KDE (I just tried it with Gnome and it did nothing, so ... )
It's great feature, though -- very clear what it does.

---

### Post by aysiu on 2007-08-26
> **maharbA said:**
> I believe that's only for KDE (I just tried it with Gnome and it did nothing, so ... )
It's great feature, though -- very clear what it does.
You can achieve the same thing in any environment (Gnome, Xfce, IceWM, Fluxbox) by binding a keyboard shortcut to the command ```
xkill
```

---

### Post by vdawg on 2007-08-26
from the xkill man page : "This command does not provide any warranty that the application whose connection to the X server is closed will abort nicely, or even abort at all. All this command does is to close the connection to the X server. Many existing applications do indeed abort when their connection to the X server is closed, but some can choose to continue."

A definitive action would be to bust out the terminal
ps -auxf
to see a list of all the processes on the system, grab the pid of the problem child
and 
kill -9 [pid]

make sure u kill all other associated processes and u'll be golden :)

PS: kill -9 -1 will kill all the processes on your system, I tried it on the school server, it rebooted my session :)

---


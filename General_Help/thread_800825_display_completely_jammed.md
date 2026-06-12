---
title: "display completely jammed"
date: 2008-05-20
forum: General Help
---

### Post by mringer on 2008-05-20
Xubuntu 8.04  recently installed & all updates as of 2008-05-18

I have somehow managed to jam my display completely. On login I get a
pale blue screen with no top or bottom panels, no application icons,
no response to mouse buttons. I can do  alt-F2  and run a command,
or  ctrl-alt-F1  and get a console login.

Other users get a normal display. Please is there a way to return all
of my config files to a default state?

---

### Post by morgengenuss on 2008-05-20
well, you could simply erase that user's profile and make a new one.

other than that you can also login, then press alt+f2 and execute "xfce4-panel", that should bring the panel back. if xfce doesn't manage your desktop (no icons, no click-reaction) you can go to settings -> desktop -> "allow xfce to manage the desktop".
if on your next login the panel and everything is still missing, simply save your session on logout.

---

### Post by mringer on 2008-05-23
The command  xfce4-panel  did restore the panels (thank you) but
they now disappear when I next log in. I have set both  

allow xfce to manage desktop

and

restore session on login

& panels are still not there on login.

---

### Post by morgengenuss on 2008-05-25
and the other option ("well, you could simply erase that user's profile and make a new one.") doesn't work?

---


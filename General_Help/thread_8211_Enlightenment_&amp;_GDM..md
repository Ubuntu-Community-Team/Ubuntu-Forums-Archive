---
title: "Enlightenment &amp; GDM."
date: 2004-12-15
forum: General Help
---

### Post by paradox on 2004-12-15
Hi!

I'm new ubuntu user :D Normally i use enlightenment like window/desktop manager. I download enlightenment with apt-get but i must insert in "GDM session list" enlightenment informations to start it. Graphic Login manager don't offer options for insert new window manager. How i can insert a new "item" in "session list" of GDM?

TNX!

---

### Post by Nikola on 2004-12-15
Add to /usr/share/xsessions file named enlightement.desktop that contains this:

```
[Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Comment=This session logs you into Enlightenment
Exec=enlightenment
TryExec=enlightenment
Type=Application

```

---

### Post by paradox on 2004-12-15
Humm....this don't work. I create this file but the elinghtenment item don't appears in menu session. 

In slackware i add a similar file suggested (in another location) but i add a line like this in /etc/X11/xdm/Xsession:

enlightenment)
	exec enlightenment
	;;

Only file enlightenment.desktop, under ubuntu, seems don't work. Others idea?

---

### Post by paradox on 2004-12-15
ah no ok, now work. I don't restart gdm correctly. :D TNX!!!

---


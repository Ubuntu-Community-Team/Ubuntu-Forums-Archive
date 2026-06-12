---
title: "xgl session fails to load"
date: 2007-01-14
forum: General Help
---

### Post by dbbolton on 2007-01-14
i have never had any xgl problems. now, when i try to start an xgl session, the splash screen doesn't come up. instead, a dialogue appears saying something like "your session lasted less than 10 seconds. you should try the failsafe sessions."

here is my .xsession-errors log :

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "daniel"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/startxgl.sh: line 2:  5200 Segmentation fault      Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer

(gnome-session:5149): Gtk-WARNING **: cannot open display:  

```i don't know what to make of it.

edit:

this started to happen after i tried to install kiba dock. i ended up aptituding a bunch of packages like libxserver-dev and compiz. could that have something to do with it ?

---

### Post by philipacamaniac on 2007-02-27
I have the same error and Xgl won't load, using Dapper/ATI/Xgl.

---

### Post by dbbolton on 2007-03-01
my hard drive has been erased twice since then, haha

---


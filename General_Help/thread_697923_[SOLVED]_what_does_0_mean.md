---
title: "[SOLVED] what does :0 mean ?"
date: 2008-02-15
forum: General Help
---

### Post by salah_tr on 2008-02-15
Hi all,

the **who** command's result is :
```
med     tty7         2008-02-15 22:47 (:0)
med    pts/0        2008-02-15 22:57 (:0.0)
```
what does **:0** and **:0.0** mean ?

---

### Post by PinkFloyd102489 on 2008-02-15
It's the X server.

---

### Post by salah_tr on 2008-02-15
do you know what's the difference between **:0** and **:0.0** ?

---

### Post by astrotech226 on 2008-02-15
> **salah_tr said:**
> do you know what's the difference between **:0** and **:0.0** ?

:0 means the X server on Display #0.

:0.0 means the X server on Display #0, Screen #0.

You can have multiple X servers running multiple displays and multiple screens on the same computer.  An example would be a computer with two monitors.  Let's say screen #0 is the left monitor and screen #1 is the right monitor.  You can open a program on either monitor by changing the DISPLAY variable.

```
DISPLAY=":0.0" gnome-terminal
```

... would open gnome-terminal on the left monitor.

```
DISPLAY=":0.1" gnome-terminal
```

... would open gnome-terminal on the right monitor.

---

### Post by salah_tr on 2008-02-15
screen is the monitor, but what is the display ?

---

### Post by astrotech226 on 2008-02-15
> **salah_tr said:**
> screen is the monitor, but what is the display ?

I think the display can be equated to the X Server instance.  When you start up your computer, an X Server is started on display #0 or ":0".  You can get to this server or display by pressing Ctl-Alt-F7.

You can start a second X Server that does something different.  It can be local to your computer or maybe even on another one.  If you've never done it, it's pretty wild.  You can actually start an X Server on display #1 or ":1", but query another computer.  Let's say they are using KDM for it's display manager.

If you press Ctl-Alt-F8, you will see the KDM login screen.  If you press Ctl-Alt-F7, you will go back to your desktop.

There are many different variations to this, but for a standard Ubuntu setup, this should ring pretty true.

---

### Post by salah_tr on 2008-02-16
Thanx all :)

---


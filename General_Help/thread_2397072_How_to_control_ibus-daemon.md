---
title: "How to control ibus-daemon?"
date: 2018-07-25
forum: General Help
---

### Post by jds102 on 2018-07-25
Ubuntu 18.04, Gnome Shell 3.28.2, Wayland. I want to use one of the m17n input methods available with ibus, but have ended up with a mess, with two instances of the daemon running simultaneously:

bombay:~$ ps aux |grep ibus
gdm      25249  0.0  0.1 362524  8644 tty1     Sl   07:36   0:00 ibus-daemon --xim --panel disable
gdm      25252  0.0  0.0 281080  6032 tty1     Sl   07:36   0:00 /usr/lib/ibus/ibus-dconf
gdm      25255  0.0  0.3 402904 28244 tty1     Sl   07:36   0:00 /usr/lib/ibus/ibus-x11 --kill-daemon
gdm      25260  0.0  0.0 278892  6080 ?        Sl   07:36   0:00 /usr/lib/ibus/ibus-portal
gdm      25317  0.0  0.0 205224  6660 tty1     Sl   07:36   0:00 /usr/lib/ibus/ibus-engine-simple
john     25451  0.3  0.1 362624  8908 tty7     Sl   07:36   0:03 ibus-daemon --xim --panel disable
john     25455  0.0  0.0 281184  6664 tty7     Sl   07:36   0:00 /usr/lib/ibus/ibus-dconf
john     25458  0.0  0.3 402800 27980 tty7     Sl   07:36   0:00 /usr/lib/ibus/ibus-x11 --kill-daemon
john     25461  0.0  0.0 279024  5972 ?        Sl   07:36   0:00 /usr/lib/ibus/ibus-portal
john     25575  0.1  0.0 205220  6528 tty7     Sl   07:36   0:01 /usr/lib/ibus/ibus-engine-simple
john     26313  0.0  0.2 269484 17220 tty7     Sl   07:37   0:00 /usr/lib/ibus/ibus-engine-m17n --ibus
john     27746  0.0  0.0  21864  1096 pts/0    S+   07:55   0:00 grep ibus

This is clearly undesirable, but more to the point it prevents ibus from working. Every reboot sees the same two versions of the daemon started.

The real problem is that I cannot find how to disable either daemon. I cannot see where gdm starts ibus-daemon, and I cannot see where I (user john) start it either -- it is not in my autostart directory.

I would like to be able to disable both invocations of ibus-daemon, so that I can then decide whether to run it via gdm or as an ordinary user. (My reason for perhaps favouring the second option is that it seems to work with emacs when started that way.) Can anyone solve either of these problems, or ideally both?

---


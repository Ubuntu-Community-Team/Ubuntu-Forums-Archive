---
title: "Screen Blanking"
date: 2017-11-17
forum: General Help
---

### Post by mongoosex on 2017-11-17
I have a problem with screen blanking in Ubuntu. Previously a fedora user about 10 years, then a debian unstable user.. and recently moved to Ubuntu 17.10 with GNOME 3

Problem:

After about a minute the screen blanks. Moving the mouse or touching a key unblanks it. No big deal... screensaver etc.

However, nothing I do disables this. It's infuriating.

I've run settings Power -> Blank never
I've tried
xset -dpms 
xset s off 
xset s noblank 
xset s 0 0 
xset s noexpose

after running those commands and then using "xset q" gives:

Screen Saver:
  prefer blanking:  no    allow exposures:  no
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0x0    WhitePixel:  0xffffff
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Disabled




but then... it will still end up blanking the screen. It's making watching youtube videos almost impossible.

Can anyone suggest a solution?

---

### Post by #&amp;thj^% on 2017-11-17
the easiest method for my self is to install "Caffeine" :  [http://www.omgubuntu.co.uk/2016/07/caffeine-indicator-applet-ubuntu-lock-screen](http://www.omgubuntu.co.uk/2016/07/caffeine-indicator-applet-ubuntu-lock-screen)

---


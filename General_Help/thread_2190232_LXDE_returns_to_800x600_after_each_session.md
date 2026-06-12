---
title: "LXDE returns to 800x600 after each session"
date: 2013-11-26
forum: General Help
---

### Post by kyle11 on 2013-11-26
I'll try to summarize a few weeks of work and frustration into a few sentences.  I use Lubuntu as a VMWare Player virtual machine.  With 13.04 I clicked "Start"->Preferences->Monitor Settings, set the screen resolution to 1280x1024, saved, and was done.  It worked perfectly for a long time.

Troubles began when I upgraded the 13.04 to 13.10 and then it always dropped to 800x600 and the screen resolution would no longer save.  Out of extreme frustration, **I deleted the VM** and created a new one from a fresh CD.  The **fresh** (not upgraded) 13.10 will not save its resolution either.  What worked perfectly on 13.04 x64 does not work at all on *upgraded or a fresh install* of 13.10 x64.

Having read dozens of web pages in the last few weeks, I have tried editing the following:
[LIST]
[*] ~/.config/lxsession/Lubuntu/autostart 
[*]~/.config/lxsession/Lubuntu/desktop.conf (Xrandr section) 
[*]/etc/xdg/lxsession/Lubuntu/audostart & desktop.conf 
[*]~/.config/autostart/lxrandr-autostart.desktop (putting @xrandr... and also xrandr... in the Exec= section) 
[/LIST]

On the command line, typing in ```
sudo xrandr --output Virtual1 --mode 1280x1024
or
xrandr -s 1280x1024
```works fine, but it is a gigantic pain to open a terminal to do this manually every time I start a session when this worked so flawlessly and automatically in 13.04.

What must I do to get Lubuntu 13.10 to set the monitor resolution automatically the way it did in 13.04?

Thanks in advance,
Kyle

---

### Post by kstevens on 2014-01-08
[http://ubuntuforums.org/showthread.php?t=2194268](http://ubuntuforums.org/showthread.php?t=2194268) seemed to solve some of the problems, although it's unclear why this isn't the default behavior anymore.

---


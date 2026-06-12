---
title: "Desktop crashes after locking screen"
date: 2017-02-10
forum: General Help
---

### Post by texpat on 2017-02-10
This is on Xubuntu 16.04.1 LTS

Sometimes, when I lock the screen from the menu, the desktop environment won't come back up again. I can switch to a console using CTRL+ALT+F1 and issue commands from there. So I found [this thread]("http://askubuntu.com/questions/215632/restart-xfce-from-tty1") over at ask ubuntu but that didn't help.

This is what they suggest, and the results I had:
```
~$ xfwm4 --replace
~$ (xfwm4:3436): Gtk-Warning **: cannot open display:
```
```

~$ sudo restart lightdm
~$ restart: Unable to connect to Upstart: failed to connect to socket /com/ubuntu/upstart: Connection refused

HOWEVER

~$ sudo service lightdm restart

does have effect, although it kills the desktop environment and brings me to the login screen. Not tested with crashed DE, yet.

```
```

~$ pkill -KILL -u <myusername>
see below

```
The last one is supposed to force-logout the user and bring you to the login screen. It works when the desktop environment is running, but not after the crash, where I get some message about not being able to open the display.

I'm really out of my depth here so I'd appreciate any hints as to how to diagnose and solve this issue. I've been looking at log files hoping to find some hint about what went wrong, but they are mostly meaningless to me: I don't know which are the relevant ones. For example, I found [FONT=Courier New]**lightdm.log**[/FONT], but I can't make head or tail of it :-/

---

### Post by texpat on 2017-02-16
This has gone unheeded for 6 days. I'll give it a bump ;-)

---


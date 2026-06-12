---
title: "Mystery login and freeze"
date: 2007-09-03
forum: General Help
---

### Post by psyncho on 2007-09-03
This occurs before I try to login:

A couple times now, I've sat down at my server to find that the screen is frozen. The panel at the bottom for XUbuntu is there and the mouse is in the middle. I can't do anything, or switch to a non GUI terminal (i.e. control F8 does nothing). 

So, it looks like it froze either when something was logging out, or something tried to login and it froze. Now, I have a fair amount of security here, only have ports 22, 80, and 443 open and everything is up to date. So I would be surprised if I got hacked.

So I'm wondering, what makes the system go from the login prompt where its usually at, to this state, without me doing anything. I use web apps, that's about it.

Any help or pointing in the right direction would be greatly appreciated.

John

---

### Post by psyncho on 2007-09-03
I just found this running process:
```

PID TTY      STAT   TIME COMMAND
 8320 tty7     Rs+  869:41 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7

```


I'm not sure what time format is printed in, but I think its minutes and 
seconds. So I suppose I'll back track to that time and look around my logs.

In either case, it appears to be the gdm window manager for X, and it does indeed appear to be some sort of initiated authentication...or something about leaving it sitting there makes it screw up? Perhaps if I just uninstall Xubuntu, although I'd rather have some sort of gui on there.

---

### Post by psyncho on 2007-09-03
I did a
>ps aux | grep gdm 
and found this:
```
root      8320 39.9  2.2  26924 21484 tty7     Rs+  Sep02 914:48 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      8627  0.0  0.1  12220  1352 ?        Ss   15:12   0:00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
root      8628  0.0  0.1  12220  1492 ?        S    15:12   0:00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
root      8639  0.0  0.0   1636   396 ?        Ss   15:12   0:00 /usr/lib/gdm/gdmopen -l /bin/sh -c /usr/bin/dialog --yesno 'There already appears to be an X server running on display :0.  Should another display number by tried?  Answering no will cause GDM to attempt starting the server on :0 again.  (You can change consoles by pressing Ctrl-Alt plus a function key, such as Ctrl-Alt-F7 to go to console 7.  X servers usually run on consoles 7 and higher.)' 16 70
root      8642  0.0  0.0   1636   288 tty9     Ss+  15:12   0:00 /usr/lib/gdm/gdmopen -l /bin/sh -c /usr/bin/dialog --yesno 'There already appears to be an X server running on display :0.  Should another display number by tried?  Answering no will cause GDM to attempt starting the server on :0 again.  (You can change consoles by pressing Ctrl-Alt plus a function key, such as Ctrl-Alt-F7 to go to console 7.  X servers usually run on consoles 7 and higher.)' 16 70

```

So it appears I have 2 window managers running but I don't know why. Again, any help in preventing this from happening would be much appreciated. I am running Xubuntu

---

### Post by psyncho on 2007-10-07
This has magically stopped happening.

---


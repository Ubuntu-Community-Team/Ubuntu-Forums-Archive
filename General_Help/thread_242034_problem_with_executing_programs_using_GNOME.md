---
title: "problem with executing programs using GNOME"
date: 2006-08-23
forum: General Help
---

### Post by opexoc on 2006-08-23
Hi. I have already experienced some unexpected problem. Any program
which uses gnome to be executed can't be executed. For example
gnome-terminal or mozilla-firefox. This situation is only problem of
users, who are not root. For root everythink is going well. Moreover,
this situation displays suddenly.
For example when I want to execute mozilla-firefox:

opexoc@ubuntu:/media/wind/Victor/d/Filmy$ mozilla-firefox
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

(firefox-bin:6162): Gtk-WARNING **: cannot open display:

This is really quite weird problem for me. I don't know what should I
do.

btw. I use ubuntu dapper.

best,
opexoc 

// this thread was appeared on comp.os.linux.misc group, and someone told me to reinstall gtk and xlib. I did it, and nextly my system was crashed and later my Xserver was crashed. I found in this forum some support. I execute "sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10" and my Xserver run again, but something is going still wrong. The problem, which was displayed on comp.os.linux.misc is still present. To now, I have one accident of such situation, but I afraid that this situation will be repeated. What should I do ?

---

### Post by mlind on 2006-08-23
try this
```

sudo rm ~/.Xauthority

```

Then restart gdm by pressing Ctrl+Alt+Backspace

If this doesn't help, could you post the outputs of
```

export | grep DISPLAY
groups

```

---

### Post by opexoc on 2006-08-24
ok thx. I will do that if this situation will be repeated. Then I will report 
everything.

---


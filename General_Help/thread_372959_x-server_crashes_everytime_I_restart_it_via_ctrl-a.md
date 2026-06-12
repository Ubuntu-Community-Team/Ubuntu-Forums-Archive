---
title: "x-server crashes everytime I restart it via ctrl-alt-backspace"
date: 2007-02-28
forum: General Help
---

### Post by harty83 on 2007-02-28
Every time I restart xorg by ctrl-alt-backspace, it crashes.  My xorg.conf file is obviously fine because it works.  But if I ctrl-alt-backspace, my server crashes with some unknown exception error.

Some things about my system:
My graphic card is an intel 9145GM and I have 915resolution installed.  I also have a patched kernel with suspend2 installed.  

 Any clue what could cause this?  Like I said, it works fine until I manually restart it.

Thanks!

---

### Post by zvacet on 2007-03-01
Disable ctrl+alt+backspace
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
```
sudo gedit /etc/X11/xorg.conf
```
in the end of file add this
```
Section	"ServerFlags"
Option	"DontZap"	"yes"
EndSection
```
save file
You will restart with this 
```
sudo /etc/init.d/gdm restart
```

---

### Post by harty83 on 2007-03-01
Thanks,

I'll do that if I have to.  But I would like to get to the root of the problem because I like the convenience of using ctrl-alt-backspace to restart x.

Alan

---


---
title: "Startx fails - stuck at login"
date: 2017-03-03
forum: General Help
---

### Post by bznm on 2017-03-03
[COLOR=#111111][FONT=Ubuntu]After a power outage, I reboot the computer.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]However when I login and press enter, the screen turns black for a moment and then the login screen comes again.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]If I press ctrl alt f1 and type 'startx' the screen turns completely black for a moment and then I see the console again, with no apparent error but "server terminated successfully". This is the xorg log:[http://pastebin.com/Q9aLxBZz](http://pastebin.com/Q9aLxBZz) .[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I've already tried to rm the .Xauthority file or sudoing startx but it doesn't work. How could I solve the problem? I urgently need to use the computer :/[/FONT][/COLOR]

---

### Post by Bashing-om on 2017-03-03
bznm; Hello;


We may have a problem:
/vmlinuz-3.19.0-30-generic
Belongs to a End_Of_life release - vivid .
What release are you running, and what is the DeskTop environment ( xfce4 ??) ?
Show:
```

hostnamectl status
lsb_release -a
ls /usr/share/xsessions

```

Have you got the liveDVD(USB) on hand in order to conduct a file system check ?

[INDENT][INDENT]maybe Yes
[INDENT][INDENT][INDENT]could be not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---


---
title: "Xorg crashes on xinitrc"
date: 2007-08-26
forum: General Help
---

### Post by ian6 on 2007-08-26
I've got a more-or-less stock Feisty install. Xorg is using the nvidia-glx drivers and has been configured to allow any user to start it. I have an ~/.xinitrc file that starts mythfrontend, but whenever I start Xorg it immediately exits. There are no errors either on the console or in the log file, save for a few (non-fatal) warnings about font paths.

I tried commenting out the lines in my xinitrc... same problem. Xorg starts, shows the nvidia logo, shows me about a second of cursor, then quits. If I remove the xinitrc, Xorg starts, but that's not an ideal long term solution.

Does anyone have any suggestions?

---

### Post by ddrichardson on 2007-08-27
Have you appended a & onto the last program loaded in .xinitrc?

---

### Post by kerry_s on 2007-08-27
post the ~/.xinitrc.
did you make it executable?

mine looks like this->

```

#!/bin/sh

eval `cat $HOME/.fehbg` 
#xsetroot -solid black &
sudo conky &
qsynaptics -r > /dev/null &
rm /home/user/.xsession-errors &
xrdb -merge ~/.Xdefaults &

jwm


```

---

### Post by ddrichardson on 2007-08-27
You've gone to bed I guess so if I'm not on in the morning, the last entry, like the above jwm, needs to not have an & otherwise it'll execute it and quit.

---


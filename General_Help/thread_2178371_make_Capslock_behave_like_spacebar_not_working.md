---
title: "make Capslock behave like spacebar not working"
date: 2013-10-03
forum: General Help
---

### Post by jmwatte on 2013-10-03
hello,
because my spacebar is broken on my old Dell,  I am trying to reconfigure my capslock to spacebar.
i got the following script ...

#!/bin/sh
# Turn Caps Lock into space
sleep 3
xmodmap -e "clear lock"
#xmodmap -e "remove  Lock = Caps_Lock" # Remove Caps Lock
xmodmap -e "keycode 66 = space" # Make the key into space

I tried different combinations but no luck...
It runs at startup.

THX
JM

---


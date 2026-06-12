---
title: "KeePassX AutoType Feature"
date: 2015-10-28
forum: General Help
---

### Post by Max_S on 2015-10-28
Hi there,

I've tried to get the KeePassX AutoType feature to get to work for me without success. The problem is e.g. that instead of a "@" it writes an "&#8539;". I've browsed the interwebs a bit and found this closely related topic: [http://sourceforge.net/p/keepassx/bugs/269/](http://sourceforge.net/p/keepassx/bugs/269/). Typing the command "setxkbmap de" in a terminal also fixes it for me but how can I automate this? I added the command as a startup application but that doesn't fix it for me. Can I somehow edit the keyboard configuration files directly?

I have Ubuntu 15.10 installed on a notebook with a german keyboard layout. This might also be useful:

max@max-ThinkPad-T440s:~$ setxkbmap -query
rules:      evdev
model:      pc104
layout:     de,us
variant:    ,
max@max-ThinkPad-T440s:~$ setxkbmap de
max@max-ThinkPad-T440s:~$ setxkbmap -query
rules:      evdev
model:      pc104
layout:     de

I ran this in a terminal after login and now the AutoType works.

Cheers,

Max

---

### Post by TheFu on 2015-10-29
I've been hit by this too. If the keyboard LANG doesn't match what was used during the creation of the keepassX DB, then it won't enter the correct keys.   I always thought it was the entire system which needed the fix, but if it  is just keepassx, then setting an env up just for 1 program is easy.

Write a tiny script.
```
#!/bin/sh

#  set environment vars here (mine would be)
export LANG=en_US.UTF-8
export GDM_LANG=en_US
export LANGUAGE=en_US

# run pre-cmds here
/usr/bin/setxkbmap us

# Lastly, run the real keepassx program here; detach it
/usr/bin/keepassx &
```
Then make the file executable and make a GUI menu for it, it you care.  Think they are .desktop files now. Haven't used those in years myself.

Hope this helps.  I was screwing around with some options and have the right-alt set to support Spanish letter input:
```
options:    compose:ralt,terminate:ctrl_alt_bksp
```
Want the CTL-ALT-Bksp to kill X/Windows, as dog intended. ;)

---


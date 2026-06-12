---
title: "Cannot Start Xorg From Within Xorg + Other Xorg Questions"
date: 2007-11-28
forum: General Help
---

### Post by Githlar on 2007-11-28
I created a little script to run a game that I want to play called "Exile III: Ruined World" in semi-fullscreen mode using a new X session and a customized Xorg screen at a 640x480 resolution, since the exile3-fullscreen-binary program is looking for XF86 configs. Here is the script.

```
#!/bin/bash

OLD_DISPLAY=$DISPLAY
if [ -z $1 ]
then
  export DISPLAY=:1
else
  export DISPLAY=$1
fi
X $DISPLAY -verbose 5 -br -screen exile &
xauth nmerge ~/.xauth
sleep 5
exile3
export DISPLAY=$OLD_DISPLAY
exit
```

When I run this code from a Virtual Terminal, it works just fine. However, when I try to start it from within X, I get this error message:

AUDIT: (date): 12722 X: client 1 rejected from local host (uid 1000)

I've tried everything I could find:
[LIST]
[*]xhost +LOCAL:
[*]xhost +
[*]Exporting and importing the key with the xauth program
[*]Generating the key with `xauth generate`
[/LIST]

And probably every combination of those that I could think of. However, no matter what I try, I still get the error.

I understand that X authorizes connection first by host and then by authorization using MIT-MAGIC-COOKIE-1. So, theoretically `xhost +` should solve my problem - or so I thought.

Anybody managed to do anything like this or seen this error and know how to fix it?

Any help would be GREATLY appreciated =)
 
P.S.: In order to get this script to work, I had to change the allowed_users directive to "anyone" in the /etc/X11/Xwrapper.config file Is there a way to allow only certain users to run the X server?

---

### Post by Githlar on 2007-11-29
Bump :)

---


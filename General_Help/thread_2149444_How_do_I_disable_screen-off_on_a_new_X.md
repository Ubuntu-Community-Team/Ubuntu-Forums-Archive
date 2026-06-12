---
title: "How do I disable screen-off on a new X?"
date: 2013-05-28
forum: General Help
---

### Post by am_i_registered on 2013-05-28
Hello guys,

I'm running my games (using wine) on a separate X in order to get a little better performance, however after 15min the screen goes off and I have to move my mouse to turn it back on.
There is no problem when I'm playing shooting games, because obviously I use the mouse and the problem does not show up, however when I use my gamepad it is very frustrated...
Does anyone know how to disable this from the terminal?
I have already disabled the screen-off on my ubuntu, but on the new X it appears... i suppose every separate X has its settings??

---

### Post by am_i_registered on 2013-05-29
100+ views and no reply?
how is it so difficult to disable screen-off functionality, that nobody knows how to do it?
:confused:

---

### Post by dodo3773 on 2013-05-29
Screen blanking can be shut off with xset (dependant whether or not something else other than DPMS is handling this on your seperate X session (hard to say since you didn't say which window manager you are running on  server :1 )). Try this:
```

xset -dpms
xset s off

```

---

### Post by am_i_registered on 2013-05-29
> **dodo3773 said:**
> Screen blanking can be shut off with xset (dependant whether or not something else other than DPMS is handling this on your seperate X session (hard to say since you didn't say which window manager you are running on  server :1 )). Try this:
```

xset -dpms
xset s off

```

Well, thank you for your answer. 
Unfortunately, this does not work...

I have created a script with the following code:
```

#!/bin/bash

xinit /usr/bin/ck-launch-session /usr/share/playonlinux/playonlinux --run "Pro Evolution Soccer 2013" %F $* -- :3 & nvidia-settings --load-config-only

```

Adding the commands you provided me with to the script does not stop the blanking.
Any other ideas?

---

### Post by dodo3773 on 2013-05-29
Are you running the xset commands from :3 or from the xsession you are loading the game from? If you are running that command from 0 you may need to do something like "xset -dpms -display :3" and "xset s off -display :3" so that it exports the display you wish to apply it to. Also, make sure you have xset and that it is working ("which xset" should return xset path). Other than that I am unsure.

---


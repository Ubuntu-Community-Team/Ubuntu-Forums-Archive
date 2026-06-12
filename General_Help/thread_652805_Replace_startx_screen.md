---
title: "Replace startx screen?"
date: 2007-12-29
forum: General Help
---

### Post by nunnst on 2007-12-29
I have my system setup for autologin staight to "startx" (no gdm).  I hate the screen that "startx" splashes up before going in xfce.  Does anyone have a clue how to replace that ugly grey screen with something more appealing?

Thanks!

---

### Post by marty_oc on 2007-12-29
I don't think it's possible. That ugly screen is blank X server desktop and remains shown up until a window manager starts.

---

### Post by kerry_s on 2007-12-29
use xsetroot in your ~/.xsession or ~/.xinit(i think, can't remember what the other ones called, i usually use xsession)
example:
xsetroot solid black &

use " man xsetroot " for more info.

---

### Post by nunnst on 2007-12-29
Thanks kerry_s, but unfortunately I didn't work. It just changed the color of my Conky window when I opened an Xfce-terminal.  Totally unexpected result!

---

### Post by kerry_s on 2007-12-30
yeah, forgot about that,  in xfce there's the root desk and then the background desk sits on top of that, conky sits in the background desk so it shows the root underneath. i think what i use to do when i used xfce4 was to use " feh " to set the exact same wallpaper as i had on the desktop.
example:
instead of using-> xsetroot solid black &
use
feh --bg-center /path/to/pic &

you'll have to install feh( sudo apt-get install feh ) if you don't already have it.
you can also just use->  eval 'cat $HOME/.fehbg'
in ~/.xsession and then just open the pic with feh, right click and set as background, that way you won't need to edit every time you change pics.
man feh <-for more info

sorry i'm a little rusty, been taking a break from linux. :)

---


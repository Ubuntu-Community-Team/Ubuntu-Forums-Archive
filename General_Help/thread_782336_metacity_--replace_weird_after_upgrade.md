---
title: "metacity --replace weird after upgrade"
date: 2008-05-04
forum: General Help
---

### Post by Tekmoor on 2008-05-04
I'm using a simple script for running games, basically it just disables compiz and a few other things, runs the game, then enables them again. After upgrading to hardy the metacity --replace command isn't working quite right.

When I run metacity --replace all my windows disappear and I get just the desktop wallpaper and the mouse cursor. I've found out that if I switch to another virtual terminal and then back to xwindows (ie. press ctrl-alt-F1 and then press ctrl-alt-F7) I get all my windows back and metacity is running instead of compiz (so the metacity --replace worked).

Anyone have any idea how I could fix this or what I could add to my script to get around it? Thanks!

---

### Post by Rocket2DMn on 2008-05-04
We can try, but can you please post the script for us that you are using?

---

### Post by Tekmoor on 2008-05-05
I've modified a script by Enrique Schiel...

```
#!/bin/bash
# runner
#
# Sun Oct 28 07:17:37 2007
# Copyright 2007 Enrique Schiel
# <ecschiel@yahoo.com.ar>

# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU Library General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor Boston, MA 02110-1301, USA

CHANGE_COMPIZ=0
CHANGE_SSAVER=0
CHANGE_AWN=0

if ps -e | grep compiz; then
CHANGE_COMPIZ=1
fi

if ps -e | grep gnome-screensav; then
CHANGE_SSAVER=1
fi

if ps -e | grep avant-window-na; then
CHANGE_AWN=1
fi

if [ $CHANGE_COMPIZ == 1 ]; then
printf "Disabling advanced desktop efects...\n"
/usr/bin/metacity --replace &
fi

if [ $CHANGE_SSAVER == 1 ]; then
printf "Disabling screensaver...\n"
gnome-screensaver-command --exit &
fi

if [ $CHANGE_AWN == 1 ]; then
printf "Disabling Avant Window Navigator...\n"
killall avant-window-navigator
fi


printf "Running the game...\n"
$@
wait $!
printf "The game is finished.\n"


if [ $CHANGE_SSAVER == 1 ]; then
printf "Restoring screensaver...\n"
gnome-screensaver &
fi

if [ $CHANGE_COMPIZ == 1 ]; then
printf "Restoring advanced desktop efects...\n"
/usr/bin/compiz --replace &
fi

if [ $CHANGE_AWN == 1 ]; then
printf "Restoring Avant Window Navigator...\n"
avant-window-navigator &
fi

```

---

### Post by Rocket2DMn on 2008-05-05
That is rather strange, what type of video card do you have?
```
lspci | grep VGA
```
Is there any output to the terminal if you manually run metacity --replace?
If you are using restricted drivers, you will probably need to reinstall them since you upgraded to Hardy.

---

### Post by Tekmoor on 2008-05-05
My output from lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GS] (rev a2)

There is no output at all when I run metacity --replace in the console.
Sorry, I said I upgraded to hardy but I actually did a clean install, I just meant upgraded in general.

There must be something that switching virtual terminals does that somehow restarts xwin and causes all my windows to show up again...

---

### Post by Rocket2DMn on 2008-05-05
I have never heard of anything like this happening, what if you try just switching workspaces instead of getting away from X?  Sounds like it's just not refreshing the screen for whatever reason.
You may consider searching [launchpad]("https://launchpad.net/") for bug reports related to this, and if you don't find one, create one yourself because this definitely sounds like a bug.

---

### Post by Tekmoor on 2008-05-06
Switching workspaces doesn't seem to work at all.
I couldn't find anything on launchpad, I've never submitted a bug before so maybe I'll look for some info on doing that first... thanks for your input.

---


---
title: "xmame"
date: 2007-12-15
forum: General Help
---

### Post by Moonfrost on 2007-12-15
Hello everybody, I have a question. I just installed xmame and kxmame (kde frontend for xmame which works with gnome by downloading the xmame sdl libraries also available through sypnatic), this is the first time I use MAME on Linux since I always used it on Windows...anyway, the problem is that when I check the properties to see what are the default directories it tells me for example that the roms folder is at /usr/lib/games/xmame/roms...I searched that directory and it doesn't exist (also used various search features that come with Ultimate Edition) and it keeps telling me the directory doesn't exist. Could it be that that's where the directories are in KDE? since I'm using a KDE frontend? because my main folders for xmame are in /home/<username>/xmame  but there's no roms folder and artwork folder and etc in there...there's only a configuration folder, a diff folder (difference files) and then some folders like "hi", inp, mem, nvram, rc and sta...anybody have any idea?

---

### Post by matthewcraig on 2007-12-16
...  try putting them in /usr/share/games/xmame/roms  ...

---

### Post by Moonfrost on 2007-12-16
> **matthewcraig said:**
> ...  try putting them in /usr/share/games/xmame/roms  ...

Oh well, I went and made my own directories and pointed it to those, thanks anyway!

---

### Post by matthewcraig on 2007-12-17
Just pop back onto the Ubuntu Forums and use the Thread Tools menu to mark your question "solved", when you get your questions figured out.

---

### Post by disturbedite on 2007-12-17
i'm gonna post some info i posted on another xmame thread...

i know no one asked for it, but if i could offer some advice:
don't use xmame.  its dead and super outdated.  use [sdlmame]("http://wallyweek.altervista.org/index.php").

if you need a frontend/gui use sdlmame w/ [kxmame]("http://sourceforge.net/project/showfiles.php?group_id=145736&package_id=174814&release_id=514402"). (<-- use that build specifically, not any other or the version available in the official ubuntu repos, its too old & doesn't support sdlmame).
you have to compile kxmame tho. if you can't get kxmame to compile try this:
```
./configure --disable-joystick
```(of course that will disable joystick/joypad support, but some ppl have reported its needed to get it to compile).

---

### Post by blackcp on 2007-12-24
> **disturbedite said:**
> i'm gonna post some info i posted on another xmame thread...

i know no one asked for it, but if i could offer some advice:
don't use xmame.  its dead and super outdated.  use [sdlmame]("http://wallyweek.altervista.org/index.php").

if you need a frontend/gui use sdlmame w/ [kxmame]("http://sourceforge.net/project/showfiles.php?group_id=145736&package_id=174814&release_id=514402"). (<-- use that build specifically, not any other or the version available in the official ubuntu repos, its too old & doesn't support sdlmame).
you have to compile kxmame tho. if you can't get kxmame to compile try this:
```
./configure --disable-joystick
```(of course that will disable joystick/joypad support, but some ppl have reported its needed to get it to compile).

How exactly do I compile kxmame?

thanks

---

### Post by Sopranosmainman on 2007-12-25
yes i too would like to know how to compile kxmame...

./configure doesnt work

you get no such file or directory message

---


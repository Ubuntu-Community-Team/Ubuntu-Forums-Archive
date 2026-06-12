---
title: "Screensaver interrupting games."
date: 2007-05-13
forum: General Help
---

### Post by thehuman on 2007-05-13
Hey everyone. First off, I love the site. I have been using Ubuntu for about a month now, and this place has been my user manual. Endless appreciation.

But, I now have a problem that I can't find, and I am guessing somebody knows how to fix it quickly.

Basically, it happens when I am playing Quake 2 and FCEUltra. I play them both on full screen, and they work fine... UNTIL my screensaver kicks in. I guess since the mouse is "windowed" in Quake and not used in FCE Ultra, the system is not registering that anything is going on, and when the screensaver kicks on, it boots me out of the program, and in the case of Quake, freezes the computer.

Now I know the obvious fix--disable the screensaver when I play. That would easily fix it, but I'm a perfectionist, and I was hoping somebody could tell me how to get an "override system idle" setting kind of thing, so that the screensaver will automatically be disabled while those programs are running. If not, I'll just stop being lazy and turn the screensaver off every time I play. Thanks a million.

---

### Post by tgoose on 2007-05-13
This is definitely possible. There are a couple of commands you can send to stop the screensaver from activating.

One is
```

gnome-screensaver-command --inhibit

```
I don't know much about this; presumably it just stops the screen from blanking while it's running and has to be closed.

Another is

```

gnome-screensaver-comand --poke

```

Which acts as though you are moving the mouse within X when it's run.

Now I don't have a clue about how to actually implement either of these commands, so either complain at someone involved with either game until he or she will implement it or read up on bash scripts. It should be incredibly simple to do; something like a three or four line script.

---

### Post by thehuman on 2007-05-13
Yeah... You know, I could probably just make my launchers for those programs use the terminal and just add the "...inhibit" command on to the end. It's kind of rough, but it seems like that should work. That was exactly the kind of answer I was looking for. Thanks. I'll let you know how it works.

---

### Post by thehuman on 2007-05-13
Ok, I got it. In case you're interested:
```

gnome-terminal --tab --command="gnome-screensaver-command -i"
cd /usr/local/games/quake2/ && quake2 +set vid_ref softsdl

```
Basically, I had to automate it to open 2 terminal windows--one to keep the screensaver inhibit open, and the other to run Quake. I probably made it more complicated than it needs to be, but it's working great! Both programs start fine, and they both automatically disable the screensaver until I tell them otherwise. Make a couple launchers for them, and I am set. Man, I love Linux.

All this work just to keep from typing my short alias to kill the screensaver.

---

### Post by joshsmith on 2008-05-28
hey,
just stumbled into this. thanks for the useful post tgoose

@thehuman
about your command
gnome-terminal --tab --command="gnome-screensaver-command -i"
cd /usr/local/games/quake2/ && quake2 +set vid_ref softsdl

i should point out that you didnt need to do cd /usr/local/games/quake2. just running the command quake2 in terminal run any programs if they are stored in the right folders (called your PATH) and /usr/local/games is one of those. (to run a program from your current directory you need to use ./quake)

anyway, to the real point of my post:
if you change your command to:
(gnome-screensaver-command -i) & (quake2 +set vid_ref softsdl && killall gnome-screensaver-command)
you should get the same result but a little bit cleaner, ie without any terminal windows needing to appear. put it in a text file and you can run it straight from your applications menu

the & runs both the brackets simultaneously, and the && runs the killall command when the quake command has finished (ie you exit the game)

hope it is helpful

---


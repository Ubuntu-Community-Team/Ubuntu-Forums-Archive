---
title: "Gnome Go Boom"
date: 2007-01-27
forum: General Help
---

### Post by juyanith on 2007-01-27
Hmmm... I seem to have broken something. I'm running 6.10 x86_64 and have been pretty successful at getting 32bit apps working. However, I was playing around with the latest wine sources today (0.9.30) and after getting WoW working I killed the x session for some reason. (I've long since forgotten why.) The session restarts and I am presented with the gnome-greeter but after I log in and the drums play I get nothing. No, seriously, I mean nothing. Nothing except a cursor. I looked about in /var/log but can't find anything that looks like an error and I'm not quite familiar enough with gnome to figure out what's wrong. I ran an xterm from the terminal on ctrl-alt-f1 using
```
DISPLAY=:0 xterm &
```
and then
```

gnome-wm&
gnome-www-browser&

```
to get to the forums but searching hasn't given me any insight. The closest thread I found was [this one]("http://www.ubuntuforums.org/showthread.php?t=181155"), but reinstalling gnome-session hasn't helped. The last thing I did was copy some ttf fonts into fonts:/// but I doubt that's the issue. Besides, I renamed .fonts to see if anything changed with no luck. I haven't yet tried getting rid of .gnome , .gnome2, and so forth but I guess I may have to since I've run out of ideas.

I'm sure the X server and nvidia drivers are fine. Heck, I can even run beryl if I like (although it does complain about dbus -- beryl: Couldn't activate plugin 'dbus'). Unfortunately, this doesn't give me a clue as to where to look next.

So, anyone have a suggestion?

---

### Post by juyanith on 2007-01-27
Er, ok. Nevermind I guess. I used a windows fix and rebooted. Everything seems fine now -- weird. I guess that's what I get for infecting my computer with windows-like libraries (wine). :D

---


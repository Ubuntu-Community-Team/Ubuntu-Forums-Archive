---
title: "Up key = Screenshot? Huh?"
date: 2007-08-25
forum: General Help
---

### Post by aldenhg on 2007-08-25
I've been messing around with my new laptop mouse and I made some changes to xmodmap to try and get the thumb button to work, which had the unintended side effect of making my arrow keys nonfunctional with the exception of the up key which now initiates a screenshot. I don't know how I did it and because I can't look through my bash history I can't tell you what the exact command I passed to xmodmap was. What logs/config files/whatever should I post?

---

### Post by jamvegan on 2007-08-25
Your bash history is stored in a file:
```
~/.bash_history
```
So you could use more or vi or any text viewer or editor to look at it.  Most recent commands are at the bottom of the file.  Note, however, that the file is not written to until you exit your terminal session, so if you haven't done that since issuing the offending command you should do so and then start a new terminal before trying to view your history.

---

### Post by aldenhg on 2007-08-25
Thanks. I guess the offending command was ```
xmodmap -e "pointer = 1 3 2 4 5 6 7 8"
```
Which really doesn't seem like it should have caused the problem.

---

### Post by aldenhg on 2007-08-25
I just realized something - my arrow keys aren't the only ones that are messed up. Page Up = /, Page Down = Right Click, Right Control = Page Down, etc. I'm guessing that I've just messed up my keyboard map. How do I set it back to the default?

---

### Post by aldenhg on 2007-08-25
OK, I figured out that it was in fact the evdev driver I was using for the mouse that was messing me up. It wanted to drive the keyboard and the mouse, so I just switched back to the mouse driver. This leaves me without my horizontal scrolling and my back button, but I'll find a workaround.

---


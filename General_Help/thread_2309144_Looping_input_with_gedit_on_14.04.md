---
title: "Looping input with gedit on 14.04"
date: 2016-01-08
forum: General Help
---

### Post by The_Marlboro_Man on 2016-01-08
Hi:

I have been trying Lubuntu 14.04 on a netbook during a few weeks now. Even though the system works flawlessly there's one particular problem that has been preventing me from switching OSs.

I have become accustomed to using gedit for my code production and found a number of useful plugins (mainly gedit-plugins and gedit-developer-plugins) to develop with. As you know, gedit it not bundled with Lubuntu so I installed it and its plugins on a fresh Lubuntu install. Along with gedit there came many dependencies (I distinctly remember zeitgeist being one of them) but the editor starts up fine.

Thing is, after working for a while with it (sometimes a minute, sometimes several, sometimes editing a single file, sometimes editing more than a single file) keyboard input starts to skip and repeat. I'll explain myself: when typing some keypresses are ignored and replaced with other input: I may be typing "Hello world" and what appears on the screen may be "H cro world" (the "ell" replaced by " cr"). To make matters worse, this is cyclical: the same "replaced" sequence appears after a few keystrokes rendering work impossible. It happens not only when writing but also when navigating the document (for example, I am using the cursor keys to scroll down and lots of " cr" may write themselves on the document). This is specially grating then instead of just a sequence of characters other things like line feeds get written.

The problem has been reproduced with both the integrated keyboard and a external one. 

I got the exact same problem when using "medit" but not when, for example, writing stuff on Firefox or the terminal so I suspect something that goes beyond the editor itself. I already tried dmesg or starting gedit from a terminal but nothing suspicious appears. It must be noted that the very same OS has been installed in another computer without this problem.

Does any of this rings any bells?. Thanks a lot.

---

### Post by Dennis N on 2016-01-08
Sounds like the ibus problem. ibus causes a text entry problem in Lubuntu 14.04 in some applications. The solution is to disable it:

**Preferences > Language Support > (close any pop up window) > Keyboard Input Method System > change from ibus to none.**

---

### Post by The_Marlboro_Man on 2016-01-08
Ok, I read about this Ibus thing for a bit and since it doesn't seem like something I would use right now, I followed your instructions to disable it. 

I can't tell you right now if it's working or not since the problem phases in and out of existance but will try my best to try and code something, see if the problem pops up.

Will report back. Thanks :).

---

### Post by The_Marlboro_Man on 2016-01-08
I have been working for almost an hour and have experienced no problems at all (I would say I can type faster now too :D!!!).

Thanks a lot. Marked as solved.

---


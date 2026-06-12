---
title: "Please help"
date: 2014-07-11
forum: General Help
---

### Post by colddesigner on 2014-07-11
So i did 
"primusrun unity"
didnt think about what would happen, and now i cant access anything
key commands wont work, no unity gui.. idk how to fix

---

### Post by lisati on 2014-07-11
*Thread moved to **General Help**.*

---

### Post by grahammechanical on 2014-07-11
For those, who like me do not know what the OP is talking about, it is this

[http://www.webupd8.org/2012/11/primus-better-performance-and-less.html](http://www.webupd8.org/2012/11/primus-better-performance-and-less.html)

> **Once installed, use "primusrun APP", to launch an application or game - this works just like the "optirun" command available in Bumblebee ("APP" is the application or game executable which you want to run using the Nvidia GPU).**

Why did you try to run Unity with the command "primusrun unity?" Unity is not an app. It is the user interface. We have to assume that you are getting to a desktop and we have to guess that you are using Ubuntu 14.04 because you give very little information about your machine. So, I may be guessing wrong.

Try Ctrl+Alt+T to get to a terminal and run these commands one after the other

```
dconf reset -f /org/compiz/
setsid unity
```

You may have to put "sudo" in front of those commands. May be not.

Regards.

---

### Post by deadflowr on 2014-07-11
If getting a terminal open with ctrl+alt+T, you might try first
ctrl+alt+F2 to get a console session going.
(You would log in like a graphical session, and from there enter the reset commands)
and if that fails, in a last effort the old REISUB method (I believe it goes likes this):
alt+shift+prntscrn + R + E + I + S + U + B
holding the alt shift and prntscrn buttons and slowwwly press ing the letter keys.
typically wait a second between pressing the letters.
(prntscrn should be the sys rq key.)
This command will run a safe shutdown and restart.
From there see how restarting runs.
Does it load as usual, or is the problem still there.
If still there, can you run those reset commands?

Good Luck

---


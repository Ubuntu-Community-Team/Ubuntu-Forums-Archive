---
title: "&quot;no saver status on root window&quot; error message from xscreensaver-command -time"
date: 2016-01-02
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2016-01-02
I'm using```
xscreensaver-command -time | grep 'locked'
```to check if the screensaver is locked in a script that runs in a visible (at least if the screen ISN'T locked), windowed terminal. Running with the screen not locked, it still seems to be working but I'm getting an error message that I'm pretty sure is new:```
no saver status on root window
```The only appearance of this phrase on the net I can find is in a python script used with mythtv. I don't speak python, but it looks to me like  the author is explicitly testing for that output from the same command:```
status = commands.getoutput("export DISPLAY=:0.0; sudo -u %s xscreensaver-command -time" % saveruser) verbose(VERBOSE_LEVEL.DEBUG, status) if status != "no saver status on root window": 
```

I checked with ```
ps -eo args | grep xscreensaver | grep -v grep
```and got```
xscreensaver -no-splash
```so xscreensaver IS running; and I further tested by locking the screen and that functions normally also.
So what does this mean?

---


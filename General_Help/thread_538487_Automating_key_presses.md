---
title: "Automating key presses"
date: 2007-08-30
forum: General Help
---

### Post by ~LoKe on 2007-08-30
I'd like to automate certain key-presses through a script that will run once my computer starts.  All I'd need to do is have this script send two simultaneous key-presses.

What would I need to do in order for this to happen?  Is there a command I could use that would do this?

---

### Post by praet on 2007-08-30
from this post: [http://ubuntuforums.org/showthread.php?t=527974](http://ubuntuforums.org/showthread.php?t=527974)

I think what you are looking for could be done in a bash script that calls a program to send keys like this:

```
xvkbd -text "string to type"
```

see:
[http://homepage3.nifty.com/tsato/xvkbd/#option](http://homepage3.nifty.com/tsato/xvkbd/#option)

You could also send individual keys/ combinations like this:
```
xsendkeys "a"
xsendkeys "Shift_L+a"
```
The first line sends the letter "a" while the second sends a capital "A".
From: [http://linux.die.net/man/8/xsendkeys](http://linux.die.net/man/8/xsendkeys)

---

### Post by ~LoKe on 2007-08-30
Perfect!  xsendkeys is **exactly** what I was looking for!  Thanks!

---


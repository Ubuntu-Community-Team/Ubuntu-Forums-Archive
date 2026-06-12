---
title: "Firefox won't start anymore..."
date: 2007-03-28
forum: General Help
---

### Post by Pikestaff on 2007-03-28
Hey guys... Firefox seems to have quit working on me; it doesn't start anymore.  The first few times I tried, I got Mozilla's Talkback Agent popping up on me, now that doesn't even show up anymore.  Trying to run Firefox from the terminal gets me this:

```
/opt/firefox/run-mozilla.sh: line 131:  5811 Segmentation fault      "$prog" ${1+"$@"}

```

The number before "Segmentation fault" is always a different number but it's always five-thousand-something.

I've tried "killall firefox" and rebooted a couple times but it didn't seem to help.

I honestly don't know what happened, it was working like normal and then I restarted my computer and it wouldn't work anymore.  I had just setup and configured SCIM if that has anything to do with it, but I don't know... I would appreciate any help.  Thanks!!

---

### Post by octavianh on 2007-03-28
Have you tried renaming your .mozilla folder in your home directory and restarting Firefox to see if that fixes it?

open a terminal

mv /home/[your username]/.mozilla mozilla.old

start firefox


If that doesn't work you can always delete the new folder firefox creates and move your old settings back.

---

### Post by Pikestaff on 2007-03-30
Reinstalling Firefox and getting an all new profile seems to have fixed it... thanks :)

---


---
title: "Zeitgeist not showing any results"
date: 2012-11-17
forum: General Help
---

### Post by aeronutt on 2012-11-17
Running Ubuntu 12.04, using gnome-shell; when I run gnome-activity-journal, there's no history.

"ps ax | grep zeit" reveals:

 3056 ?        Sl     0:00 /usr/bin/zeitgeist-daemon
 3062 ?        Sl     0:00 /usr/lib/zeitgeist/zeitgeist-fts
 3064 ?        Sl     0:00 zeitgeist-datahub
 3483 pts/1    S+     0:00 grep --color=auto zeit

So it looks like zeitgeist is running, but it appears to not be keeping a history of anything.

Any thoughts?

---

### Post by aeronutt on 2012-11-18
I still can't figure out what's up with zeitgeist. Same results in Unity as gnome-shell (which I didn't think would make a difference).

Anyone?

---

### Post by Habitual on 2012-11-18
> **aeronutt said:**
> ...So it looks like zeitgeist is running, but it appears to not be keeping a history of anything.

Any thoughts?

But I never got past this issue myself. The utility got me hooked and then took all the Zeitgeistaway from me.

I had this problem in Linux Mint 10 and OpenSUSE 11.4 and never did get it back the way I found it.

---

### Post by aeronutt on 2012-11-18
Well, I deleted the directory ~/.local/shared/zeitgeist, rebooted, and now all is well. Odd.

---

### Post by Habitual on 2012-11-19
Yes, I've done that in the past also, but the problem re-appears and then gets to the point where even deleting ~/.local/shared/zeitgeist doesn't help.

YMMV.

Glad it's working, for now!

---


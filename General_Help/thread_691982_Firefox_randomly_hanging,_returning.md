---
title: "Firefox randomly hanging, returning"
date: 2008-02-09
forum: General Help
---

### Post by EyeFlys on 2008-02-09
So I can use Firefox for a bit, and then it will randomly stop responding and the window will desaturate.  If I leave it, after maybe 20 seconds it will come back and be usable for maybe 5 seconds, then it will desaturate and stop respsonding again.  This then loops until I restart firefox.  This only very recently started happening after having Gutsy installed for about a month, I don't know what I could have done to make this happen.  Just wondered if anyone else is experiencing this annoying issue?

EDIT:
Ah, after a search for ```
DCOPClient::attachInternal. Attach failed Could not open network socket
``` I came across [this thread](http://ubuntuforums.org/showthread.php?t=380520) which lead me to running the 'dcopserver' command.  I did this in the middle of a freeze and it unfroze.  I'm therefore assuming this has fixed the issue.  I feel pretty silly now, having answered my own question :P.

---

### Post by EyeFlys on 2008-02-09
Aha, on running firefox from a terminal, this was revealed, appearing every time firefox freezes up.
```
DCOPClient::attachInternal. Attach failed Could not open network socket
```
Any ideas?

---

### Post by BrendanM on 2008-04-22
> **EyeFlys said:**
> Aha, on running firefox from a terminal, this was revealed, appearing every time firefox freezes up.
```
DCOPClient::attachInternal. Attach failed Could not open network socket
```
Any ideas?

Sorry, I don't have any ideas or suggestions, but I would like to say that I have run into this same issue. So you're not crazy and the problem is reproducible.

---


---
title: "Firefox %u.com help?"
date: 2007-12-23
forum: General Help
---

### Post by tenkabuto on 2007-12-23
I've been having the same problem as other users with my Firefox browsers opening up to "*[http://www.%u.com](http://www.%u.com)*" and I Googled it and found [this](http://ubuntuforums.org/showthread.php?t=528949) help request and it helped for the next two Firefox sessions, but now it's back at it. =/ I launch Firefox from a panel shortcut and have removed the "%u" from the command, as well as for the start menu listing, and it still happens, is there any way to correct it? It's not much of a problem, I just thought it would stop happening.

Oh, and I've been requesting tidbits of help quite a bit this week and I'd like to thank you guys for all of your excellent advice and support, you've got to be one of the *best* supporting community I've taken part in. :)

---

### Post by p_quarles on 2007-12-23
Check your home page settings under Edit >> Preferences >> Main (in Firefox). I vaguely recall running into the same problem, and I believe the issue was there.

If that doesn't fix it, try running Firefox straight from the terminal:
```
firefox &
```
If that changes it, it's possible that the "%u" argument is still set somewhere in your shortcuts.

---


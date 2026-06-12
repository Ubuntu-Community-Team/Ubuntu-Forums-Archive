---
title: "System freeze diagnosis"
date: 2007-10-26
forum: General Help
---

### Post by griblik on 2007-10-26
Hey all,

I've just installed gutsy, and my system always freezes not long after logging in (anywhere from a few minutes to half an hour). Usually I can still move the mouse at a frame or two a second, but nothing on the desktop responds. Ctrl+Alt+Backspace doesn't work either.

I have no idea how to track down the problem.

Last time, I left tail -f /var/log/messages running in a command prompt and the system resources monitor up in case anything showed up - everything looked normal. No unusual network traffic, both processors idling along, no memory usage spikes. The message log didn't show anything either.

Any suggestions as to where I could start? If I can work out where the problem is coming from, I'm sure there's going to be a forum thread somewhere about it.

Things I've tried:
[LIST]
[*]Thought it might have been firefox for a while, but same thing happens when FF's not running. Doesn't seem to be related to any specific app.
[*]Checking logs - no errors appearing anywhere.
[*]Memory test - nothing showed up.
[*]No errors in dmesg
[/LIST]

I'm running xubuntu 7.10 on a core2duo, 2 GB ram, nvidia 8800 GTS with restricted drivers enabled, dual head (2 x X windows config - couldn't get twinview to play nicely with different resolutions on different monitors)... erm, happy to post anything else that might help :)

Thanks in advance

G

---

### Post by griblik on 2007-10-26
Apologies, it appears the first step in problem diagnosis is to search the forums properly - doh!

Think this problem is the same one as described in this thread:
[http://ubuntuforums.org/showthread.php?t=412125&highlight=dual+display](http://ubuntuforums.org/showthread.php?t=412125&highlight=dual+display)

---


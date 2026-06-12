---
title: "Flash cause complete crash"
date: 2013-06-28
forum: General Help
---

### Post by achelis on 2013-06-28
Hi all,

I'm having issues on my Ubuntu 13.04 (x64) installation.

Sometimes when playing flash in Firefox the flash will suddenly get stuck (like a scratch in an old music CD) and just loop the same split second over and over (audio, not visual).
At this point mouse, keyboard becomes unresponsive. Graphics on screen are frozen.

I've tried the obvious ctrl-alt-f1 to get to a shell, but like I said, keyboard is unresponsive. Only thing that works is to hold in the power button for 5 seconds. 

This doesn't happen everytime, and I can go for a long time without any crash.

So, I guess my question(s) is(are):

1. Have anybody experienced the same (and maybe found a solution :)
2. Is there a log somewhere I can find/post/read that would hint at what is happening? 
3. Is there some way I can "sandbox" my flash process so even if that dies, my system doesn't die with it?
4. Suggestions in general are welcome :) - the problem is though, that it happens very irregularly (twice yesterday, none so far today, etc.)

I was sure I had more.. I will try and set up ssh and see if that dies as well or if it's only UI related stuff that's gone.


(oh, and the about: plugins page shows: )
```
Shockwave Flash

    File: libflashplayer.so
    Path: /usr/lib/flashplugin-installer/libflashplayer.so
    Version: 11,2,202,291
    State: Enabled
    Shockwave Flash 11.2 r202

MIME Type	Description	Suffixes
application/x-shockwave-flash	Shockwave Flash	swf
application/futuresplash	FutureSplash Player	spl
```

---

### Post by achelis on 2013-06-30
*Bump*

No one else has experienced this or know of what could be wrong?
It justed happened again and I looked through /var/log/syslog, but I couldn't really see anything that should be an error - but then, I don't know what I'm really looking for...

---

### Post by artscoop on 2013-07-09
> **achelis said:**
> *Bump*

No one else has experienced this or know of what could be wrong?
It justed happened again and I looked through /var/log/syslog, but I couldn't really see anything that should be an error - but then, I don't know what I'm really looking for...
This has just happened to me three times on the same page in Firefox 22 x64. Obviously, that page uses Flash, and the system always freezes when an item pops up on the page.
It has never happened until today.
I've found no log file with information related to this crash

---


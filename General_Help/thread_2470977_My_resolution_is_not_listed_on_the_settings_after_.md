---
title: "My resolution is not listed on the settings after I used XRANDR"
date: 2022-01-18
forum: General Help
---

### Post by sparex on 2022-01-18
Hello.

After using Xrandr on Ubuntu (latest version) to add a new resolution "**1366x768**", it is not listed on the settings.

I tried this command "**xrandr --output XWAYLAND0 --mode 1366x768**", it shows this error:

*  **[COLOR=#000000]X Error of failed request:  BadMatch (invalid parameter attributes)[/COLOR]******[COLOR=#000000]  Major opcode of failed request:  139 (RANDR)[/COLOR]***
***[COLOR=#000000]  Minor opcode of failed request:  7 (RRSetScreenSize)[/COLOR]***
***[COLOR=#000000]  Serial number of failed request:  22[/COLOR]***
[COLOR=#000000]***  Current serial number in output stream:  23***

[/COLOR]
I tried this with even some lower existing resolutions and it shows the same error.

NOTE: I've already added then used this resolution successfully in Manjaro.

THANKS IN ADVANCE :o

---

### Post by TheFu on 2022-01-19
I had some crazy idea that Wayland isn't supported by X programs. Is that not true?

Alternatives are: kanshi, wdisplays, wlr-randr

---

### Post by sparex on 2022-01-20
hey bro, can you please show me how to use one of them. I just moved up to linux.

---

### Post by TheFu on 2022-01-20
> **sparex said:**
> hey bro, can you please show me how to use one of them. I just moved up to linux.

Sorry. I haven't a clue. I don't use Wayland. It breaks some of my important workflows - or it did last time I checked - due to the lack of being a 100% drop in for X11.

You are on your own. I'd never heard of those programs before DDG'ing them to post in this thread.

---


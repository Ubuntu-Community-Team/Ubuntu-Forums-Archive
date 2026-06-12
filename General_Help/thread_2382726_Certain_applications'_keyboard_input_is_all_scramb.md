---
title: "Certain applications' keyboard input is all scrambled"
date: 2018-01-16
forum: General Help
---

### Post by goemonburo on 2018-01-16
I am noticing a weirdness when I run certain applications within VNC.  When I run them in a native display (:0, I presume?) they run fine.  

But when I run my VNC server on the same machine and connect (either from a different computer on my home network or from outside the system or to VNC viewer on the same machine), I see some garbled text when I try to type.

For instance, I'll hit the backspace 3 times and it might (just making it up), look like "//b//b//b" or something.  

One application that does this is Calibre.  I also notice that Telegram does this.

Not sure if it's connected, but I am also unable to input in Korean or Japanese inside VNC, even though I can do it fine on the native machine by hitting ctrl-space, then choosing the input.  In VNC, I hit cntl-space and can manipulate the input bar, yet nothing happens and I get no cursor change or hiragana pulldown options.

I believe this may be something to do with my VNC display settings, perhaps, or encodings that are not matching the native server?  If that's true, is there any way to make my .vnc config pull from the exact display setup that my desktop uses?

Thank you in advance for any and all help.  It's been tough to search for answers as I do not know the right keywords to use to search for.

---


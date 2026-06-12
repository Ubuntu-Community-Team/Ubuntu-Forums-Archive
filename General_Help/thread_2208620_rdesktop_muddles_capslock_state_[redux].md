---
title: "rdesktop muddles capslock state [redux]"
date: 2014-03-01
forum: General Help
---

### Post by bkline on 2014-03-01
Some time back, I posted a message about a problem I've experienced with rdesktop under Ubuntu.  The problem causes random characters I type to come out capitalized, as if I had the caps lock key on. Sometimes it's even so erratic that the state flips bAcK aNd fOrtH raNdoMLy while I'm typing. Doesn't happen with any other apps, so I'm pretty confident it's not a hardware problem. Anyone else experiencing this weirdness? 

I am still wrestling with the problem, which effectively blocks me from using Ubuntu for my work supporting Windows software for my customer remotely.  The only response I got to the original thread (to which I can no longer post, as the thread has been closed by the forum gods), said:

>  looks like a borked .local config; delete it and log out/in, it will be recreated with the good settings ...

I immediately wrote back showing that I had no config files in the ~/.local tree, and asked for clarification.  When I got no further reply, I asked again for any help available, but got nothing.

So I'm trying again.  Does anyone have any idea what the "borked .local config" reference might mean?  Does anyone have any clues about what's causing this problem or how to solve it?

I will provide one additional clue myself: when this happens I am often (but not always) working with nested RDP connections (in other words, I connect using rdesktop from my Ubuntu workstation to one customer server, and from within that session I make another RDP connection to a third machine).  This problem doesn't ever happen if I'm connecting from my Windows 7 system, no matter how deeply nested the connections are.  But I'd really rather do my work from the Ubuntu machine.  I just can't get any work done if I'm spending all day backspacing over what I type to fix the case of the typed letters.

---

### Post by bkline on 2014-04-22
Bump. I really would like an answer, please.

---


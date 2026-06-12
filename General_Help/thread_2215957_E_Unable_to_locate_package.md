---
title: "E: Unable to locate package"
date: 2014-04-09
forum: General Help
---

### Post by zane99 on 2014-04-09
I've seen many posts about this issue, but everything I've tried has not worked yet.
The main things I've tried are:
[LIST]
[*]sudo apt-get upgrade && sudo apt-get update 
[*]Restarting the computer 
[/LIST]
I have the OS on a LiveUSB that is recognized as a local disk (not fixable to my knowledge)
Any ideas as to what's happening?

---

### Post by steeldriver on 2014-04-09
Hello and welcome to the forums

Can you start by telling us what version of Ubuntu you are running, and what package(s) you are trying to install?

---

### Post by su:bhatta on 2014-04-09
Are you running a live session from the USB?
If so then spt-get update & apt-get upgrade will not work.

Or is the OS installed in the USB?

---

### Post by zane99 on 2014-04-09
Thanks for the warm welcome :p
I'm currently booting from Ubuntu 13.10 32-bit and this happens for all packages I try to install via Terminal.
I can install stuff through Ubuntu Software Center, but some of the stuff I want isn't in there.

Packages that give me an error so far:
[LIST]
[*]sudo apt-get install ubuntu-restricted-extras
[*]sudo apt-get install tree
[/LIST]

---

### Post by zane99 on 2014-04-09
I'm choosing the option: Try Ubuntu Without Installing
But I have a persistence file (built with Universal USB Installer) on the USB key so I can keep all my data and settings.

---

### Post by su:bhatta on 2014-04-09
**[SIZE=2][/SIZE]**[SIZE=2]oops,  please ignore[/SIZE][B][SIZE=2]
[/SIZE][/B]

---

### Post by zane99 on 2014-04-09
Didn't really help that much.
I know a lot about setting up and keeping storage, installing packages etc. on a LiveUSB.  I actually did have this setup working for a while until a friend ripped out the USB while it was running.
It's not that I don't know how to set it up, it's more that I'm having errors while running it.  I've been using Linux for almost a year now.

---

### Post by su:bhatta on 2014-04-09
Guessed as much, thats why, i edited my post. :)

Did you try redoing the USB thing again, after there was problems when it was ripped out while running?

---

### Post by zane99 on 2014-04-09
Yes, I did a fresh reinstall after formatting the USB key.
I did not redownload the .iso file though, but I don't see how that'd be a problem.

---

### Post by steeldriver on 2014-04-09
AFAIK there should be nothing to prevent adding packages to the live boot - even without persistence, although of course they wouldn't persist ;)

For the ubuntu-restricted-extras package, you first would need to enable the **multiverse **repository - either by adding it to your sources.list file manually and then running an apt-get update, or by checking the appropriate box under 'Edit --> Software Sources...' 

OTOH I don't know why 'tree' would not be found since that should be in **universe **- unless you only have the local 'CD-ROM' repository enabled?

---

### Post by zane99 on 2014-04-09
I'll try this and tell you what I get (I'm running Windows 8.1 at the moment so bare with me for the slow reply)

---

### Post by zane99 on 2014-04-09
I went into Software & Updates and checked the 'universe' one.
I don't know why I didn't have this enabled by default but now it's working!  Thanks so much for bringing this to my attention!  I think I can close this thread now.

---


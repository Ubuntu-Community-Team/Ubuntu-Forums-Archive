---
title: "Using an Ubuntu machine as a second screen?"
date: 2023-03-31
forum: General Help
---

### Post by dyingsun on 2023-03-31
Greetings all, just returning to the Linux world after a long absence and figuring out how to make it play nicely with all the new tech.

So when I'm working from home, I use a Windows PC, with a tiny netbook as my second screen. Not ideal, so when I inherited an older iMac, of course I wiped it and installed Ubuntu. I usually set up my netbook to allow my PC to cast to it, then run the VPN and remote desktop software and Bob's yer auntie, my two screens at the office are being duplicated at home. Is there a way I can achieve the same outcome using the imac/Ubuntu setup as the second screen? Don't seem to be able to find a way to do it - maybe I'm just using crappy search terms! If anyone has any suggestions, I'd be grateful to hear them!

Thanks :)

DS

---

### Post by ActionParsnip on 2023-03-31
Something like synergy will allow you to move the mouse pointer between the 2 systems and use both using one keyboard and mouse. You won't be able to drag application windows between the two systems though.

---

### Post by dyingsun on 2023-04-01
Thanks for the reply, might have a tinker with that and see what I can do with it!

---

### Post by HermanAB on 2023-04-01
See Barrier:
[https://ubuntuhandbook.org/index.php/2021/06/setup-barrier-share-mouse-keyboard-between-computers/amp/](https://ubuntuhandbook.org/index.php/2021/06/setup-barrier-share-mouse-keyboard-between-computers/amp/)

You can use SSH to run a program on one machine with the display on another machine.

So between Barrier and SSH, it is a matter of keeping track of where is the data and where is the computing power.  It can get kinda confusing, but it works well.

---

### Post by dyingsun on 2023-04-13
Thanks guys, much appreciated. Will see what I can come up with over the weekend :)

---


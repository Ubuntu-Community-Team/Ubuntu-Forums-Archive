---
title: "how to get newest edgy eft"
date: 2006-07-02
forum: General Help
---

### Post by oldmanstan on 2006-07-02
how do you get the latest compile or sources of edgy eft? just to try out, i'm not looking to get the sources unless that's the only way to install it at this point, i just want to take a peek and see what's goin on.

---

### Post by aysiu on 2006-07-02
You want breakage? Okay.

Edit your /etc/apt/sources.list
Change every *dapper* to *edgy*
```
sudo aptitude update
sudo aptitude dist-upgrade
``` Welcome to a broken system.

---

### Post by woedend on 2006-07-03
ah...dont be so negative.  its not ALWAYS broken...but more broken than dapper for sure(i still think breezy was the worst).  
I wouldnt recommend doing dist-upgrade but just upgrade...last time I used edgy dist-upgrade removed a bunch of important things.

---

### Post by aysiu on 2006-07-03
Well, it won't be broken all the time, but it will certainly be broken many times between now and October.

---

### Post by burzum on 2006-07-19
Hahaha, even Dapper actualy IS still broken for me!

It crashes all the time randomly. I've tried the open source and closed source nvidia driver, my memory is ok, its not overheating and overall - windows XP is running fine without ANY trouble...

I'll hope a newer kernel in edgy eft will do the trick to get it running if not i have to stay with windows.

[IMG]http://www.doomzone.de/bilder/linuxcrash.jpg[/IMG]

---


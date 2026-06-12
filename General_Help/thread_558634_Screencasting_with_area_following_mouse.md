---
title: "Screencasting with area following mouse"
date: 2007-09-24
forum: General Help
---

### Post by zed_at_uw on 2007-09-24
Hi,

I would like to make some screencasts on my ubuntu machine.
I've tried istanbul, gtk-recordmydesktop and xvidcap.

They all work without too many problems, but I've yet to find is a way that the recording area is following my mouse. Anyone know how to do this ?

Thx a lot,

Zeddicus

---

### Post by gautada on 2007-09-24
Not sure what you mean.  Are you trying to just record an area around your mouse?

---

### Post by zed_at_uw on 2007-09-24
Well,

what i do is setup a 640x480 area. no problem here.

What i would like to have is that it would follow my mouse. so if i move my mouse to to the upper right corner of my screen, the area i'm recording would follow. If i would like to show something on the lower left part of my screen, then the area would follow my mouse to to that part of my screen.

The thing is this way i could keep my screencast not to big and my text would still be very readable when viewing my screencast.

Hope this makes is clearer

---

### Post by gautada on 2007-09-25
I have looked into screencasts for a while now and I have not found anything that will do what you are describing.  I like the idea for solving the resolution and readability issues.  My best guess to get this ability would be to make a recording convert that recording to individual frames (a series of single images).  Then, write an algorithm to crop to the mouse as a center.  I know that is not what you want to here but it is at least possible.

---


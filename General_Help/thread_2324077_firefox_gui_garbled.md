---
title: "firefox gui garbled"
date: 2016-05-10
forum: General Help
---

### Post by jaarvidsen on 2016-05-10
i recently started having a problem with the firefox gui becoming garbled
see screenshot [http://i.imgur.com/dzySUlO.png](http://i.imgur.com/dzySUlO.png)

this  happens on my ultrabook, but not on my desktop computer. to be sure i  copied my firefox profile from the desktop to the ultrabook and it still  occurs on the ultrabook, but not the desktop even though they are  running the same firefox profile. ive also tried with a brand new  profile and no extensions but the same happens. it does not happen in thunderbird.

both computers are running ubuntu gnome 16.04 - the ultrabook using intel graphics, the desktop is proprietary nvidia. 

this *might* have occured ever since i installed 16.04, not sure because i havent used the ultrabook very much since then. i only noticed the other day after i cleaned some dust off the ultrabook keyboard so my dust cloth might have pressed some keys but i cant figure out what that might have been either

im pretty sure ive seen some screenshots years ago displaying something similar but i cant find anything

any help is appreciated :)

---

### Post by JonoBNZ on 2016-05-15
I've got a similar problem showing up at the moment, but in the content frame rather than the GUI.  I'm running Ubuntu Mate and it started happening straight away after the upgrade to 16.04, but never happened on 15.10.  This is on an Intel i5 NUC with Intel graphics.

Basically it's just the same deal, horizontal lines through images/text on the web pages.  On some pages it doesn't seem to happen at all, on others it happens a lot.  It looks almost like the segments where it happens, every 2nd line is offset to the right by 30-40 pixels or something.

No solution, just throwing another data point into the mix...

---

### Post by hvbakel on 2016-05-17
For what it's worth, I'm experiencing the same issue. Intel graphics as well with a hidpi display.

---

### Post by berte on 2016-06-02
Same issue here, horizontal glitches in Firefox 46.0.1.
Ubuntu 16.04, fresh install.
Asus UX305FA, hidpi 3200x1800, Intel® HD Graphics 5300 (Broadwell GT2)

I had no issue with Ubuntu 15.10 before.
No issue with Chromium 50.0.2661.102

---

### Post by berte on 2016-06-02
Example: [https://jpst.it/J5r3](https://jpst.it/J5r3)

(link updated)

---

### Post by berte on 2016-06-03
Hi,
Disabling smooth scrolling reduce the frequency of these glitches to almost zero (but still happening sometimes). Disabling hardware acceleration do not change anything.
Best

---

### Post by berte on 2016-06-12
Update to Firefox 47.0 and kernel 4.4.0-24 solved the issue :-)
Whether it was a Firefox bug or a kernel bug is still not clear...

---


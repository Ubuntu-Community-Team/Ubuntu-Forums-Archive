---
title: "[SOLVED] Firefox 2.0.0.11 painfully slow"
date: 2007-12-15
forum: General Help
---

### Post by djbon2112 on 2007-12-15
I seem to have all my graphics drivers and updates installed, but Firefox is painfully slow. Scrolling down pages is choppy, and it can take several seconds for a new tab to open up or to switch between tabs, or for an interaction to respond. Sites with lots of scripts (like Digg) are much worse. I only have two plugins (ABP and Noscript), but it was slow before installing these. Anyone have any ideas what might be causing this?

---

### Post by siciliancasanova on 2007-12-15
> **djbon2112 said:**
> I seem to have all my graphics drivers and updates installed, but Firefox is painfully slow. Scrolling down pages is choppy, and it can take several seconds for a new tab to open up or to switch between tabs, or for an interaction to respond. Sites with lots of scripts (like Digg) are much worse. I only have two plugins (ABP and Noscript), but it was slow before installing these. Anyone have any ideas what might be causing this?

Is your swap partition mounted?

---

### Post by djbon2112 on 2007-12-15
I don't know how to check, but I'd assume so because every other program seems to run fine.

---

### Post by berlinbrown on 2007-12-15
Firefox 2 sucks, I refuse to use it.  I went with Firefox Beta.  Only problem with Firefox beta is that I can't some of the plugins to work.  Eg, like some of the Flash videos.  So I have to use Opera for videos and FF3beta for normal browsing.

---

### Post by djbon2112 on 2007-12-15
> **djbon2112 said:**
> I don't know how to check, but I'd assume so because every other program seems to run fine.
Actually, come to think of it, a program I run in Wine all the time (Sibelius) also suffers the same problem: it's painfully slow to do basic things and I KNOW it should be faster. I was just chocking it up to Wine, but perhaps there's something going on here.

How does one check if their Swap partition is mounted?

---

### Post by rfruth on 2007-12-15
use the top command to check on swap - also tried a different Firefox (.mozilla) profile ? Firefox 2.x works fine 4 me

---

### Post by finferflu on 2007-12-15
I think it's how it's supposed to be, i.e. *slow* :P
I recently switched to Epiphany and then to Opera, since I couldn't stand Firefox anymore. I'm not even using Ubuntu, I'm on Arch, which is supposed to be ultra fast, i686 optimised, and Firefox is still too slow, and consumes too much RAM and CPU. I have tried the beta of version 3, and it seems quite an improvement. I really hope they reach the lightness of Opera. When using Firefox I was having headaches because of the fan spinning, now that I have ditched it my head can finally rest :P

---

### Post by djbon2112 on 2007-12-15
*smacks head on desk*

After I installed the Ubuntu Studio packages, it disabled restricted drivers, and hence my nVidia driver. >.< That was my problem.

Thanks though guys! Haha!

---

### Post by finferflu on 2007-12-15
Is it.. ahem.. fast.. and less resources consuming now? I'm curious now :P

---

### Post by djbon2112 on 2007-12-15
It is faster, but still crashes about half the time I load a Digg or Youtube page... *rolleyes

I was so good on Windows...

---

### Post by r-mo on 2007-12-15
I really hope things get better with firefox 3.  I want my lean, mean browsing machine back :(  Whatever happened to that philosophy of it's just a browser, add whatever extras you want through extensions?  I just want them to concentrate on rendering the pages and running the scripts quickly and correctly.

---

### Post by r-mo on 2007-12-15
> **djbon2112 said:**
> It is faster, but still crashes about half the time I load a Digg or Youtube page... *rolleyes

I was so good on Windows...

Digg is bad on windows firefox too, FF can't cope with the ajax they use on the comments. It's never crashed on me though just doesn't respond for a while...

Youtube crashes because adobe flash player is the suckiest thing that ever did suck.

---

### Post by berlinbrown on 2007-12-15
It is funny that most are in agreement on this.  You don't hear alot about FF2 sucking because I guess most people are using Firefox on Windows now.

Firefox 2.0.11 works fine on windows, but someone dropped the ball on the linux versions.  Too bad.

---

### Post by finferflu on 2007-12-16
> **berlinbrown said:**
> 
Firefox 2.0.11 works fine on windows, but someone dropped the ball on the linux versions.  Too bad.

Exactly, on the PCs I use at uni they have Windows with Firefox 2 and it works well, I can browse with peace of mind. On Linux it's a complete nightmare. It's a shame that Opera, being closed source, works better than Firefox on Linux. It's a case where a closed source product supports Linux better than an open source one.

---


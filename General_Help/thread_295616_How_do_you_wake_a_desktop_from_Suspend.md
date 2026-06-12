---
title: "How do you wake a desktop from Suspend?"
date: 2006-11-08
forum: General Help
---

### Post by lowracer on 2006-11-08
I have a home-brew Intel Core 2 Duo system with an Intel D975XBX motherboard, just built and installed Edgy last night (It worked right out of the box too, amazing!).  

Tried a Suspend to see if it worked, and the system quickly went dark and silent as expected, but then I wasn't able to wake it up.  On every other system I've used I would expect a mouse click or spacebar to wake the system up.  Neither of these actions had any effect on my new system in its suspended state.  Eventually I just hit the reset button and rebooted.  

Any clues?  I couldn't find documentation on this particular topic after a lengthy google search.

---

### Post by an.echte.trilingue on 2006-11-08
Betcha money its your video card.  What is it?

---

### Post by lowracer on 2006-11-08
Dang, that was fast.  This is my video card:

eVGA 256-P2-N554-AX e-Geforce 7600GT KO 256MB Dual DVI w/HDTV PCI Express x16

---

### Post by an.echte.trilingue on 2006-11-08
In general, suspend support in linux is not very good yet.  A quick google search for your card seems to indicate that you need suspend2 to get it to work.  (you tried the power button, right?) Basically you have three routes, as far as I know:

1. You can add the feisty repositories to your sources.list in for apt, (be sure to pin edgy's repositories higher than feisty's or you will mess up your install) and install kernel 2.6.18 when it hits the mirrors if it has not already with suspend2 compiled in.  This MIGHT work.  This MIGHT break other things.

2.  You can fetch the kernel source and suspend2 and recompile the kernel yourself.  This is more likely to work but hard to do if you don't know how and you have to recompile you kernel every time there is an update.

3.  Live without suspend.

I can help you with the first one but the second is over my head.  Before you go through this check the power button and everything possible to make sure that it is not working.  [This page]("http://www.linux.com/article.pl?sid=06/05/24/1716222") has some good background info.

Hope this helps and I hope somebody with a simpler solution posts!

---

### Post by lowracer on 2006-11-08
Thanks for the info.  I will give the power button a try to see if that works first.  Then I might try 2.6.18.

---

### Post by SnTholiday on 2006-11-09
Is there any difference between "sleep", which is an option in
Preferences-> Power management, and "suspend"?

---


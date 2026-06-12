---
title: "Compiz fusion + Old Intel Integrated graphics - SLOW SCROLLING"
date: 2008-04-28
forum: General Help
---

### Post by speaker219 on 2008-04-28
hi. I just installed ubuntu 8.04, and i have a fairly old intel card: 915 GM. The main problem i'm having is that in firefox, the scrolling is very slow. If compiz is turned off, it is speedy as usual, but as soon as it is turned back on, it becomes slow again. I really want to use compiz, and the part that really baffles me is that this was not a problem in the least on Ubuntu 7.10. On the same system, with compiz fusion enabled, the scrolling was perfect. Any ideas? I'd really appreciate it! This is probably the only major issue i'm having with hardy.
Note: This was a clean install, not an upgrade

---

### Post by Twitch6000 on 2008-04-29
This is odd I have a intel card that is just a bit higher then yours and runs just like it did on gusty.Ofcourse I did always have a few mess up install where it hated my card and didn't let me use compiz.Maybe reinstall and see what happens.

---

### Post by speaker219 on 2008-04-29
hmm, do you have the 945GM? weird. mine works fine with direct rendering and stuff but scrolling in firefox when compiz is enabled is just horridly slow. what driver are you using?

---

### Post by tigersrock on 2008-05-26
i have a 945gm and had slow scrolling in firefox with compiz. Opacity in the cube was the problem, using it at 100% solved my issue as posted [here]("http://ubuntuforums.org/showthread.php?t=785118")

---

### Post by spectrevk on 2008-06-07
I have a laptop with an ATI Radeon Xpress 200M, and I'm having the same problem with slow scrolling when I enable Compiz. All of the effects look smooth, but the scrolling is really slow. I thought maybe there was a scrolling speed setting in there somewhere, but so far I've had no luck in finding it.

---

### Post by Rocket2DMn on 2008-06-07
You may have xserver-xgl installed, but this can conflict when running Compiz.  Try removing it
```
sudo apt-get remove xserver-xgl
```
There are a number of threads and bug reports with slow scrolling in firefox, but there doesn't seem to be a fix-all solution.  Post back if you still have problems.

---

### Post by spectrevk on 2008-06-08
> **Rocket2DMn said:**
> You may have xserver-xgl installed, but this can conflict when running Compiz.  Try removing it
```
sudo apt-get remove xserver-xgl
```
There are a number of threads and bug reports with slow scrolling in firefox, but there doesn't seem to be a fix-all solution.  Post back if you still have problems.

Nope, it wasn't installed. :(

Guess I'm out of luck for now.

---

### Post by Rocket2DMn on 2008-06-08
Not necessarily.  However, rather than me listing a bunch of other links and other options to try, it would be faster if you actually ran the search yourself and tried some things that seem reasonable.  Here are a couple of google search queries that will turn up some useful results:
```
site:launchpad.net firefox slow scrolling compiz
site:ubuntuforums.org firefox slow scrolling compiz
```
Some relate to certain video drivers, others are more generic.  Good luck.

---

### Post by Tomatz on 2008-06-08
edit

---


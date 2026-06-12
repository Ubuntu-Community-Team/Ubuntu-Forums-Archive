---
title: "KDE3 + compiz-fusion = flicker"
date: 2008-07-06
forum: General Help
---

### Post by kian.tern on 2008-07-06
I want to make a switch (or at least to try to make a switch) to KDE3.
When I start compiz-fusion I get a lot of flicker when the menus are drawn. 
I've read somewhere that this is qt3 problem, but also I read a lot of ppl are using compiz+kde without any problems. 
Is there any workaround to this flickering? 
The video card is nVIDIA GeForce 7300 SE and the system is Hardy x86 with all the latest updates (this is my workstation at work, I didn't try this at home yet). 
Any help will appreciated.

---

### Post by kian.tern on 2008-07-07
Did some testing on my home machine
Hardy x64
Video Nvidia GeForce 8800GT.

I found that it's not flickering, but the effect of the opening  animation is doubled.
For example if I use the Fade effect for opening animation. The menu
starts to appear, in the middle the animation stops and starts again (with fast fade effect it looks like flickering) I've tried this with other effect and the result is same. I also tried to turn KDE native effects off but it didn't help either. The strange thing it happens only
with menus (right click/application menu etc.)
I didn't install kubuntu I had ubuntu installed then "apt-get install kde3 compiz-kde"
maybe I'm missing some package?

EDIT: Forgot to mention, window resize is extremely slow and jumpy.

---


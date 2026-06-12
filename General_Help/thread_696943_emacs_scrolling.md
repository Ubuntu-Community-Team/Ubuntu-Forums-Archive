---
title: "emacs scrolling"
date: 2008-02-14
forum: General Help
---

### Post by iislucas on 2008-02-14
I've found an odd thing about scrolling emacs in Ubuntu (7.10) and I can't tell if it's a recent emacs thing, or something special to ubuntu...

scrolling a little bit, slowly with the mouse wheel works as expected, but scrolling more seems to cause the scrolled amount to multiply. In other applications (firefox) the amount of movement between the mouse wheel and the amount scrolled is proportional (linear), but in emacs on ubuntu 7.10, it seems to be polynomial or exponential, or something that's certainly not linear! The same thing happens when holding down the up or down scrolling buttons on the scroll bar.

Is this some oddity in a message/event passing mechanism? or (I hope not) some feature of recent emacs...? It is really annoying...

Here's a simple way to see what I mean: 
1. open emacs with a largeish file.
2. hold down the down-arrow. Observe that it scrolls at a linear speed.
3. now double-click on the down-arrow, holding down the button on the second click. Observe that it scrolls much faster. Now try some random multiple fast clicking on the arrow and observe that scrolling now is pretty much random. 

Any workarounds? 

cheers,
lucas

---


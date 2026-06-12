---
title: "XGL / compiz - keyboard &amp; mouse issues"
date: 2006-11-02
forum: General Help
---

### Post by satinet on 2006-11-02
Hello,

I´ve installed the 64 bit version of ubuntu on my new pc.

I´ve also installed XGL and compiz - it seems to work okay.

However, if i add ¨xmodmap /usr/share/xmodmap/xmodmap.gb¨ to my config file (at start up) it screws things up - You have to hold the control key for the left mouse button to work normally.  If you go into keyboard settings and remove the default keyboard (british english in my case) and add it again, it stops the mouse behaviour.  however the keyboard still behaves very badly - i have to double press puncuation marks etc.  If i don´t double tap the aposotrophe key i get something like ¨it&#347;¨ rather than ¨it´s¨.  

Removing the ¨xmodmap /usr/share/xmodmap/xmodmap.gb¨ line solves the mouse problem, but not the keyboard problem.  can anyone help???  :confused:

EDIT - it´s only   ¨ and ´ that are affected. other keys work fine.... :(

---

### Post by sdyson on 2006-11-17
I have the exact same problem. I tried all variants of gb (gb, gb-102. gb-105) but none of them worked. I'm not sure whether it's a problem with my keyboard or with xmodmap.gb.

---

### Post by satinet on 2006-11-18
hi i descovered that the problem was gnome and still happened with XGL turned off. The simple solution was to select "restore defaults" in the keyboard preferences.

i think it was to do with gnome choosing a different key map to Xorg....

---

### Post by sdyson on 2006-11-18
I've examined xmodmap.gb and it doesn't seem to be set up for a British keyboard at all. For example Shift-3 should be £ but instead is mapped to +. By chance I looked in xmodmap.uk which as far as I know should be for the Ukraine but this seems to be mapped to a British keyboard since Shift-3 is mapped to £. I'm now running using xmodmap.uk and all seems to be working fine.

---


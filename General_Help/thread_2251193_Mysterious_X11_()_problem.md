---
title: "Mysterious X11 (?) problem"
date: 2014-11-02
forum: General Help
---

### Post by ulrichmuc on 2014-11-02
I experience the following problem with xfig, but I don't believe that it is a xfig problem:

In xfig, I draw a text and then I can move it around with the mouse (after going into move-mode). As I move the mouse, the text follows, 
until I hit the mouse button again. So far, so good. However, when I increase the text size to more than 24 points, this doesn't work anymore.
Picking the text in move mode, it just disapears. It comes back when I move the xfig-window, sometimes, when I just click into the desktop
outside any window. I hunted in xfig's source code, to no avial.
Finally I found a solution: When I hit CNTR ALT F1 to go to a text console and then CTRL ALT F7 to go back to graphics, from then on xfig behaves as expected: big texts follow the mouse.
Any ideas what causes this strange behaviour?

My system: Linux <hostname> 3.13.0-39-generic #66~precise1-Ubuntu SMP Wed Oct 29 09:59:20 UTC 2014 i686 i686 i386 GNU/Linux.
Hardware: Asus Eee PC

Cheers,

  ulrich

---

### Post by ulrichmuc on 2014-11-03
I now found out, that I get into the described state when the system is wakened up after a suspend.
So it might be a bug in the suspend/resume code.

ulrich

---


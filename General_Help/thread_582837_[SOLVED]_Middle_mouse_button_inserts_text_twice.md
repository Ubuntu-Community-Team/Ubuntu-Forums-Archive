---
title: "[SOLVED] Middle mouse button inserts text twice"
date: 2007-10-20
forum: General Help
---

### Post by popch on 2007-10-20
In Gnome you can highlight some text in one window and paste it into another one by klicking the middle mouse button. This is very quick and convenient for pasting things into the terminal window.

In Ubuntu the text is pasted ***twice*** - once on button down, then again on button up. This is a good thing overdone. It is neither convenient nor fast any more.

The problem appears to exist since edgy or even earlier. None of my installations did it properly so far.

Is there anything I can do to fix or circumvent  it? Or do I have to wait until some developer becomes aware of the 'feature'?

---

### Post by DoktorSeven on 2007-10-20
It works properly here.  It's possible that some misconfiguration could be sensing the middleclick twice and thus pasting twice -- maybe something odd in /etc/X11/xorg.conf with the mouse settings?

---

### Post by popch on 2007-10-21
Thanks to your feedback I had another look.

I now think it is actually a hardware problem: the mouse seems to send several clicks. Most times, it sends two, from time to time it also sends one or three. 

Perhaps I am just too clumsy to use a mouse?

Edit: Definitely a hardware problem. One press on mouse button sends several clicks (1..3)

---


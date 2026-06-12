---
title: "Gnome-shell floating text"
date: 2018-01-22
forum: General Help
---

### Post by shaligar on 2018-01-22
Hi!

I've just finished configuring Ubuntu 17.10 to my liking, and have found out a problem I can't solve: suddenly, the world 'NORMAL' in a huge pixelated font started showing up in the upper left corner of the screen right after boot. I don't know where does it come from, it is on top of all windows, and doesn't appear in screenshots. It only goes away if I logout and log in again, and only some times.

Can someone point me in the direction to solve it? It's quite annoying.

I'm using:

Ubuntu 17.10, gnome-shell 3.26.2
Nvidia drivers on XORG

If you need any more information, I will gladly provide it.

I attach a pic I took with my phone, as the text doesn't show in screenshots.

[ATTACH=CONFIG]278283[/ATTACH]

---

### Post by JasonFWard on 2018-01-22
From the font, my *guess* is that is the monitor doing that, which would also explain why it doesn't appear in screen shots.

---

### Post by shaligar on 2018-01-22
That's not it.

If I mouse over the text, it goes darker. Also, if I kill gnome-shell process, it goes away, along with the desktop icons.

The monitor has a very differnt HUD, with a smooth font and windows.

---

### Post by JasonFWard on 2018-01-22
See if your mouse goes under or over the text when you move your mouse to it.

If it goes over the top, then its for sure not the monitor, if it goes under then it almost certainly is.

Killing the gnome-shell will also change the mode your monitor is in, which in turn could stop the monitor showing the text (if that were the source).

---

### Post by shaligar on 2018-01-22
Mouse goes on top.  When I click, text darkens.

Killing gnome-shell doesn't change resolution as it doesn't close Xorg, only desktop and window decorator it seems.

---


---
title: "Change scroll bar behavior?"
date: 2015-04-22
forum: General Help
---

### Post by sgage on 2015-04-22
This query pertains to Gnome Shell: Is there any way to change the behavior of the vertical scroll bar so that when you click anywhere in the scroll bar below the 'thumb' it scrolls down one page, rather than to the position in the document corresponding to where you clicked? I find the current behavior rather annoying.

If there is any way to make the scroll bar a bit wider, I'd like to know that as well :-)

TIA...

---

### Post by sgage on 2015-04-22
I finally searched out the solution:

You have to create a file in ~/.config/gtk-3.0 called 'session.ini' (if it doesn't exist already - it didn't in my case), and put the following text in there:

[Settings]
gtk-primary-button-warps-slider = false

After you log out/in, scroll bar behavior is as I prefer it.

[edit: Upon further testing this only seems to work for a few programs...]

---


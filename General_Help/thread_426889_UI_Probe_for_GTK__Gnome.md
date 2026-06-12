---
title: "UI Probe for GTK / Gnome?"
date: 2007-04-28
forum: General Help
---

### Post by Mr. Picklesworth on 2007-04-28
Back when I thought Windows' GUI was good (I've learned since then, I promise!), I used a program called [Windowse](http://www.greatis.com/delphicb/windowse/) to find out all sorts of information regarding how an application's native UI is set up. It listed the style for a particular UI widget as well as any children or parents, among other things.

It was a *fantastic* learning tool, as it helped me to figure out how the pros did it (or didn't; the lazy oafs). It also works well to manipulate programs :)

Since I am just now learning my way around developing for Gnome, I can see that such a tool (except for GTK instead of Windows' UI) would be hugely useful! Is there anything like that around?

---

### Post by jpeddicord on 2007-04-30
Have you ever used Glade? It is a GUI designer, but if you know your away around your system, you can inspect (and even edit) UI files. Just do a search on your system for *.glade, and any applications that use it will appear. From there, open the .glade file, where you can view and edit the tree, move widgets, etc.

Keep in mind that GTK uses containers (kind of like HTML) instead of fixed positions like the Windows GDI+ system.

Jacob

UAResolved

---

### Post by Mr. Picklesworth on 2007-04-30
Yes, I do use Glade. (It's quite cool!). It definitely helped to teach me the wonderful (easy and accessible) ways of GTK.
I can't think of any examples off the top of my head, but there are just some cases where a UI probe comes in really handy.

---

### Post by Mr. Picklesworth on 2007-05-14
Okay, if anyone comes across this looking for the same thing as me, I have come accross two solutions for Gnome: [Accerciser](http://live.gnome.org/Accerciser) and at-poke. (at-poke is currently in the Ubuntu repos).

---


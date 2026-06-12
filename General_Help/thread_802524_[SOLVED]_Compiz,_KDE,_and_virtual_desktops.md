---
title: "[SOLVED] Compiz, KDE, and virtual desktops"
date: 2008-05-21
forum: General Help
---

### Post by ChompTheMan on 2008-05-21
I'm using 8.04 with KDE 3.5.  I'm am having a bit of a problem with virtual desktop behaviour.  I seem to have 4 desktops, but my pager acts quirky.  When I switch to another desktop the window thumbnail disappears from the previous desktop and when I open something the window thumbnail appears in desktop 1.  It doesn't matter what desktop it's on it only displays the window thumbnail on desktop 1.  All the other desktops are labelled desktop 1.  When I hover over the first desktop it lists all open apps under desktop 1, despite which desktop they're on.

In the CCSM general options I can't change the number of dekstops but I can change the number of horizontal and vertical virtual size.  Anyone know how I can fix this?

---

### Post by russo.mic on 2008-05-21
Did you install the compiz desktop pager?  the problem lies in the way kdm and compiz talk.  Compiz only "sees" and uses one desktop.  the package is called kicker-compiz.  

Russo

---

### Post by ChompTheMan on 2008-05-21
Yes, I have kicker-compiz installed.  Thanks for the reply.

---

### Post by ChompTheMan on 2008-05-24
Well, I've just installed AWN and, oddly enough, my pager now works(though it still displays each desktop as "desktop 1").  I've had a look through the dependancies but can't figure out which one, if any, just magically fixed my pager issue.

I guess I should also mention I installed the base system with the alternate cd then installed x-window-system-core and kde-core.  Can anyone explain this to me?

---

### Post by ChompTheMan on 2008-05-24
I uninstalled AWN, I don't like it and it doesn't play nice with KDE.  I then discovered that I need to add 'Desktop Preview & Pager - Compiz' and not the normal pager.  I didn't realize this before.  I suppose this is solved now.  I'd like to thank myself :-P

---


---
title: "Weird crashes and hungs with 8.04"
date: 2008-05-01
forum: General Help
---

### Post by chrismfz on 2008-05-01
Hello,
I recently installed 8.04 on a HP 500 laptop
(pentium M with ipw2200 for network and intel's i915gm for graphics)

Very often (everyday) every application with no reason,
hung for a while (2-3 secs) then it goes black for a 20-30seconds period
only the application/window which hunged and after this time (20-30 seconds)
its ok back to normal.

This happens in every application and the rest of the system is ok
(I can minimize the "hunged" window and do something else)

For example, writing this post, firefox hunged twice in just a few minutes
without having something else running.


First, I thought that it might something wrong with the graphics card
or driver. So I have searched over the net about i915 and found some other stuff like the i810 driver, or the 915resolution etc.
I tried to play around with theese but nothing worked. The same weird hungs...

Not only firefox hungs but everything. From the top menu when I
access a subcategory and it hungs for 30 secs aprox. to totem, firefox, thunderbird, vlc, even the virtual console from gnome..

They just hung for a while and then they suddenly goes live again...

edit: Firefox finally hunged 4 times till I finish this post. Very annoying...

Please help... :(

Regards,
Chris

---

### Post by TeoBigusGeekus on 2008-05-01
How much ram do you have?

---

### Post by chrismfz on 2008-05-01
Yes sorry, I forgot to mention that. I had 512 ram initially
and I thought that the crashes/hungs was from lack of RAM.
(a free -m then showed me about 5-15 mb RAM average free.)
I bought a 1GB module (Transcend Jetram) and I have now average 450-550 Free RAM.
So, I believe this isn't a ram problem...

edit: I now have total 1GB (not 1.5) ram because hp 500 has only one slot for ram mudule

---

### Post by TeoBigusGeekus on 2008-05-01
Whenever this happens, go to System Monitor, tab Processes and check which particular application causes the overload in the cpu or ram. 
It might be that when you use firefox, firefox is the culprit, or when you use evolution, evolution causes the overload, but it could be something else, common in all these applications.

---


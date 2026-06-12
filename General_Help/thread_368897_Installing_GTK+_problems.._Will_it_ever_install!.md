---
title: "Installing GTK+ problems.. Will it ever install?!?"
date: 2007-02-23
forum: General Help
---

### Post by Nectron on 2007-02-23
I've been trying to install gtk for three nights, but the issue just keeps getting more and more complicated..

I'm trying to install it from source. Why? Cause there's no other way, and I can't install Edgy because I've already installed more than 40 packages of the software I need on Dapper.

I only need to get ATK then Pango installed, and gtk should be ok after that.

ATK requires GLIB, but I need a newer version than the one I have..

- How can I remove ALL old glib files before I compile a newer one from source?

I really need to work on this with your help step by step.. I have many packages left that depend on GTK, and its's become impossible for me to do it alone now.

Thanks in advance,

---

### Post by Nectron on 2007-02-24
This is really important guys..

I hope someone of interest to solve this would pass by this thread..

---

### Post by ShackledMystic on 2007-03-05
Look buddy its a messy messy affair 


trust me -- i came here to look for answers -- but it seems u need answers urself :p

to install gtk properly -- u need libtiff n libjpeg 

google to get their latest versions 

when installin libjpeg use the line :

./configure --prefix=/usr --enable-static --enable-shared

n tat shud clear the way for most o the issues 



BUT i get a message while installin GTK tat "x development libraries " not found


im yet to find a solution to tat -- do send me the solution if u get one ? 

PEACE

---


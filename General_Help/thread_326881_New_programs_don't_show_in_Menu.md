---
title: "New programs don't show in Menu"
date: 2006-12-28
forum: General Help
---

### Post by lift_test on 2006-12-28
Have added a couple of programs, one via Synaptic (Eagle PCB program) this runs on installation but I can find no trace thereafter.  The other is Real Player, installed from downloaded binary.  This can be accessed if I try to use it to listen to the radio in Firefox.  Won't work embedded but works stand alone!

I've tried using Alacarte to attempt to tick the unticked items ie Debian, Applications and Other in the hope that missing programs come into one of these categories.  However Alacarte will not tick/untick the boxes.  A single click does nothing and a double click brings up a dialogue box where the name and comment can be altered.  

Or do I have to wait until there is an R in the month?

---

### Post by bruenig on 2006-12-28
> **lift_test said:**
> Have added a couple of programs, one via Synaptic (Eagle PCB program) this runs on installation but I can find no trace thereafter.  The other is Real Player, installed from downloaded binary.  This can be accessed if I try to use it to listen to the radio in Firefox.  Won't work embedded but works stand alone!

I've tried using Alacarte to attempt to tick the unticked items ie Debian, Applications and Other in the hope that missing programs come into one of these categories.  However Alacarte will not tick/untick the boxes.  A single click does nothing and a double click brings up a dialogue box where the name and comment can be altered.  

Or do I have to wait until there is an R in the month?

First, on some of these programs make sure they aren't command line only programs because those won't be in the menus. As far as real player is concerned, unless whatever script you used to install it decided to create a menu entry, it won't be there. You will need to do it yourself. The menu entries are located in /usr/share/applications/ you should be able to open one of those up with a text editor and figure out the setup, pretty self explanatory. I would suggest opening up one that is in the same part of the menu you want real player to go in, and then just changing it a bit as far as name and such are concerned.

---


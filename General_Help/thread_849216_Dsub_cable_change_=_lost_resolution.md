---
title: "Dsub cable change = lost resolution"
date: 2008-07-04
forum: General Help
---

### Post by pcjunkie on 2008-07-04
I recently installed ubuntu using a dsub cable for the monitor. I had to use another monitor for 4 days (same resolution) using DVI cable. Now I have changed it back to Dsub (this monitor only has Dsub) the things gone nuts.

The loading screen is the correct resolution
The log in screen is so zoomed in I cant see what I am typing. It out of the window
And now even though the card setting is stating 1680x1050 the highest I can set it is 1400x1050

This is totally nuts~ A simple cable change and Ubuntu freaks out like it does a dummy spit?

Both monitors are 1680x1050/
One PC has a different mobo same GFX card. would not detect the monitor on Dsub, have to use DVI.

The PC in question is an older AMD / Nvidia Mobo. Same 7800 gt GFX card did detect resolution on Dsub installing. Changed cable for a moment. now resolution is lost and I can't get it back.

Does this mean that I have to re-install Ubuntu for the sake of a flipping monitor cable? Insane~ 

 

> sudo apt-get install nvidia-settings

Solved it but not really

The problem of a cable change trashing the x server configuration is bad form. Newbies will see that, freak out and run as fast as they can...
Nvidia settings should go with the driver IMHO

---


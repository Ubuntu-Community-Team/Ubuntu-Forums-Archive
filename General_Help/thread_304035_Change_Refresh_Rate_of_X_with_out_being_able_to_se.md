---
title: "Change Refresh Rate of X with out being able to see screen"
date: 2006-11-21
forum: General Help
---

### Post by jon_z on 2006-11-21
Just upgraded to edgy but it changed the refresh rates of my drivers, normally my computer boots without being able to see the bootscreen, thats fine, i have no problems, but it changed my X refresh rates.  Any commands to change my refresh rate from 59 to 60? vveeeerrryyyy picky LCD screen.

thank you.

---

### Post by wongdai on 2006-11-21
If you open a terminal, and type this...

sudo dpkg-reconfigure xserver-xorg 

It will take you through a series of prompts, one of which allows you to change your refresh rate.

---

### Post by jon_z on 2006-11-21
I cant see anything on the screen in the console.. I can't remember the exact command, but there is one to set X11 to use fglrx instead of ati. without going through the steps.  Anything like that for refresh rate?

---


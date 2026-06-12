---
title: "Mouse freeze problem"
date: 2013-01-22
forum: General Help
---

### Post by Crazy K on 2013-01-22
I recently got a used computer from my Aunt and it currently has a little under a gig of RAM. Anyways I noticed a lot of the time that when I'm doing something, my mouse will freeze in the closing fist cursor. 

It keeps doing this to me, and it's getting on my nerves. I have to force shut-down on my PC. I use a regular USB Optical Mouse. I'm not on a laptop (I checked this issue out and it happened to people with laptops). 

Anyways is there anything I can do to fix this problem? Like maybe get control of my mouse back? Everything is still working on my PC. I can move the cursor, but I cannot click, move, and so on. 

I just want to know if there's something I can do to fix this? Because I don't want to end up breaking my computer for shutting it down every time it happens.

---

### Post by Crazy K on 2013-01-23
Can anyone help me out with this problem? Also I'm guessing this is in the wrong area, so please move it to the correct one.

---

### Post by kridybel on 2013-02-26
UP.

I have a similar problem. I work on asus EEE pc 1011 px. When an external usb optical mouse is connected it works for a couple of days. Then all of a sudden the next start up the mouse works for a couple of minutes and then shuts down (the laser tracking stops and everything). Re-plugging the mouse helps, but it is not something I like to do every 2 minutes. The trackpad of the eee pc keeps working normally. I have this problem now with 2 mice. With last mouse the problem started after yesterdays' kernel upgrade.

---

### Post by kridybel on 2013-02-26
I just found out that my mouse external mouse problem was caused by laptop-mode-tools. Which I have installed separately earlier.


Anyway it won't hurt to do:
```
sudo apt-get remove laptop-mode-tools
```

But then again I doubt if that would solve your problem.

---


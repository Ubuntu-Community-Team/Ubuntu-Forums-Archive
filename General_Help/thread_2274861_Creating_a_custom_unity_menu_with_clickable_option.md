---
title: "Creating a custom unity menu with clickable options"
date: 2015-04-22
forum: General Help
---

### Post by dylan16 on 2015-04-22
I have an Acer 2 in 1 touchscreen computer, and I want to be able to use it as a tablet sometimes.  I made a script to disable keyboard/mouse and rotate screen, but I can't seem to find whatever device controls the screen orientation.  My solution is to have a unity drop down menu from the indicator area (like the WiFi one or the battery one) that just has 2 options: Touch Mode and Laptop Mode.  These options would be bound to something that would execute my scripts.  Problem is, I don't know how to make a indicator.  I know it should be possible, but I have only ever programmed in Java and TI-84 language, so I have a hard time wrapping my head around the python scripts that I found.  Is there any other way (bash script/java) that I could make an indicator?

---

### Post by kerry_s on 2015-04-22
i don't know about indicator, but you can use menulibre to create a launcher with a action button for other options. do you hold the touch for right click ?

you should look at ubuntu next, it's made for touchscreen.
[http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/)

---

### Post by dylan16 on 2015-04-22
I'm reluctant to use Ubuntu Next for two reasons: it's a nightly build of 15.04, and while I enjoy breaking things, I think that Next will have too much brokenness for my liking.  Two, it's made for touchscreens, and I want to be able to switch between using just the touchscreen and using the traditional keyboard/touchpad, although now that I think of it, it probbably shouldn't be too hard to get a normal X11 mouse on the touchscreen... right?

---

### Post by dylan16 on 2015-04-23
I ended up making a custom .desktop file in /usr/share/applications and adding it to the launcher, binding it to my scripts that disable/enable the keyboard and mouse.  I tried Ubuntu Next, but the browser wouldn't start and it thought that I had a 3G antenna plugged in.

---


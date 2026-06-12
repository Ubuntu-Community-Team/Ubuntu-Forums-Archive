---
title: "Why must I start gnome-settings-daemon explicitly??"
date: 2007-03-14
forum: General Help
---

### Post by fsando on 2007-03-14
(I've posted and bumped [over there]("http://www.ubuntuforums.org/showthread.php?p=2292802#post2292802") so I'll try here in stead).
This only happens in xgl-session (with or without Beryl) not in normal gnome session.
It started a few days ago after I'd done various things: I changed the screen resolution, then changed it back. I installed some extra fonts through Synaptics (I don't know if this is significant or not). After that Application font was far too big (14pt in stead of 10pt) any change through the menu (**System > Preferences > Fonts**) had no effect. All other font settings could be changed like before - only Application Font were unaffected.

I went through the forum and found that starting 'gnome-settings-daemon' explicitly would make the system responsive to changes to Application Font. I have put this in the startup menu so it is started automatically together with Beryl/xgl. Now the panel font looks as before (or perhaps nearly as before, though it's hard to tell). 

But there are still problems:
Fonts in applications do respond to changes but do still not look quite as before (as if a different font - bigger and bolder), window decorator is not always loaded, applications are generally slower to load, they are more often not loaded properly (the window does not show but the process is listed), htere is more load on the processor. 
In short: things are not quite right.

I believe that the way I start 'gnome-settings-daemon' is not the right way but what else can I do? I have no idea what is going on.

What I would like to know:
1) Is there a genuine solution to my problem?
Additionally:
2) What is the correct way to get 'gnome-settings-daemon' started?
3) Where do the panel (and the applications) get their default font settings from?
4) Where are the changes made through the menu stored?
I tried to find the settings by changing them and then searching for recently changed files without success.
Thanks in advance for any pointers.

---

### Post by fsando on 2007-03-15
Bump?

---

### Post by fsando on 2007-03-16
Bump 2! 

Anyone got an idea?

Has this issue to do with dbus? I have no idea what dbus is or what it does but I've seen dbus mentioned several times in connection with similar issues. Maybe my problems stems from dbus not properly starting for some reason - or perhaps dbus is expected to start gnome-settings-daemon but does not do that any more?

---

### Post by fsando on 2007-03-17
Bump, bump, bump!

---

### Post by fsando on 2007-03-18
Bump, bump, bump, bump! 

Feels a bit lonely in here :-({|=

---


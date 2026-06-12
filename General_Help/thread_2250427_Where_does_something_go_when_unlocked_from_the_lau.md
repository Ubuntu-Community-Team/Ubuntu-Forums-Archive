---
title: "Where does something go when unlocked from the launcher?"
date: 2014-10-28
forum: General Help
---

### Post by michael-piziak on 2014-10-28
I unlocked a game from my launcher, thinking the icon would show up on the desktop, but it didn't.  Where would the game be in my folders ?

p.s. Using Ubuntu 12.04 lts

---

### Post by CaptainMark on 2014-10-28
You can still type it into the dash (menu) to find it, you can also drag it back to the launcher to re-pin it.

---

### Post by deadflowr on 2014-10-28
I think 12.04 still had the ability to drag the icon from the dash, directly onto the desktop, if you want.
(You can't drag it from the launcher to the desktop, though, from what I remember(I'm not on my main machine now, so can't confirm)

and where inside the folders depends on where/how you installed it.
Most applications, games included, have launchers inside /usr/share/applications.
This, and a folder in the home directory called ~/.local/share/applications, is where the system looks for the launchers and applications on the system.

---

### Post by michael-piziak on 2014-11-01
I would still like to know how I can drag someting from the Launcher and place it on the desktop.  I installed 2 emulators and I want to store them somewhere besides the dock.

---

### Post by deadflowr on 2014-11-01
On 14.04 and beyond, look in the place I mentioned, using the nautilus(Files) and find the .desktop file for the application you want. Then you need to copy them from that location, and then paste it into the folder in you home directory called Desktop.
Not ideal, but it works
 I forget, but sometime between 12.04 and 14.04 drag and drop from the dash to the desktop broke.I'm also not sure if it is a feature or a bug, but seems far more like a feature.In which case don't expect it to be fixed.


ftr, I can confirm that in 12.04 if you try dragging the launcher from the launcher dock/side-bar/panel/thingy onto the desktop, it'll simply slingshot back onto the dock/thingy. Comically.

---

### Post by michael-piziak on 2014-11-02
Using nautilus, what exactly do I type in to get to the .desktop file for the application I want to copy and paste ?

I typed in desktop and .desktop but couldn't find it.

---

### Post by buzzingrobot on 2014-11-02
They're in /usr/share/applications.

---

### Post by michael-piziak on 2014-11-02
Thanks, found it.

---


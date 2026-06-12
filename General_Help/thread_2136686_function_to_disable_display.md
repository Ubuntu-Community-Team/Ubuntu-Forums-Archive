---
title: "function to disable display?"
date: 2013-04-18
forum: General Help
---

### Post by lightsaberlesbian on 2013-04-18
I like to use my computer before bed to listen to music/audiobooks but I would like to have a way of using Kubuntu without having an active display unless I actually require so.  Is there a way to attach a shortcut to disabling the display?

---

### Post by AmbiguousOutlier on 2013-04-18
Sounds like you could do with a screensaver, never really used one myself on Ubuntu but there seems to be a few options in Google.

---

### Post by lightsaberlesbian on 2013-04-18
You're right. I guess I was hoping for a more convenient and command line based answer that didn't involve opening the menu and adjusting the time and settings every night.  But that's not too bad really.

---

### Post by AmbiguousOutlier on 2013-04-18
Apparently Ctrl+Alt+L starts the screensaver, not at my Ubuntu machine to test it though

---

### Post by rnerwein on 2013-04-18
hi
i have an icon (pause.desktop) to start the screensaver with a klick: /usr/bin/xdg-screensaver activate
ciao

---

### Post by lightsaberlesbian on 2013-04-18
awesome script.  i don't know what kclick is but I'll make an sh out of it.  unfortunately it activates the "locked screen" b/c that's what I want as my default screensaver.  I'll just change it to blank screen and try to accept if someone gets on my laptop while I'm away they're just reducing their karma in life.

---

### Post by Habitual on 2013-04-18
Think that a translation issue, I think any shortcut you create for the Screensaver may perhaps have this command: /usr/bin/xdg-screensaver activate
Have a great Day and let us know...

---

### Post by lightsaberlesbian on 2013-04-19
works great thanks

---

### Post by lightsaberlesbian on 2013-04-19
I guess while we're on the same topic does anyone know how to make a shortcut for sleeping the computer? I know the command is "sudo pm-suspend" but making a script for that doesn't work.

---

### Post by lightsaberlesbian on 2013-04-19
Also. I tried to change my screen saver .."screen locker" in kde to a blank screen but activating the screensaver still only "locks" the screen without turning off the display

---


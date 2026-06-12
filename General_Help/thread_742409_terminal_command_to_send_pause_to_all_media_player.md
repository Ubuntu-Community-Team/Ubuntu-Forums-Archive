---
title: "terminal command to send pause to all media players like in &amp;amp;quot;keyboard shortc"
date: 2008-04-01
forum: General Help
---

### Post by duncan.hawthorne on 2008-04-01
does anyone know of one?
for each program i can work out the pause command (like "mpc pause" for mpd) but the command given when you press the keybaord shortcut assigned in "keyboard shortcuts" pauses all media players. 
how can achieve the same command from the terminal (so that i could eventually put it into a script)
of course, i want this not just for pause, but vol up, vol down, skip forward skip back, etc. are these things possible

Ideally, i want to make a progam that when run i can use my wireless mouse as a media player control, by mapping different button presses to different media commands (by using xev and grep etc). 
for example 
middle mouse button = play/pause
left mouse button = previous track (hold button for skip back)
right mouse button = next track (hold button for skip back)
scroll up = volume up
scroll down = volume down

Anyone know of a better way to do this, or a program existing already to do it?

Perhaps i could achieve the same thing by temporarily changing the keyboard shortcut for pause to say "mouse button 3". This is not possible to set in the gui, as it is looking for KEYBOARD shortcuts. Is there anyway to do this?

---

### Post by pointone on 2008-04-01
```
/etc/acpi/volupbtn.sh
/etc/acpi/voldownbtn.sh
/etc/acpi/playbtn.sh
/etc/acpi/stopbtn.sh
/etc/acpi/nextbtn.sh
/etc/acpi/prevbtn.sh
```

... and so on... 

The names should be fairly self-explanatory.

Run as root.

---

### Post by duncan.hawthorne on 2008-04-01
awesome, thanks :D

---

### Post by duncan.hawthorne on 2008-04-03
looking futher....
there is no script in /etc/acpi for toggle play/pause. you can pause, but you cant start again. any ideas? 
the script /etc/acpi/playbtn.sh doesnt do anything (well anything that i can work out)
i would ideally like a script that did toggling of play pause so that my script doesnt have to work out the current state

EDIT: just tried this on a hardy heron computer and /etc/acpi/playbtn.sh does the toggling like i wanted. maybe gutsy has a bug, or i've broken something. difficult to tell

one more question....
is there any way to do this with requiring root permission? i'm guessing the keyboard shortcuts run without root permissions, you are controlling non root permision owned media players after all

thanks if you can help :)

---


---
title: "Screensavers don't work after the computer is running for a while"
date: 2007-01-18
forum: General Help
---

### Post by statictonic on 2007-01-18
The first couple of times i walk away from my computer or lock it screensavers show up just fine, after that I just get a blank screen screensaver.  I'm using gnome on Edgy, I have this problem on multiple computers, anyone know a solution?

---

### Post by tronica on 2007-01-18
make sure you don't have the screensaver set on random. to choose a new one each time.

---

### Post by statictonic on 2007-01-18
It is not set on random, currently it's set to GLMatrix.

---

### Post by tronica on 2007-01-18
it works for me. Do you have the correct video card drivers installed.

---

### Post by statictonic on 2007-01-18
I have the nvidia binary drivers installed, and they work just fine, I also have this problem on my laptop which happens to use an ATI video card, so I'm not really sure what's happening here.

nvidia driver 1.0-8776

---

### Post by tronica on 2007-01-18
if you preview it does it work

---

### Post by tribble222 on 2007-01-18
This sounds like the problem I was experiencing.  It appears it's a bug in gnome.  I followed the solution given in post #42 here ([_http://www.ubuntuforums.org/showthread.php?t=288651&page=5_]("http://www.ubuntuforums.org/showthread.php?t=288651&page=5")) and it solved my problem.  Read posts #43 and #45 first for minor corrections to the instructions in post #42.

---

### Post by medley on 2007-01-18
> **tribble222 said:**
> This sounds like the problem I was experiencing.  It appears it's a bug in gnome.  I followed the solution given in post #42 here ([_http://www.ubuntuforums.org/showthread.php?t=288651&page=5_]("http://www.ubuntuforums.org/showthread.php?t=288651&page=5")) and it solved my problem.  Read posts #43 and #45 first for minor corrections to the instructions in post #42.

I have virtually the same problem using an NVidia card and KDE. I try to use GL screensavers, and when I walk away from my system the screensaver is doing its thing,  but at some point over night, the screen saver stops animating. The screen appears 'frozen' although moving the mouse or touching the keyboard brings me back to the desktop. I have a theory that it is related to interaction with ACPI (power saving), which I also have enabled to come on after a few hours. My guess is that when ACPI tells the monitor to go to sleep, the screensaver freezes and the monitor doesn't go dark.

But that's just my theory, and I haven't taken the time to prove it. Power saving does work with the screen saver(s) disabled, and that's really more important to me that fancy 'wow' type screen animations.

Take it for what it's worth.

Phil

---

### Post by Lil_Eagle on 2007-01-30
> I have virtually the same problem using an NVidia card and KDE. I try to use GL screensavers, and when I walk away from my system the screensaver is doing its thing, but at some point over night, the screen saver stops animating. The screen appears 'frozen' although moving the mouse or touching the keyboard brings me back to the desktop. I have a theory that it is related to interaction with ACPI (power saving), which I also have enabled to come on after a few hours. My guess is that when ACPI tells the monitor to go to sleep, the screensaver freezes and the monitor doesn't go dark.
I think you're on the right track.  It happens occasionally on my KDE system as well.  I'll play around with the ACPI settings and see what happens.  I do know on this compaq computer if I disable the ACPI in the kernel, I run into all sorts of other problems.  You can be assured the next computer I buy will not be one of the name brands unless it comes pre-installed with Linux.

---

### Post by teknosexual on 2007-05-21
> **tribble222 said:**
> This sounds like the problem I was experiencing.  It appears it's a bug in gnome.  I followed the solution given in post #42 here ([_http://www.ubuntuforums.org/showthread.php?t=288651&page=5_]("http://www.ubuntuforums.org/showthread.php?t=288651&page=5")) and it solved my problem.  Read posts #43 and #45 first for minor corrections to the instructions in post #42.

I have this same problem. And thank you for the link tribble222; I read through that, but wow, that is a bit too advanced for me at the moment. :( It looks like at least one person had some issues with booting up after that patch, and since I don't understand all that I would be doing in those steps, I think I'll just deal with the screensaver issues for now unless I find a simpler fix.

---


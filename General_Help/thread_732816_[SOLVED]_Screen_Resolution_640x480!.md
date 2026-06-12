---
title: "[SOLVED] Screen Resolution 640x480?!"
date: 2008-03-23
forum: General Help
---

### Post by Hazed on 2008-03-23
Hey all,

Ive been running Ubuntu Gutsy on my Dell Vostro 1500 for the past few weeks now, and all has been going great.

However, I just booted it up this morning, and for some reason the NVidia logo appeared before the login screen (This has never happened before). I thought nothing of it, but when I logged in, my resolution had gone from 1280x800 (My default widescreen resolution that I have been using since I installed it) down to 640x480?!

I have no idea why this has happened, I shut the computer down properly last night and all was working fine.

Anyone have any suggestions?

---

### Post by Taino on 2008-03-23
Try and change it back to 1280x800 by going to... System --> Preferences --> Screen Resolutions.

If that doesnt work then open a terminal window and run this...

```

sudo dpkg-reconfigure xserver-xorg

```

Go thru the choices until you get to the screen resolution part, in that section (pick) your 1280x800 resolution (use spacebar to mark it) then continue on to the end of the settings and save it.

then log out... (Ctrl-Alt-Backspace) keys log you out, so you can log back in.

:popcorn:

---

### Post by Hazed on 2008-03-23
Thanks, I just read that on another post to.

Luckily "sudo dpkg-reconfigure xserver-xorg" WAS the solution to my problem :)

Cheers!

---

### Post by Taino on 2008-03-23
good to hear :^)

---


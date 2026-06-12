---
title: "[SOLVED] Problem with two screens"
date: 2008-01-08
forum: General Help
---

### Post by graabein on 2008-01-08
I'm on Ubuntu 7.10 and I have a problem with my setup of monitor and television set. I use the **System > Administration > Screens and Graphics** application and I've not touched the graphic card driver nor **xorg.conf**. I have a Nvidia GeForce 6600GT btw.

I'd like to have my television set to the left of my monitor and keep the desktop icons and menu panels on screen 1 (monitor). When I run a movie full screen from VLC I want it to show up on my TV (screen 2) and not on my monitor (screen 1) as it does now. 

I don't think I can accomplish this in the **Screens and Graphics** application, or can I?

Here are my settings:
[LIST]
[*]Screen 1: LCD Panel (default screen)
[*]Screen 2: Monitor 800x600 (secondary screen to the left)
[/LIST]

---

### Post by MobiusNZ on 2008-01-08
Do your screens share one desktop? ie can you drap an app from one to the other? I think that if you move VLC onto the other screen when you make it fullscreen it will use that one.

---

### Post by graabein on 2008-01-09
They act like one desktop and Compiz disables when I have two screens. VLC goes fullscreen on the monitor (screen 1) no matter where I have the application when I enable fullscreen.

---

### Post by MobiusNZ on 2008-01-09
In VLC go Settings->Preferences->Video->Output modules->XVideo, and check the Advanced options box. There is a setting there for "Screen for fullscreen mode"

---

### Post by graabein on 2008-01-11
Yeah, that worked great, thanks!! I think screen 1 (in the **Screens and Graphics** dialog) equals screen 0 in the VLC settings. Just like in the *xorg.conf* file. 

:popcorn:

Can I post a follow up question? How do I tell GNOME that I want my icons mapped out on a specific screen? I mean as default? Looks like GNOME thinks I have two screens next to each other and start counting x=0 at the left-most, not x=0 at screen 1...

---

### Post by MobiusNZ on 2008-01-11
Yeah I've had trouble with that sort of thing before. I don't think I ended up finding a workaround sorry. Maybe start a new topic with that question in Multimedia & Video...

---


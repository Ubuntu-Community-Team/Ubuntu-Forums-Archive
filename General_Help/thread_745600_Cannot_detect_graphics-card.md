---
title: "Cannot detect graphics-card"
date: 2008-04-04
forum: General Help
---

### Post by amarant on 2008-04-04
My computer is a Dell Inspirion 1525 Laptopp.

My installation has worked flawlessy until i started messing around with some screen settings. 

In the Screens and Graphics Preferences i accedently changed the screen drivers, this made me end up with 800x600 resolution. I rebooted the computer and got this message:

```
Your screen and graphics card could not be detected correctly. To use higher resolutions, visual effects or multiple screens, you have to configure the display yourself
```

and i get to choose "Configure", "Shutdown" and "Continue".

I chose configure and found a driver setting, "vesa - Generic VESA-compliant video cards" that made it (kinda) go back to the way it was before, but it still dosent seem to work quite right.

Whenever i start the computer it looks like ubuntu has problem starting X, it gives it a few tries and then displays the error message ("Your screen and graphics card..."), i choose continue the screen flashes a few more times, some parts become green and pink and then fter a few flashes i get a picture.

How can i solve this and get back to the way it was before?

---

### Post by Rocket2DMn on 2008-04-04
To get it back to the initial display settings that Ubuntu detected, run
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Then restart X with CTRL+ALT+BACKSPACE
Alternatively you can manually configure X by not using the -phigh flag.

---

### Post by amarant on 2008-04-05
Thanks! this worked.

---

### Post by Flyerfye on 2008-04-13
Victory.

---


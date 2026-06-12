---
title: "Script help. Adding imwheel to new display for gaming."
date: 2006-12-13
forum: General Help
---

### Post by Drezliok on 2006-12-13
ok, I am playing World of WarCraft with this script to run the game in it's own xserver. [atleast thats how I understand it]
I tried adding imwheel to it myself and the output on the terminal said it was starting.. But it doesn't activate the side buttonson my mouse. I was thinking either the script needs instructions for imwheel the follow or I had to alter some config files. But I don't know where to start.

My side buttons do work, and when I ran the game with out the script they worked too.

```
#!/bin/sh
 
 X :3 -ac &   # Launches a new X session on display 3 
 sleep 2   # Forces the system to have a break for 2 seconds 
 DISPLAY=:3 /usr/X11R6/bin/imwheel # my addition for my side buttons
 DISPLAY=:3 /usr/X11R6/bin/wine /media/sda5/games/World\ Of\ Warcraft/WoW.exe -opengl   # Launches WoW
```

Thankyou for your time.
Drezliok

---

### Post by Drezliok on 2006-12-15
Any takers?

---


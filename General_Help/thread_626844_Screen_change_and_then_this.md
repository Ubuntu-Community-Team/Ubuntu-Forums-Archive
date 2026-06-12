---
title: "Screen change and then this"
date: 2007-11-29
forum: General Help
---

### Post by Windows_RiscOS_&amp;_Linux on 2007-11-29
After upgrading from 7.04 to 7.10, I found there was an extra option for setting Monitor Res. I managed to set 1280x1024 (Max for my TFT), and successfully restarted. But I then discovered all the windows and filer folders have lost the title bar/border, so I am unable to resize or move things around the desktop. This happened when I changed screen size, and was fine before.
Should I have closed all apps and windows before changing screen screen size, or have I over looked something. Thankfully Firefox opens to a sensible size.

---

### Post by jken146 on 2007-11-29
What window manager are you using?  You could try running ```
compiz --replace
``` or ```
metacity --replace
```  That has worked for me in the past.
It seems strange that changing the screen res alone would do this though.

---

### Post by Windows_RiscOS_&amp;_Linux on 2007-11-30
I've tried opening the terminal, and all I get is a white box. I'm suspecting this is related to the missing title bars.

---


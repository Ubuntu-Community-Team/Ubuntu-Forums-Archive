---
title: "LibreOffice Calc: keyboard shortcut for &quot;sum&quot;?"
date: 2015-08-16
forum: General Help
---

### Post by vasa1 on 2015-08-16
Does Calc in LibreOffice 5 have a keyboard shortcut for the *sum* function? In 4.4.5, I can only access *sum* by using the mouse.

---

### Post by vasa1 on 2015-08-16
A workaround for Calc 4.4.5 is to use *xdotool* but it has the limitation that it works only for a particular window geometry[SUP]*[/SUP].

I made the following script:```
#!/usr/bin/env bash

# hint: use "xdotool getmouselocation" to get values
xdotool mousemove --sync 218 144 click 1 
#sleep 0.3
#xdotool mousemove restore


```and assigned a keyboard shortcut to it.

[SUP]*[/SUP]The limitation arises because the script moves the mouse to a specific location. I mostly use Calc maximized and so the "sum" icon (&#931;) always has the same coordinates (x = 218; y = 144 on my laptop).

---

### Post by PaulW2U on 2015-08-16
*Thread moved to **General Help**.*

---


---
title: "Just upgraded to edgy, two problems"
date: 2006-12-12
forum: General Help
---

### Post by web250 on 2006-12-12
I just upgraded from Dapper to Edgy, and I had everything perfect in Dapper.

Two problems with edgy:

I can't seem to get fglrx working (fglrxinfo says:```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
```)

Also, my fonts are all weird. Tabs in Firefox are really bold, they look like the looked when I used to have XGL/compiz on dapper. How can I make these look nice again?

---

### Post by web250 on 2006-12-12
Ok, fixed the fglrx problem (added to modules). But my fonts are still awful.

Any suggestions?

---

### Post by kd7swh on 2006-12-12
I don't know what fonts firefox needs but try re-installing it with aptitude"

'sudo aptitude install firefox -f'

or something like that...

aptitude is really good at dealing with dependencies.


or 
you might try installing the ms core fonts 

that might help

good luck

---

### Post by web250 on 2006-12-12
It's not just firefox, and i have ms core fonts installed.

---

### Post by drphilngood on 2006-12-12
> **web250 said:**
> Ok, fixed the fglrx problem (added to modules). But my fonts are still awful.

Any suggestions?

Enable &#8220;sub-pixel smoothing&#8221; in your &#8220;System&#8221; menu under &#8220;Font&#8221; -> ¨Font Rendering¨.

---

### Post by web250 on 2006-12-13
> **drphilngood said:**
> Enable “sub-pixel smoothing” in your “System” menu under “Font” -> ¨Font Rendering¨.

That worked! Great. Now everything is working pretty well.

Except on my dell laptop the play/pause button wont work Amarok anymore, all the other buttons still work. Weird.

---


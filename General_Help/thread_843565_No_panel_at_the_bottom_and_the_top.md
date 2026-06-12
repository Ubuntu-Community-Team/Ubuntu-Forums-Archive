---
title: "No panel at the bottom and the top?"
date: 2008-06-28
forum: General Help
---

### Post by chroncile on 2008-06-28
Hi, I have a problem where when I open something in places, all the panels are gone, I have compizfusion running, but this doesn't happen with anything else expect for that. Please help me. :)

---

### Post by Forlong on 2008-06-28
I didn't even know Nautilus had a fullscreen mode.

Make sure the file browser is not running at all (no folders open).
Then open a terminal and run this:
```
nautilus -g 750x500
```
Then resize it to whatever you want.
Afterwards, close the window and see if it helped.

---

### Post by chroncile on 2008-06-28
YES! Thank you, that solved it :D

---


---
title: "Change Defaul Unit MM to PX in Inkscape"
date: 2017-06-14
forum: General Help
---

### Post by braznyc on 2017-06-14
I need to change the default unit to be in pixels instead of mm.

Any help is welcome.

---

### Post by Dennis N on 2017-06-14
Permanent (maybe not what you are looking for): 
Edit > Preferences > Interface > Grids > Default Grid Settings > Grid Units > set to px
Current document only (checked - works):
File > Document Properties > Page Tab > General > Display Units > set to px

---

### Post by braznyc on 2017-06-14
It didn't work.
:(

I'm looking for a permanent change. I work with px most of time.

[https://ibb.co/mgXJdQ](https://ibb.co/mgXJdQ)

---

### Post by Dennis N on 2017-06-14
> **braznyc said:**
> It didn't work.
:(

I'm looking for a permanent change. I work with px most of time.

[https://ibb.co/mgXJdQ](https://ibb.co/mgXJdQ)

Inkscape version 0.92 in 17.04 defaults the ruler units to mm when you open a new document, while the previous versions defaulted to px.

To change rulers on side and top back to px as default, I changed **File > Document Properties > Page Tab > General > Display Units** from mm to px. Then save the document as: 

**~/.config/inkscape/templates/default.svg**

Next time you start Inkscape, the rulers on the side and top of the new document will show pixels.

---


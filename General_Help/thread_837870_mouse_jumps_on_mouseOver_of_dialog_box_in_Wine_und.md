---
title: "mouse jumps on mouseOver of dialog box in Wine under Hardy Heron"
date: 2008-06-22
forum: General Help
---

### Post by briancady413 on 2008-06-22
I have cursor jump problems on mouseOver inside Wine dialog boxes. 
In other words, when I move the arrow cursor over any part of a Wine window/dialog box (except the top grab bar), the arrow jumps left and up about a centimeter. Unfortunately mouse clicks are sent as though the mouse was still where one would expect it to be. In other words, with the arrow cursor over the Wine dialog box, the cursor is up and left of where mouse clicks are sent from.
I tried disabling Compiz, with no effect. In fact it appeared that compiz was already disabled, despite talk of default enabling under 8.04

---

### Post by pvdeynse on 2011-02-27
Bug [14074]("http://bugs.winehq.org/show_bug.cgi?id=14074") - mouse/cursor position error - jumps on mouseOver of Wine-related window

---


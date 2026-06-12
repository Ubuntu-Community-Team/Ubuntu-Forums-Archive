---
title: "Gutsy:  scrollback buffer contents lost when switching VT's"
date: 2007-12-30
forum: General Help
---

### Post by jhansonxi on 2007-12-30
I've noticed that when I'm working a virtual terminal (Ctrl-Alt-F1 - F6), the scrollback buffer contents are lost when I switch from one VT to another.

Example:
Login to tty1 and tty2
Then on tty1:
ls /usr/lib
Shift-PgUp to see buffer contents
Ctrl-Alt-F2 or Alt-Right Arrow to tty2 then switch back.
Shift-PgUp
Nothing is displayed (or maybe key is ignored?)

Is this normal behavior?  If not, can anyone else reproduce this, maybe in a different Ubuntu release?

---


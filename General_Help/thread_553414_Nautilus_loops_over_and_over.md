---
title: "Nautilus loops over and over"
date: 2007-09-17
forum: General Help
---

### Post by Traceur-UK on 2007-09-17
Basically, when I go to places > home (and most other places), nautilus will open, then close, over and over. Can't think what might be up.
I tested and it happens in both metacity and emerald.

---

### Post by Gremlinzzz on 2007-09-17
command
killall nautilus

---

### Post by Traceur-UK on 2007-09-18
I've not had a chance to test this yet (I'm currently on the college computers) but by the sound of this, it'll just close Nautilus. The looping problem happens every time I open it (Perhaps I was unclear in this, I posted this thread fairly late at night). If I'm wrong in my assumption then I apologise.

---

### Post by Traceur-UK on 2007-09-18
Ok I got it sorted... not sure exactly what was up but perhaps someone else might know. I had copies of libGL.so and libGL.so.1 in there. And also a java .class and .java file (just started learning java, nothing more than a 'hello world' terminal message). My best guess is it's something crazy to do with the libGL files as I can't imagine java having anything to do with it (isn't nautilus C?).

---


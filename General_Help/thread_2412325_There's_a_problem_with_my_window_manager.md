---
title: "There's a problem with my window manager"
date: 2019-02-11
forum: General Help
---

### Post by ash22 on 2019-02-11
I reinstalled Xorg and now I can't move or resize windows. When I tried going to the window manager settings, I got an error message saying "the window manager is unsupported. I alreddy have compiz and Compton installed but I can't switch between them anymore and now the GUI on my system is unusable.

---

### Post by oldos2er on 2019-02-11
What window manager are you using?

---

### Post by #&amp;thj^% on 2019-02-11
Going into CompizConfig Settings Manager (CCSM), Window Management and ticking the box next to Resize, Move, and effects, should get you proper.
Also Compton and Compiz is just a bit overkill, pick one.

---

### Post by deadflowr on 2019-02-11
Since you tagged this as Ubuntu mate what does
```
gsettings get org.mate.session.required-components windowmanager
```
show?
Assuming you can open a terminal.

---

### Post by ash22 on 2019-02-11
> **deadflowr said:**
> Since you tagged this as Ubuntu mate what does
```
gsettings get org.mate.session.required-components windowmanager
```
show?
Assuming you can open a terminal.

It replied with "marco" so I just installed it and now I can move windows but the window title bars aren't there. What is marco for?

---

### Post by ash22 on 2019-02-11
It's all working now

---

### Post by deadflowr on 2019-02-11
> What is marco for? 
It the default wm for mate, usually.
Meaning it should have already been installed.
It's design is based on metacity (a fork really), which in itself is designed to be a barebones simple wm, with little eye candy and graphical effects.
> how do I get my desktop to work as a folder? 
What do you mean?

Edit: I see you've solved the desktop kerfuffle.

---


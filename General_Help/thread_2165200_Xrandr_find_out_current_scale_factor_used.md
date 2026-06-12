---
title: "Xrandr find out current scale factor used"
date: 2013-08-03
forum: General Help
---

### Post by josvanr on 2013-08-03
I want to create a 'desktop zoom' for use with xfce using xrandr

Normally I work with a scaled desktop: at start of session I do on my 1920x1080 laptop screen:

xrandr --output LVDS1 --scale 1.3x1.3 --panning 2496x1404

giving me a slightly larger desktop.

Now in my 'zoomin' button which is supposed to zoom in one step, I do something like

xrandr --output LVDS1 --scale 1.17x1.17 --panning 2496x1404
 
so I can move around the same desktop showing an enlarged area . I want to implement a button that
zooms in steps. But then I need to know the current scale factor or size of the viewport. But I cant seem to 
find that as output of xrandr. Am I missing something?

josvanr

---

### Post by josvanr on 2013-08-03
hmm never mind ... scaling doesnt seem to work well when the factor is smaller than 0.5 or so.....

---

### Post by josvanr on 2013-08-03
I mean smaller than 1... hmm

---


---
title: "compiz - gnome panel - cube rotation - bug?"
date: 2008-04-30
forum: General Help
---

### Post by benste on 2008-04-30
I can't get an automaticly hided panel at the left border - back when compiz cube is activated.

Do you also have this mistake?

---

### Post by klange on 2008-04-30
It's not a mistake, and it's not even a bug.
Cube Rotate reserves the leftmost and rightmost columns of pixels for detecting mouse drags. Wall does the same, but for the top and bottom as well.
Make sure you're not all the way to the left and that your panel hides to at least 2 pixels wide.
(Supposedly we're going to "fix" this someday)

---

### Post by benste on 2008-04-30
I hope this fix will be released soon,
> Make sure you're not all the way to the left and that your panel hides to at least 2 pixels wide.
how can I adjust that panel hides at least 2 pixel?
- in my gui i only can change the normal width of the panel and not the hided one 

And at the top of the page is no reserved place for me (maybe because of cube)

---

### Post by klange on 2008-04-30
gconf-editor:
/apps/panel/toplevels/[your panel]
auto_hide_size -> Make sure it is at least 2. It should be higher anyway, you just need to make sure you're not all the way to the left with your mouse.
If it does not exist, you'll have to make the key...

---

### Post by benste on 2008-04-30
There is no such option, but I'm using another solution now - panel top orientated - with hide button

But if you find another solution please notice me

---


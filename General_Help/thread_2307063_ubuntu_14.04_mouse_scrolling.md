---
title: "ubuntu 14.04 mouse scrolling"
date: 2015-12-21
forum: General Help
---

### Post by amtrakuk on 2015-12-21
I can't see a way of stopping the mouse pad scrolling.  I ran synclient HEdgeScroll=0 but it still seems to scroll, I think along the bottom.  How to I disable ALL scrolling using y mouse pad?

Thanks

---

### Post by SlidingHorn on 2015-12-21
looking at the syanptics man page, it looks like the option should be "HorizEdgeScroll" instead.  Give that a try and report back :)



```
synclient HorizEdgeScroll=0
```

---

### Post by amtrakuk on 2015-12-21
Thanks I'll give it a try.   It only really happens when playing settlers online when the view suddenly zooms in and/or out.

---

### Post by amtrakuk on 2015-12-22
Managed to solve it with a combination of the both as when I set the horizontal the vertical activated and vice versa

```
synclient VertEdgeScroll=0 HorizEdgeScroll=0
```

---


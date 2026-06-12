---
title: "Compiz cuts off bottom of screen"
date: 2008-06-14
forum: General Help
---

### Post by Hotaka on 2008-06-14
Whenever I enable Compiz effects (in the Appearance window) the bottom of the screen is cut off (about 1/5 or 1/4)

Basically, when you first do it the strip being "cut off" is invisible, and if you leave it like that and restart it turns the color of your background.

It's the equivalent of gluing a piece of paper over your moniter, everything still functions perfectly under it.

If I turn all the effects back off, it goes back to normal, if I lower the resolution, it goes back to normal. (using a resolution lower than 1280x1024 with my moniter size is out of the question)

---

### Post by Hotaka on 2008-06-15
Update: Here's a screen [http://img517.imageshack.us/img517/589/screenshot1wu8.png](http://img517.imageshack.us/img517/589/screenshot1wu8.png)

---

### Post by Hotaka on 2008-06-15
Bump...

---

### Post by prshah on 2008-06-15
> **Hotaka said:**
> Whenever I enable Compiz effects (in the Appearance window) the bottom of the screen is cut off (about 1/5 or 1/4)

It's the equivalent of gluing a piece of paper over your moniter, everything still functions perfectly under it.




Do you have a dual monitor setup by any chance? There is a limitation on the maximum resolution with Compiz.

Failing that point, open a terminal (Applications-Accessories-Terminal), then give the following commands and post the output here. ```

compiz --replace

```

---


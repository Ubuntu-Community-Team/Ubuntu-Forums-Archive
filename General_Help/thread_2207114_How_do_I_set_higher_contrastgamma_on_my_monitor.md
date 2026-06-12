---
title: "How do I set higher contrast/gamma on my monitor?"
date: 2014-02-22
forum: General Help
---

### Post by vladimirvilimaitis on 2014-02-22
I have a GPU fault in my laptop where my machine reacts negatively to deep shades of black(lines and rectangles across the screen, flicker, makes it unusable in some cases). I've been wondering if I could brighten up the monitor my setting the contrast/gamma whiter, like I did in some PS2 games, so I could get rid of this problem. I've seen some solutions which allow me to get my screen darker, but not whiter.

---

### Post by sam_baker2 on 2014-02-22
have you tried the xgamma command from terminal?
```

xgamma -gamma 1.0 

```

1.0 should be normal
.8 less,  1.3 more, etc, etc

some info here:[URL="http://www.x.org/releases/X11R7.5/doc/man/man1/xgamma.1.html"]
http://www.x.org/releases/X11R7.5/doc/man/man1/xgamma.1.html[/URL]
[http://www.ubuntufieldmanual.com/?q=node/38](http://www.ubuntufieldmanual.com/?q=node/38)

---

### Post by vladimirvilimaitis on 2014-02-22
Thank you very much.

---


---
title: "rendering problems when running MATLAB remotely"
date: 2008-04-08
forum: General Help
---

### Post by event on 2008-04-08
I am using Gusty Gibbon

I'm connecting to the university computers using ssh -X, but when I do this, MATLAB doesn't fully render. I can still click on stuff I can't see, but new windows won't render at all. Here is a screen shot: [http://i32.tinypic.com/mt8pom.png](http://i32.tinypic.com/mt8pom.png)

Any ideas?

---

### Post by event on 2008-04-08
anybody know what the deal is?

---

### Post by Nepherte on 2008-04-08
If you have enabled the compiz fusion visual effects, I suggest you disable them and try again. If I have it enabled, I can't see a thing except the window bar.

---

### Post by Whiffle on 2008-04-08
Try ssh -Y instead, it relaxes teh security a bit but seems to make it work better.

---

### Post by event on 2008-04-08
Disabling them fixed it... thanks a lot

-Y helped too, thanks

---

### Post by Whiffle on 2008-04-08
You might try doing:
export AWT_TOOLKIT=MToolkit

before running Matlab, I think that helped when i was runing compiz.

---


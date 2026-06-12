---
title: "Non-fglrx ATI drivers"
date: 2004-11-30
forum: General Help
---

### Post by link on 2004-11-30
Is there any way to get DRI (3D acceleration) support to the point where I can run the OpenGL xscreensaver modules at a decent framerate? I'm not looking to game, just looking to get a few hundred FPS in glxgears. Ubuntu picked the 'ati' driver by default to use in my XF86Config. How might I go about enabled DRI? I have a Radeon 9700. Is it possible to get DRI support with this card (and not use the fglrx drivers)? In my experience, the fglrx drivers crank up my framerate & enable 3D acceleration, but when I try to play half of my videos (mpg and such), they all die with a BadAlloc error from X. These error's never happen when I use the radeon or the ati driver, only the fglrx.
Has anyone successfully gotten a newer Radeon to work without using the fglrx drivers?

---

### Post by daniels on 2004-12-01
All r3xx/r4xx-based cards (9500 and above) won't do DRI without fglrx, sorry.

---

### Post by orestis82 on 2004-12-08
I have a Radeon 9200, how can I enable 3d acceleration ? The fglrxinfo says i'm running the Mesa drivers.

---

### Post by HungSquirrel on 2004-12-08
[http://www.ubuntuforums.org/showthread.php?t=3713](http://www.ubuntuforums.org/showthread.php?t=3713)

---

### Post by orestis82 on 2004-12-08
I've seen this thread, however I've read that Radeon 9200 doesn't need fxglr drivers, just the built-in ati drivers. However, DRI is not available, and both 2d and 3d are slow.

---

### Post by K6-III on 2004-12-15
Upgrading to X.Org should work for the Radeon 9200...

---

### Post by link on 2004-12-15
[QUOTE=daniels]All r3xx/r4xx-based cards (9500 and above) won't do DRI without fglrx, sorry.[/QUOTE]

Thanks. I was afraid of that.

---

### Post by orestis82 on 2004-12-15
To get X.org I must upgrade to hoary, right ?

---

### Post by CvFloy8138 on 2007-05-15
> **K6-III said:**
> Upgrading to X.Org should work for the Radeon 9200...


[physics memory Equity Loans memory Loans](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/latin-porn.html)

---


---
title: "firefox leaking memory???"
date: 2008-05-17
forum: General Help
---

### Post by anaconda on 2008-05-17
I am trying to read this page:
[http://www.scribd.com/doc/2945245/Drawing-realistic-textures-in-pencil-](http://www.scribd.com/doc/2945245/Drawing-realistic-textures-in-pencil-)

But the page seems to eat every bit of memory I have.. 512MB of RAM and 1GB of swap. And everything becomes reaaaally reeeeaaaly slow. 

Is it just me, or is this a firefox bug? And what happens if you have more memory? Does it eat all anyway?

---

### Post by sdennie on 2008-05-17
I just tried that page with Epiphany (which uses the same backend as Firefox 3) and it didn't noticeably increase memory usage.  I would try disabling your plugins and see if Firefox still has problems or trying Epiphany or Opera and see if they have the same problem.

---

### Post by Xiong Chiamiov on 2008-05-17
Firefox is notorious for memory leaks, but usually not in the application itself, but rather in the extensions you install.  If you're like me, then you have quite a few ;).  Try disabling some and gradually narrow down what is causing the problem, if it is an extension.

---

### Post by jongkind on 2008-05-17
> **vor said:**
> I just tried that page with Epiphany (which uses the same backend as Firefox 3) and it didn't noticeably increase memory usage.  

If you wait a bit Epiphany also displays increased memory usage. It is related to that Ipaper that is loading.

---


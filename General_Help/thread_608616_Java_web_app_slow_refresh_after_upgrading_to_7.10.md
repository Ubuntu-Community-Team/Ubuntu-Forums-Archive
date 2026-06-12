---
title: "Java web app slow refresh after upgrading to 7.10"
date: 2007-11-10
forum: General Help
---

### Post by cyberkoa on 2007-11-10
After searching in google, still no luck.

I am using an online share trading system written in Java . It works fine in 7.10 , however, after upgrading to 7.10 , that application runs too slow . The screen will refresh many times before it settle down and let me to click . Every click also trigger the refresh of the screen and it takes almost 5 seconds to settle down and let me continue to the next action.

I have tried to uninstall the 1.6 , 1.5 version and use the 1.4 version (sun-java) but still no luck. 

I believe is the problem between Java and XGL because it does not have this problem in 7.04.

Anybody face the same problem ? 

Thanks in advance for any help.

---

### Post by Elegorod on 2007-11-10
I have subscribed to 5 themes with this problem on ubuntuforums.org. Still no solution.
It's a problem with X11 pixmaps. They are used by Java2D. Pixmaps can be disabled by adding an argument to JVM:
```

-Dsun.java2d.pmoffscreen=false

```
as described in [Changing Rendering Pipelines and Their Properties]("http://java.sun.com/javase/6/webnotes/trouble/TSG-Desktop/html/gcghe.html")
Also OpenGL can be turned on, but it's not working on my computer.

---

### Post by jamuir on 2007-11-12
I've also found that one of my favourite Java applets became unusably slow after upgrading to  Gutsy.  However, I just found a solution:  boot the 2.6.20-15 kernel rather than the 2.6.22-14 kernel.  When I do this the applet runs fine.

I've read about Java running slowly under Gutsy in other threads.  However, I think it only affects particular motherboards.  On the box in my office, the applet runs fine under 2.6.22-14, but on my home box it does not.

-James

---

### Post by cyberkoa on 2007-11-17
thx for all the reply, i'll try them and see how

---


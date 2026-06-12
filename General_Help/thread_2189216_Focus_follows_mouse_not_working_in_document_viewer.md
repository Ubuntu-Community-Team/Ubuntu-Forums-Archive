---
title: "Focus follows mouse not working in document viewer 13.10"
date: 2013-11-21
forum: General Help
---

### Post by MorrisseyJ on 2013-11-21
Hi, 

I am running 13.10 and have noticed what i think is a small problem in document viewer. 

While in other programs focus-follows-mouse works well - so that if i have one maximised application with another running as a smaller window on top of it, i can scroll down the maximised app simply by hovering the mouse over that window and using the scroll wheel - it seems not to be working in document viewer. 

This is frustrating if i am reading a pdf and trying to do something else. In this case i am learning python. I want to run a small terminal window on top of the maximised document viewer window and be able to scroll down the document, without having to click it and lose sight of my terminal. At the moment, however, in order to scroll down in document viewer i have to click the window, thereby losing sight of my terminal. 

This does not happen in firefox - there i can scroll down a maximised firefox window simply by hovering the mouse over it (i.e. without losing sight of my terminal window).

I am not sure if this is a bug or if there is something that i am missing. 

Could someone either tell me how to fix it, or confirm it so that i can file a bug. 

Thanks,

j

---

### Post by grier-devon on 2013-11-21
> **MorrisseyJ said:**
> Hi, 

I am running 13.10 and have noticed what i think is a small problem in document viewer. 

While in other programs focus-follows-mouse works well - so that if i have one maximised application with another running as a smaller window on top of it, i can scroll down the maximised app simply by hovering the mouse over that window and using the scroll wheel - it seems not to be working in document viewer. 

This is frustrating if i am reading a pdf and trying to do something else. In this case i am learning python. I want to run a small terminal window on top of the maximised document viewer window and be able to scroll down the document, without having to click it and lose sight of my terminal. At the moment, however, in order to scroll down in document viewer i have to click the window, thereby losing sight of my terminal. 

This does not happen in firefox - there i can scroll down a maximised firefox window simply by hovering the mouse over it (i.e. without losing sight of my terminal window).

I am not sure if this is a bug or if there is something that i am missing. 

Could someone either tell me how to fix it, or confirm it so that i can file a bug. 

Thanks,

j
Looks like a bug from what I can see, Your exact problem has not been reported but some extremely similar. If you want I will give you the link and you can report your issue, seems like there are quiet a few issues when it comes to the document viewer and focus. Best of luck!


[https://bugs.launchpad.net/ubuntu/+source/evince/+bugs?field.tag=i386](https://bugs.launchpad.net/ubuntu/+source/evince/+bugs?field.tag=i386)

---

### Post by MorrisseyJ on 2013-11-21
Hi, 

Thanks grier. It looks like this is the problem though: [https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1240957](https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1240957)

Its not just evince but a number of programs. 

j

---

### Post by Anshul_Joshi on 2013-12-28
hi MorrisseyJ 
i am a beginner in ubuntu as well and am suffering from the same problem, 
but recently i've found a way to scroll in document viewer without selecting the window
I don't know if you you already know about this, but if you place your cursor at the vertical scroll (that appear when you move your mouse over it to the right), 
you can scroll down the document without selecting the window, only with your mouse wheel.
Also, if you find the original solution to this problem, just let the other users know.
by the way i'm also using ubuntu 13.10

---


---
title: "Mouse freezes and then restarts but why?"
date: 2008-03-10
forum: General Help
---

### Post by Robbyx on 2008-03-10
I read of an application  that makes the mouse move more smoothly. Mine jams as I drag an item across the screen. The application was only for gutsy. Any ideas what it is called?

Alternatively is there a way of adjusting the interrupts or priority of the mouse? 

I really would like to have the mouse work properly and not keep sticking.

Mouse=logitech Mx500
Gutsy

Robin

---

### Post by phrawzty on 2008-03-10
> **Robbyx said:**
> Alternatively is there a way of adjusting the interrupts or priority of the mouse? 

Have you tried adjusting the settings in "Mouse Preferences" ?

System -> Preferences -> Mouse ^ Motion

---

### Post by Robbyx on 2008-03-10
I have tried those settings and they did not help. Do you know of any others?

---

### Post by phrawzty on 2008-03-10
> **Robbyx said:**
> I have tried those settings and they did not help. Do you know of any others?

I don't know of any others off the top of my head.  Note, however, this thread :
[http://ubuntuforums.org/archive/index.php/t-67287.html](http://ubuntuforums.org/archive/index.php/t-67287.html)
Wherein a user with an MX-1000 mouse notes a similar (the same?) problem as you; however, using another "normal" USB mouse was flawless, indicating that it was a problem with the mouse.  In fact, a quick google search for Logitech mice and choppy response under Linux turns up quite a few hits, which isn't a good sign... Of course, that doesn't necessarily help you. :P

Note this blog entry as well :
[http://www.voidstar.com/node.php?id=2901](http://www.voidstar.com/node.php?id=2901)
The user had a problem with choppy mouse movement, and discovered that disabling powernowd solved it.  I can't vouch for the reason or the solution, but it may be worth looking into.

---

### Post by Robbyx on 2008-03-10
Thank you. Your reply helped greatly. I put in a replacement mouse and switched off the powernowd service. So far I have not experienced the problem again.

Robin

---


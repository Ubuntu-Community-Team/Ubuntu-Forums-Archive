---
title: "Ubuntu 13.04 - Reduce Mouse Acceleration"
date: 2013-06-24
forum: General Help
---

### Post by carmen2012 on 2013-06-24
I've done a clean install of Ubuntu 13.04 and found that the mouse was to fast.  Using the mouse and touchpad icon, I've been able to slow down the mouse, but what I believe is the mouse acceleration is to fast.

If the mouse pointer is not moving and I go to move it to say highlight text or something, it starts off very fast.

How do I go about slowing this down?

Thank you

---

### Post by dino99 on 2013-06-24
you can set the mouse speed by opening System Settings menu then choose mouse icon: there move the slider

---

### Post by aqkshin on 2013-12-29
i know i am late in answering. But just thought it might be helpful to someone.
Basicly there are 4 parameters you can change by using terminal:

use _xinput set-prop_ to change these three parameters:
1.  Device Accel Constant Deceleration    
2.  Device Accel Adaptive Deceleration     
3.  Device Accel Velocity Scaling

and use 
4.  _xset m 3 1_ (first value for acceleration, second value for threshold)

you can look them up on the internet for more details. I am also dealing with this problem, and haven't managed to set mouse movement settings to my liking yet. But, at least, better than default. I hope someone quite informative on this issue will post more tweaking options for mouse.

---


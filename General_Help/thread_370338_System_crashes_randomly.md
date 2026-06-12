---
title: "System crashes randomly"
date: 2007-02-25
forum: General Help
---

### Post by Sou Portugues on 2007-02-25
OK-
So my stuff keeps going down, and I haven't been able to find a thread that links the instances.  Here are some of the "what I was doing at the time" and some theories;

Changing to twin view- Something to do with nvidia driver?
Watching a DVD on Totem- Something to do with nvidia driver?
Burning a DVD/CD- bad repository (other programs have had a hard time finding lame)?
Ripping a DVD/CD- bad repository (other programs have had a hard time finding lame)?
Starting up- immeadiately after crashing, crashed during startup

Not sure what is going on here, but I'm pretty sure it isn't the power supply for the following reason, the power light never dies.  It stays on unitl I shut the computer down (via holding in the power button).

Any help is appreciated, I'm having a rough time with most of the components in my system.

---

### Post by watson540 on 2007-02-25
Bad power supplies are more apt to cause random restarts than just freezing. One thing that comes to mind (because i just went through it myself) is to make sure that if your running nvidia's drivers then remove the stock xortr  ones.

I just typed apt-get remove nvidia* . although that may not work for you, it works for me because i nstalled the nvidia driver manually. But I did experience a lot of random crashes until I removed the 'nv' driver. Hope this is understandable :)

---

### Post by Sou Portugues on 2007-02-25
> **watson540 said:**
> Bad power supplies are more apt to cause random restarts than just freezing. 
Actually- it isn't freezing, everything just turns off.  I mean everything.  It's like the system send a command out to everything to commit hari-kiri.  even the monitors instantly go to powersave, bypassing the no signal screen.

> **watson540 said:**
> One thing that comes to mind (because i just went through it myself) is to make sure that if your running nvidia's drivers then remove the stock xortr  ones.

I just typed apt-get remove nvidia* . although that may not work for you, it works for me because i nstalled the nvidia driver manually. But I did experience a lot of random crashes until I removed the 'nv' driver. 
OK- so I need to remove the driver (I'm a bit confused as to what will run my video card)?  I did not install manually, I used automatix (mea culpa right).:confused:

---


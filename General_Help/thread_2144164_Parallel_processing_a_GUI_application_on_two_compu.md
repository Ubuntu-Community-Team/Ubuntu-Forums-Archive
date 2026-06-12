---
title: "Parallel processing a GUI application on two computers?"
date: 2013-05-11
forum: General Help
---

### Post by Ranko Kohime on 2013-05-11
I use OpenShot for editing HD videos, and it takes a while on my computer to fully render a video.  I'm soon going to be adding a gaming-focused desktop to my mix, and I'm wondering if there is a simple way in Ubuntu to send some of the worker threads onto the CPU of the other computer.  Basically, some program that would expose the cores of the 2nd computer to OpenShot.

So, is there such a program?

---

### Post by 2F4U on 2013-05-11
This is not so much something the OS does, rather the application must be able to distribute its work over more than one core or processor, because at the end of the processing it must collect all the parts together.

---

### Post by tgalati4 on 2013-05-11
There are several clustering frameworks.  I have not used them, but you can explore each one to see if any of them will work.  What you want is called a *render farm*.  I would hang out in the openshot [forums]("http://openshotusers.com/forum/") and ask there and send an email to the [developer]("http://openshot.org/developers/jonathan/").

---

### Post by zemega on 2013-05-11
mpi is what you need, but I myself can't get it to work on my own yet. Its mainly used in research area (heavy computing and modelling). I'm sure it will works with video rendering, but gaming, I'm not sure about that.

---

### Post by Ranko Kohime on 2013-05-11
> **zemega said:**
> mpi is what you need, but I myself can't get it to work on my own yet. Its mainly used in research area (heavy computing and modelling). I'm sure it will works with video rendering, but gaming, I'm not sure about that.
Ehh, no, not gaming, I just meant that the rig I'm going to be adding is going to be a dedicated gamer, and in it's idle time I'd use it as a slave to render videos on my current production machine.

I'll check mpi out, and see if I can get it running for me.  :)

---


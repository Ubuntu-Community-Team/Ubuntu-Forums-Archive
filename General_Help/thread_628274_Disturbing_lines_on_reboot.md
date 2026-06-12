---
title: "Disturbing lines on reboot"
date: 2007-12-01
forum: General Help
---

### Post by JaggedOne on 2007-12-01
Sometimes when I power down my sager NP2090 laptop running gutsy I get a weird white screen with colorful lines running up and down it. The system locks up on this screen and all I can do at this point is hold to power button down to hard reboot it.

Here is a picture of what it looks like. I know it looks like monitor damage but the monitor is 100% fine elsewhere. I only see that when I shut down and when the machine comes back up everything is fine.

[IMG]http://i13.tinypic.com/8byos3r.jpg[/IMG]

Does anyone have any idea wtf that is and how to fix it?

---

### Post by lightstream on 2007-12-01
I've never experienced anything like this, but it does remind me of the sort of things you see sometimes when a graphics card is initialising or shutting down. Often caused in those cases by it switching graphics mode, but not clearing the display memory so what's in the video buffer isn't valid display data.

Do the lines move at all, or are they quite still once they appear? It could be that for some reason Gutsy is dumping weird stuff into the display memory which could indicate a problem somewhere...

---

### Post by Lord Illidan on 2007-12-01
I get these when hibernating/suspending on my laptop, a sony vaio. Wierd, yes, but it doesn't seem to have any negative effects, apart from scaring me sometimes, as I think that my monitor went bonkers!

---

### Post by JaggedOne on 2007-12-01
The lines don't move at all.

---

### Post by skymera on 2007-12-01
i get that with my laptop and also some other patterns.

seems normal for lappys.

---

### Post by lightstream on 2007-12-02
> **skymera said:**
> seems normal for lappys.

Normal for ~some~ lappys - I wonder what it is that all your laptops have in common? 

Maybe if you (and anyone else who gets this issue) can post your hardware specs a pattern may emerge?

It's good that no-one seems to have any problems because of it, but it might be that Ubuntu is writing some data to the wrong place during shut-down (ie to the video buffer rather than to wherever it should go).

---


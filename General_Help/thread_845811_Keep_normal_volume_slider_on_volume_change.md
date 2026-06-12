---
title: "Keep normal volume slider on volume change"
date: 2008-07-01
forum: General Help
---

### Post by syko21 on 2008-07-01
When running ubuntu without compiz fusion the slider looks like the first picture, small and simple. With fusion the icon is a rather large transparent square that takes up a large part of the screen. Is there any way to keep it so that it looks non-composited even when fusion is running?

---

### Post by rainwalker on 2008-07-01
This is going to sound really dumb, but try changing your theme around a bunch of times.

I noticed that huge volume slider when I first installed Ubuntu, but somehwere between then and now it got changed to the attached image...that bar shows up in the middle of my screen whenever I change the volume.

---

### Post by syko21 on 2008-07-01
Did not work. I just kept getting different variations of the large transparent slider.

---

### Post by rainwalker on 2008-07-01
Hmm...lucky :? 
I actually kinda liked the big display icon.

Although, maybe it wasn't changing themes. I also use [KeyTouch]("http://keytouch.sourceforge.net/") to get my multimedia keys working. I guess that could have done it?

I'll keep looking

---

### Post by 16777216 on 2008-07-01
Yes, KeyTouch is drawing the volume bar for you rainwalker.

---

### Post by rainwalker on 2008-07-01
> **16777216 said:**
> Yes, KeyTouch is drawing the volume bar for you rainwalker.

Ah...how do you know?

---

### Post by 16777216 on 2008-07-02
It has a screen shot on their web site.
Also, I installed it just to make sure, and sure enough gtk themed progress bar for the volume.

---

### Post by rainwalker on 2008-07-02
> **16777216 said:**
> It has a screen shot on their web site.
Also, I installed it just to make sure, and sure enough gtk themed progress bar for the volume.

Hmm ok, well thank you then, I'd been wondering about that :)

---

### Post by isaacj87 on 2008-07-02
> **rainwalker said:**
> Hmm...lucky :? 
I actually kinda liked the big display icon.

Although, maybe it wasn't changing themes. I also use [KeyTouch]("http://keytouch.sourceforge.net/") to get my multimedia keys working. I guess that could have done it?

I'll keep looking

Off topic: Rainwalker, I can confirm it was KeyTouch that did it. In fact, it managed to screw up my laptop somehow. I had to remove it.

---

### Post by rainwalker on 2008-07-02
> **isaacj87 said:**
> Off topic: Rainwalker, I can confirm it was KeyTouch that did it. In fact, it managed to screw up my laptop somehow. I had to remove it.

Ack, sorry, it works great for me :?

---

### Post by syko21 on 2008-07-02
I tried installing it but I have no idea what keyboard my laptop has and really don't want to screw it up because it's working really well right now.

---

### Post by isaacj87 on 2008-07-02
> **syko21 said:**
> I tried installing it but I have no idea what keyboard my laptop has and really don't want to screw it up because it's working really well right now.

No! lol, don't install KeyTouch unless you have an external keyboard (such as a wireless usb keyboard). I don't think your system will like you if you do ;)

Sorry we got off topic, but I have some new information concerning your question. According to a dev that works closely with Compiz Fusion (his name is b0le), CF is only indirectly responsible for the drawing of the "other" volume indicator. Here's what he said: 

> It already happens for the sound overlay, but this is something that needs to be handled by whatever is drawing it, not compiz... (whatever is doing the drawing of the volume indicator (in gnome) detects if there is a compositing manager, and acts on that)

Apparently, the volume indicator comes in the gnome-control-center package. This has a composite extension that detects if a compositor (i.e. Compiz Fusion) is running and will change on its own. I've been looking for a way to disable that extension (via gConf), but I haven't had any luck.

---


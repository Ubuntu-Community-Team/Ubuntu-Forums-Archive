---
title: "AiGLX on old computers?"
date: 2006-11-26
forum: General Help
---

### Post by Sunnz on 2006-11-26
I found an old computer today (P2 55mhz) and installed Xubuntu.10 on it, it is great - fast enough for such old machine.

However I noticed that the drawing can be a bit slow at times...

So I am wondering if getting AiGLX/Beryl on it would help? (Using GPU to cut CPU consumption?)

Its got a GeForce2 graphics card... would the new nvidia driver work on it?

---

### Post by viciouslime on 2006-11-26
I believe only the legacy driver will work with this card so you would have to setup xgl and do it that way. Good luck!

---

### Post by sumguy231 on 2006-11-26
Not all Geforce2 cards require legacy drivers, there's a list [here]("http://download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-a.html") for future reference.
Believe it or not,  I'm actually successfully running AIGLX and Beryl on my Geforce2.
Edit: But I'm not so sure it would help out your PII that much.

---

### Post by K.Mandla on 2006-11-28
Ditto that. I use the nvidia-glx-legacy driver on a GeForce2 Ti and a GeForce4 440 Go and a GeForce2 GTS, but nvidia-glx on a GeForce4 440 MX. The only one that couldn't do Beryl was the Ti card, so I believe it to be a hardware issue and not a driver one.

Of course, how *well* I could run XGL and Beryl depended on the amount of memory on the card. The Ti and the 440s had 64Mb but the GTS had 32Mb. It was a wee bit sluggish at 1280x1024, as you might imagine.

---

### Post by ~LoKe on 2006-11-28
I can understand why you'd want to run AIGLX on that machine, but why on earth would you even consider using Beryl?

---

### Post by K.Mandla on 2006-11-28
For a challenge! :biggrin:

---

### Post by Sunnz on 2006-11-29
Read first post would help lol.

Thanks for the suggestions!

---

### Post by madmetal on 2006-11-29
i found this one..
[http://youtube.com/watch?v=h3Y6F1dSR8A](http://youtube.com/watch?v=h3Y6F1dSR8A)
XGL + Beryl on UBUNTU Linux (Dapper)
Config:
PII-450 mHz
128 Mb Ram
GeForce MX440 32 Mb RAM

so good news..;)

---

### Post by strabes on 2006-11-29
wait you want to use aiglx+beryl to *speed up* your computer???? maybe just aiglx...

---

### Post by RAOF on 2006-11-29
> **strabes said:**
> wait you want to use aiglx+beryl to *speed up* your computer???? maybe just aiglx...

It can speed things up.  Among it's other (crazy effects driven) features, Beryl is a composite manager, and that **really** helps in moving windows around and stuff.

---


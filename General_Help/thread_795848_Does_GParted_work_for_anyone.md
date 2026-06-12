---
title: "Does GParted work for anyone?"
date: 2008-05-15
forum: General Help
---

### Post by Jordanwb on 2008-05-15
I've tried two different versions (0.3.7 and 0.3.1) on four different computers and it won't work. Xorg keeps on crashing on me. Each computer has a different video card.

ATI Radeon x1600 Pro
S3 Savage 4
Intel 82810
NVidia something or other.

Has anyone got GParted to work?

---

### Post by Joeb454 on 2008-05-15
Through a fully installed system? No I've never tried it.

From the Ubuntu Live CD? Yes it works everytime :) You may also want to look into the GParted Live CD, though I'm sure the normal Ubuntu one would work fine for you :)

---

### Post by Fenris_rising on 2008-05-15
i use it. but i ant get it to detect my sata drive. IDE HDD no problem
works gr8.

---

### Post by ccw127 on 2008-05-15
I used to use the a live cd version of gparted quite a bit. Though I don't remember if I ever tried it with a SATA drive like the previous RE. Perhaps find an older revision?

note: I just took a look in my 'tools cd case' and the version I have is "GPARTED-CLONEZILLA LiveCD". I did a quick search and here is the link...

[http://gpartedclonz.tuxfamily.org/](http://gpartedclonz.tuxfamily.org/)

I use 2.3 (I checked and that is still the newest version).

Chris

---

### Post by Jordanwb on 2008-05-19
I use the one from the GParted website and it always fail on me.

---

### Post by kellemes on 2008-05-19
> **Jordanwb said:**
> I use the one from the GParted website and it always fail on me.

You're not very clear on how it's not working..
You start it up.. what happens next?

---

### Post by p_quarles on 2008-05-19
Yeah, GParted has always worked fine for me. Generally speaking, if video fails to load it will give you instructions on forcing a safe video mode. 

In any case, just about every live CD out there (Puppy, Knoppix, Sidux, Slax) has GParted.

---

### Post by Jordanwb on 2008-05-19
Well I don't know what to say really. I get a message saying the Xorg failed to start and that I should try the Forcevideo command. For my laptop (for example) I selected S3 and it failed to start again.

---

### Post by p_quarles on 2008-05-19
> **Jordanwb said:**
> Well I don't know what to say really. I get a message saying the Xorg failed to start and that I should try the Forcevideo command. For my laptop (for example) I selected S3 and it failed to start again.
Again, there is a "safe" option (something like VESA at 800x600) that should work with just about anything.

---

### Post by Jordanwb on 2008-05-19
Yay it works now.

---

### Post by Fenris_rising on 2008-05-19
cheers chaps glad to say that after abject faliure with the gparted live cd (not detecting my sata drive) having viewed this post ive down loaded "GPARTED-CLONEZILLA LiveCD" and it works perfectly. i only had to select the correct method for my display to work. heres to the ubuntu forums \-/ cheersssssss

---

### Post by ccw127 on 2008-05-19
Glad to hear it Fenris!

Chris
[email]hololight@gmail.com[/email]

---


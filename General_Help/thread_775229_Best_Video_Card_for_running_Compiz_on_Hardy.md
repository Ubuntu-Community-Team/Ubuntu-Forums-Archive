---
title: "Best Video Card for running Compiz on Hardy?"
date: 2008-04-29
forum: General Help
---

### Post by JimTDI on 2008-04-29
Can one of you experts please tell me what a good video card for Compiz is?  I have a Dell 400sc server which I believe has integrated Intel graphics card.  I want to replace my video card with probably an AGP, and probably Nvidia as I understand this chipset works well with Compiz.  Is this true?

Here's a couple of choices I have (link below).  Can someone tell me what I should get?  Any recommendations would be really appreciated!

[http://nanosys1.com/video-agp-video-cards-nvidia-chipset.html](http://nanosys1.com/video-agp-video-cards-nvidia-chipset.html)

---

### Post by gsiliceo on 2008-04-30
I use the cheapest one on that page (fx5200) and im very pleased, ubuntu installed the drivers without problems and compiz works excellent.

---

### Post by acelin on 2008-04-30
Best one? The highest Nvidia- any Nvidia GPU's will work.

---

### Post by JimTDI on 2008-04-30
> **gsiliceo said:**
> I use the cheapest one on that page (fx5200) and im very pleased, ubuntu installed the drivers without problems and compiz works excellent.

Thanks for the info!  That card fits nicely into my budget right now too!  :-)

---

### Post by JimTDI on 2008-04-30
> **acelin said:**
> Best one? The highest Nvidia- any Nvidia GPU's will work.

OK - thank you!  I'm probably going to get the low end card just due to my budget.  I really don't need a gamer's card or something with a gazillion megs of RAM on it, but I'd have to agree that the high end card would be the "best".  Appreciate your reply!

---

### Post by sujoy on 2008-04-30
generally ATIs arent good with linux, so go for nvidia

---

### Post by toobitz on 2008-04-30
> **sujoy said:**
> generally ATIs arent good with linux, so go for nvidia

I can back up this statement, both nvidia and ATI/AMD are actually not ideal since their own drivers are proprietary (i.e. available binary only) but I've never experienced any problems on boxes with nvidia cards whereas my laptop with an ATI is a constant pain in the ***.

---

### Post by Devlin67 on 2008-04-30
Set up Hardy on two systems two days ago. One ATI1600XT and a Nvidia FX5200. Used Envy for both. Both runs compiz and AWN flawlessly.

---

### Post by klange on 2008-04-30
Depends on *exactly* what you're looking for. If you want it to just plain work and work fairly well, Intel is the way the go. First off, completely open and true drivers - the open source drivers are *the* drivers. Secondly, they're cheap - they come with virtually all machines now unless you bought a gaming rig, you already said you believe your machine has one. Third, they're really not that bad - mine can pump out Compiz at a respectable framerate on two screens totaling 2960x1050. Last, they're the easiest to use - just install Ubuntu and bam!

If you're looking for best performance, I can't really say. I've heard great things about nVidia, but you have to go through the install process. ATi's own drivers suck, but the open-source 'radeon' is just as stable as the Intel driver.

If you're an open-source addict, stick with your Intel. It'll be the most feature-ful driver as soon as DRI2 is merged into master.
If you're a gamer, I've heard nothing but good things about nVidia.
If you're looking for performance and open-source, for now you should stick with an older ATi card (my x800 works great.)

---

### Post by JimTDI on 2008-05-01
> **WindowsSucks said:**
> Depends on *exactly* what you're looking for. If you want it to just plain work and work fairly well, Intel is the way the go. First off, completely open and true drivers - the open source drivers are *the* drivers. Secondly, they're cheap - they come with virtually all machines now unless you bought a gaming rig, you already said you believe your machine has one. Third, they're really not that bad - mine can pump out Compiz at a respectable framerate on two screens totaling 2960x1050. Last, they're the easiest to use - just install Ubuntu and bam!


Hey - I appreciate your comments (and everyone else's!)  I got the case cracked open - turns out I had an ATI card (not AGP) inside.  That card (made for Dell by ATI I would guess) would NOT do Compiz desktop, so I went and bought the $39 nVidia and now Hardy does Compiz just fine.  That and AWN is about all I want to do - surf the web, read the forums, and just have some eye candy to show off when my Windows friends come over.  :-)

Thanks again everyone for your suggestions - what a difference $39 can make...  !!

---

### Post by Mrandersonjr on 2009-03-08
If you need a video card for compiz on hardy,look no further than the Nvidia 2600.It's old enough so that the devs will support it,all you need to do is envyNG the drivers.

---


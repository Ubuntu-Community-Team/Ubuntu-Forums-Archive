---
title: "Minecraft, dual screen"
date: 2014-08-23
forum: General Help
---

### Post by nathan-cooley on 2014-08-23
Hello Ubuntu forums, 

Working for a Minecraft server hosting company, I tend to play the game a lot. I seem to have run into a weird and very annoying issue that I can't seem to determine the cause of. 

The whole Ubuntu experience on a dual screen set up is quite nice, but when I close the window for Minecraft, whether or not it was running in full screen or windowed, my left screen becomes disabled. I have to go to the display settings and enable it again, and all is well. But, this happens every single time, and the most confusing part of this is that this issue seems to be limited to *only* Minecraft. 

I know this may not be the right place for such an inquiry, but I thought I'd give the forums a go because I cannot for the life of me figure this one out. Any help or insight on the matter would be greatly appreciated. 

Loosely applicable system details attached in a screenshot below.

---

### Post by oldos2er on 2014-08-23
Screenshot is quite difficult to read for my old eyes. Could you please tell us which video card you're using, and any proprietary drivers that are in use?

---

### Post by nathan-cooley on 2014-08-23
> **oldos2er said:**
> Screenshot is quite difficult to read for my old eyes. Could you please tell us which video card you're using, and any proprietary drivers that are in use?

Hey, thanks for replying -- No problem: 

I have two cards in my machine currently. An Nvidia GF199 (GeForce GT 620 OEM) and using X.org Nouveau driver (open source) This card is enabled, having two monitors attached, but is not "in use" because I've been running into problems with getting that card to communicate and play nicely with my other card: 

Second card is an AMD Cape Verde XT (Radeon Hd 7770 GHz by XFX), again using the open source X.org display driver wrapper. This is the card this is running my two active monitors. I'm planning on getting an identical card to replace the OEM that came with the machine when I first bought it, maybe SLI them together. 

But more to the point, I am not using any proprietary drivers for either card at the moment.

---

### Post by sotiris2 on 2014-08-24
Not sure about your problem but I do not think crossfire actually 'works' in linux. Sure you can enable it via catalyst but there doesn't really seem to be much benefit. Open driver doesn't support it at all yet.

---

### Post by lah7 on 2014-08-24
Seeing as Minecraft is a Java game: Which Java runtime do you use? You could try an alternate or newer runtime to see if that changes the behaviour.

There's the **OpenJDK Runtime** (open source, in the repository/software centre) and **Oracle's Runtime** (which I believe is closed source and isn't in the repository), but can be [easily installed one search away]("https://www.google.co.uk/#q=install+oracle+java+ubuntu+14.04").

---

### Post by speedwell68 on 2014-08-24
> **lah7 said:**
> Seeing as Minecraft is a Java game: Which Java runtime do you use? You could try an alternate or newer runtime to see if that changes the behaviour.

There's the **OpenJDK Runtime** (open source, in the repository/software centre) and **Oracle's Runtime** (which I believe is closed source and isn't in the repository), but can be [easily installed one search away]("https://www.google.co.uk/#q=install+oracle+java+ubuntu+14.04").

As an aside, it might help.  Mojang recommend that Oracle's Java is used rather than OpenJDK.

---


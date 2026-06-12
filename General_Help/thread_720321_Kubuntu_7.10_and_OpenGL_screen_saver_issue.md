---
title: "Kubuntu 7.10 and OpenGL screen saver issue"
date: 2008-03-10
forum: General Help
---

### Post by TWO on 2008-03-10
Hi

I'm currently running Kubuntu 7.10 and KDE 3.5.8. I've had a problem with the OpenGL screen savers, where on selecting the corresponding 'setup' button for the screen saver makes the system reset to the KDM login window. 

Has anyone else experienced this problem and if so, any ideas on how to resolve this? 

Thanks in advance.

TWO

---

### Post by kuja on 2008-03-10
Well, it's crashing X. Can you run other OpenGL apps okay? Were you able ot use the OpenGL screensavers previously?

---

### Post by FuturePilot on 2008-03-10
What graphics card do you have and what driver are you using? If you are using a non 3D accelerated driver, certain graphic intensive things will tend to crash X.

---

### Post by TWO on 2008-03-12
I'm not using any noteworthy graphics card. It's a low-end dell laptop, the inspiron 1300. They stopped doing this model last year I think. 
Anyway, the xorg.conf file shows the following under devices:

> 
Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"


I don't know whether I was capable of using OpenGL screen savers previously since I've only had Kubuntu installed for like a week or so after jumping between various OSes. It was only when I went to look at the settings that I discovered that I have the problem.

Any OpenGL tests I can run to check this out?

Thanks

TWO

---

### Post by kuja on 2008-03-12
Hmmm, games work well, how about the game crack-attack?

---

### Post by TWO on 2008-03-13
> **kuja said:**
> Hmmm, games work well, how about the game crack-attack?

Just installed it now and it ran without a problem. I don't think games have ever caused a problem. Just seems to be when I select 'setup' for OpenGL screensavers...

---

### Post by TWO on 2008-03-18
OK, I just installed and played Scorched Earth 3D and after a few minutes of play, my system crashed and I was just left with a black screen. 

I suppose this indicates that I have a problem with OpenGL? 

Is this just because of my Intel Corporation Mobile 915GM/GMS/910GML card, or could it be the driver?

(I will one day invest in a better laptop...:-?)

---


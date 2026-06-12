---
title: "Laptop shuts down randomly"
date: 2007-07-20
forum: General Help
---

### Post by mondokoosh737 on 2007-07-20
Hi, I've been using Ubuntu for a few weeks now (and am pretty new to it), but recently it will randomly shut down. It didn't do this sort of thing when it was on XP or Vista, but it does it now. It doesn't crash or quickly shut off, but it goes through a shutdown sequence. And it's never in screensaver mode or anything, because I'll be working on something when it does this (and I've already checked the settings). It won't be doing something difficult either, I'll be word processing or something. 

And it can't be heat issues because the laptop will only have been running for 10 minutes or so, and it's not hot to the touch. But one time it did say it reached critical temperature (100 degrees Celsius or something), but I felt it and it barely felt warm. Since then though it doesn't display that message when shutting down. Is there anything I can do?

---

### Post by n00bWillingToLearn on 2007-07-20
Does it only do this when you are running off battery? It could be that for whatever reason Ubuntu thinks that you are running low on battery when you are not. If suspend works with your laptop try setting it to suspend instead of shutting down when it thinks you are running low in System -> Preferences -> Power Management if it starts suspending instead of shutting down then you can narrow down the possible problems.

---

### Post by mondokoosh737 on 2007-07-20
I've had that setting set to hibernate instead of shut down for a while, and it instead shuts down, so at least it's not that. I've noticed that when I have my laptop cooler under it, it takes longer for it to shut down. It's possible it thinks its getting too hot and needs to shut down, even though it shuts down when it's barely warm.

---

### Post by steevols on 2007-07-20
Well, if you've got the tools, pop the bottom panel off and clean the CPU heatsink. Who knows? Linux, like everything else, has its little idiosyncrasies, and this might be one of them.

What model of laptop do you have? It could be a known issue.

---

### Post by mondokoosh737 on 2007-07-21
Okay, I opened up my laptop and cleaned it out, and cleaned the fans, but my laptop still randomly shuts down all the time. Well at least it's clean! :) But my laptop's pretty obscure - it's a Systemax Pursuit 4110.

---

### Post by n00bWillingToLearn on 2007-07-22
Try using something like lm-sensors to see what the temperature sensors are reading

---

### Post by mondokoosh737 on 2007-07-23
I installed lm-sensors, but it says "No sensors found", even though I went through the whole sensors-detect thing. Which is weird because I know I have a temperature sensor in my laptop. 

But it hasn't randomly shut down for a few days now, so I think the cleaning of it has helped! Thanks to everyone for helping me out!

---

### Post by mondokoosh737 on 2007-07-23
Grr! Literally two minutes after I posted the last post, my laptop randomly shuts down! And it wasn't even warm, it was like lukewarm.

Is there any way to change the temperature threshold or turn off the sensors?

---

### Post by henriquemaia on 2007-07-30
> **mondokoosh737 said:**
> Grr! Literally two minutes after I posted the last post, my laptop randomly shuts down! And it wasn't even warm, it was like lukewarm.

Is there any way to change the temperature threshold or turn off the sensors?

I’m having a problem similar to yours on a friend’s laptop. I wish I know a way to change the temperature threshold. Can anyone help?

---

### Post by QCompson on 2007-07-30
I'm afraid I can't help you change the temperature shut-off threshold, but for my laptop I can get the temperature using:
```
acpi -t
```
lm-sensors won't detect any sensors for me either.

---

### Post by henriquemaia on 2007-07-31
I had the laptop turned off for several hours. I tuned it on, had it working for less then 1 minute (it was finishing the boot procedure) and it shut down with temperature critical of 40 C. Really weird bug.

---

### Post by henriquemaia on 2007-08-02
> **henriquemaia said:**
> I had the laptop turned off for several hours. I tuned it on, had it working for less then 1 minute (it was finishing the boot procedure) and it shut down with temperature critical of 40 C. Really weird bug.

I solved this issue installing PCLinuxOS on my friend’s laptop. This is a Ubuntu specific bug.

---


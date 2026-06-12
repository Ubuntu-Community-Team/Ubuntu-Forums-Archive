---
title: "Ubuntu randomly dies"
date: 2008-02-29
forum: General Help
---

### Post by magikdonkey on 2008-02-29
Hi, Well I have a dual boot system with Windows XP and Ubuntu 7.10

Windows seems to be running fine no crashes to note.

When I'm using Ubuntu occasionally it will just die like someone has pulled out the power. I have checked the logs but there doesn't seem to be any at the time of the crash.  Normally when the crashes occur I'm running Firefox and Rhythmbox. 

My system:
Processor: AMD  4600+ AM2 
Ram: 2GB
Mobo: MSI NVIDIA nForce 570 SLI (i think)
Graphics: Geforce 7900gs
Powersupply: Antec truepower 2 550W

Please can anybody help?

Edit: Update

After checking temperatures at Idle and in 3d applications they seemed fine until I came across a game that causes the crash every time I run it - 'planet penguin racer'. It normally occurs less than 2 mins into the game.

---

### Post by kesman on 2008-02-29
Could this be due to overheating?
Can you install some program that would show the temperature of your cpu, like gkrellm with lm-sensors ?

---

### Post by magikdonkey on 2008-02-29
Thanks for the reply, I checked in xp and the temps were fine so i'll try checking the temps in Ubuntu.

---

### Post by lavinog on 2008-03-02
> **magikdonkey said:**
> Hi, Well I have a dual boot system with Windows XP and 
After checking temperatures at Idle and in 3d applications they seemed fine until I came across a game that causes the crash every time I run it - 'planet penguin racer'. It normally occurs less than 2 mins into the game.

Was there a time that ubuntu hasn't crashed (previous version...etc)?

What happens when you run glxgears (type glxgears in a terminal)
approx what are your frame rates and does your computer crash after a couple mins of using it?
If it does then the problem would most likely be due to your video driver...are you using the restricted driver?

If it is a temperature issue you should be able to notice that after restarting from a crash that the system would crash much quicker...opposed to when your system has been off for a couple of hours...If this is the case watch your cpu load (add the system monitor applet to your gnome panel...or install gkrellm) if you see that your cpu load is over 5% when idle, then there could be a program causing your issue.

---

### Post by Crafty Kisses on 2008-03-02
> **magikdonkey said:**
> Thanks for the reply, I checked in xp and the temps were fine so i'll try checking the temps in Ubuntu.

A couple of things you can do is, check your X server logs, or post the following output:
```
top
``` From that we can see how much RAM is being used, and see if anything is causing the crash.

---


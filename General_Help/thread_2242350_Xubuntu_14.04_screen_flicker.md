---
title: "Xubuntu 14.04 screen flicker"
date: 2014-09-01
forum: General Help
---

### Post by royston2 on 2014-09-01
Toshiba Satellite P200D, 2GB, AMD Turion 64X2

Every few seconds the entire screen flickers. This began after updates over the weekend (30-31 August)

Things I've tried:
Restart and cold start
Display compositing ON or OFF makes no difference
Screen refresh is 60Hz, I get no alternatives to this on the pull down (Note: If I set resolution to any non-native size screen refresh sets itself to 59.8Hz)
After reading forums I tried installing compton and typing compton --vsync opengl. No effect.

I'll be grateful for help with this.

---

### Post by joan-nadal-brotat on 2014-09-11
I have the same problem. I am looking for a solution, because is really uncomfortable!

---

### Post by ThatBum on 2014-09-11
Is it the backlight that's flickering? If so it could be a hardware issue, failing inverter perhaps.

---

### Post by lchurch2 on 2014-11-22
Although no one seems to be addressing the real issue. This is a change in the linux kernel starting with 3.13.35 and is ongoing.  It actually effects more than Ubuntu and its derivatives and is not limited to any one particular GPU.  It can be documented on everything from Dells to Toshibas and GPUs by Intel to Nvidia.  The main systems generally effected are laptops or desktops with onboard integrated GPUs.  The only solution I have been able to find thus far is to downgrade the kernel to 3.13.34 and freeze it there.  Upstream is not particularly interested in looking into the problem as a number of different blogs have told those effected to 'buy a better machine'.

---

### Post by aixin on 2014-12-22
Ongoing, unsolved, is there a bug report for this we should be cheering for?

---

### Post by mörgæs on 2014-12-22
A bug report for 15.04 will get more attention. Before reporting please see how it works here. 

A live boot will do.

---


---
title: "PC extreamly slow after left opened for long periods"
date: 2007-05-17
forum: General Help
---

### Post by Browser_ice on 2007-05-17
I have this PC in the office where I installed Ubuntu 7.04 but I noticed that if we let it opened for long periodes of time (hours or over 24hrs), it because extreamly slow (takes 10-15 min to react to a mouse click) and during that time the disk led doesn`t show any activities.

I had the same problem on the previous linux version on it (Fedora Core 6) but the guy who installed it said it was slow because it was trying to always connect to the network for anything. 

It is permanently connected to the network.

So I do not know how to go about it. How should I investigate ?

Which monitoring tools can I use to find out what the heck is going on, where and why ?

PC Specs :
IBM Netvista Pentium-4
No idea on how many Megs it has as it is currently slllloooooowwwwwww trying to run Synaptic update manager

---

### Post by meldroc on 2007-05-17
This sounds like a heat problem.  When you take the cover off the machine, all of the sudden, the airflow is messed up, and the fans can't blow as much air over the processor and other components that need cooling.  Chances are good the system will respond by slowing its clock speed down, or even shutting off.  Also, if heat is an issue for too long, you'll end up frying components.

Best to look into this...  I'd suggest installing ksensors or some similar program designed to monitor things like CPU temperature.

---

### Post by Browser_ice on 2007-05-17
Is ksensors accessible through the Synaptic manager ?

What about monitoring tools for Disk activities, network activities and also for analysing a disk for possible errors ?

---

### Post by meldroc on 2007-05-18
Yes, you should be able to install ksensors with Synaptic.  Ksensors is a KDE-specific tool, but I imagine there's equivalent tools for GNOME if you're using that.

Also, if it is a heat problem, I've worked around such problems in the past by getting a desk fan and pointing it directly at the motherboard.  See if that helps you.  It's ugly, but it will at least tell you if this is a heat issue.

---

### Post by Cene on 2007-05-18
You should also check the "top" command by issuing it from terminal.

---

### Post by Browser_ice on 2007-05-22
I installed xsensors 0.50 but when I start it (even after restarting PC), nothing shows up in its window and the menu contains now options, nothing but windows's options.

I heard something about hdtemp to monitor hd temperature but cannot find it in the add package -all sources.

---

### Post by mills on 2007-05-22
you'll need lm-sensors to use ksensors


```
sudo aptitude install lm-sensors
```

---

### Post by Browser_ice on 2007-05-22
I did.

I just started to follow the "[How to: Install and configure lm-sensors]("http://ubuntuforums.org/showthread.php?t=2780&highlight=xsensors")".  But when I got to "**3. Now run sensors-detect**", I replied YES to the first 2-3 questions and then the whole graphic screwed up completly and I couldn't do anything else. I had to reboot completly. I'm typing on another PC cause I didn't know if I screwed up my Ubuntu or not.

---


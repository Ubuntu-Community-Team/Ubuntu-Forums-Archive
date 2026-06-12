---
title: "Ubuntu optimization"
date: 2013-08-08
forum: General Help
---

### Post by daaatz on 2013-08-08
Hi guys,
can You write in this topic your ideas about optimizating ubuntu ?

What I've done is:

<code>sudo apt-get install preload

</code>

Set up GRUB_TIMEOUT to 0.
and changes swappines to 10.
Like in:
[http://www.upubuntu.com/2012/06/11-tips-to-speed-up-computers-running.html](http://www.upubuntu.com/2012/06/11-tips-to-speed-up-computers-running.html)
[http://www.howtogeek.com/115797/6-ways-to-speed-up-ubuntu/](http://www.howtogeek.com/115797/6-ways-to-speed-up-ubuntu/)

But Im looking for some more advanced ( staying of course in unity ) solutions.
Thanks!

---

### Post by daaatz on 2013-08-08
Im also curious does compiling kernel influences on speed up system ?

---

### Post by Sly14Cat on 2013-08-08
If you open the program "Startup Applications" after entering
***sudo sed -i "s/NoDisplay=true/NoDisplay=false/g" /etc/xdg/autostart/*.desktop***
into the terminal, you'll see a list of things that are started up by default on your cmoputer that are usually hidden. I've disabled things I don't need such as: Backup Monitor, Desktop Sharing, Chat and Orca Screen Reader. So I suggest you research your startup programs and find what they do and remove them if they are not needed. As to compiling the kernel, I've always heard of this but have used linux on and off for about a year and have never had to comple the kernel. I get a boot time of 19 seconds on both Xubuntu and Ubuntu. If you're looking for a snappy system use Xubuntu and install compiz if you like the effects.

---

### Post by 3rdalbum on 2013-08-08
> **daaatz said:**
> Hi guys,
can You write in this topic your ideas about optimizating ubuntu ?

What I've done is:

<code>sudo apt-get install preload

</code>


It's always slowed down any computer I've tried it on. I don't recommend preload.

> Set up GRUB_TIMEOUT to 0.

Rather a bad idea for a dual-boot system, of course.

> and changes swappines to 10

If you've got plenty of RAM (two gigabytes or more), you don't need swap at all:

```
sudo swapoff -a
```

---

### Post by daaatz on 2013-08-08
> **3rdalbum said:**
> 
Rather a bad idea for a dual-boot system, of course.


I have only ubuntu ;)

---

### Post by daaatz on 2013-08-08
Hmm will try with ths auto start thanks ;)
Preload really ? Does anyone think about preload same ? Wonder why it is in every speed up ubuntu tricks ;)

---

### Post by Cheesemill on 2013-08-08
Preload will make your system start slower as it has to load all of your most used applications from the HD into RAM.

However once the system is booted the applications will start quicker.

I use preload on my machines and have never had any problems with it.

---

### Post by daaatz on 2013-08-12
Hmm I moved to XFCE working on it for few days, seems working faster :) But no fireworks.
Any way good fast stable system for developing ;-)

---

### Post by VMC on 2013-08-12
Regarding compiling the kernel. I use to do that a lot, and found I can reduce the size but never the speed. The kernel is optimized in areas where speed is a factor.

---

### Post by deadflowr on 2013-08-12
If you want to optimize Ubuntu/w unity, then figure out which parts/effects to disable in compiz.

I myself cannot help in this regard as I move in the opposite direction and enable more and more options.
I like eye candy, and exploding windows.

---

### Post by daaatz on 2013-08-13
I had times when on slackware is was working only on fluxbox :D
But Im using mainly for developing so need for efects ;)

---


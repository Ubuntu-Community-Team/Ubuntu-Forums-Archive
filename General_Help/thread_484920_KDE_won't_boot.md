---
title: "KDE won't boot"
date: 2007-06-26
forum: General Help
---

### Post by TorchlightJay on 2007-06-26
Okay so I have a friend whom is having graphical errors. Basically, Kubuntu won't start. I just updated it from Dapper to Feisty. My friend cannot boot into kubuntu now. Essentially, when he starts, kdm won't start and he gets a blank screen with a blinking cursor. They are using nvidia card. Now I haven't seen the actual computerbut am trying to repair it over SSH. Maybe I should mkae it VESA? Any ideas? Thanks.

---

### Post by reckless2k2 on 2007-06-26
you can try vesa driver but i think the path to fiesty from dapper was through edgy. if you didn't follow that path, you mgiht not be able to fix it. not sure.

---

### Post by ronniet on 2007-06-26
I had a similar problem when I installed the nVidia drivers from the repos on my Kubuntu.

From what I can gather, it seems as though its being put into a bad/unsupported resolution?

If I remember rightly, I pressed Alt+F1 to take me to a command line and from there I had to run the X config utility and just chose defaults for everything and hey presto! Got my Kubuntu back.

---

### Post by TorchlightJay on 2007-06-26
Sounds like it might work. Really retarded question, how do I run the X config utility? I think it may be a Nvidia problem too. My other computer that I personally have runs nvidia too and I have had a hell of a time trying to get proprietary drivers working. I think it might be that so ya, just let me know how to do that and I will.

---

### Post by dabl on 2007-06-26
I'd go at it like this:

First, get a working GUI.  In the console:

```
sudo dpkg-reconfigure xserver-xorg
```

on the first screen, do NOT let it autodetect the graphics chip, on the second screen choose "VESA", and then accept defaults up to the monitor section.  Pick one screen resolution to "x" that you can live with for awhile, like 1024 x 768, and then a reasonable refresh rate for your monitor or LCD.  When you finish the script, it will dump you back to the command line.  Type ```
startx
``` to get your GUI desktop.

Next, do whatever updating/upgrading you want to do with your system, using apt-get or Synaptic.

Then, un-install whatever remains of your previous graphics driver may be lurking in /etc/init.d/, or as nvidia-glx packages.

Last, re-install the appropriate video driver and configure your /etc/X11/xorg.conf file (or perhaps restore your last backup).  If it's an Nvidia chip, I like the Envy script installer, which you can download from here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) 

HTH:)

---

### Post by TorchlightJay on 2007-06-26
Yo, it worked like a charm, thank you all for your help!

---


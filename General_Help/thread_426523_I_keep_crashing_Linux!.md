---
title: "I keep crashing Linux!"
date: 2007-04-28
forum: General Help
---

### Post by Crashing on 2007-04-28
I don't know what's wrong with me! I've crashed multiple distros so badly that they had to be reinstalled. Ubuntu crashed 3 times during installation, I broke Mandriva 2007 free 3 times in 2 days and the 4th install was bad, I broke Open SUSE 10.3 once and this will be the second time I've broken Kubuntu. I would like to stay with Kubuntu as it is the most durable distro I've found yet, but I'd like to figure out what I do to screw it up. I have no idea what happened the first time Kubuntu wrecked. I'm wondering if it crashed this time because of some modifying/configuring I did to X11 and Xorg.conf to make my screen resolution higher. 
Each time Kubuntu has crashed, I boot it up and I get a wallpaper and pointer and it goes no further. I do a ctrl + alt+ Backspace and go to a console login. I try to run Katapult, but It says it couldn't connect to the X-server. I have rebooted several times and get the same error. Is there something I need to do or stop doing? I'm getting rather frustrated at some times.](*,) ](*,)

---

### Post by K.Mandla on 2007-04-28
Stick with it: It's a good way to learn things. 

What kind of machine are you using? Can you tell us what you were doing before you restarted Kubuntu? Did you install anything funky, or use outside software?

---

### Post by Crashing on 2007-04-30
> **K.Mandla said:**
> 
What kind of machine are you using? Can you tell us what you were doing before you restarted Kubuntu? Did you install anything funky, or use outside software?
AMD Athlon 1GHz processor
458 MB RAM
ATI Rage 128 graphics card
I had hooked it up to a big monitor that could do 1600x1200 to see if I could make it work at higher resolutions than 1024x768. I did a sudo apt-get install xorg-driver-fglrx. Then I did some of the other steps mentioned in the Ubuntu wiki. I think what I did wrong was I switched the xorg driver to fglrx without configuring it all the way.:rolleyes: 
that reminds me...... how do I figure out what the address of the graphics card is? It is in the AGP slot on my mobo. That's where I stopped during configuration because I couldn't figure it out.

---

### Post by Crashing on 2007-05-03
Bump..........
Anyone?

---

### Post by zvacet on 2007-05-03
Boot up in recovery mode nad type 

```
dpkg-reconfigure xserver-xorg
```

Select **vesa** and after your graphic works go and find proper drivers for your card.

---


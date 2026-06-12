---
title: "Screen Alignment"
date: 2007-04-26
forum: General Help
---

### Post by sparxx on 2007-04-26
Just made the switch from XP to ubuntu and so far so good, aside from one minor issue.. my screen isnt aligned properly. 

Everything is shifted to the right about 1 centimeter, cutting off the 'x' button when apps are maximized. My monitor (Samsung syncmaster 913n) will not let me manually align the screen since it is plugged into a DVi gfx card (Nvidia 7900gs), and I suppose in these cases it should happen automatically. 

I've checked all the system settings and had a quick gander at xorg.conf but can't see anything which might help. If this is a common issue and is stickied in huge letters somewhere then sorry. Otherwise, any suggestions? :)

---

### Post by sparxx on 2007-04-27
No suggestions?

Google hasn't come up with anything and i've gone through every system setting in ubuntu but dont see anything. Running out of idea's now :(

---

### Post by Turellius on 2007-04-27
What gfx driver are you using?  Are you using the default video driver that ships with Ubuntu or are you using the closed-source driver from Nvidia?  My guess is that you are using the default drivers, I am far from a Ubuntu guru, but I would download the drivers from nvidia's website and install those and see if this fixes the problem.  If it doesn't fix it automatically then it's possible there is a config utility inculded with the drivers that could help you fix your problem.  Once you download the dirvers you should be able to install with the dpkg -i /location of driver package  Hope this helps.

---

### Post by sparxx on 2007-04-27
Fixed it!

I had a look at the graphics driver (closed source nvidia) and stumbled across the nvidia control panel (nvidia-settings). After messing around with the setup I discovered 'Meta Mode' in the advanced display configuration. Setting this to 'nvidia-auto-select' solved my problem.

Thanks! :D

---

### Post by Ozdemon on 2007-07-03
> **sparxx said:**
> Fixed it!

I had a look at the graphics driver (closed source nvidia) and stumbled across the nvidia control panel (nvidia-settings). After messing around with the setup I discovered 'Meta Mode' in the advanced display configuration. Setting this to 'nvidia-auto-select' solved my problem.

Thanks! :D

I have just installed ubuntu and have exactly the same problem.  Can you please tell me where I find the setting?

**Update**
Problem fixed by using automatix to upgrade the nvidia driver.

---


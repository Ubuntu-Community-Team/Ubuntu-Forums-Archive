---
title: "PLEASE help"
date: 2007-01-12
forum: General Help
---

### Post by deaddylan123 on 2007-01-12
Hi, i just got finished installing ubuntu, and i just installed the nvidia drivers, and in the tutorial it says to press ctrl+alt+backspace to see if the installation was sucessful, but all it did was bring me to like, a terminal version ubuntu.  Is there a way to get out of this 'terminal' version, and go back to the fun, sexy gui version? :-P.  Whenever I reboot, it just goes straight to the 'terminal' version of ubuntu.

PLEASE HELP! I did this cause i needed the drivers so cedega would work better, so please help!!!

Thanks alot!

---

### Post by RaZoR-x11 on 2007-01-12
Hey, 

and hell yes :D, all you need to do is 
```
startx
```

or

```
/etc/init.d/gdm start
```

Welcome to UbunTU! 

RaZoR:D:D:D:D

---

### Post by ~LoKe on 2007-01-12
I would use
```
sudo /etc/init.d/gdm restart
```
Rather than just start.

---

### Post by deaddylan123 on 2007-01-12
poo, both methods fail :-(

---

### Post by NeoLithium on 2007-01-12
If there's an error message, something might have gone wrong with the change in xorg.conf. HOPEFULLY the tutorial you followed, told you to back up your xorg configuration, so you just need to copy your backup over the newly modified one; and try again.

---

### Post by RaZoR-x11 on 2007-01-12
You say you upgraded ya grffic card, has it come with any error on boot?

---

### Post by RaZoR-x11 on 2007-01-12
if you didn't back up you can alway's reconfig. 
:D

---

### Post by ~LoKe on 2007-01-12
It certainly does provide an error.  When the X server fails, you'll get an ugly blue screen saying "do you wish to view the whatever whatever".  Choose yes and tell us what the last few lines says.

If for some reason that doesn't help..
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_iscreweditupbadly
```
```
sudo cp /etc/X11/xorg.conf~ /etc/X11/xorg.conf
```

Then you should be able to boot, because we just undid the changes you made.

Worst case scenario..
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by ardchoille42 on 2007-01-12
> **deaddylan123 said:**
> Hi, i just got finished installing ubuntu, and i just installed the nvidia drivers, and in the tutorial it says to press ctrl+alt+backspace to see if the installation was sucessful, but all it did was bring me to like, a terminal version ubuntu.  Is there a way to get out of this 'terminal' version, and go back to the fun, sexy gui version? :-P.  Whenever I reboot, it just goes straight to the 'terminal' version of ubuntu.

PLEASE HELP! I did this cause i needed the drivers so cedega would work better, so please help!!!

Thanks alot!

I had to open a terminal and type

```

sudo nvidia-glx-config enable

```

before the nvidia drivers would work, but that's part of the wiki tutorial. Then I just typed "sudo /etc/init.d/gdm restart" to restart X - I was told this is the proper way to do it. I just installed nvidia drivers 10 minutes ago and everything works fine after following that wiki page. BTW, I'm running Ubuntu 6.06.1 LTS (Dapper).

---


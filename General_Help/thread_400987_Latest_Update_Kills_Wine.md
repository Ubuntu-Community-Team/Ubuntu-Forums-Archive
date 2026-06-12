---
title: "Latest Update Kills Wine?"
date: 2007-04-04
forum: General Help
---

### Post by RoboNuggie on 2007-04-04
Hi

Wine worked like a peach before the latest update fot Ubuntu, I think it may have been the Xfree/Xserver update.... anyone else have any issues?





Robo

---

### Post by handaxe on 2007-04-04
I suppose it could depend on what you do in wine, but my install works just fine in testing with a simple Windows GIS viewer. Update applied.

So, ........

HA

---

### Post by max69 on 2007-04-04
Hi,
same here, wine kills the Xserver since ubuntu update.

---

### Post by handaxe on 2007-04-04
Is that with an Open GL application?

HA

---

### Post by beaudoin996 on 2007-04-04
I've got the same problem and it's with a non-OpenGL application.  Everything was fine until yesterday update.  The X server simply reboot when I use wine.

---

### Post by handaxe on 2007-04-04
Searching for clues - is this the standard Edgy issue Wine or the latest vintage from  [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt)?

I am on the latter and as noted, have no problem running wine with the update.

HA

---

### Post by beaudoin996 on 2007-04-04
It's the standard Edgy.

> **handaxe said:**
> Searching for clues - are this the standard Edgy issue Wine or the latest vintage from  [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt)?

I am on the latter and as noted, have no problem running wine with the update.

HA

---

### Post by handaxe on 2007-04-04
If of interest, you can try   

[http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

 in Synaptic and update your wine and see if it copes.

HA

---

### Post by boots on 2007-04-04
I can confirm this as well. Forcing previous versions of wine don't seem to help.

---

### Post by handaxe on 2007-04-04
There are enough confirms here for a bug report on launchpad. I searched briefly and it is not reported. If done by one of you the others need to report the confirmation so liaise.

Out of interest, can someone confirm if the latest wine (see above post) also fails? I am wondering why I don't have the issue.

Using Nvidia proprietary driver (Edgy version) on a core duo... I wonder what hardware might be at issue here or what....

HA

---

### Post by beaudoin996 on 2007-04-05
I can confirm that the latest version of wine also fail.  My graphic card is GeForce 6600 with the NVIDIA drivers.  This is the list of the package update that cause the problem:

libfreetype6 (2.2.1-5) to 2.2.1-5ubuntu0.1
libfreetype6-dev (2.2.1-5) to 2.2.1-5ubuntu0.1
libkadm55 (1.4.3-9ubuntu1.1) to 1.4.3-9ubuntu1.2
libkrb5-dev (1.4.3-9ubuntu1.1) to 1.4.3-9ubuntu1.2
libkrb53 (1.4.3-9ubuntu1.1) to 1.4.3-9ubuntu1.2
libxfont1 (1:1.2.0-0ubuntu3) to 1:1.2.0-0ubuntu3.1
xserver-xorg-core (1:1.1.1-0ubuntu12.1) to 1:1.1.1-0ubuntu12.2
xserver-xorg-dev (1:1.1.1-0ubuntu12.1) to 1:1.1.1-0ubuntu12.2

---

### Post by horsey on 2007-04-05
I had this (quick way to reproduce is 'nvidia-settings' and click on an OpenGL option).

I'm using a downloaded nvidia driver, not the one from the repositories, and re-running the nvidia installer seems to have fixed the problem.

---

### Post by beaudoin996 on 2007-04-05
Same for me, by re-running the NVIDIA installer it fixes the problem.  

[http://ubuntuforums.org/showthread.php?t=336412](http://ubuntuforums.org/showthread.php?t=336412)

> **horsey said:**
> I had this (quick way to reproduce is 'nvidia-settings' and click on an OpenGL option).

I'm using a downloaded nvidia driver, not the one from the repositories, and re-running the nvidia installer seems to have fixed the problem.

---

### Post by boots on 2007-04-07
I should have checked back on the thread sooner ... I just thought to re-install my nvidia driver (using the latest envy script [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) ) and it worked a charm. I thought it might not be wine related when even just a plain glxinfo was causing the same problem.

---

### Post by tomm3h on 2007-04-08
Even uTorrent was killing X when I tried to run it but, as per everyone else -- installing the latest Nvidia driver (9755) sorted the problem :)

---


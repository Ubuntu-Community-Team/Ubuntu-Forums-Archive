---
title: "[SOLVED] Trouble downgrading xorg-core because of X window system error"
date: 2008-01-18
forum: General Help
---

### Post by Rudi Völler on 2008-01-18
Moved this to its own thread. 

I was following the advice given [here]("http://ubuntuforums.org/showthread.php?t=671065") for the X Window system error when starting Eclipse and ran into the following problems:

I had the same problem and tried to downgrade xserver-xorg-core. The downgrade using 
sudo apt-get remove xserver-xorg-core
and then 
sudo apt-get install xserver-xorg-core=2:1.3.0.0.dfsg-12ubuntu8

seemed to work fine. Then I restarted the machine and now kde doesnt start?!? On the screen says:
```
Starting up...
Loading, please wait...
kinit: name_to_dev_t(/dev/sda5) = sda5(8,5)
kinit: trying to resume from /dev/sda5
kinit: No resume image, doing normal boot...

```
and then I get the login prompt....

Did I miss any steps during the downgrade that I can resolve? or do you guys have any suggestions on how I can resolve this issue?

thanks!

---

### Post by fyo on 2008-01-18
SpitInTheFaceGuy (sorry, that's what I remember Rudi Völler for),

I'm not sure I follow the "downgrade" instructions you say you followed. The following line is ALL you should have needed:

sudo apt-get install xserver-xorg-core=2:1.3.0.0.dfsg-12ubuntu8

Otherwise, you could have used Synaptic to do the same thing (find the xserver-xorg-core package and select "Force version" from the menu and chose the ....8 version instead of ....8.1 version).

From the instructions you list, I'm not even sure you have xserver-xorg-core installed anymore (which would certainly prevent you from booting into KDE).

Try firing off the command above and see if that helps any.

---

### Post by Rudi Völler on 2008-01-19
> **fyo said:**
> I'm not sure I follow the "downgrade" instructions you say you followed. The following line is ALL you should have needed:

sudo apt-get install xserver-xorg-core=2:1.3.0.0.dfsg-12ubuntu8

From the instructions you list, I'm not even sure you have xserver-xorg-core installed anymore (which would certainly prevent you from booting into KDE).

This is exactly the second command that I fired but I will try it again after I figure out how to activate my wireless network connection from the command line...

But what other steps can I take to start booting into KDE again?

---

### Post by Rudi Völler on 2008-01-19
Now I have tried
sudo apt-get install xserver-xorg-core
which installed version 8.3 and also tried
sudo apt-get update and upgrade and check

But this does not seem to fix things for me... When I run startx I get the following error:
```
(EE) Failed to load module "nvidia" (module does not exist, 0).
(EE) No drivers available.
``` 
Running startkde also fails...

I tried to update the symlink as suggested in [this post]("http://ubuntuforums.org/showthread.php?t=671091") but I could not find a file called "libglx.so.100.14.11" or similar in /usr/lib/xorg/modules/extensions/ so Im pretty lost here...

Should I try reinstalling the Nvidia drivers and if so how?
Trying really hard here not to mess up my system more than it already is because I need to get Eclipse up and running A.S.A.P. :?

---

### Post by Rudi Völler on 2008-01-19
Solved!

When I executed sudo apt-get remove xserver-xorg-core it also removed the package nvidia-glx-new!?! And when I installed it again, the nvidia package was not installed with it...

So I just executed sudo apt-get install nvidia-glx-new, rebooted and everything worked!

---


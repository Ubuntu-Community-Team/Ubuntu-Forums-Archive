---
title: "[SOLVED] So...no GeForce2 support?"
date: 2008-04-01
forum: General Help
---

### Post by nachomania on 2008-04-01
I've gone through numerous installs, countless sleepless nights, and more than one occasion of cd throwing. The threads that popped up consisted of my own. I'm asking now only for confirmation. Is everyone out here with a GEforce2 MX unable to use it? Does Envy not work for you either? Did Nvidia's installer not even start on your comps too? Do any AGP4X cards work that well, for that matter? :-({|=

---

### Post by Cygoku on 2008-04-01
Use [Envy Legacy]("http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu9_all.deb") to install your nVidia driver.  

Cygoku

---

### Post by nachomania on 2008-04-01
I've used Envy multiple times, using automatic, the recommended driver in manual and the others. It doesn't work. I'm asking people with Gefroce2mx cards if they do or do not have their card workingl.

---

### Post by kostkon on 2008-04-01
> **nachomania said:**
> I've used Envy multiple times, using automatic, the recommended driver in manual and the others. It doesn't work. I'm asking people with Gefroce2mx cards if they do or do not have their card workingl.

Check my sig. I use the driver from the repos (*nvidia-glx* package) and it works just fine. No problems at all.

---

### Post by Crafty Kisses on 2008-04-01
> **nachomania said:**
> I've gone through numerous installs, countless sleepless nights, and more than one occasion of cd throwing. The threads that popped up consisted of my own. I'm asking now only for confirmation. Is everyone out here with a GEforce2 MX unable to use it? Does Envy not work for you either? Did Nvidia's installer not even start on your comps too? Do any AGP4X cards work that well, for that matter? :-({|=

Have you tried Vesa drivers, I'm pretty sure GeForce 2 would work with Vesa, I think it's old enough by now.

---

### Post by Doorslammer on 2008-04-01
> **nachomania said:**
> I've gone through numerous installs, countless sleepless nights, and more than one occasion of cd throwing. The threads that popped up consisted of my own. I'm asking now only for confirmation. Is everyone out here with a GEforce2 MX unable to use it? Does Envy not work for you either? Did Nvidia's installer not even start on your comps too? Do any AGP4X cards work that well, for that matter? :-({|=

I have a geforce2 mx400  yes agp4x card yes  works great :popcorn:

it worked  fine with the restricted drivers 
you have to use nvidia-settings if you want to change your res   because if you use the one in the control panel it will break the install .
so once you enable the restricted driver 
change any setting  with nvidia-settings 
hope that helps

---

### Post by forrestcupp on 2008-04-01
> **kostkon said:**
> Check my sig. I use the driver from the repos (*nvidia-glx* package) and it works just fine. No problems at all.

This is right.  You need the nvidia-glx package.  The nvidia-glx-new package is for newer cards.  Open a terminal and type
```
sudo apt-get --purge remove nvidia*
```
To remove everything you've done so far, then type
```
sudo apt-get install nvidia-glx
```
And reboot.  You may need to make sure that your xorg.conf is set for the 'nvidia' driver.

Edit:
actually, it's the **nvidia-glx-legacy** package that you need for geforce 2

---

### Post by Doorslammer on 2008-04-01
ya I would just  do like above 
```
sudo apt-get --purge remove nvidia*
``` then  just enable the restriced driver  that should download & install the correct drivers nvidia-glx-legacy

or ```
sudo apt-get install nvidia-glx-legacy 
```

but i never had trouble with the restricted driver
just make sure you  use" nvidia-settings" to change any thing that has to do with the card! thats a must

---

### Post by bettlebrox on 2008-04-01
U probably need the nvidia-glx-legacy package. I think you need to install this and then compile the module (driver).

---

### Post by nachomania on 2008-04-12
Ok. I've followed the steps in # 9. The problem now is, that I don't have nvidia-settings. Trying to start nvidia-settings gets me 
```

The program 'nvidia-settings' can be found in the following packages:
 * nvidia-glx
 * nvidia-settings
 * nvidia-glx-new
Try: sudo apt-get install <selected package>
bash: nvidia-settings: command not found
```

If I enter sudo apt-get install nvidia-settings, I get the following

```
[sudo] password for kaipraths:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nvidia-glx-legacy
The following NEW packages will be installed:
  nvidia-settings
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 691kB of archives.
After unpacking, 8360kB disk space will be freed.
Do you want to continue [Y/n]? n
```

Should I go ahead, install nvidia-settings, and then try to install nvidia-glx-legacy?

---

### Post by nachomania on 2008-04-12
Great, now I've got nvidia-settings, but the same thing pops up when I try to reinstall nvidia-glx-legacy. Is there some other package, or way around this?

---

### Post by nachomania on 2008-05-27
Bought a cheap ATI ALl-in-wonder. Solved.

---

### Post by Redsandro on 2008-07-03
I wouldn't call this SOLVED, but WALKAROUND.. I'm having trouble with the MX200 as well. Now, all seems fine. Got glx-legacy running and all, but cannot get tv-out to work. I use nvidia-settings on all other pc's to turn it on, but on this pc it sais "You are not running the NVIDIA driver."

Although I really think I am. xorg sais so. Not the NV one. :confused:

---

### Post by Hairy Heron on 2008-07-20
When I started using Ubuntu for the first time (after a fresh, clean install - not an uprade) - it recognised my GeForce2 MX and asked if I wanted to install the special driver for it. I said "Yes please" and it works fine.

This is NOT the legacy driver, even though the legacy driver is listed in Synaptic as the one to use for the GeForce2.

So just try installing the nvidia-glx driver and see if it works for you.

---


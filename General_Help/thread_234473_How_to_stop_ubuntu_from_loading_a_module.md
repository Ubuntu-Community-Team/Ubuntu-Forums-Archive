---
title: "How to stop ubuntu from loading a module?"
date: 2006-08-11
forum: General Help
---

### Post by zirrush on 2006-08-11
Alright, so here's my prob... when I boot up ubuntu tries to autodetect and configure my NIC I'm assuming (linksys wmp54g).  It inserts a bcm43xx module for broadcom cards and tries to configure the interface over that.  However, I'm using ndiswrapper with the bcmwl5 driver.  ndiswrapper works fine, however every reboot I have to unload the bcm43xx module and load ndiswrapper.  

I know how to add modules to /etc/modules but I have no clue where to go to disable ubuntu from loading the bcm43xx module, any help would be highly appreciated :)

---

### Post by Jagot on 2006-08-11
From Terminal:

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

---

### Post by zirrush on 2006-08-11
tyvm, everything's as smooth as butter on reboots now :)

---

### Post by ooolongT on 2006-08-20
I am way more of a linux novice than the originator of this thread however, i seem to be having a similar problem.  I am trying to test ubuntu by using the live CD ver. 5.04 on an old Toshiba laptop (4G hard drive).  The other operating system on it is Windows 2000  Pro.  As the live CD is booting i get two erors.  the first it seems to be o.k. with. it says:
```
 The system has relatively little free memory, so ti will install in low memory mode.  
Among other things, this means that the installation will proceed in english. 
You should set up swap space as soon as possible.
```

I gather that that means I need to partition the hard drive. ok.  I will get to that later.  However, it then also hangs up when trying to load the nic drivers and cant poroceed any further.  When it gets to:
```
 unpacking nic-modules-2.6.10-5-386-di 
``` 
it gets to 3% and then starts over again and again, never completeing the install.  I dont think I really need to nic drivers to load as I am just trying Linux for the first time and plan to do most of my work in Windows until I get the hang of it.  Is there some way to skip this part of the install?  Will the above code work for me?

---


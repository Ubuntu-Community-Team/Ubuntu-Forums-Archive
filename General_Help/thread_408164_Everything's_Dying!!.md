---
title: "Everything's Dying!!"
date: 2007-04-13
forum: General Help
---

### Post by SomethingUniqueHere on 2007-04-13
This is a strange one.  I've been booting into the same kernel for a long time, everythings been great, no problems and then a few minutes ago all the windows grey out and nothing is responsive.  I can't open a terminal, i can't switch windows, it's dead.  I reboot, after about 5 minutes same thing.  Reboot.  after about 2 minutes same thing.  I reboot again, select an older kernel, same thing happens after 5 minutes.  right now i booted up in recovery mode for the newest kernel, i haven't the slightest idea about how to start debugging this one.  Any help would be greatly appreciated, I'm really at the forums mercy here!

---

### Post by amohanty on 2007-04-13
Did you update anything else recently , for e.g. Xserver, binary video drivers, restricted kernel modules etc??

---

### Post by SomethingUniqueHere on 2007-04-13
No major changes, just whatever update manager sends my way.  I had been running the computer all day long without incident and then after viewing a txt file in gedit everything seemed to die.  the computer would crash even when i didn't load up gedit.  The strange thing though is that i tried booting the regular kernel again, which i'm on now, everything seems to be running fine though the only application i've dared to launch is firefox so far.

---

### Post by amohanty on 2007-04-13
Well the thing is that if you have been updating everything else, there's a possibility that X or the driver or something does not like the older kernel. Not likely since the MOTUs would make sure of the dependencies but possible. 

Have you tried a full update:

sudo apt-get update
sudo apt-get upgrade

AM

---

### Post by SomethingUniqueHere on 2007-04-13
I just ran a full upgrade, nothing new installed and i haven't had issues since my last post so whatever it was seems to have gone away, at least for now!

---


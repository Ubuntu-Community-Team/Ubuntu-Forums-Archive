---
title: "Which Nvidia Graphics Driver Do I Install for Games?"
date: 2015-09-16
forum: General Help
---

### Post by taurusx5 on 2015-09-16
I got a laptop with an Nvidia graphics card. I'll be trying out Ubuntu from my external hard drive. I'm new to Ubuntu and am testing it out. Again, I'm not installing it, just running it from the external hard drive. I got 2 questions:

1) Where in the repository do I download this driver that would be compatible with my Nvidia graphics card?

2) How or what command do I use (if any) to install this driver?

---

### Post by Bashing-om on 2015-09-16
taurusx5; Hello;

In the software center app enable the "partner" repository 
in software center update
and in software center last tab is "Additional Drivers"
Install the recommended driver .

[INDENT][INDENT]just as quick and easy
[INDENT][INDENT][INDENT]as that
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by pqwoerituytrueiwoq on 2015-09-17
depending on your video card (eg gtx 700 series) you may need to add the xorg edgers ppa to get newer drivers
*these are not officially stable but i have not had any issues in years
```
sudo apt-add-repository ppa:xorg-edgers/ppa -y && sudo apt-get update && sudo apt-get dist-upgrade -y
```
this will add some options to the driver list you would get my doing the above

---

### Post by efflandt on 2015-09-17
> **taurusx5 said:**
> 1) Where in the repository do I download this driver that would be compatible with my Nvidia graphics card?

My crystal ball is a bit cloudy, which nvidia card might that be? What shows up when in a terminal you do:```
lspci | grep VGA
```also (especially laptop with dual graphics) see if anything shows up for:```
lspci | grep 3D
```

Which nvidia drivers are in the standard repositories depends up which Ubuntu version you are running. If you have GTX 750 series the default nouveau or nvidia-current package does not work with the new Maxwell chip, but **nvidia-331-updates** package should work, which is now a 340 version driver (although, my PC is currently running nvidia-352 from xorg-edgers ppa). Not sure of specifics of 9xx cards/chips if they need newer driver version (possibly from xorg-edgers which currently has up to nvidia-355 package). It is possible that default nouveau driver in 15.04 would work for new cards, but nvidia drivers would very likely be faster.

---


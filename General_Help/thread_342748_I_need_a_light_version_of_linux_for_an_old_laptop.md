---
title: "I need a light version of linux for an old laptop"
date: 2007-01-20
forum: General Help
---

### Post by pixelterra on 2007-01-20
I've tried installing ubuntu and kubuntu on an old laptop from '98. But the install process takes FOREVER (over an hour) and then it finally stalls completely. I guess the poor little laptop doesn't have the resources.

I've also tried two REALLY small linuxes (puppy something and I can't remember the second) and neither of them could control the screen output very well so it wasn't very readable. Is there a middle ground out there? Maybe a fedora version? Something light enough to run, but not so light that basic functionality is missing?

---

### Post by fenian on 2007-01-20
Have you tried Xubuntu using the alternative install method?

---

### Post by DerHesse on 2007-01-20
Have eyou tried DSL? [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

The good thing: It`s debian ;)

---

### Post by cracker on 2007-01-20
I agree with the Xubuntu suggestion. I have an IBM Thinkpad 600 (333MHz, 192MB RAM) and it can handle regular Ubuntu (thanks to the memory upgrade), but required installing from the alternate CD. With it's stock memory (64MB) it probably wouldn't work with gnome, and I'd use Xubuntu.

---

### Post by aysiu on 2007-01-20
Do a server install from the Ubuntu Alternate CD.

Once you're done, log in and type these commands: ```
sudo aptitude update
sudo aptitude install x-window-system-core xterm gdm icewm menu firefox synaptic
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by pissedoffdude on 2007-01-20
you might also want to give fluxbuntu a try

---

### Post by pixelterra on 2007-01-22
Thanks for the suggestions. I've taken a look into them. I've tried xubuntu from the alternate cd now, but it didn't pass the integrity check (twice). But fortunately I tried the ubuntu alternate cd and did a text install and all went smoothly (although slowly). So I'm up and running and I only have 159MB ram, but all seems fine. It's not a development machine or anything, just trying to put an old laptop to some use. Now I have a good alternative to having my friends use my dev machine.

---


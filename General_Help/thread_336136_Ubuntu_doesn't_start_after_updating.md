---
title: "Ubuntu doesn't start after updating"
date: 2007-01-11
forum: General Help
---

### Post by endless_dark on 2007-01-11
Well, two days ago I started my ubuntu, and the first thing I made was running the console and I did "sudo apt-get update" and "sudo apt-get upgrade". It installed two packages that now I can't remember. Then I rebooted my computer and after that it doesn't run.

Ubuntu looks normally, but when it's starting gnome, when the nautilus icon appears, It comes back to the login screen.

Does anyone know how to fix it? or some way to undone the installation of those packages I installed?

Thank you!!




PD: Sorry for my english ](*,)

---

### Post by DerHesse on 2007-01-11
Did you install beryl and / or manufacturers device drivers for your graphics card?
So then you are not alone. 

check here:  [http://www.ubuntuforums.org/showthread.php?t=334839&highlight=update](http://www.ubuntuforums.org/showthread.php?t=334839&highlight=update)

---

### Post by endless_dark on 2007-01-11
Thank You for replying but I tried and I can't solve it. Gdm doesn't start in blank screen it starts but suddenly it comes back to the login screen so I think it's not a graphical driver problem

---

### Post by tagginannie on 2007-01-11
> **endless_dark said:**
> Well, two days ago I started my ubuntu, and the first thing I made was running the console and I did "sudo apt-get update" and "sudo apt-get upgrade". It installed two packages that now I can't remember. Then I rebooted my computer and after that it doesn't run.

Ubuntu looks normally, but when it's starting gnome, when the nautilus icon appears, It comes back to the login screen.

Does anyone know how to fix it? or some way to undone the installation of those packages I installed?

Thank you!!

PD: Sorry for my english ](*,)



Hi Endless

When you get your computer running again get Synaptic (sudo install synaptic) witch is better for new Linux users than Adapt. By default Synaptic will pause and ask you if it is ok to proceed.

Suzy

---

### Post by endless_dark on 2007-01-11
Yeah, I use Synaptic & Aptitude both, but now I don't use anything because Gnome restarts and comes back to the login screen all time :(

---

### Post by neymac on 2007-01-11
The same here.
I can run WindowMaker, Fluxbox and FVWM, but Gnome.
Any fix out there?

PS:
I fixed the problem with "envy" script wich reinstall the last NVidia driver. I got it at [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by endless_dark on 2007-01-11
Well, finally it was some graphical driver problem. I solved it reinstalling the latest nvidia drivers. Thank you everybody! :-D

---

### Post by DerHesse on 2007-01-15
yes.

>> "Envy" is a script written in Python which will download the latest Nvidia driver or the Legacy driver (for older cards) from Nvidia's website and set it up for you handling dependencies (compilers, OpenGL, etc.) which are required in order to use the driver on Ubuntu Linux.<<
[[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)]

envy rocks!

---

### Post by Sef on 2007-01-15
> PD: Sorry for my english 

Nothing wrong with your English.

---


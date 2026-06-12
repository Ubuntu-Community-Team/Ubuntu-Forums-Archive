---
title: "Ubuntu &amp; Grub"
date: 2013-02-05
forum: General Help
---

### Post by adrianp918 on 2013-02-05
is there any way to have grub not automatically start up with linux?

i have ubuntu and windows on a side by side install, and when i restart the machine it automatically goes to linux first cause it is the first one in the list of choices.

is there any way i can move the windows 7 os first in choice default and ubuntu last, i dont use ubuntu as much as i use windows but use it enough to have it on there as a choice

Thank you for your help

---

### Post by SuperFreak on 2013-02-05
You could install Grub Customizer (it is in Software centre). In it you can change the order of Grub entries (and thereby what starts first) and the timeout period (time before it boots to OS)

---

### Post by furything on 2013-02-05
Yes there is
```
sudo cp /boot/grub/grub.cfg /boot/grub/grub.bak
sudo vi /boot/grub/grub.cfg

```Change vi for gedit nano vim whatever you feel comfortable with

Count the number of linux kernels and memtest (in the grub.cfg file) starting at 0
so 2 kernels 2 memtest one windows means windows is 4

Change set default="0" to set default="4"

---

### Post by NobleYorkshire on 2013-02-05
> **SuperFreak said:**
> You could install Grub Customizer (it is in Software centre). In it you can change the order of Grub entries (and thereby what starts first) and the timeout period (time before it boots to OS)

I searched for this in the Software center but couldn't find it (on Ubuntu 12.04 LTS).  I found some sort of legacy app but I don't think that was it.

---

### Post by SuperFreak on 2013-02-05
The installed package I have on my machine looks like screenshot below (taken from Software Center). I have 12.04 64 bit installed

---

### Post by oldfred on 2013-02-06
It is not in repository.

       New Grub Customizer works with 12.10
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)
HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)
The Grub 2 Guide - drs305 also link to grub customizer
Ubuntu Community Documentation site
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by SuperFreak on 2013-02-06
My mistake I had added the PPA into Synaptic.
The links Old Fred gives show how to to install Grub customizer

---


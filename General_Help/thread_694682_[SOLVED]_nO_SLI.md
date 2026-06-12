---
title: "[SOLVED] nO SLI"
date: 2008-02-12
forum: General Help
---

### Post by wikiguy on 2008-02-12
Hey, guys recently ive just bought the 2 nd nvidia video card the model is: 7600 GS , I had a 7600 gs before with no problems , so yeasterday when i plugged the 2nd video card the system doesnt display anything.I just can hear some drums so ubuntu is normally booting but i dont get any picture.I have nvidia-glx-new package downloaded from synaptic, my mobo is a gigabyte GA-M57SLI-S4.

So i decided to put the live cd in and reinstall ubuntu but still no picture:mad:



CHEERS

---

### Post by danwood76 on 2008-02-12
Do you see the POST screen etc?
If not I would be looking at possibly a power issue, if you have a cheap PSU then it may not be able to power enough juice to both GPUs.

---

### Post by apetresc on 2008-02-12
> **danwood76 said:**
> Do you see the POST screen etc?
If not I would be looking at possibly a power issue, if you have a cheap PSU then it may not be able to power enough juice to both GPUs.
That's probably not the problem since he *was* able to boot the LiveCD to reinstall.

---

### Post by Therion on 2008-02-12
I can't tell from your original post, so I have to ask... You DO know there's more to enabling SLI than just popping in the additional GPU, right?

---

### Post by wikiguy on 2008-02-12
look i have a powerful psu a 600 watt coolermaster extremepower, SLI works with windows but i wanna use these cards with ubuntu . I cant reinstall the system :( . And i know theres a way to enable sli but when i edit xorg.conf by adding Option "SLI" "Auto". Nothing happens.

cheers

---

### Post by Therion on 2008-02-12
> **wikiguy said:**
> ... but when i edit xorg.conf by adding Option "SLI" "Auto". Nothing happens.
I think the syntax for the SLI Section of the xorg.conf is **"On"**, not "Auto"... But I'm not sure.  Try it?

---

### Post by wikiguy on 2008-02-12
Hey guys , i finally get this thing going , first i ran de live cd, ,then nothing appeared but doing a CTRL+ALT+F1 text mode came up :guitar:.So i edited in Device section default output from PCI 2:00:..etc to 3:00..etc, then i did a :

$ sudo /etc/init.d/gdm stop

$sudo /etc/init.d/gdm start


And guess what mates.....................I ve now video :lolflag:.


So i did a clean instalation of ubuntu after updating i downloaded the 169.09 drivers form [www.nvidia.com](www.nvidia.com)

then:


$ sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

CTRL+ALT+f1

$sudo /etc/init.d/gdm stop
 
cd where nvidia installer is, then:

$sudo sh NVIDIA-Linux-x86_64-169.09-pkg2.run

YES TO ALL :P

THEN:

$ sudo /etc/init.d/gdm start

after login in

make sure that SLI is enable by doing a

$ sudo nvidia-xconfig --sli=AFR


PSD: COMPIZ FUSION RUNS LIKE CHARM

THANKS TO ALL FOR YOUR PATIENTE AND TIME

CHEERS

---


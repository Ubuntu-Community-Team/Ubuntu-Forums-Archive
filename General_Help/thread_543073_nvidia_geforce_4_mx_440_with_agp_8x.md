---
title: "nvidia geforce 4 mx 440 with agp 8x"
date: 2007-09-04
forum: General Help
---

### Post by darkenemy on 2007-09-04
so,  i have tried to a greater extent, for about a 6 months to get this graphics card to work with ubuntu, but it doesnt seem to want to

i am using 7.04, and just recently got everything working just how i like, other than this card.  it's a Nvidia GeForce 4 MX 440 with AGP 8x.

the problem is, when i try to boot in linux (im doing a dual boot in xp for those rare occasions i need it) the spalsh screen loads, until moments later when it tells me the x server wont work because of a problem with the graphical interface.  to make matters worse, it does this in that blue-screen-of-death type look, that just doesnt seem pretty.

i then am able to go to the console (if that's the name of the place you go when you pres control+alt+F1 to get into, and control+alt+F7 to get out of).  but here i am stuck.

i have downloaded the proper driver from nvidia, it seems to be installed.  other than that, i got nothin...

can anyone help?

---

### Post by nitro_n2o on 2007-09-04
all right, then while in your in the terminal (console) or even the black screen try this: 
```
sudo dpkg-reconfigure xserver-xorg 
```
this will reconfigure your xserver and gives you the basic functionality... 
after that get the nvidia driver from the repositories via apt-get it's way better than installing this manually 
```
sudo apt-get install nvidia-glx 
```
then 
```
gksudo nvidia-settings 
```
which will give you a nice gui to set up your graphics card.. 
have fun

---


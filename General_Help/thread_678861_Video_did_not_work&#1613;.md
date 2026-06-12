---
title: "Video did not work&#1613;"
date: 2008-01-26
forum: General Help
---

### Post by Ibrahim mufeed on 2008-01-26
Hi, I have installed ubuntu 7.10 , everything perfect except three things, that:

1- The video did not work at all, I run the the included examples, I hear the audio but I did not see the pictures "VIDEO", instead I see a dark screen.

2- When I try to switch the visual effects to Normal or Extra. It did not work and display a message said:"Desktop effects could not be enabled".??

3- How can I change the input language, The layout and use keyboard shortcut to move from input language to another.

Thank you in advance.

---

### Post by jan quark on 2008-01-26
to point 2
I had to install the xorg server to run the special effects just search for it via synaptic
and of course the drivers for your graphic card

and then via the add/remove the Advanced Desktop Effect Settings application
or via the terminal
sudo apt-get install compizconfig-settings-manager

to point 3
do you mean the input layout of your keyboard? then go to the keyboard preferences and change it there


to point 1 ( weird answering order)

perhaps you are missing the right video codecs
installing ubuntu restricted extras should solve this issue

---

### Post by jan quark on 2008-01-26
update to point 2

the package I had to install was   xserver-xgl and its dependencies, just search for it in synaptic

my old brain needs some time "sigh"

then you have to select run xclient script during the login screen, click on sessions and you will see what I mean
if problems occur ask

---

### Post by Ibrahim mufeed on 2008-01-26
Thank you...
I am a newbie and I did not know alot, 

point 2:
I searched for xserver-xgl and I mark them but I could not apply??
I need more simple explination, steps What should I do.

Point 1:
how can I install the "ubuntu restricted extras"? also step by step.

I am so sorry.

---

### Post by Ibrahim mufeed on 2008-01-27
Thank you...

All of my problems solved, I am happy.
:lolflag:

---


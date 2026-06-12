---
title: "Huion stylus pen + Aiptek 12000 graphics tablet"
date: 2021-03-29
forum: General Help
---

### Post by grey1beard on 2021-03-29
I've plugged my old aiptek graphics tablet into my ubuntu 20.04 system, and lsusb recognizes its presence.
I've bought a new hulon pen, and trying to set up the combination.
Problem - trying to install the driver.
In termial, I've used apt-get update, apt-get upgrade, then apt-get dist-update, then 

>      
john@john-HP-ProDesk-600-G1-SFF:~$ sudo apt-get install -y xserver-xorg-input-aiptek
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xserver-xorg-input-aiptek

I've googled over the last two days, trying to find an answer that is recent and understandable, but no luck so far.
Grateful for help over this particular hurdle.
John

---

### Post by coffeecat on 2021-03-29
I have no experience of using any graphics tablet in Ubuntu, but I was curious about the non-existence of the xserver-xorg-input-aiptek package for 20.04, so had a look on packages.ubuntu.com and came up with something even more curious: [https://packages.ubuntu.com/search?keywords=aiptek&searchon=names&suite=all&section=all](https://packages.ubuntu.com/search?keywords=aiptek&searchon=names&suite=all&section=all)

It would seem that xserver-xorg-input-aiptek is only available for 16.04, 18.04 and the soon-to-be released hirsute/21.04. Why, I have no idea. A non-LTS may not suit you, nor a version still in development, but would you consider setting up a test installation of Hirsute and seeing if you can get your tablet pen combination working on that?

Alternatively, you are still showing 18.04 in your profile. Do you still have a working 18.04 install you could try?

---

### Post by grey1beard on 2021-03-29
Thanks for the speedy response. 
I've got a laptop running 16.04, and I'll try that as well, though the 20.04 desktop is my preferred  machine for the graphics work, so still need a solution.
Re 18.04 usage - a bit sluggish in keeping my info up-to-date, I fear !

---

### Post by coffeecat on 2021-03-29
Just a reminder: 16.04 goes end of life at the end of April. But at least that gives you time to try it out on that before the repos for 16.04 close.

Good luck!

---

### Post by grey1beard on 2021-03-29
As a trial, I've got the tablet driver installed on a 16.04 machine(yes, just a month to go) but do I need a separate driver to get the pen recognized by the tablet/gimp ?

---


---
title: "Frozen after login on pink screen, a reaction of installing open office and compiz?!"
date: 2008-01-24
forum: General Help
---

### Post by richandcreamy on 2008-01-24
**The Problem:**

After login the screen stays pink with the mouse pointer / cursor movable.  

**What I did before this:**

I was trying to get compiz fusion working as per this guide 

[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

Completed this step
> 
deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main universe 
deb-src [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main universe

Then did this:

> sudo apt-get update 

Now running that line took a lot longer than it ever did.  It spent a long time giving me Open Office updates.

During the next step running

> sudo apt-get install compiz compizconfig-settings-manager 

Failed.  I wish I took note of how, but I tried running synaptic to install all the updates at once + compiz.  Doing so left me with the most broken packages I ever had in an update.  

Every open office update was broke plus to other files that began with Lib.  Uninstalling gave me a huge list of things being installed uninstalled and upgraded which looked odd because I didn't see any relation between all the different mentioned programs.  I stupidly assumed it to be safe.

Then I uninstalled Emerald and other compiz apps I could find in synaptic.

I had an error about restarting gdm and several other 3 letter acronyms.  Figured out how to do it, restarted and got the pink screen. 

**What I've tried and has failed:**

Going back to kernel 2.6.20-16-generic.  Can't get to login at all.
Xorg setting drivers to vesa to nvidia doesnt change anything
Can't reinstall programs because I don't know how to connect to the internet wirelessly with command lines.


**Specs:**

HP DV9220us
2gb Ram
150gb Hard Drive
1.6 Core Duo Centrino 
Nvidia Geforce Go 7600

Ubuntu Feisty 
2.6.24-4 Generic Kerne0l

What other info do I need to dig up and how?

**Other Variables:**
I tried for so long to figure this out on my own I forgot exactly what I tried to install/uninstall.  



**Rant:**

\\:D/Figuring out what to do involves me searching the forum and google with as many keywords as I can think of that relate to my problem and cut and pasting the solutions I find.  Sometimes mix and matching answers to see if they will work.  I don't know what I'm doing but I think I follow directions fairly well.:?

](*,) This is the deepest hole I've dug for myself ever since trying to tweak Ubuntu.  The install was easy with my DV9220us but I wanted to install all the latest features.  After 4 back breaking days, easily spending 10 or more hours I figured out how to install Kernel 2.6.24-4 generic, this is after trying 4 other kernels that are newr than 2.6.20-16  Now I'm stuck, even after 5 hours of searching for an answer.:confused:

---


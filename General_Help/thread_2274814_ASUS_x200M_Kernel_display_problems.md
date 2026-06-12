---
title: "ASUS x200M Kernel display problems"
date: 2015-04-22
forum: General Help
---

### Post by Derelinquat fenestras on 2015-04-22
Hello all,

I have an ASUS X200M laptop and I'm running Ubuntu 14.04 on it.  
I was wondering if anyone knows about the display issues it is having.  Here's what I mean.  

In February, I upgraded my kernel from: 
linux-headers-3.13.0-44-generic to linux-headers-3.13.0-45-generic   
After I restarted the computer, all I got was a blank display.  Now I installed GrubCustomizer, so that I could get the GRUB menu to initialize every time I start my comuter so that I can always use: 
linux-headers-3.13.0-44-generic 

I have upgraded the kernel all the way to:

linux-headers-3.13.0-46-generic

but I am still having the same display issues.  Now apt-get is telling me that there is another new one, but I'm leery to upgrade to it for fear that there will be the same problem. Now I have a whole bunch of kernels taking up space on my hard drive, and I don't know how to dump the ones I'm not using without dumping the one that works.

I was wondering if anyone else is having this problem, or knows a way to fix it, or knows if the new kernel is also having this problem with my computer, or any ideas at all.
This is my second post about this issue, and I hope someone responds this time!

Thank you so much in advance for any help!

---

### Post by dino99 on 2015-04-22
Looks like it might be a graphic issue: which driver is used ?
Installing the stock kernel (not the backported ones that often have issue/conflict) from archive install 2 headers and 2 images packages for each new kernel; is that the case ?
Do you also have some non-trusted packages installed ? (from ppa)

---

### Post by Derelinquat fenestras on 2015-04-22
Thanks for the reply!
The graphics card is a Intel® Bay Trail 
Not sure how to check what driver is used...

When I upgrade the kernel its always through:
sudo apt-get dist-upgrade

does that install the stock kernels?  Is there a better way to do so?

I do have some ppa packages, but I don't think they would effect the graphics.  Like I have the ppa of a package called synapse, that I really liked for 12.04, but had no package for it for 14.04

---

### Post by J_Me on 2015-04-22
> Now I have a whole bunch of kernels taking up space on my hard drive, and I don't know how to dump the ones I'm not using without dumping the one that works.
I used this help page for removing old kernels individually.
[http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/](http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/)
For the rest I couldn't tell you.

---

### Post by Derelinquat fenestras on 2015-05-20
Thank you all for your help and suggestions!  
Finally resolved!

  
Ended up, last night, removing all but the newest and the functioning kernel, following instructions outlined here:  


[http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/](http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/)

Today I installed package:


linux-firmware-nonfree 
via synaptic (can also do apt-get)
and


    sudo apt-get dist-upgrade


Which updated my kernel once more and the package linux-firmware.


Rebooted and the newest kernel booted up with no display problems...
Not sure which step did the trick but thought I should let you know.


Good luck!

---


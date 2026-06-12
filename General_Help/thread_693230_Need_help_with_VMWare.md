---
title: "Need help with VMWare"
date: 2008-02-10
forum: General Help
---

### Post by Philio on 2008-02-10
I really want to get some good VM software going on my PC, I've tried Qemu and it works ok but I am getting all sorts of errors in Windows.

I've been trying to get VMWare to work but every time I start a virtual machine my computer resets itself!!!

I've tried Workstation, Player, Server, none work.

What the hell could be causing this, I have no idea which logs I can look at to try and find the cause, can anyone help?

---

### Post by mrsteveman1 on 2008-02-10
Are you running VMWare on top of ubuntu or windows?

---

### Post by Philio on 2008-02-10
Trying to install on Ubuntu so the 1 or 2 Windows apps I need occasionally can be used without a reboot.

---

### Post by mrsteveman1 on 2008-02-10
How did you install VMWare? Was it the standalone package from the website, or did you do it through the package manager in Ubuntu?

I'm quite curious why VMWare (which is a userspace program other than its network driver), would even be able to cause a system to reboot. It should at most cause the program to crash.

If you can, look through /var/log/messages and see if there are any errors or anything from VMWare that you can see easily.

---

### Post by Philio on 2008-02-10
There is no mention of vmware anywhere in /var/log/messages or any of the archived versions... Does vmware keep it's own logs anywhere?

---

### Post by Philio on 2008-02-11
Can anyone suggest anything?
Is it possible to install vmware via the live CD? Might be a good way to figure out if it's just not liking something about my hardware or a software setting?

---

### Post by zvacet on 2008-02-11
You have VMware-server in synaptic.But,first chek that you have all repos open.System>admin<software sources>chek all boxes under ubuntu software and updates tab if you didn´t do it allready.Reload.Go to the synaptic and in search box type vmware-server and install all packages related to vmware-server and then install vmware-server.You will need ome serial number so here it is 98TDH-YPY4K-2C224-4A13D.

---

### Post by Philio on 2008-02-11
> **zvacet said:**
> You have VMware-server in synaptic.But,first chek that you have all repos open.System>admin<software sources>chek all boxes under ubuntu software and updates tab if you didn´t do it allready.Reload.Go to the synaptic and in search box type vmware-server and install all packages related to vmware-server and then install vmware-server.You will need ome serial number so here it is 98TDH-YPY4K-2C224-4A13D.

I didn't realise it was there, I downloaded the latest version from the vmware website! I will give this a try and see if I have any joy with this version. I am using a slightly modified version of the standard Ubuntu kernel (I added dmraid5 and xfi SLAB support), hopefully this doesn't make any difference!

---

### Post by zvacet on 2008-02-11
If you didn´t download 2.0 beta then you downloaded asme version that you have in synaptic.Nevermind now.

---

### Post by Philio on 2008-02-11
Is it completely unmodified from the vmware version?

---

### Post by Poleh on 2008-02-11
Odd that you're having issues with VMware, I have VMware Workstation 6 installed on my Gusty/7.10 and it works brilliantly - that's installed from the tarball off the vmware website.

I wouldn't recommend Server 2 just yet, it's beta and VERY unstable in my experience - another good option would be to try Virtual Box ([http://www.virtualbox.org/](http://www.virtualbox.org/)) which should work find on Ubuntu....

---

### Post by Philio on 2008-02-12
Tell me about it!

I've not been able to find a single article on the web regarding the hard reset issue...

I'm guessing it really just doesn't like something about my hardware, or maybe the custom Kernel I'm running - although it's not very customised, all I did was change SLUB -> SLAB for X-Fi support and added dmraid45 as a module. It's compiled from the Ubuntu sources with the Ubuntu patches applied.

My hardware is as follows: QX6700, 4Gb, 8800 GTX, X-Fi gamer.

The X-Fi driver sometimes locks up the machine on boot, so it makes me wonder if this could cause other instabilities, like many others I'm another one that is rather disappointed with Creative's efforts concerning drivers for the X-Fi, I originally built my PC to play games on so this seamed like the logical option. As it happens I rarely end up playing games very often on here and mostly use it for work, considering that there are still bugs with the Vista x64 driver as well and it only cost £50 it might be worth looking around for an alternative.

I think my best cause of action would be to boot the live cd, install vmware and see what happens, I would have done it already but I'm in the process of writing a patch for some software and didn't want to reboot and open everything up again!

---

### Post by Mongo5000 on 2008-02-12
> **zvacet said:**
> You have VMware-server in synaptic.But,first chek that you have all repos open.System>admin<software sources>chek all boxes under ubuntu software and updates tab if you didn´t do it allready.Reload.Go to the synaptic and in search box type vmware-server and install all packages related to vmware-server and then install vmware-server.You will need ome serial number so here it is 98TDH-YPY4K-2C224-4A13D.

I must be blind cause I don't see vmware in synaptic even with all sources :confused:

---

### Post by benyau on 2008-02-12
It is available under this repository:

[http://archive.canonical.com](http://archive.canonical.com) gutsy/partner

The version there is vmware-server 1.0.4-1gutsy2

I am trying to install it at the moment.  The package was not there a few days ago.

Cheers

---

### Post by zvacet on 2008-02-13
@ **Philio**

Run ```
uname -a
```  just to see what kind of kernel you are working with.I think vmware-server works with generic kernel.

---

### Post by mrsteveman1 on 2008-02-13
I'm definitely biased here, I've seen creative drivers crash more systems than i can count.

My advice would be to grab the Ubuntu kernel source again, and append a suffix to it when it builds (you can do this in the config) so that you can install 2 versions of the kernel at the same time.

Then you'll be able to keep the 2 kernels separate even if they are the same version, and boot into each one when you want to. Note this isnt a good way to run the system permanently but it should help isolate the problem. If vmware starts working on a stock built kernel, that was the problem.

It may be that the creative drivers have nothing to do with it, it may be that this is some odd bug, but thats where i would start.

---


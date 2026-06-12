---
title: "Keeping my system clean by removing orphaned packages"
date: 2007-02-24
forum: General Help
---

### Post by astronic on 2007-02-24
Dear Forums,

I wonder how to solve the following scenario:

1) I install Application X, which leads to the installation of dependencies libA, libB, progamC (which itself might pull in other dependencies and so on).

2) Now some time later I want to remove Application X and every dependency that got installed because of application X (also those which got installed recursively), if it is a) not needed by another packages I want to keep or b) not a program that I actually want to use.

So, how do I cleanly accomplish getting all unneeded and unwanted dependencies removed?

I know about "apt-get autoremove" and "deborphan" but both don't really get the job done. The main problem is: They can't know which applications I want to use and which are only there as a dependency.

Example: I install a graphical cdrecording application and cdrecord will get pulled in as a dependency. Now I deinstall this graphical cdrecording application. How can "apt-get autoremove" or "deborphan" know, if I want to keep cdrecord to use it directely? As far as I can see, they can't. So they will either try to remove cdrecord, because no other packages depends on it (which is bad, if I want to keep cdrecord) or they will not try to remove cdrecord (which is bad if I don't want to use cdrecord personally and it got only installed as a dependency).

So the only chance I have at the moment, is to run "deborphan --all-packages" and inspect each listed package there by hand. But this is not very feasable, because a lot of packages installed by the Ubuntu installer are not a dependency of something and I have to know the function of each and every package to be able to safely remove it.

For example: I've got a RAID system and mdadm got installed automatically during the installation of Ubuntu. Now if I run "deporphan --all-packages" mdadm (the RAID device manager) is listed as a package without anything depending on it, still it wouldn't be wise to remove it. Also I have absolutely no idea about packages like "ubuntu-minimal" (and a lot of others). I didn't install it, I don't have personal use for it, but I also don't know what will happen to my system and the dependency graph if I should decide to just remove it.

From the point of view of somebody who wants to keep his system as clean as possible, this situation is unsatisfactory. A possible solution has been implemented by others (like Gentoo) and is actually quite simple:

Provide a "system file" which contains all packages needed by the system and create a "world file" which contains all packages personally wanted by the user. Now every time the user directly installs a packages, it gets automatically registered in the world file. But the user also has the possibility to change the world file himself. For example in the cdrecord-example above, the user will just add cdrecord to the world file, in case it only got installed indirectly as a dependency and he still wants to use it directly.

Finding unrequired dependencies would be very easy now. Just calculate a dependency graph of all packages in the system and world file, and all packages that are installed but not part of this dependency graph could be removed safely.


Maybe I am overlooking some possibility to get this done with Ubuntu? Maybe there is some third-party wrapper script for apt that already implements this functionality? Or how do you keep your system safely and comfortably clean of orphaned packages?


Thanks in advance for any hints!

Regards,
Stefan

---

### Post by rocknrolf77 on 2007-02-24
If you use aptiude instead of apt-get, the depenencies will be handled much better. :) 

Have a look here : [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by aysiu on 2007-02-24
Well, if you don't like *autoremove* or *aptitude*, then you are going to have to use *deborphan* or *gtkorphan*.

Programs can be smart, but they can't be mindreaders.

---

### Post by Maestro23 on 2007-02-24
Aptitude is what I use as well.  Here's another good link for cleaning out junk: [http://doc.gwos.org/index.php/RemoveJunkFiles](http://doc.gwos.org/index.php/RemoveJunkFiles)

---

### Post by spacelem on 2008-06-13
> **aysiu said:**
> Well, if you don't like *autoremove* or *aptitude*, then you are going to have to use *deborphan* or *gtkorphan*.

Programs can be smart, but they can't be mindreaders.

The way Gentoo does this, is it has a small core of packages (whose entry is called system), and then anything else you explicitly request gets put into a world file in /var/lib/portage/world. When you uninstall something, it gets removed and its entry is removed from world.

When you want to remove the dependencies, portage creates a complete list from world of everything that should be installed, compares that to what actually is installed, and removes the difference. No mindreading required.

It's not perfect, some things get built against libraries they don't depend on and then stop working when you remove that library, but Gentoo has revdep-rebuild to handle that. Ubuntu shouldn't have this problem at all, since all its packages are precompiled.

---


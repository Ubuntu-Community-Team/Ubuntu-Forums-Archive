---
title: "Package 1 depends on Package 2, but Package 2 depends on Package 1?!"
date: 2008-05-06
forum: General Help
---

### Post by pj_rage on 2008-05-06
I'm trying to install build-essential on my laptop.  I cannot have internet on this laptop so I have to install stuff manually.  The only way I have found to do this is to search packages.ubuntu.com for the package, download it and then download the dependencies one by one as I find that I need them.  It is very very slow and tedious, but has worked so far.

I wish I could just sudo apt-get install build-essential as I've read I should be able to, but alas without internet that does not work.

The problem here is that I started working at the dependencies, but I found this one to be something I haven't seen yet.  I need to install g++-4.2 but it depends on libstdc++6-4.2-dev.  So I grabbed libstdc++6-4.2-dev and tried to install it, but it says it depends on g++-4.2!!  So what do I do?  It seems to be a recursive problem??

---

### Post by chrisccoulson on 2008-05-06
Put all the debs (including dependencies) in to one folder, then do:
```
sudo dpkg -i *.deb
```
This will work as long as all the dependencies are available

---

### Post by pj_rage on 2008-05-06
Awesome, that worked!  Thanks alot!

---

### Post by pj_rage on 2008-05-07
Kind of an auxiliary question..

Is there any easier to way "manually" install the packages?  That is, specifically, a way to quickly know every single dependency needed to install a package in a quick and efficient way?  Or do I need to dpkg search (on my ubuntu machine) every dependency needed for every single package I want to get, then check the dependencies for the dependents I need for the original wanted package on packages.ubuntu.com, then dpkg search THOSE dependencies to see if I have them, then follow the tree down as deep as it goes.  It takes me forever to install a package by doing this, when I need ~10-12 packages and I have to find them out one by one and and copy them over via usb drive.  It seems like linux (or maybe just ubuntu) wasn't really well designed for "off-line" (no internet) use?

---

### Post by az on 2008-05-07
> **pj_rage said:**
> Kind of an auxiliary question..

Is there any easier to way "manually" install the packages?  That is, specifically, a way to quickly know every single dependency needed to install a package in a quick and efficient way?  Or do I need to dpkg search (on my ubuntu machine) every dependency needed for every single package I want to get, then check the dependencies for the dependents I need for the original wanted package on packages.ubuntu.com, then dpkg search THOSE dependencies to see if I have them, then follow the tree down as deep as it goes.  It takes me forever to install a package by doing this, when I need ~10-12 packages and I have to find them out one by one and and copy them over via usb drive.  It seems like linux (or maybe just ubuntu) wasn't really well designed for "off-line" (no internet) use?

Exactly.  That's what APT (Advanced package tool) is for.  But you need to be online.  There are ways of generating a list of links to download packages.  For example

~$ sudo apt-get install --print-uris penguin-command
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  penguin-command
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 952kB of archives.
After this operation, 1573kB of additional disk space will be used.
'http://mirrors.us.kernel.org/ubuntu/pool/universe/p/penguin-command/penguin-command_1.6.11-1_i386.deb' penguin-command_1.6.11-1_i386.deb 952096 SHA256:7a14b2769be837ec2a9ae3cfa9bd048c4642379fb6e79c7560a87974704e3189

You can pipe the output into a file and then use that with a download manager on a networked-machine to download all the debs.

On another note, build-essential is on the desktop cd.  Just put the cd into your drive after you have installed and the repo will be added to your list.  The repository on the live cd is not part of the live session.

---

### Post by pj_rage on 2008-05-07
If the computer isn't online, how will apt know if a particular package even exists?

For example, I tried your example, and I got the message "E:  Couldn't find package penguin-command" .

Unless there is some database that the machine has that is a huge list of uninstalled, but available packages, and their dependencies, I guess it's just not possible to do?

That does bring up an interesting idea though.  Is there some place I can get a program/database/script that essentially downloads the name and dependencies of every single package available on packages.ubuntu.com and then runs on my offline ubuntu machine to cross-reference the necessary dependencies for any particular available package based on what is currently installed on the system?  Sort of an offline version of apt I guess?

---

### Post by oldos2er on 2008-05-07
See [http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/) (althought it appears to be down at the moment).

---


---
title: "Dependancy problem with Owncloud installation."
date: 2015-08-27
forum: General Help
---

### Post by Dubser on 2015-08-27
Allo

According to Seafile manual I try a Owncloud installation on Ubuntu 14.04  with

> 
apt-get install update 
apt-get install owncloud

I have a dependency problem and I m jam......
> 
Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 owncloud : Depends: owncloud-server (= 8.1.1-1) but it is not going to be installed
            Depends: owncloud-config-apache (= 8.1.1-1) but it is not going to be installed
            Recommends: curl but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


I need some helpfull hand to guide me !

Thanks a lot.

---

### Post by Dubser on 2015-08-27
I uninstall curl with apt-get remove curl. Than I pass autoremove apt-get , I reinstall curl and after everyting was good with apt-get install owncloud. 

Solved

---


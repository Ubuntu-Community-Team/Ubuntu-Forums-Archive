---
title: "Cannot install zoneminder on mythbuntu 12.04 server"
date: 2012-11-02
forum: General Help
---

### Post by singogli on 2012-11-02
I have a working mythtv installation on an Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-32-generic x86_64) system.  This is a quad processor 64 bit machine.  I am attempting to add a zoneminder install remotely from an rlogin terminal but am getting the following error :

 root@mythbuntu64:/home/steve# apt-get install zoneminder
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 zoneminder : Depends: libgnutls-openssl27 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

I have tried: 
apt-get purge zoneminder apt-get clean apt-get update
apt-get install -f
apt-get install zoneminder
But always the same error. 
If I attempt to install libgnutls-openssl27 with:
apt-get install libgnutls-openssl27
I get a similiar error ending with:
The following packages have unmet dependencies:
 libgnutls-openssl27 : Depends: libgnutls26 (= 2.12.14-5ubuntu3) but 2.12.14-5ubuntu3.1 is to be installed
E: Unable to correct problems, you have held broken packages.

Can this be resolved and zoneminder added without damaging the existing mythtv install?

---


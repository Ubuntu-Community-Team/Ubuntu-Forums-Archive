---
title: "Can not install libpython2.6"
date: 2012-10-20
forum: General Help
---

### Post by alexoracle2004 on 2012-10-20
Hi to all, 


I an new to Ubuntu.. i have installed Ubuntu 12.04.1 LTS, but actually it is upgraded to Ubuntu 12.04.1 LTS because i could not install directly this version.. 

After a few days of usage i tried to install font manager because is a prereque of another program i wanna install. 

But i am getting a msg saying that font manager needs python 2.6. I tried installing it from apt-get but i could not do it. So i download it and compiled it and installed it. 

And now i am getting a msg that libpython2.6 needs to be installed . 

I have tried this: 

alex@alex-Latitude-D600:~$ sudo apt-get install libpython2.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libpython2.6 : Depends: python2.6 (= 2.6.8-2+precise1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
---------------------------------------------------------------------------------------------
alex@alex-Latitude-D600:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  librhythmbox-core5 libmusicbrainz3-6
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  font-manager
The following packages will be upgraded:
  font-manager
1 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
1 not fully installed or removed.
Need to get 0 B/638 kB of archives.
After this operation, 147 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  font-manager
Install these packages without verification [y/N]? y
dpkg: dependency problems prevent configuration of font-manager:
 font-manager depends on libpython2.6 (>= 2.6); however:
  Package libpython2.6 is not installed.
dpkg: error processing font-manager (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 font-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)


How can i install it ???

---

### Post by ibjsb4 on 2012-10-20
It looks like you need to install either 2.7 or 3.2.

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=libpython](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=libpython)

---


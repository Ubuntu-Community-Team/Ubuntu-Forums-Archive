---
title: "[SOLVED] AWN update"
date: 2008-05-24
forum: General Help
---

### Post by nima352000 on 2008-05-24
Hi guy , i was having trouble installing AWN but i finally managed to install  and run it, but for some reason i still can get it to update and weather applet carshes all the time .
here what i get when im trying to update 

Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator Sources
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator Packages
  404 Not Found
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator Sources
  404 Not Found
Fetched 1B in 11s (0B/s)
Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/gutsy/avant-window-navigator/binary-i386/Packages.gz](http://download.tuxfamily.org/syzygy42/dists/gutsy/avant-window-navigator/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/gutsy/avant-window-navigator/source/Sources.gz](http://download.tuxfamily.org/syzygy42/dists/gutsy/avant-window-navigator/source/Sources.gz)  404 Not Found
Reading package lists... Done



any solution ?

---

### Post by moonbeam on 2008-05-24
reacocard changed the location of his repo:

see  [http://ubuntuforums.org/showthread.php?t=762363&highlight=avant+window+navigator](http://ubuntuforums.org/showthread.php?t=762363&highlight=avant+window+navigator)

---

### Post by nima352000 on 2008-05-25
i uninstall it and i follow the instruction on that link but i get the following error





nima@nima-laptop:~$ sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn0-bzr but it is not going to be installed
                              Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                              Depends: libawn0-bzr (= 0.3.1.bzr242.2~gutsy) but it is not going to be installed
  awn-core-applets-bzr: Depends: libawn0-bzr but it is not going to be installed
                        Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                        Depends: libawn0-bzr but it is not going to be installed
  awn-manager-bzr: Depends: python-awn-bzr but it is not going to be installed
E: Broken packages

---

### Post by moonbeam on 2008-05-25
> **nima352000 said:**
> i uninstall it and i follow the instruction on that link but i get the following error





nima@nima-laptop:~$ sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn0-bzr but it is not going to be installed
                              Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                              Depends: libawn0-bzr (= 0.3.1.bzr242.2~gutsy) but it is not going to be installed
  awn-core-applets-bzr: Depends: libawn0-bzr but it is not going to be installed
                        Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                        Depends: libawn0-bzr but it is not going to be installed
  awn-manager-bzr: Depends: python-awn-bzr but it is not going to be installed
E: Broken packages

In general it's best to post install issues with reacocard's repo in the support thread linked above.

---


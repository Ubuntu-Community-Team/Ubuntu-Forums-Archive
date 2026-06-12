---
title: "Can't install Calligra"
date: 2012-12-31
forum: General Help
---

### Post by zerubbabel on 2012-12-31
I added the kubuntu backports ppa and tried to install Calligra, with the following results:

[INDENT]zerubbabel@dz:~$ sudo apt-get install calligra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 calligra : Depends: braindump (>= 1:2.5.3-0ubuntu2) but it is not going to be installed
            Depends: calligraflow (>= 1:2.5.3-0ubuntu2) but it is not going to be installed
            Depends: calligraplan (>= 1:2.5.3-0ubuntu2) but it is not going to be installed
            Depends: calligrasheets (>= 1:2.5.3-0ubuntu2) but it is not going to be installed
            Depends: calligrastage (>= 1:2.5.3-0ubuntu2) but it is not going to be installed
            Depends: calligrawords (>= 1:2.5.3-0ubuntu2) but it is not going to be installed
            Depends: karbon (>= 1:2.5.3-0ubuntu2) but it is not going to be installed
            Depends: kexi (>= 1:2.5.3-0ubuntu2) but it is not going to be installed
            Depends: krita (>= 1:2.5.3-0ubuntu2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
zerubbabel@dz:~$ [/INDENT]

How can I get past this?

---


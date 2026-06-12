---
title: "Restore from livecd"
date: 2014-08-19
forum: General Help
---

### Post by dmwarren2 on 2014-08-19
Hi,

After login I get a blank desktop with no launcher or top tool bar. I am unable to get a terminal up however can get to a terminal using Crtl+Alt+F2.

If possible I would like to launch Timeshift and restore a snapshot of when the system was working correctly but it seems I can't launch it from this "tty1" command line.

I've read that its possible to use timeshift with a liveCD/USB but when i boot up with a liveUSB i am unable to install it due to package dependencies.

Any help appreciated.

---

### Post by ubudog on 2014-08-19
What happens when you try to install it?  What are the errors?

---

### Post by dmwarren2 on 2014-08-20
(Having added the repository and apt-get update)...

ubuntu@ubuntu:~$ sudo apt-get install timeshift
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 timeshift : Depends: gksu but it is not installable
E: Unable to correct problems, you have held broken packages.
ubuntu@ubuntu:~$

SOLVED. I still had the browser open when trying to install Timeshift on the liveUSB, closing the browser allowed it to install. System restored :D

---

### Post by ubudog on 2014-08-21
Glad to hear you got your system restored, that is a weird bug if it was that!  :D

---


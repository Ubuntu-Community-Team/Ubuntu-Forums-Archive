---
title: "Error with apt-get [Kubuntu 16.04"
date: 2016-05-03
forum: General Help
---

### Post by AccessDen1ed on 2016-05-03
Hello, new to this. Wanted to use a linux distro for fun and for pen testing, but decided I didn't want kali so I went with Kubuntu 16.04. I tried to use katoolin ( Which I now recognize as a poor life decision) And I thik I may have broken apt-get. Here is the error I get whenever I try to use "sudo apt-get -f install

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 libjpeg8 : Breaks: libjpeg8:i386 (!= 8c-2ubuntu8) but 8d1-2 is installed
 libjpeg8:i386 : Breaks: libjpeg8 (!= 8d1-2) but 8c-2ubuntu8 is installed
 libncursesw5 : Depends: libtinfo5 (= 6.0+20160213-1ubuntu1) but 6.0+20160319-1 is installed
 samba-libs : Depends: python-talloc (>= 2.1.6) but 2.1.5-2 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies



If you need any more information, just tell me. Again, I'm rather new so I'm not sure what logs you'd need. Just tell me where to go and what to do, and I'll do it.

---

### Post by T.J. on 2016-05-06
Have you tried: 

*sudo apt-get check*

or 

*sudo dpkg --configure -a*

---

### Post by ian-weisser on 2016-05-06
'package Foo (A) but Foo (B) is installed' errors like this usually indicate a *version conflict*.

Version conflicts are usually caused by software from PPAs, third party sources, internet websites, and other unclean repositories.

Each package (Foo) can have only one version installed at a time. To upgrade Foo 1.1 to Foo 1.2, the older package must be removed and replaced by the newer version. The classic example of a version conflict occurs when you install Bar, (which requires Foo 1.1), and install Baz (which requires Foo 1.2). See the conflict? The system cannot isntall both required versions. This is where apt gives up and starts throwing errors 'package Foo (1.1) but Foo (1.2) is installed' at you.

Ubuntu's solution is to compile all packages against the same version of Foo. Only one version is in the Ubuntu repositories, and its guaranteed to be compatible with all other software in the Ubuntu repositories.

You broke this solution when you installed non-Ubuntu software. Uninstall that software, and delete that source - it is not your friend. Revert to Ubuntu-only software, which will fix your version problem, and look for an appropriate application for your needs in the Ubuntu repositories first.

If you decide to install non-Ubuntu software (you can. it's *your* system), compare the dependency requirements with what you already have onboard before installing...or contact the developer and ask them to post a snap (which doesn't have version conflicts) instead of a deb.

---


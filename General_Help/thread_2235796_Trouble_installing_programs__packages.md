---
title: "Trouble installing programs / packages"
date: 2014-07-23
forum: General Help
---

### Post by blue carrot on 2014-07-23
Hi all,

I'm having trouble installing packages, regardless of what method I try (terminal command, .deb files, etc.) I have some very basic video editing I need to do ASAP for work so it's a little frustrating. 

I'm using Lubuntu 13.04  

Here's what my Terminal tells me when I tried to install OpenShot

bart@bart-System-Product-Name:~$ sudo apt-get install openshot
[sudo] password for bart: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 openshot : Depends: melt but it is not going to be installed
            Depends: python-httplib2 but it is not going to be installed
            Depends: python-mlt5 but it is not going to be installed or
                     python-mlt3 but it is not installable or
                     python-mlt2 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


Any help solving this would be greatly appreciated, thanks!!

---

### Post by QIII on 2014-07-23
Hello!

The most likely cause for this is that 13.04 has passed end of life, the repositories have been moved and it is no longer supported by Canonical.

I recommend a fresh install of a supported release of Lubuntu.  [http://lubuntu.net/](http://lubuntu.net/)

We no longer support threads requesting support for End Of Life (EOL) releases of Ubuntu flavors.  Please see the sticky at [http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730).

Thread closed.

---


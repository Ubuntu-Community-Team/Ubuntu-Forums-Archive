---
title: "Cannot Install Skype - Ubuntu 13.10"
date: 2014-02-17
forum: General Help
---

### Post by VinceRR on 2014-02-17
Been trying to install Skype on Ubuntu 13.10 (3.11.0-15-generic), but with no success. Have tried:

  
$ sudo dpkg --add-architecture i386 $ sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner" 
$ sudo apt-get update -y 
$ sudo apt-get install skype

  Reading package lists... Done Building dependency tree Reading state information... Done Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming. The following information may help to resolve the situation:

  The following packages have unmet dependencies.  skype : Depends: skype-bin 
E: Unable to correct problems, you have held broken packages.

  
So then I try:

  
$ sudo apt-get install skype-bin

  Reading package lists... Done Building dependency tree Reading state information... Done Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming. The following information may help to resolve the situation:

  The following packages have unmet dependencies.  skype-bin:i386 : Depends: libqtwebkit4:i386 (>= 2.2~2011week36) but it is not going to be installed                   Depends: libgl1-mesa-glx:i386 but it is not going to be installed 

E: Unable to correct problems, you have held broken packages.

  
Have tried through aptitude, but the same result. Any suggestions? Thanks.

---

### Post by plucky on 2014-02-17
> E: Unable to correct problems, you have held broken packages.


Have you tried ```
sudo apt-get install -f
```?

---


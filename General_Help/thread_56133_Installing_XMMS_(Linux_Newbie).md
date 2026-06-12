---
title: "Installing XMMS (Linux Newbie)"
date: 2005-08-11
forum: General Help
---

### Post by Illsaide on 2005-08-11
Hi, I'm new to linux, I have tried most of the popular distros, but I like Ubuntu best, as it has the clean, simple looks.


I needed to install xmms, so I open the Root Terminal, key in my password, and followed the instruction on [http://ubuntuforums.org/archive/index.php/t-6485.html](http://ubuntuforums.org/archive/index.php/t-6485.html) , but I could'nt get pass "sudo apt-get install xmms"

root@ubuntu:/home/myusername # sudo apt-get install xmms
Reading package lists... Done
Building dependency tree... Done
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [ftp://ftp.belnet.be](ftp://ftp.belnet.be) warty/main
Packages (/var/lib/apt/lists/ftp.belnet.be_packages_ubuntu_dists_warty_main_binary-i386_Packages)
- stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.belnet.be](ftp://ftp.belnet.be)
warty/restricted Packages
(/var/lib/apt/lists/ftp.belnet.be_packages_ubuntu_dists_warty_restricted_binary-i386_Packages)
- stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.belnet.be](ftp://ftp.belnet.be)
warty/universe Packages
(/var/lib/apt/lists/ftp.belnet.be_packages_ubuntu_dists_warty_universe_binary-i386_Packages)
- stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.belnet.be](ftp://ftp.belnet.be)
warty/multiverse Packages
(/var/lib/apt/lists/ftp.belnet.be_packages_ubuntu_dists_warty_multiverse_binary-i386_Packages)
- stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package xmms has no installation candidate
root@ubuntu:/home/myusername #


Thx in advance  :smile: 

Cheers,

---

### Post by jasmuz on 2005-08-11
Those servers you have listed in you /etc/apt/sources.list are strange, here use mine for Hoary:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe


#backup Mirror - FAST
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security multiverse

---


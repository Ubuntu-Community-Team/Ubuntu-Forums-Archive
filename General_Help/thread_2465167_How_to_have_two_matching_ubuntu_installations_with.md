---
title: "How to have two matching ubuntu installations with the same set of installed packages"
date: 2021-07-23
forum: General Help
---

### Post by jeclark2006 on 2021-07-23
Is there a simple method of setting up a second newly installed Ubuntu system, such that it has the same set of packages at the same level as the first?

And needless to say, I can't afford 'landscape'.

Thanks.

---

### Post by crip720 on 2021-07-24
Very easy to do.  One way is to partition your drive and install second Ubuntu(or any OS) and set it up any way you choose.  Can also copy any data from one Ubuntu to the other, so they both match.  Can only use one at a time and need to reboot to use the other.  Second way is using another computer/laptop and installing onto that one.  Can use both OSs at same time, if both are on.  First way is your basic dual boot configuration, mistakes by you can be made, so backup of important data is strongly recommended.

---

### Post by grahammechanical on 2021-07-24
Every installation of Ubuntu will come with the same set of default applications. To have the same version of (for example) the Firefox web browser in two different installs of Ubuntu you must have the same version of Ubuntu installed twice.

Also it is best to install Long Term Support (LTS) versions of Ubuntu. The latest LTS version is Ubuntu 20.04.2. The next LTS version will be 22.04 which is released towards the end of April 2022. We can do a direct online upgrade from 20.04 LTS to 22.04 LTS.

Each version of Ubuntu has its own software repositories from which applications are downloaded and installed. If you put in two different versions of Ubuntu any applications you choose to install in each OS will be at different version numbers.

Regards

---

### Post by CatKiller on 2021-07-24
There are lots of threads already that deal with including your list of installed packages with your backup so that you can restore them all later. This is no different, except you're "restoring" to a different computer.

---

### Post by monkeybrain20122 on 2021-07-24
Of course you can do it manually like you copy the package list when you do an OS upgrade by fresh install, but I think OP wants some way to sync the packages of his two Ubuntus. I don't have an answer for that.

---

### Post by HermanAB on 2021-07-25
This is very easy to do with rpm based distros: [https://www.aeronetworks.ca/2014/06/replicating-fedora-machines-using.html?m=1](https://www.aeronetworks.ca/2014/06/replicating-fedora-machines-using.html?m=1)

Debian and Ubuntu has a cripple kickstart method called preseed: https://wiki.debian.org/AutomatedInstallation

---


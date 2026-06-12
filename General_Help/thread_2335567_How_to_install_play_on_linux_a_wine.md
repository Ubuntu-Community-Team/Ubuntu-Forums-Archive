---
title: "How to install play on linux a wine"
date: 2016-08-30
forum: General Help
---

### Post by 4kody-c on 2016-08-30
UBUNTU 12.04

Play on Linux Err - sudo apt-get install playonlinux
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 playonlinux : Depends: wine but it is not installable or
                        wine-unstable but it is not installable
E: Unable to correct problems, you have held broken packages.

WINE ERR - sudo apt-get install wine1.8
E: Unable to locate package wine1.8
E: Couldn't find any package by regex 'wine1.8'

Does Anyone have a fix none of the other forms have an answer

---

### Post by howefield on 2016-08-30
Thread moved to the "*General Help*" forum.

Try

```
sudo apt-get -f install
```

What's the output of..

```
apt-cache policy wine
```

---

### Post by ian-weisser on 2016-08-30
The package manager is telling you that Wine 1.8 is not available for any 12.04 sources that it knows about.

Either use the generic 'Wine' package that apt does know about (in the Ubuntu repositories), or inform the package manager about a Wine 1.8 source by adding that source or PPA.

---

### Post by grahammechanical on 2016-08-30
If you have the universe repository enabled in System Settings>Software sources you should be able to install wine 1.4. But even Ubuntu 16.04 will only give you wine 1.6. To get wine 1.8 we have to install the wine PPA.

[http://packages.ubuntu.com/search?keywords=wine](http://packages.ubuntu.com/search?keywords=wine)

[https://www.winehq.org/download](https://www.winehq.org/download)

Regards

---

### Post by 4kody-c on 2016-08-30
First one says package not found out put is wine:
  Installed: (none)
  Candidate: (none)
  Version table:
(precise)kody@localhost:~$

---

### Post by 4kody-c on 2016-08-30
My Architecture is armv7l

---


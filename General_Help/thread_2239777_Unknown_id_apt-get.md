---
title: "Unknown id: apt-get"
date: 2014-08-15
forum: General Help
---

### Post by emcquinn8 on 2014-08-15
Hi, I'm trying to install a client with the commands from here [https://github.com/GaelCoin/GaelCoin/blob/master/doc/readme-qt.rst](https://github.com/GaelCoin/GaelCoin/blob/master/doc/readme-qt.rst) from the ubuntu 12.04 section.

this is the output from terminal:

[HTML]
 apt-get install qt4-qmake libqt4-dev build-essential libboost-dev libboost-system-dev     libboost-filesystem-dev libboost-program-options-dev libboost-thread-dev     libssl-dev libdb++-dev libminiupnpc-dev
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
max@max:~$ sudo su apt-get install qt4-qmake libqt4-dev build-essential libboost-dev libboost-system-dev     libboost-filesystem-dev libboost-program-options-dev libboost-thread-dev     libssl-dev libdb++-dev libminiupnpc-dev
[sudo] password for max: 
Unknown id: apt-get
max@max:~$ sudo su - apt-get install qt4-qmake libqt4-dev build-essential libboost-dev libboost-system-dev     libboost-filesystem-dev libboost-program-options-dev libboost-thread-dev     libssl-dev libdb++-dev libminiupnpc-dev
Unknown id: apt-get

[/HTML]

What should I do next to get this client installed on my system (12.04)?

---

### Post by steeldriver on 2014-08-15
You need to remove the **su** - just

```

sudo apt-get install qt4-qmake ...

```

---

### Post by emcquinn8 on 2014-08-16
Here is the terminal output:

```
sudo apt-get install qt4-qmake libqt4-dev build-essential libboost-dev libboost-system-dev     libboost-filesystem-dev libboost-program-options-dev libboost-thread-dev     libssl-dev libdb++-dev libminiupnpc-dev
[sudo] password for max: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
libssl-dev is already the newest version.
libssl-dev set to manually installed.
qt4-qmake is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libminiupnpc-dev : Depends: libminiupnpc8 (= 1.6-3ubuntu1.1) but 1.6-precise2 is to be installed
E: Unable to correct problems, you have held broken packages.


```

---

### Post by oldos2er on 2014-08-16
Try ```
sudo apt-get install -f
```

---


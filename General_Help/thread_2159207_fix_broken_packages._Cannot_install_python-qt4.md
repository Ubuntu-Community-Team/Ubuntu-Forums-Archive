---
title: "fix broken packages. Cannot install python-qt4"
date: 2013-07-02
forum: General Help
---

### Post by questworld on 2013-07-02
Hi all,

I am trying to install tortoisehg on Ubuntu 12.04 64 bit but cannot as there are broken packages.

```
sudo apt-get install tortoisehg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 tortoisehg : Depends: mercurial (< 2.2) but 2.6.1-1ppa1~precise1 is to be installed
              Depends: python-qt4 (>= 4.7) but it is not going to be installed
              Depends: python-qscintilla2 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Synaptic does not show any broken package. Tried following that also did not help. 

```
sudo apt-get update
sudo apt-get install -f 
```

Tried installing python-qt4 manually but got following output. 

```
sudo apt-get install python-qt4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 python-qt4 : Depends: libqt4-designer (>= 4:4.8.0-1~) but it is not going to be installed
              Depends: libqt4-help (>= 4:4.8.0-1~) but it is not going to be installed
              Depends: libqt4-scripttools (>= 4:4.8.0-1~) but it is not going to be installed
              Depends: libqt4-test (>= 4:4.8.0-1~) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Any ideas how do I resolve this. I do not know which package is broken.

---

### Post by seruling on 2013-07-02
Have you try running "Software Updater"
In some cases, it will fix pending/unfinished installation.

---

### Post by questworld on 2013-07-02
Yes I have tried that too. No luck

---

### Post by dino99 on 2013-07-02
install that ppa, update and voila :P  [https://launchpad.net/~tortoisehg-ppa/+archive/releases](https://launchpad.net/~tortoisehg-ppa/+archive/releases)

---

### Post by questworld on 2013-07-02
have tried that too. Added [http://ppa.launchpad.net/tortoisehg-ppa/releases/ubuntu](http://ppa.launchpad.net/tortoisehg-ppa/releases/ubuntu) but did not work. :-(

---

### Post by questworld on 2013-07-10
Fixed it ! :D

Use

sudo aptitude install tortoisehg

And accepted the following solution. 


```
The following actions will resolve these dependencies:

      Downgrade the following packages:                                            
1)      libqt4-dbus [4:4.8.1-0ubuntu4.4 (now) -> 4:4.8.1-0ubuntu4 (precise)]       
2)      libqt4-declarative [4:4.8.1-0ubuntu4.4 (now) -> 4:4.8.1-0ubuntu4 (precise)]
3)      libqt4-network [4:4.8.1-0ubuntu4.4 (now) -> 4:4.8.1-0ubuntu4 (precise)]    
4)      libqt4-opengl [4:4.8.1-0ubuntu4.4 (now) -> 4:4.8.1-0ubuntu4 (precise)]     
5)      libqt4-script [4:4.8.1-0ubuntu4.4 (now) -> 4:4.8.1-0ubuntu4 (precise)]     
6)      libqt4-sql [4:4.8.1-0ubuntu4.4 (now) -> 4:4.8.1-0ubuntu4 (precise)]        
7)      libqt4-sql-sqlite [4:4.8.1-0ubuntu4.4 (now) -> 4:4.8.1-0ubuntu4 (precise)] 
8)      libqt4-svg [4:4.8.1-0ubuntu4.4 (now) -> 4:4.8.1-0ubuntu4 (precise)]        
9)      libqt4-xml [4:4.8.1-0ubuntu4.4 (now) -> 4:4.8.1-0ubuntu4 (precise)]        
10)     libqt4-xmlpatterns [4:4.8.1-0ubuntu4.4 (now) -> 4:4.8.1-0ubuntu4 (precise)]
11)     libqtcore4 [4:4.8.1-0ubuntu4.4 (now) -> 4:4.8.1-0ubuntu4 (precise)]        
12)     libqtgui4 [4:4.8.1-0ubuntu4.4 (now) -> 4:4.8.1-0ubuntu4 (precise)]         
13)     qdbus [4:4.8.1-0ubuntu4.4 (now) -> 4:4.8.1-0ubuntu4 (precise)]   
```

---


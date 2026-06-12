---
title: "I need information about these lines start with W:"
date: 2017-03-17
forum: General Help
---

### Post by luhollanda on 2017-03-17
luciana@luciana-Lenovo-Z40-70:~$ sudo apt update
Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) devel-security InRelease                                                         
Hit:2 [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial InRelease                                                  
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) devel InRelease [246 kB]                                            
Hit:4 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) devel InRelease                         
Hit:5 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) devel-updates InRelease                 
Hit:6 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) devel-backports InRelease                            
Hit:7 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                                               
Fetched 246 kB in 2s (99.2 kB/s)                                                           
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
W: Conflicting distribution: [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) devel-security InRelease (expected devel-security but got zesty)
W: Conflicting distribution: [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) devel InRelease (expected devel but got zesty)
W: Conflicting distribution: [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) devel-updates InRelease (expected devel-updates but got zesty)
W: Conflicting distribution: [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) devel-backports InRelease (expected devel-backports but got zesty)
W: Conflicting distribution: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) devel InRelease (expected devel but got zesty)

---

### Post by ajgreeny on 2017-03-17
Which version of Ubuntu are you actually using, xenial, yakkety or zesty, (16.04, 16.10 or 17.04)?

You appear to have a bit of a mixture of versions showing in the software-sources and the W is an indication of "Warning"

---


---
title: "I need some help removing VWware Player."
date: 2014-07-03
forum: General Help
---

### Post by ManyBeers on 2014-07-03
Xubuntu 12.04
Yesterday I installed VMware Player (which i got from VMware) using this exact command
...gksudo bash ./VMware-Player-6.0.3-1895310.x86_64.bundle...
which then ran a gui installation program and installed the program. I have now changed my mind and would like to remove it from my system. It does not show up in Software Center or Synaptic Package Manager so it will probably need some command line code. I have searched on here and there was a command that worked on earlier versions
...vmware-player installer -u somethibn something.. but not on mine. I have also been to VMware website and couldn't find anything there. Oh and I have also tried by rerunning the install script which again brings up the gui only now it reports all is up to date and there are no options other than to close.

---

### Post by ManyBeers on 2014-07-04
I got it fixed the command to remove is...vmware-installer -u vmware-player
...For some reason when i initially tried it the command failed. This is solved.

---


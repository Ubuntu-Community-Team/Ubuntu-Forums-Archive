---
title: "Synaptic errors"
date: 2004-11-15
forum: General Help
---

### Post by trivialpackets on 2004-11-15
Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
click ok
Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
click ok

Open Repositories>
Error Not Locked

Any ideas of how to get at upgrades and installations?  Possibly apt-get?  Never ventured into that yet.

---

### Post by amoser on 2004-11-15
Do you have another Synaptic window open?

---

### Post by sfw5000 on 2004-11-15
it does sound like you have another synaptic window open... but anyway to use apt open a terminal and type ```
sudo apt-get update
``` to update the list of available software, then to upgrade all the packages you have installed ```
sudo apt-get upgrade
```. To install a particular package ```
 sudo apt-get install packagename 
``` to search for a package ```
sudo apt-cache search keyword
```

of course, much more comprehensive guides can be found -- look in the howto section of these forums. Also, FYI synaptic is a front end for apt -- so it does the same thing.

HTH

---

### Post by trivialpackets on 2004-11-16
Thanks, got it now.  I must have messed something up, as I could not log into the system after I logged out.  Reinstalled and am in synaptic now.

---


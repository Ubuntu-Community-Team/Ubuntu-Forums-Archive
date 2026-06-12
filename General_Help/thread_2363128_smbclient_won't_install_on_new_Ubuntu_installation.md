---
title: "smbclient won't install on new Ubuntu installation"
date: 2017-06-06
forum: General Help
---

### Post by aeronutt on 2017-06-06
I've got fresh install of Ubuntu 16.04, and am trying to install smbclient.
I'm getting dependancy errors:

```
$ sudo apt install smbclient 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 smbclient : Depends: libwbclient0 (= 2:4.3.8+dfsg-0ubuntu1) but 2:4.3.11+dfsg-0ubuntu0.16.04.7 is to be installed
             Depends: samba-libs (= 2:4.3.8+dfsg-0ubuntu1) but 2:4.3.11+dfsg-0ubuntu0.16.04.7 is to be installed
E: Unable to correct problems, you have held broken packages.

```

Trying the usual fixes does nothing:
```
sudo apt-get install --fix-broken
sudo apt-get autoremove 
sudo apt-get update 
sudo apt-get install smbclient
```

That is, no broken packages are fixed, and "sudo apt-get install smbclient" simply repeats the above dependancy error.

Help!!

---


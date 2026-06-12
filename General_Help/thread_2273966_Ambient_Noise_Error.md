---
title: "Ambient Noise Error"
date: 2015-04-16
forum: General Help
---

### Post by jelanithompson on 2015-04-16
Hey there,

My name's Jelani and I'm a bit new to the Ubuntu OS. I'd like to install the Ambient Noise app listed here: [http://anoise.tuxfamily.org/](http://anoise.tuxfamily.org/)

However, every time I try to install it, the terminal ends up giving me this error:

dpkg: error processing package smbclient (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 samba-common
 samba-common-bin
 samba
 winbind
 libnss-winbind:amd64
 libpam-winbind:amd64
 smbclient
E: Sub-process /usr/bin/dpkg returned an error code (1)

Would someone be able to help me out with this issue? Thanks a bunch!

---

### Post by Impavidus on 2015-04-17
0: Welcome here. I hope Ubuntu will be a pleasant experience for you.
1: I assume you tried installing ambient noise using the instructions on the linked page. Can you confirm? This installs the software using a PPA, which is the preferred way to install software not present in the Ubuntu repositories.
2: Which version of Ubuntu do you run?
3: To get some details, could you post the complete output of these commands:```
sudo apt-get update
sudo apt-get upgrade
```

---


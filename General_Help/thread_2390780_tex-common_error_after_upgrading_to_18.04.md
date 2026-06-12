---
title: "tex-common error after upgrading to 18.04"
date: 2018-05-02
forum: General Help
---

### Post by rveska on 2018-05-02
Hi,

I get an error with tex-common every time I use apt (or other package managers) after upgrading to 18.04. I have tried to remove the package and reinstalling, but I still get the same error. It appears no matter what I do with apt, but it does not seem to affect anything though...
```

sudo apt-get dist-upgrade 
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 
Setting up tex-common (6.09) ...
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... 
updmap-sys failed. Output has been stored in
/tmp/updmap.u71mEa1f
Please include this file if you report a bug.

Sometimes, not accepting conffile updates in /etc/texmf/updmap.d
causes updmap-sys to fail.  Please check for files with extension
.dpkg-dist or .ucf-dist in this directory

dpkg: error processing package tex-common (--configure):
 installed tex-common package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 tex-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Thanx
  R

---

### Post by PaulW2U on 2018-05-02
A known issue for some time. See the following bug reports:

[https://bugs.launchpad.net/ubuntu/+source/tex-common/+bug/1514474](https://bugs.launchpad.net/ubuntu/+source/tex-common/+bug/1514474)
[https://bugs.launchpad.net/ubuntu/+source/tex-common/+bug/1746865](https://bugs.launchpad.net/ubuntu/+source/tex-common/+bug/1746865)

---


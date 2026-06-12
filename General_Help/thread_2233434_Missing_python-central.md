---
title: "Missing python-central"
date: 2014-07-08
forum: General Help
---

### Post by peter120 on 2014-07-08
Hi,
Using 14.04 server. 
I am trying to install a Subversion web based control panel.
Submin or USVN seem top of the list.


Following instructions in [http://supermind.nl/submin/download.html](http://supermind.nl/submin/download.html)
On
```
sudo apt-get install submin2
```
I get the error:

```
The following packages have unmet dependencies.
 submin2 : Depends: python-central (>= 0.6.11) but it is not installable
E: Unable to correct problems, you have held broken packages.

```

I tried 
```
sudo aptitude install python-central
```
but that gives

```
 submin2 : Depends: python-central (>= 0.6.11) which is a virtual package.
The following actions will resolve these dependencies:
```

How do I get python-central?

Alternatively has anyone installed a web control panel?
[http://www.linuxgurru.com/2012/05/how-to-install-uvn-on-ubuntu/](http://www.linuxgurru.com/2012/05/how-to-install-uvn-on-ubuntu/)
doesn't work either. Just hangs when I attempt to run the install.php

---

### Post by peter120 on 2014-07-08
OK, got it.
Manually download & dpkg -i

---


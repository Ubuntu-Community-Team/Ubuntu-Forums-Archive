---
title: "Package manager is stuck in 18.04"
date: 2018-08-27
forum: General Help
---

### Post by jlh68 on 2018-08-27
On my newly upgraded Netbook I was trying to install some new apts and the installation failed and now I can not clean it out so I can install other software.  I get a "Do not Enter" symbol on my top panel.

How do I clean out the offending package?  so that I can add other software.

---

### Post by mörgæs on 2018-08-27
Please reboot and post the output from ```
sudo apt update
sudo apt dist-upgrade
```
in CODE tags.

---

### Post by jlh68 on 2018-08-27
Here Is the last part

> $ sudo apt dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ttf-mscorefonts-installer needs to be reinstalled, but I can't find an archive for it.

---

### Post by jlh68 on 2018-08-27
I copied the last command output:
> $ sudo apt dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ttf-mscorefonts-installer needs to be reinstalled, but I can't find an archive for it.

I was tryiing to install the Restricted Applications for media.

---

### Post by jlh68 on 2018-08-28
This is the notice I got and Package Manager is lockedup
> E: The package ttf-mscorefonts-installer needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I have not found a way to unlock Package Manager, so I cannot install any more applications.

---


---
title: "security updates anomaly"
date: 2015-08-25
forum: General Help
---

### Post by fade2gray on 2015-08-25
I've just revived an old machine (intel core duo quad) with Ubuntu 14.04.3 LTS server edition.

After doing the 'sudo apt-get update/upgrade' thing and installing Virtualmin, subsequent logins inform me...
> Using username "fade2gray".
Welcome to Ubuntu 14.04.3 LTS (GNU/Linux 3.19.0-25-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Tue Aug 25 15:43:08 BST 2015

  System load: 0.37              Memory usage: 1%   Processes:       119
  Usage of /:  2.6% of 88.65GB   Swap usage:   0%   Users logged in: 0

  Graph this data and manage this system at:
    [https://landscape.canonical.com/](https://landscape.canonical.com/)

[B]7 packages can be updated.
7 updates are security updates.[/B]


but any further 'sudo apt-get upgrade' results in...
> fade2gray@u64s:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic-lts-vivid linux-headers-generic-lts-vivid
  linux-image-generic-lts-vivid
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.


I certainly don't want to upgrade to vivid, but can anyone advise my about the 7 missing security updates?

EDIT: Forgot to mention I also installed openbox and x11vnc.

---

### Post by deadflowr on 2015-08-25
Those kernels themselves won't upgrade you to vivid.
14.04.3 comes with the vivid hardware stack, if you installed from the 14.04.3 iso.
Part of this:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Basically, though, since those packages are kernels, you need to run the *apt get dist-upgrade* command, instead of the *apt-get upgrade* command.
the bland upgrade command only updates any existing package within the system.
the dist-upgrade command allows to install new packages, which is what happens when you install a new kernel package.

Hope that makes sense.

---

### Post by Bucky Ball on 2015-08-25
As suggested by deadflowr, run these:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

This will NOT upgrade the release to a newer one, just upgrade the software of the release you already have installed. *Always* 'sudo apt-get update' prior to 'sudo apt-get upgrade'. Good luck.

---

### Post by fade2gray on 2015-08-25
Thanks for the replies.

So, doing a dist-upgrade will solve the missing 7 missing security updates and wont upgrade me to 15.04? Virtualmin only supports LTS releases, hence the next release it will support is 16.04 - I don't want to mess that up.

EDIT: It's ok - I was confusing dist-upgrade with do-release-upgrade. Thanks

---

### Post by Bucky Ball on 2015-08-25
> **Bucky Ball said:**
> 
This will NOT upgrade the release to a newer one, just upgrade the software of the release you already have installed.

^^
This. :)

---


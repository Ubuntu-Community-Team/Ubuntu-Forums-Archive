---
title: "Package half installed don't go away"
date: 2008-06-19
forum: General Help
---

### Post by Daniel de Paula on 2008-06-19
My box is refusing do install new packages. If I run ```
dpkg --audit
``` I get the following:

```
The following packages are only half installed, due to problems during
installation.  The installation can probably be completed by retrying it;
the packages can be removed using dselect or dpkg --remove:
 linux-ubuntu-modules-2.6.22-14-generic Ubuntu supplied Linux modules for versi

```

Ok. No problem. I **should** be easy to fix: all I need is to ```
sudo dpkg -r  linux-ubuntu-modules-2.6.22-14-generic
```

But it doesn't work... This is the message I get: 

```
(Reading database ... 173440 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-14-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-14-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Cannot find /lib/modules/2.6.22-14-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-14-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-14-generic


```Any help?

---

### Post by Happy_Man on 2008-06-19
Does ```
sudo apt-get -f install
``` help?

---

### Post by iaculallad on 2008-06-19
Create the file since it does not exist:

```
sudo touch /boot/System.map-2.6.22-14-generic
```

Recreate it's missing file and directory:

```
sudo mkdir /lib/modules/2.6.22-14-generic
sudo touch /lib/modules/2.6.22-14-generic/modules.dep.temp
```

Remove the file:

```
sudo apt-get remove linux-ubuntu-modules-2.6.22-14-generic
```

---


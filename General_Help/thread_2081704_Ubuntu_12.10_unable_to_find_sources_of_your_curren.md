---
title: "Ubuntu 12.10 unable to find sources of your current kernel"
date: 2012-11-07
forum: General Help
---

### Post by pmla on 2012-11-07
Doing something wrong?
New fresh install of ubuntu 12.10 64x.
Did all updates... including new kernel 3.5.0-18-generic
Also installed
sudo apt-get install dkms

download the virtualbox for ubuntu 12.10 64x and extension pack
created a win7 guest machine
and kabummmmm

```
    Kernel driver not installed (rc=-1908)

    The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

    '/etc/init.d/vboxdrv setup'

    as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
```


running sudo /etc/init.d/vboxdrv setup
log file:

    ```
Uninstalling modules from DKMS
    removing old DKMS module vboxhost version 4.2.4

    ------------------------------
    Deleting module version: 4.2.4
    completely from the DKMS tree.
    ------------------------------
    Done.
    Attempting to install using DKMS

    Creating symlink /var/lib/dkms/vboxhost/4.2.4/source ->
    /usr/src/vboxhost-4.2.4

    DKMS: add completed.
    Failed to install using DKMS, attempting to install without
    Makefile:181: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again. Stop.
```

Anyone with this problem?

---

### Post by pmla on 2012-11-07
ahhh missing packages:

```
sudo apt-get install dkms build-essential linux-headers-generic
```
```

sudo /etc/init.d/vboxdrv setup
```

---


---
title: "Problems inserting the kernel module for VirtualBox"
date: 2013-06-11
forum: General Help
---

### Post by Smajjk on 2013-06-11
I am running kernel 3.8.9 and I have some problems running any virtual OS through Virtualbox. When I press Start I get the following error message:

```
Failed to open a session for the virtual machine...

The virtual machine ... has terminated unexpectedly during startup with exit code 1.
```

It then gives me this advice:

```
Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
```

The DKMS package is already installed and when I run the command given above I get:

```
[15:46]:/etc/init.d/vboxdrv setup
zsh: no such file or directory: /etc/init.d/vboxdrv
```

I can however find a file virtualbox:

```
[15:54]:/etc/init.d/virtualbox start
* Starting VirtualBox kernel modules            
* No suitable module for running kernel found
```

This obviously doesn't help either. Any advice? :p

---

### Post by howefield on 2013-06-11
Try running the command with sudo...

```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by gordintoronto on 2013-06-11
Where did you install VirtualBox from? Does the 3.8 kernel correspond to Ubuntu 13.04? If so, go to the VirtualBox site and select the Ringtail version of VirtualBox.

---


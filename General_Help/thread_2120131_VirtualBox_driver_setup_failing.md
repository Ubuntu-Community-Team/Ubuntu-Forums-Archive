---
title: "VirtualBox driver setup failing"
date: 2013-02-25
forum: General Help
---

### Post by Cario on 2013-02-25
Hello everyone.

I've been having a problem with virtualbox in ubuntu 12.04. Earlier today I had it installed and it was working properly, but then I installed a ubuntu package called m4 so that I could setup a cross-compiler. When I installed it, it asked if it could remove virtualbox, and I said yes (stupid move). So then I uninstalled m4 and tried to install virtualbox again. At first I tried from the download here: [https://www.virtualbox.org/wiki/Download_Old_Builds_4_0](https://www.virtualbox.org/wiki/Download_Old_Builds_4_0)
And I got the when I tried running it:
```

Verifying archive integrity... All good.
Uncompressing VirtualBox for Linux installation...........
VirtualBox Version 4.0.18 r82821 (2012-12-18T11:37:47Z) installer
Please install the build and header files for your current Linux kernel.
The current kernel version is 3.2.0-29-generic-pae
Problems were found which would prevent VirtualBox from installing.
Please correct these problems and try again.

```I tried installing another kernel version but that made no difference.
So then after that I tried installing virtualbox using this:
```
sudo apt-get install virtualbox-4.1
```So that installed virtualbox, but when I run it I get an error saying, "Kernel driver not installed (rc=-1908)  Please reinstall the kernel module by executing: /etc/init.d/vboxdrv setup"

So I tried running "/etc/init.d/vboxdrv setup" with root in the teminal, but that gave me the following error:
```

Stopping VirtualBox kernel modules ...done.
Uninstalling old VirtualBox DKMS kernel modules/etc/init.d/vboxdrv: 293: /etc/init.d/vboxdrv: /usr/share/virtualbox/src/vboxhost/do_dkms: not found
 ...done.
Trying to register the VirtualBox kernel modules using DKMS/etc/init.d/vboxdrv: 311: /etc/init.d/vboxdrv: /usr/share/virtualbox/src/vboxhost/do_dkms: not found
 ...failed!
  (Failed, trying without DKMS)
Recompiling VirtualBox kernel modules ...failed!
  (Look at /var/log/vbox-install.log to find out what went wrong)

```So I tried looking at /var/log/vbox-install.log using the following command
```
cat /var/log/vbox-install.log
```Which gave me the following
```
/etc/init.d/vboxdrv: 314: /etc/init.d/vboxdrv: /usr/share/virtualbox/src/vboxhost/vboxdrv/build_in_tmp: not found
```What should I do?

Thank you very much for your time,
Cario

---


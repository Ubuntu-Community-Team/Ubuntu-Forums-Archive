---
title: "vmware-server problems"
date: 2007-07-14
forum: General Help
---

### Post by TheRingmaster on 2007-07-14
I am trying to install vmware-server through [this howto]("http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html"). I keep getting this error during the installation. Note that I have most of the things installed already.

> $ sudo apt-get install vmware-server vmware-tools-kernel-modules
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vmware-tools-kernel-modules is already the newest version.
The following extra packages will be installed:
  libssl0.9.7
The following NEW packages will be installed:
  libssl0.9.7 vmware-server
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/81.7MB of archives.
After unpacking 136MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package libssl0.9.7.
(Reading database ... 125433 files and directories currently installed.)
Unpacking libssl0.9.7 (from .../libssl0.9.7_0.9.7k-3_i386.deb) ...
Unpacking vmware-server (from .../vmware-server_1.0.3-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/vmware-server_1.0.3-1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/vmware-server_1.0.3-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by Koybe on 2007-07-15
Maybe the installer finds something already installed about vmware.

```
sudo apt-get --purge remove vmware-server vmware-tools-kernel-modules
```
Pay attention of what it will uninstall.
Be sure nothing's left
```
sudo find / -name *vmware*
```

Then retry installing.

I really am not sure about this issuer, this is just a suggestion.

---


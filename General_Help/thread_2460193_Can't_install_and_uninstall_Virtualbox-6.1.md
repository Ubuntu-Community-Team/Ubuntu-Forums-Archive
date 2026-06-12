---
title: "Can't install and uninstall Virtualbox-6.1"
date: 2021-04-04
forum: General Help
---

### Post by username2758 on 2021-04-04
Hey,

After a broken attempt to install Virtualbox 6.1 on Ubuntu 20.04, I can't either install or uninstall Virtualbox.

```
$ sudo apt remove virtualbox-6.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpython2-stdlib libpython2.7-minimal libpython2.7-stdlib libqt5opengl5
  libqt5printsupport5 libqt5x11extras5 libsdl-ttf2.0-0 libsdl1.2debian
  python-is-python2 python2 python2-minimal python2.7 python2.7-minimal
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  virtualbox-6.1
0 upgraded, 0 newly installed, 1 to remove and 11 not upgraded.
1 not fully installed or removed.
After this operation, 216 MB disk space will be freed.
Do you want to continue? [Y/n] y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 192974 files and directories currently installed.)
Removing virtualbox-6.1 (6.1.18-142142~Ubuntu~eoan) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another p
rocess: Resource temporarily unavailable
dpkg: error processing package virtualbox-6.1 (--remove):
 installed virtualbox-6.1 package pre-removal script subprocess returned error e
xit status 1
dpkg: too many errors, stopping
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another p
rocess: Resource temporarily unavailable
vboxdrv.sh: failed: modprobe vboxdrv failed. Please use 'dmesg' to find out why.

There were problems setting up VirtualBox.  To re-start the set-up process, run
  /sbin/vboxconfig
as root.  If your system is using EFI Secure Boot you may need to sign the
kernel modules (vboxdrv, vboxnetflt, vboxnetadp, vboxpci) before you can load
them. Please see your Linux system's documentation for more information.
Errors were encountered while processing:
 virtualbox-6.1
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
$ sudo apt-get purge "^virtualbox-.*"
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'virtualbox-source' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-guest-utils' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-ose' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-guest-modules' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-guest-additions-iso' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-guest-dkms' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-dkms' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-guest-dkms-hwe' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-ext-pack' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-guest-modules-hwe' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-guest-x11-hwe' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-guest-source' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-qt' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-guest-source-hwe' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-2.0' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-2.1' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-2.2' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-modules' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-3.0' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-3.1' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-3.2' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-4.0' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-4.1' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-4.2' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-4.3' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-5.0' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-5.1' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-5.2' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-guest-utils-hwe' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-6.0' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-6.1' for regex '^virtualbox-.*'
Note, selecting 'virtualbox-guest-x11' for regex '^virtualbox-.*'
Package 'virtualbox-5.0' is not installed, so not removed
Package 'virtualbox-5.1' is not installed, so not removed
Package 'virtualbox-5.2' is not installed, so not removed
Note, selecting 'virtualbox-dkms' instead of 'virtualbox-modules'
Package 'virtualbox-2.0' is not installed, so not removed
Package 'virtualbox-2.1' is not installed, so not removed
Package 'virtualbox-2.2' is not installed, so not removed
Package 'virtualbox-3.0' is not installed, so not removed
Package 'virtualbox-3.1' is not installed, so not removed
Package 'virtualbox-3.2' is not installed, so not removed
Package 'virtualbox-4.0' is not installed, so not removed
Package 'virtualbox-4.1' is not installed, so not removed
Package 'virtualbox-4.2' is not installed, so not removed
Package 'virtualbox-4.3' is not installed, so not removed
Package 'virtualbox-guest-modules-hwe' is not installed, so not removed
Package 'virtualbox-ose' is not installed, so not removed
Package 'virtualbox-dkms' is not installed, so not removed
Package 'virtualbox-ext-pack' is not installed, so not removed
Package 'virtualbox-guest-additions-iso' is not installed, so not removed
Package 'virtualbox-guest-dkms' is not installed, so not removed
Package 'virtualbox-guest-dkms-hwe' is not installed, so not removed
Package 'virtualbox-guest-source' is not installed, so not removed
Package 'virtualbox-guest-source-hwe' is not installed, so not removed
Package 'virtualbox-guest-utils' is not installed, so not removed
Package 'virtualbox-guest-utils-hwe' is not installed, so not removed
Package 'virtualbox-guest-x11' is not installed, so not removed
Package 'virtualbox-guest-x11-hwe' is not installed, so not removed
Package 'virtualbox-qt' is not installed, so not removed
Package 'virtualbox-source' is not installed, so not removed
Package 'virtualbox-6.0' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libpython2-stdlib libpython2.7-minimal libpython2.7-stdlib libqt5opengl5 libqt5printsupport5 libqt5x11extras5 libsdl-ttf2.0-0 libsdl1.2debian python-is-python2 python2 python2-minimal python2.7
  python2.7-minimal
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  virtualbox-6.1*
0 upgraded, 0 newly installed, 1 to remove and 11 not upgraded.
1 not fully installed or removed.
After this operation, 216 MB disk space will be freed.
Do you want to continue? [Y/n] y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 192974 files and directories currently installed.)
Removing virtualbox-6.1 (6.1.18-142142~Ubuntu~eoan) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package virtualbox-6.1 (--remove):
 installed virtualbox-6.1 package pre-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
vboxdrv.sh: failed: modprobe vboxdrv failed. Please use 'dmesg' to find out why.

There were problems setting up VirtualBox.  To re-start the set-up process, run
  /sbin/vboxconfig
as root.  If your system is using EFI Secure Boot you may need to sign the
kernel modules (vboxdrv, vboxnetflt, vboxnetadp, vboxpci) before you can load
them. Please see your Linux system's documentation for more information.
Errors were encountered while processing:
 virtualbox-6.1
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Ok. How do I go about uninstalling Virtualbox now?

---

### Post by CelticWarrior on 2021-04-04
> [COLOR=#000000][FONT=&quot]If your system is using **EFI Secure Boot** you may need to sign the[/FONT][/COLOR]kernel modules (vboxdrv, vboxnetflt, vboxnetadp, vboxpci) before you can load them.[COLOR=#222222][FONT=Verdana]
Or, much easier, disable Secure Boot in UEFI and try again to install even if you you don't want it in the end. You have to fully install/re-install partially installed softwarebefore you can remove.[/FONT][/COLOR]

---

### Post by username2758 on 2021-04-04
Thank you CelticWarrior, disabling Secure Boot did it. I don't even know why I had this feature enabled in the first place!

---


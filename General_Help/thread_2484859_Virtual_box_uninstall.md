---
title: "Virtual box uninstall?"
date: 2023-03-13
forum: General Help
---

### Post by chicocanada on 2023-03-13
[SIZE=3]Hi everyone, I'm a Linux FoB (newbie).

I installed Virtualbox via this method [https://www.itzgeek.com/post/how-to-install-virtualbox-on-ubuntu-20-04/](https://www.itzgeek.com/post/how-to-install-virtualbox-on-ubuntu-20-04/)

I then got distracted (my son) and I did not at boot "[/SIZE][COLOR=#000000][FONT=&amp]**Enroll MOK**[/FONT][/COLOR][COLOR=#000000][FONT=&amp] » [/FONT][/COLOR][COLOR=#000000][FONT=&amp]**Continue**[/FONT][/COLOR][COLOR=#000000][FONT=&amp] » [/FONT][/COLOR][COLOR=#000000][FONT=&amp]**Yes**[/FONT][/COLOR][COLOR=#000000][FONT=&amp] » [/FONT][/COLOR][COLOR=#000000][FONT=&amp]**Enter Password**[/FONT][/COLOR][COLOR=#000000][FONT=&amp] » [/FONT][/COLOR][COLOR=#000000][FONT=&amp]**Reboot**[/FONT][/COLOR][COLOR=#000000][FONT=&amp].[/FONT][/COLOR][SIZE=3]

Now Virtualbox will not launch a VM.

Via Software I see Virtualbox but I cannot uninstall it to start over as it gives me this error: Unable to remove "Oracle VM Virtualbox": no packages to remove.

When I run 'dpkg --list' I see the following packages:

[/SIZE]rc  virtualbox                                 6.1.38-dfsg-3~ubuntu1.22.04.1   >
ii  virtualbox-7.0                             7.0.6-155176~Ubuntu~jammy       >
ii  virtualbox-dkms                            6.1.38-dfsg-3~ubuntu1.22.04.1
[SIZE=3]
I would like to uninstall it and remove the related files so I can start over and install it this time via Software.


Please help!


Cheers



[/SIZE]

---

### Post by deadflowr on 2023-03-13
try
```
sudo apt purge virtualbox*
```

---

### Post by chicocanada on 2023-03-13
I had tried with the wildcard (*) and it didn't work. Thanks a bunch!!!

Unfortunately I get this error:

```
$ sudo apt purge virtualbox*
[sudo] password for chicocanada: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'virtualbox-ext-pack' for glob 'virtualbox*'
Note, selecting 'virtualbox' for glob 'virtualbox*'
Note, selecting 'virtualbox-guest-x11' for glob 'virtualbox*'
Note, selecting 'virtualbox-ose' for glob 'virtualbox*'
Note, selecting 'virtualbox-ose-fuse' for glob 'virtualbox*'
Note, selecting 'virtualbox-guest-additions-iso' for glob 'virtualbox*'
Note, selecting 'virtualbox-guest-modules' for glob 'virtualbox*'
Note, selecting 'virtualbox-guest-utils' for glob 'virtualbox*'
Note, selecting 'virtualbox-guest-utils-hwe' for glob 'virtualbox*'
Note, selecting 'virtualbox-guest-x11-hwe' for glob 'virtualbox*'
Note, selecting 'virtualbox-modules' for glob 'virtualbox*'
Note, selecting 'virtualbox-qt' for glob 'virtualbox*'
Note, selecting 'virtualbox-2.0' for glob 'virtualbox*'
Note, selecting 'virtualbox-2.1' for glob 'virtualbox*'
Note, selecting 'virtualbox-2.2' for glob 'virtualbox*'
Note, selecting 'virtualbox-3.0' for glob 'virtualbox*'
Note, selecting 'virtualbox-3.1' for glob 'virtualbox*'
Note, selecting 'virtualbox-3.2' for glob 'virtualbox*'
Note, selecting 'virtualbox-4.0' for glob 'virtualbox*'
Note, selecting 'virtualbox-4.1' for glob 'virtualbox*'
Note, selecting 'virtualbox-4.2' for glob 'virtualbox*'
Note, selecting 'virtualbox-4.3' for glob 'virtualbox*'
Note, selecting 'virtualbox-5.0' for glob 'virtualbox*'
Note, selecting 'virtualbox-5.1' for glob 'virtualbox*'
Note, selecting 'virtualbox-5.2' for glob 'virtualbox*'
Note, selecting 'virtualbox-6.0' for glob 'virtualbox*'
Note, selecting 'virtualbox-6.1' for glob 'virtualbox*'
Note, selecting 'virtualbox-7.0' for glob 'virtualbox*'
Note, selecting 'virtualbox-source' for glob 'virtualbox*'
Note, selecting 'virtualbox-dkms' for glob 'virtualbox*'
Package 'virtualbox-ose' is not installed, so not removed
Package 'virtualbox-ose-fuse' is not installed, so not removed
Package 'virtualbox-5.2' is not installed, so not removed
Package 'virtualbox-5.1' is not installed, so not removed
Package 'virtualbox-5.0' is not installed, so not removed
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
Package 'virtualbox-ext-pack' is not installed, so not removed
Package 'virtualbox-guest-additions-iso' is not installed, so not removed
Package 'virtualbox-guest-utils' is not installed, so not removed
Package 'virtualbox-guest-utils-hwe' is not installed, so not removed
Package 'virtualbox-guest-x11' is not installed, so not removed
Package 'virtualbox-guest-x11-hwe' is not installed, so not removed
Package 'virtualbox-qt' is not installed, so not removed
Package 'virtualbox-source' is not installed, so not removed
Package 'virtualbox-6.0' is not installed, so not removed
Package 'virtualbox-6.1' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  dctrl-tools dkms libgsoap-2.8.117 liblzf1 libqt5opengl5 libsdl-ttf2.0-0
  libsdl1.2debian
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  virtualbox* virtualbox-7.0* virtualbox-dkms*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 225 MB disk space will be freed.
Do you want to continue? [Y/n] y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 392790 files and directories currently installed.)
Removing virtualbox-7.0 (7.0.6-155176~Ubuntu~jammy) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another p
rocess: Resource temporarily unavailable
dpkg: error processing package virtualbox-7.0 (--remove):
 installed virtualbox-7.0 package pre-removal script subprocess returned error e
xit status 1
dpkg: too many errors, stopping
vboxdrv.sh: failed: modprobe vboxdrv failed. Please use 'dmesg' to find out why.


There were problems setting up VirtualBox.  To re-start the set-up process, run
  /sbin/vboxconfig
as root.  If your system is using EFI Secure Boot you may need to sign the
kernel modules (vboxdrv, vboxnetflt, vboxnetadp, vboxpci) before you can load
them. Please see your Linux system's documentation for more information.
Errors were encountered while processing:
 virtualbox-7.0
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by deadflowr on 2023-03-13
Here's your issue
> debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable

See this for a solution: [https://askubuntu.com/questions/136881/debconf-dbdriver-config-config-dat-is-locked-by-another-process-resource-t]("https://askubuntu.com/questions/136881/debconf-dbdriver-config-config-dat-is-locked-by-another-process-resource-t")

Then rerun the purge command.

---

### Post by chicocanada on 2023-03-13
Thank you so much!

Would you say it's done and no issues?

```

chicocanada@ChicoCanada:~$ sudo kill 5358
chicocanada@ChicoCanada:~$ sudo apt purge virtualbox*
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'virtualbox-ext-pack' for glob 'virtualbox*'
Note, selecting 'virtualbox' for glob 'virtualbox*'
Note, selecting 'virtualbox-guest-x11' for glob 'virtualbox*'
Note, selecting 'virtualbox-ose' for glob 'virtualbox*'
Note, selecting 'virtualbox-ose-fuse' for glob 'virtualbox*'
Note, selecting 'virtualbox-guest-additions-iso' for glob 'virtualbox*'
Note, selecting 'virtualbox-guest-modules' for glob 'virtualbox*'
Note, selecting 'virtualbox-guest-utils' for glob 'virtualbox*'
Note, selecting 'virtualbox-guest-utils-hwe' for glob 'virtualbox*'
Note, selecting 'virtualbox-guest-x11-hwe' for glob 'virtualbox*'
Note, selecting 'virtualbox-modules' for glob 'virtualbox*'
Note, selecting 'virtualbox-qt' for glob 'virtualbox*'
Note, selecting 'virtualbox-2.0' for glob 'virtualbox*'
Note, selecting 'virtualbox-2.1' for glob 'virtualbox*'
Note, selecting 'virtualbox-2.2' for glob 'virtualbox*'
Note, selecting 'virtualbox-3.0' for glob 'virtualbox*'
Note, selecting 'virtualbox-3.1' for glob 'virtualbox*'
Note, selecting 'virtualbox-3.2' for glob 'virtualbox*'
Note, selecting 'virtualbox-4.0' for glob 'virtualbox*'
Note, selecting 'virtualbox-4.1' for glob 'virtualbox*'
Note, selecting 'virtualbox-4.2' for glob 'virtualbox*'
Note, selecting 'virtualbox-4.3' for glob 'virtualbox*'
Note, selecting 'virtualbox-5.0' for glob 'virtualbox*'
Note, selecting 'virtualbox-5.1' for glob 'virtualbox*'
Note, selecting 'virtualbox-5.2' for glob 'virtualbox*'
Note, selecting 'virtualbox-6.0' for glob 'virtualbox*'
Note, selecting 'virtualbox-6.1' for glob 'virtualbox*'
Note, selecting 'virtualbox-7.0' for glob 'virtualbox*'
Note, selecting 'virtualbox-source' for glob 'virtualbox*'
Note, selecting 'virtualbox-dkms' for glob 'virtualbox*'
Package 'virtualbox-ose' is not installed, so not removed
Package 'virtualbox-ose-fuse' is not installed, so not removed
Package 'virtualbox-5.2' is not installed, so not removed
Package 'virtualbox-5.1' is not installed, so not removed
Package 'virtualbox-5.0' is not installed, so not removed
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
Package 'virtualbox-ext-pack' is not installed, so not removed
Package 'virtualbox-guest-additions-iso' is not installed, so not removed
Package 'virtualbox-guest-utils' is not installed, so not removed
Package 'virtualbox-guest-utils-hwe' is not installed, so not removed
Package 'virtualbox-guest-x11' is not installed, so not removed
Package 'virtualbox-guest-x11-hwe' is not installed, so not removed
Package 'virtualbox-qt' is not installed, so not removed
Package 'virtualbox-source' is not installed, so not removed
Package 'virtualbox-6.0' is not installed, so not removed
Package 'virtualbox-6.1' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  dctrl-tools dkms libgsoap-2.8.117 liblzf1 libqt5opengl5 libsdl-ttf2.0-0
  libsdl1.2debian
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  virtualbox* virtualbox-7.0* virtualbox-dkms*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 225 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 392790 files and directories currently installed.)
Removing virtualbox-7.0 (7.0.6-155176~Ubuntu~jammy) ...
Removing virtualbox-dkms (6.1.38-dfsg-3~ubuntu1.22.04.1) ...
Module virtualbox-6.1.38 for kernel 5.19.0-35-generic (x86_64).
Before uninstall, this module version was ACTIVE on this kernel.


vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/5.19.0-35-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/5.19.0-35-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/5.19.0-35-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod...
Deleting module virtualbox-6.1.38 completely from the DKMS tree.
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for shared-mime-info (2.1-2) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
(Reading database ... 391779 files and directories currently installed.)
Purging configuration files for virtualbox-7.0 (7.0.6-155176~Ubuntu~jammy) ...
dpkg: warning: while removing virtualbox-7.0, directory '/usr/local' not empty s
o not removed
Purging configuration files for virtualbox (6.1.38-dfsg-3~ubuntu1.22.04.1) ...



```

---

### Post by chicocanada on 2023-03-13
I installed Virtualbox from Software and it's working great so far :)

---


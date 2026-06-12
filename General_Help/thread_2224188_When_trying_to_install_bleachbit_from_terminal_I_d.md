---
title: "When trying to install bleachbit from terminal I do get a dpkg error"
date: 2014-05-15
forum: General Help
---

### Post by nina3 on 2014-05-15
Hello, everyone :KS

Well, today I been trying to install the bleachbit but everytime I do so do get an odd error.

How everything began?
I was looking methods and programs to clean my laptop/system, so I did found a code that allowed me to clean it since terminal

```
sudo apt-get autoclean
```

Then, if my memory doesn't fail there was the first message from dpkg error and being interrupted suggesting me to run a code to fix it
```
sudo dpkg --configure -a

```

So did run it everything worked fine...and closed the terminal (my mistake), open another terminal and run the update and upgrade, apparently everything was fine but after flash plugin installation found this message
```

[SIZE=1]flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.359.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.359.orig.tar.gz)
[/SIZE][SIZE=1]Installing from local file /tmp/tmpFfDi9p.gz[/SIZE]
[SIZE=1]Flash Plugin installed.[/SIZE]
[SIZE=1]Processing triggers for install-info (5.2.0.dfsg.1-2) ...[/SIZE]
[B][SIZE=1]dpkg: error processing package iputils-ping (--configure):[/SIZE]
[SIZE=1] package is in a very bad inconsistent state; you should[/SIZE]
[SIZE=1] reinstall it before attempting configuration[/SIZE][/B][SIZE=1]
[/SIZE]
```
But it did continue upgrading...as you can see below

[SIZE=1]```
Setting up libudev1:i386 (204-5ubuntu20.2) ...
```[/SIZE]```

[SIZE=1]Setting up udev (204-5ubuntu20.2) ...[/SIZE]
[SIZE=1]udev stop/waiting[/SIZE]
[SIZE=1]udev start/running, process 15604[/SIZE]
[SIZE=1]Removing 'diversion of /bin/udevadm to /bin/udevadm.upgrade by fake-udev'[/SIZE]
[SIZE=1]update-initramfs: deferring update (trigger activated)[/SIZE]
[SIZE=1]Setting up libsystemd-daemon0:i386 (204-5ubuntu20.2) ...[/SIZE]
[SIZE=1]Setting up systemd-services (204-5ubuntu20.2) ...[/SIZE]
[SIZE=1]Installing new version of config file /etc/systemd/logind.conf ...[/SIZE]
[SIZE=1]Setting up libpam-systemd:i386 (204-5ubuntu20.2) ...[/SIZE]
[SIZE=1]systemd-logind start/running, process 15686[/SIZE]
[SIZE=1]Setting up libsystemd-login0:i386 (204-5ubuntu20.2) ...[/SIZE]
[SIZE=1]Setting up libfreetype6:i386 (2.5.2-1ubuntu2.1) ...[/SIZE]
[SIZE=1]Setting up google-chrome-stable (34.0.1847.137-1) ...[/SIZE]
[SIZE=1]Setting up libgudev-1.0-0:i386 (1:204-5ubuntu20.2) ...[/SIZE]
[SIZE=1]Setting up libwbclient0:i386 (2:4.1.6+dfsg-1ubuntu2.14.04.1) ...[/SIZE]
[SIZE=1]Setting up libxfont1:i386 (1:1.4.7-1ubuntu0.1) ...[/SIZE]
[SIZE=1]Setting up lightdm (1.10.1-0ubuntu1) ...[/SIZE]
[SIZE=1]Setting up samba-libs:i386 (2:4.1.6+dfsg-1ubuntu2.14.04.1) ...[/SIZE]
[SIZE=1]Setting up python-samba (2:4.1.6+dfsg-1ubuntu2.14.04.1) ...[/SIZE]
[SIZE=1]Setting up samba-common (2:4.1.6+dfsg-1ubuntu2.14.04.1) ...[/SIZE]
[SIZE=1]Setting up samba-common-bin (2:4.1.6+dfsg-1ubuntu2.14.04.1) ...[/SIZE]
[SIZE=1]Setting up libsmbclient:i386 (2:4.1.6+dfsg-1ubuntu2.14.04.1) ...[/SIZE]
[SIZE=1]Setting up smbclient (2:4.1.6+dfsg-1ubuntu2.14.04.1) ...[/SIZE]
[SIZE=1]Setting up libsystemd-journal0:i386 (204-5ubuntu20.2) ...[/SIZE]
[SIZE=1]Setting up initramfs-tools-bin (0.103ubuntu4.1) ...[/SIZE]
[SIZE=1]Setting up initramfs-tools (0.103ubuntu4.1) ...[/SIZE]
[SIZE=1]update-initramfs: deferring update (trigger activated)[/SIZE]
[SIZE=1]Setting up gettext-base (0.18.3.1-1ubuntu3) ...[/SIZE]
[SIZE=1]Setting up libgirepository-1.0-1 (1.40.0-1ubuntu0.1) ...[/SIZE]
[SIZE=1]Setting up gir1.2-glib-2.0 (1.40.0-1ubuntu0.1) ...[/SIZE]
[SIZE=1]Setting up gir1.2-freedesktop (1.40.0-1ubuntu0.1) ...[/SIZE]
[SIZE=1]Setting up iputils-tracepath (3:20121221-4ubuntu1.1) ...[/SIZE]
[SIZE=1]Setting up openssl (1.0.1f-1ubuntu2.1) ...[/SIZE]
[SIZE=1]Setting up python3-update-manager (1:0.196.12) ...[/SIZE]
[SIZE=1]Setting up update-manager-core (1:0.196.12) ...[/SIZE]
[SIZE=1]Setting up update-manager (1:0.196.12) ...[/SIZE]
[SIZE=1]Setting up libnautilus-extension1a (1:3.10.1-0ubuntu9) ...[/SIZE]
[SIZE=1]Setting up nautilus-data (1:3.10.1-0ubuntu9) ...[/SIZE]
[SIZE=1]Setting up nautilus (1:3.10.1-0ubuntu9) ...[/SIZE]
[SIZE=1]Setting up empathy-common (3.8.6-0ubuntu9.1) ...[/SIZE]
[SIZE=1]Setting up empathy (3.8.6-0ubuntu9.1) ...[/SIZE]
[SIZE=1]Setting up nautilus-sendto-empathy (3.8.6-0ubuntu9.1) ...[/SIZE]
[SIZE=1]Setting up mcp-account-manager-uoa (3.8.6-0ubuntu9.1) ...[/SIZE]
[SIZE=1]Setting up account-plugin-yahoo (3.8.6-0ubuntu9.1) ...[/SIZE]
[SIZE=1]Setting up account-plugin-salut (3.8.6-0ubuntu9.1) ...[/SIZE]
[SIZE=1]Setting up account-plugin-jabber (3.8.6-0ubuntu9.1) ...[/SIZE]
[SIZE=1]Setting up account-plugin-aim (3.8.6-0ubuntu9.1) ...[/SIZE]
[SIZE=1]Setting up python3-problem-report (2.14.1-0ubuntu3.1) ...[/SIZE]
[SIZE=1]Setting up python3-apport (2.14.1-0ubuntu3.1) ...[/SIZE]
[SIZE=1]Setting up apport (2.14.1-0ubuntu3.1) ...[/SIZE]
[SIZE=1]apport start/running[/SIZE]
[SIZE=1]Setting up apport-gtk (2.14.1-0ubuntu3.1) ...[/SIZE]
[SIZE=1]Setting up compiz-core (1:0.9.11+14.04.20140423-0ubuntu1) ...[/SIZE]
[SIZE=1]Setting up libcompizconfig0 (1:0.9.11+14.04.20140423-0ubuntu1) ...[/SIZE]
[SIZE=1]Setting up libdecoration0 (1:0.9.11+14.04.20140423-0ubuntu1) ...[/SIZE]
[SIZE=1]Setting up compiz-plugins-default (1:0.9.11+14.04.20140423-0ubuntu1) ...[/SIZE]
[SIZE=1]Setting up compiz-gnome (1:0.9.11+14.04.20140423-0ubuntu1) ...[/SIZE]
[SIZE=1]Setting up compiz (1:0.9.11+14.04.20140423-0ubuntu1) ...[/SIZE]
[SIZE=1]Setting up cups-browsed (1.0.52-0ubuntu1.1) ...[/SIZE]
[SIZE=1]cups-browsed start/running, process 16308[/SIZE]
[SIZE=1]Setting up cups-filters-core-drivers (1.0.52-0ubuntu1.1) ...[/SIZE]
[SIZE=1]Setting up libgs9-common (9.10~dfsg-0ubuntu10.1) ...[/SIZE]
[SIZE=1]Setting up libgs9 (9.10~dfsg-0ubuntu10.1) ...[/SIZE]
[SIZE=1]Setting up ghostscript (9.10~dfsg-0ubuntu10.1) ...[/SIZE]
[SIZE=1]Setting up ghostscript-x (9.10~dfsg-0ubuntu10.1) ...[/SIZE]
[SIZE=1]Setting up cups-filters (1.0.52-0ubuntu1.1) ...[/SIZE]
[SIZE=1]
[/SIZE]
[SIZE=1]Setting up flashplugin-installer (11.2.202.359ubuntu0.14.04.1) ...[/SIZE]
[SIZE=1]Setting up gettext (0.18.3.1-1ubuntu3) ...[/SIZE]
[SIZE=1]Setting up gir1.2-gudev-1.0 (1:204-5ubuntu20.2) ...[/SIZE]
[SIZE=1]Setting up librhythmbox-core8 (3.0.2-0ubuntu2) ...[/SIZE]
[SIZE=1]Setting up rhythmbox-data (3.0.2-0ubuntu2) ...[/SIZE]
[SIZE=1]Setting up gir1.2-rb-3.0 (3.0.2-0ubuntu2) ...[/SIZE]
[SIZE=1]Setting up rhythmbox (3.0.2-0ubuntu2) ...[/SIZE]
[SIZE=1]Setting up rhythmbox-plugin-zeitgeist (3.0.2-0ubuntu2) ...[/SIZE]
[SIZE=1]Setting up rhythmbox-plugin-magnatune (3.0.2-0ubuntu2) ...[/SIZE]
[SIZE=1]Setting up rhythmbox-plugins (3.0.2-0ubuntu2) ...[/SIZE]
[SIZE=1]Setting up rhythmbox-plugin-cdrecorder (3.0.2-0ubuntu2) ...[/SIZE]
[SIZE=1]Setting up rhythmbox-mozilla (3.0.2-0ubuntu2) ...[/SIZE]
[SIZE=1]Setting up iputils-arping (3:20121221-4ubuntu1.1) ...[/SIZE]
[SIZE=1]Setting up liblightdm-gobject-1-0 (1.10.1-0ubuntu1) ...[/SIZE]
[SIZE=1]Setting up linux-firmware (1.127.2) ...[/SIZE]
[SIZE=1]Setting up linux-headers-3.13.0-24 (3.13.0-24.47) ...[/SIZE]
[SIZE=1]Setting up linux-headers-3.13.0-24-generic (3.13.0-24.47) ...[/SIZE]
[SIZE=1]Setting up linux-image-extra-3.13.0-24-generic (3.13.0-24.47) ...[/SIZE]
[SIZE=1]**Running depmod.**
**update-initramfs: deferring update (hook will be called later)**
**Not updating initrd symbolic links since we are being updated/reinstalled **
**(3.13.0-24.46 was configured last, according to dpkg) **
**Not updating image symbolic links since we are being updated/reinstalled       **
**(3.13.0-24.46 was configured last, according to dpkg)  **[/SIZE]

[SIZE=1]Examining /etc/kernel/postinst.d.[/SIZE]
[SIZE=1]run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic[/SIZE]
[SIZE=1]run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic[/SIZE]
[SIZE=1]update-initramfs: Generating /boot/initrd.img-3.13.0-24-generic[/SIZE]
[SIZE=1]run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic[/SIZE]
[SIZE=1]run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic[/SIZE]
[SIZE=1]run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic[/SIZE]
[B][SIZE=1]Generating grub configuration file ...[/SIZE]
[SIZE=1]Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.[/SIZE]
[/B][SIZE=1]Found linux image: /boot/vmlinuz-3.13.0-24-generic[/SIZE]
[SIZE=1]Found initrd image: /boot/initrd.img-3.13.0-24-generic[/SIZE]
[SIZE=1]Found linux image: /boot/vmlinuz-3.11.0-19-generic[/SIZE]
[SIZE=1]Found initrd image: /boot/initrd.img-3.11.0-19-generic[/SIZE]
[SIZE=1]Found memtest86+ image: /boot/memtest86+.elf[/SIZE]
[SIZE=1]Found memtest86+ image: /boot/memtest86+.bin[/SIZE]
[SIZE=1]done[/SIZE]
[SIZE=1]Setting up linux-libc-dev:i386 (3.13.0-24.47) ...[/SIZE]
[SIZE=1]Setting up patch (2.7.1-4ubuntu1) ...[/SIZE]
[SIZE=1]Setting up python-problem-report (2.14.1-0ubuntu3.1) ...[/SIZE]
[SIZE=1]Setting up python-apport (2.14.1-0ubuntu3.1) ...[/SIZE]
[SIZE=1]Setting up python-cupshelpers (1.4.3+20140219-0ubuntu2.1) ...[/SIZE]
[SIZE=1]Setting up python3-software-properties (0.92.37) ...[/SIZE]
[SIZE=1]Setting up software-properties-common (0.92.37) ...[/SIZE]
[SIZE=1]Setting up software-properties-gtk (0.92.37) ...[/SIZE]
[SIZE=1]Setting up qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets (0.23+14.04.20140422-0ubuntu1) ...[/SIZE]
[SIZE=1]Setting up qtdeclarative5-ubuntu-ui-extras-browser-plugin:i386 (0.23+14.04.20140422-0ubuntu1) ...[/SIZE]
[SIZE=1]Setting up webbrowser-app (0.23+14.04.20140422-0ubuntu1) ...[/SIZE]
[SIZE=1]Setting up webapp-container (0.23+14.04.20140422-0ubuntu1) ...[/SIZE]
[SIZE=1]Setting up simple-scan (3.12.1-0ubuntu1) ...[/SIZE]
[SIZE=1]Setting up system-config-printer-common (1.4.3+20140219-0ubuntu2.1) ...[/SIZE]
[SIZE=1]Setting up system-config-printer-gnome (1.4.3+20140219-0ubuntu2.1) ...[/SIZE]
[SIZE=1]Setting up system-config-printer-udev (1.4.3+20140219-0ubuntu2.1) ...[/SIZE]
[SIZE=1]Setting up unity-greeter (14.04.10-0ubuntu1) ...[/SIZE]
[SIZE=1]Setting up xserver-xorg-video-radeon (1:7.3.0-1ubuntu3.1) ...[/SIZE]
[SIZE=1]Setting up xserver-xorg-video-ati (1:7.3.0-1ubuntu3.1) ...[/SIZE]
[SIZE=1]Processing triggers for libc-bin (2.19-0ubuntu6) ...[/SIZE]
[SIZE=1]Processing triggers for menu (2.1.46ubuntu1) ...[/SIZE]
[SIZE=1]Processing triggers for initramfs-tools (0.103ubuntu4.1) ...[/SIZE]
[SIZE=1]update-initramfs: Generating /boot/initrd.img-3.13.0-24-generic[/SIZE]
[B][SIZE=1]Errors were encountered while processing:[/SIZE]
[SIZE=1] iputils-ping[/SIZE]
[SIZE=1]E: Sub-process /usr/bin/dpkg returned an error code (1) [/SIZE][/B]
```
But still did continue with the bleachbit...

[SIZE=1]```
nina@nina-HP-Mini:~$ sudo apt-get install bleachbit
[sudo] password for nina: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bleachbit is already the newest version.
The following package was automatically installed and is no longer required:
  libpostproc52
Use 'apt-get autoremove' to remove it.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/50,6 kB of archives.
After this operation, 0 B of additional disk space will be used.

```[/SIZE]```
[SIZE=1]Do you want to continue? [Y/n] y[/SIZE]
[B][SIZE=1]dpkg: error processing package iputils-ping (--configure):[/SIZE]
[SIZE=1] package is in a very bad inconsistent state; you should[/SIZE]
[SIZE=1] reinstall it before attempting configuration[/SIZE]
[SIZE=1]Errors were encountered while processing:[/SIZE]
[SIZE=1] iputils-ping[/SIZE]
[SIZE=1]E: Sub-process /usr/bin/dpkg returned an error code (1)[/SIZE]
[/B][SIZE=1]
[/SIZE]nina@nina-HP-Mini:~$ 
```

Oh! yes later did run the suggested code 
```
apt-get autoremove
```

And got this message
[SIZE=1]```
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
```[/SIZE]```

[SIZE=1]E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?[/SIZE]
```



So what would be your kindly advice on fixing the dpkg?
In advance thank you for your support

---

### Post by T.J. on 2014-05-15
Hi Nina3!

This error was caused by forcibly interrupting the package manager (starting the package manager in a terminal, then forcing it closed) while it was updating files, which left the package broken.  It leaves a bit of a mess.  If you are concerned that the iputils-ping package is not properly installed you can request its re-installation.

First try:

*sudo apt-get -f install *(tells the package manager to check the package database)
*sudo apt-get install --reinstall iputils-ping*  (tells it to try to reinstall the package) 


If that does not fix the problem to your satisfaction, you can forcibly override the package system's safety routines, and force the package manager to replace the files without checks, but I'd advise against it, unless you still have trouble.  It can be done safely, but it should not be done without a good reason.  

Please let me know.

---

### Post by oldos2er on 2014-05-15
Moved to General Help.

Since the system suggested you "should reinstall it before attempting configuration," try that if you haven't already. ```
sudo apt-get install --reinstall iputils-ping
``` 

*apt-get autoremove* needs to be preceded by *sudo*

---

### Post by nina3 on 2014-05-21
> **T.J. said:**
> Hi Nina3!

This error was caused by forcibly interrupting the package manager (starting the package manager in a terminal, then forcing it closed) while it was updating files, which left the package broken.  It leaves a bit of a mess.  If you are concerned that the iputils-ping package is not properly installed you can request its re-installation.

First try:

*sudo apt-get -f install *(tells the package manager to check the package database)
*sudo apt-get install --reinstall iputils-ping*  (tells it to try to reinstall the package) 


If that does not fix the problem to your satisfaction, you can forcibly override the package system's safety routines, and force the package manager to replace the files without checks, but I'd advise against it, unless you still have trouble.  It can be done safely, but it should not be done without a good reason.  

Please let me know.

Everything got fixed. Thank you so much Mr. T.J. :D

---

### Post by nina3 on 2014-05-21
> **oldos2er said:**
> Moved to General Help.

Since the system suggested you "should reinstall it before attempting configuration," try that if you haven't already. ```
sudo apt-get install --reinstall iputils-ping
``` 

*apt-get autoremove* needs to be preceded by *sudo*

Thank you for moving my thread Miss Oldos2er. <3
*changing to solved*

---


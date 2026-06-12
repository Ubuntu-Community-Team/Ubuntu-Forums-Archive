---
title: "installing Ubuntu Sever on thinkpad400(labtop)"
date: 2017-04-16
forum: General Help
---

### Post by davisghxie on 2017-04-16
Hello everyone,

Would like to learn more about Ubuntu Server, but have been failing while installing. Any help is appreciated!


[LIST=1]
[*] it is a good idea to install Ubuntu server on a old laptop like thinkpad 400 for learning purpose?
[*]if so, can anyone please help figure out why I keep failing while installing ? I have attached the syslog.
[*]Thank you so much in advance.
[/LIST]



```
Apr 16 17:10:18 in-target:   Hash Sum mismatch
Apr 16 17:10:18 in-target: Get:9 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial/main amd64 linux-image-generic-hwe-16.04 amd64 4.8.0.36.8 [2,472 B]
Apr 16 17:10:18 in-target: Get:10 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial/main amd64 linux-headers-4.8.0-36 all 4.8.0-36.36~16.04.1 [10.3 MB]
Apr 16 17:10:19 in-target: Get:11 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial/main amd64 linux-headers-4.8.0-36-generic amd64 4.8.0-36.36~16.04.1 [823 kB]
Apr 16 17:10:19 in-target: Get:12 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial/main amd64 linux-headers-generic-hwe-16.04 amd64 4.8.0.36.8 [2,448 B]
Apr 16 17:10:19 in-target: Get:13 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial/main amd64 linux-generic-hwe-16.04 amd64 4.8.0.36.8 [1,802 B]
Apr 16 17:10:19 in-target: E: Failed to fetch cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8)/pool/main/l/linux-hwe/linux-image-4.8.0-36-generic_4.8.0-36.36~16.04.1_amd64.deb  Hash Sum mismatch
Apr 16 17:10:19 in-target: 
Apr 16 17:10:19 in-target: E: Failed to fetch cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8)/pool/main/l/linux-hwe/linux-image-extra-4.8.0-36-generic_4.8.0-36.36~16.04.1_amd64.deb  Hash Sum mismatch
Apr 16 17:10:19 in-target: 
Apr 16 17:10:19 in-target: E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
Apr 16 17:10:20 in-target: Reading package lists...
Apr 16 17:10:20 in-target: 
Apr 16 17:10:20 in-target: Building dependency tree...
Apr 16 17:10:20 in-target: 
Apr 16 17:10:20 in-target: Reading state information...
Apr 16 17:10:20 in-target: The following additional packages will be installed:
Apr 16 17:10:20 in-target:   linux-headers-4.8.0-36 linux-headers-4.8.0-36-generic
Apr 16 17:10:20 in-target: The following NEW packages will be installed:
Apr 16 17:10:20 in-target:   linux-headers-4.8.0-36 linux-headers-4.8.0-36-generic
Apr 16 17:10:20 in-target:   linux-headers-generic-hwe-16.04
Apr 16 17:10:20 in-target: 0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Apr 16 17:10:20 in-target: Need to get 0 B/11.1 MB of archives.
Apr 16 17:10:20 in-target: After this operation, 80.7 MB of additional disk space will be used.
Apr 16 17:10:20 in-target: Get:1 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial/main amd64 linux-headers-4.8.0-36 all 4.8.0-36.36~16.04.1 [10.3 MB]
Apr 16 17:10:20 in-target: Get:2 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial/main amd64 linux-headers-4.8.0-36-generic amd64 4.8.0-36.36~16.04.1 [823 kB]
Apr 16 17:10:20 in-target: Get:3 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial/main amd64 linux-headers-generic-hwe-16.04 amd64 4.8.0.36.8 [2,448 B]
Apr 16 17:10:21 in-target: Selecting previously unselected package linux-headers-4.8.0-36.^M
Apr 16 17:10:21 in-target: (Reading database ... ^M
Apr 16 17:10:21 in-target: (Reading database ... 5%^M
Apr 16 17:10:21 in-target: (Reading database ... 10%^M
Apr 16 17:10:21 in-target: (Reading database ... 15%^M
Apr 16 17:10:21 in-target: (Reading database ... 20%^M
Apr 16 17:10:21 in-target: (Reading database ... 25%^M
Apr 16 17:10:21 in-target: (Reading database ... 30%^M
Apr 16 17:10:21 in-target: (Reading database ... 35%^M
Apr 16 17:10:21 in-target: (Reading database ... 40%^M
Apr 16 17:10:21 in-target: (Reading database ... 45%^M
Apr 16 17:10:21 in-target: (Reading database ... 50%^M
Apr 16 17:10:21 in-target: (Reading database ... 55%^M
Apr 16 17:10:21 in-target: (Reading database ... 60%^M
Apr 16 17:10:21 in-target: (Reading database ... 65%^M
Apr 16 17:10:21 in-target: (Reading database ... 70%^M
Apr 16 17:10:21 in-target: (Reading database ... 75%^M
Apr 16 17:10:21 in-target: (Reading database ... 80%^M
Apr 16 17:10:21 in-target: (Reading database ... 85%^M
Apr 16 17:10:21 in-target: (Reading database ... 90%^M
Apr 16 17:10:21 in-target: (Reading database ... 95%^M
Apr 16 17:10:21 in-target: (Reading database ... 100%^M(Reading database ... 
Apr 16 17:10:21 in-target: 10458 files and directories currently installed.)^M
Apr 16 17:10:21 in-target: Preparing to unpack .../linux-headers-4.8.0-36_4.8.0-36.36~16.04.1_all.deb ...^M
Apr 16 17:10:21 in-target: Unpacking linux-headers-4.8.0-36 (4.8.0-36.36~16.04.1) ...^M
Apr 16 17:10:31 in-target: Selecting previously unselected package linux-headers-4.8.0-36-generic.^M
Apr 16 17:10:31 in-target: Preparing to unpack .../linux-headers-4.8.0-36-generic_4.8.0-36.36~16.04.1_amd64.deb ...^M
Apr 16 17:10:31 in-target: Unpacking linux-headers-4.8.0-36-generic (4.8.0-36.36~16.04.1) ...^M
Apr 16 17:10:33 in-target: Selecting previously unselected package linux-headers-generic-hwe-16.04.^M
Apr 16 17:10:33 in-target: Preparing to unpack .../linux-headers-generic-hwe-16.04_4.8.0.36.8_amd64.deb ...^M
Apr 16 17:10:33 in-target: Unpacking linux-headers-generic-hwe-16.04 (4.8.0.36.8) ...^M
Apr 16 17:10:34 in-target: Setting up linux-headers-4.8.0-36 (4.8.0-36.36~16.04.1) ...^M
Apr 16 17:10:34 in-target: Setting up linux-headers-4.8.0-36-generic (4.8.0-36.36~16.04.1) ...^M
Apr 16 17:10:34 in-target: Setting up linux-headers-generic-hwe-16.04 (4.8.0.36.8) ...^M
Apr 16 17:10:35 base-installer: error: exiting on error base-installer/kernel/failed-install
Apr 16 17:12:28 main-menu[1109]: (process:21671): 0
Apr 16 17:12:28 main-menu[1109]: (process:21671): 0
Apr 16 17:12:28 main-menu[1109]: (process:21671): 0
Apr 16 17:12:28 main-menu[1109]: (process:21671): 0
Apr 16 17:12:28 main-menu[1109]: (process:21671): 0
Apr 16 17:12:28 main-menu[1109]: (process:21671): 0
Apr 16 17:12:28 main-menu[1109]: (process:21671): 0
Apr 16 17:12:28 main-menu[1109]: (process:21671): 0
Apr 16 17:12:28 main-menu[1109]: (process:21671): 0
Apr 16 17:12:28 main-menu[1109]: (process:21671): 0
Apr 16 17:12:28 main-menu[1109]: (process:21671): 0
Apr 16 17:12:28 main-menu[1109]: (process:21671): 0
Apr 16 17:12:28 main-menu[1109]: (process:21671): 0
Apr 16 17:12:28 main-menu[1109]: (process:21671): 0
Apr 16 17:12:28 main-menu[1109]: (process:21671): 0
Apr 16 17:12:28 main-menu[1109]: (process:21671): 0
Apr 16 17:12:28 main-menu[1109]: (process:21671): 0
Apr 16 17:12:28 main-menu[1109]: (process:21671): 0
Apr 16 17:12:28 main-menu[1109]: (process:21671): unknown udeb squashfs-modules
Apr 16 17:12:28 main-menu[1109]: WARNING **: Configuring 'live-installer' failed with error code 1
Apr 16 17:12:28 main-menu[1109]: WARNING **: Menu item 'live-installer' failed.
Apr 16 17:12:30 main-menu[1109]: INFO: Modifying debconf priority limit from 'high' to 'medium'
Apr 16 17:12:30 debconf: Setting debconf/priority to medium
Apr 16 17:12:31 main-menu[1109]: INFO: Falling back to the package description for brltty-udeb
Apr 16 17:12:32 main-menu[1109]: INFO: Falling back to the package description for brltty-udeb
Apr 16 17:12:32 main-menu[1109]: INFO: Menu item 'live-installer' selected
Apr 16 17:12:32 base-installer: warning: attempting to install to unclean target
Apr 16 17:12:33 base-installer: info: Using squashfs support for /cdrom/install/filesystem.squashfs
Apr 16 17:12:33 anna-install: Installing squashfs-modules
Apr 16 17:12:39 live-installer: WARNING: no live-config script matching /target/lib/live/config/*-ssl-cert !
Apr 16 17:12:39 base-installer: Using CD-ROM mount point /media/cdrom/
Apr 16 17:12:39 base-installer: Identifying... [baf52e5369ed154366c2a297e784a7e4-2]
Apr 16 17:12:39 base-installer: Scanning disc for index files...
Apr 16 17:12:39 base-installer: Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
Apr 16 17:12:39 base-installer: This disc is called: 
Apr 16 17:12:39 base-installer: 'Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8)'
Apr 16 17:12:39 base-installer: Copying package lists...
Apr 16 17:12:39 base-installer: gpgv: Signature made Wed Feb 15 20:36:12 2017 UTC using RSA key ID EFE21092
Apr 16 17:12:39 base-installer: gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>"
Apr 16 17:12:39 base-installer: ^MReading Package Indexes... 0%^M
Apr 16 17:12:39 base-installer: ^MReading Package Indexes... Done^M
Apr 16 17:12:39 base-installer: Writing new source list
Apr 16 17:12:39 base-installer: Source list entries for this disc are:
Apr 16 17:12:39 base-installer: deb cdrom:[Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8)]/ xenial main restricted
Apr 16 17:12:39 base-installer: Repeat this process for the rest of the CDs in your set.
Apr 16 17:12:39 base-installer: Ign:1 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial InRelease
Apr 16 17:12:39 base-installer: Hit:2 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial Release
Apr 16 17:12:39 base-installer: Reading package lists...
Apr 16 17:12:39 base-installer: 
Apr 16 17:12:40 in-target: Reading package lists...
Apr 16 17:12:40 in-target: 
Apr 16 17:12:40 in-target: Building dependency tree...
Apr 16 17:12:40 in-target: 
Apr 16 17:12:40 in-target: Reading state information...
Apr 16 17:12:40 in-target: locales is already the newest version (2.23-0ubuntu5).
Apr 16 17:12:40 in-target: 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Apr 16 17:12:40 localechooser: Generating locales (this might take a while)...
Apr 16 17:12:40 localechooser:   en_US.UTF-8
Apr 16 17:12:40 localechooser: ...
Apr 16 17:12:41 localechooser:  done
Apr 16 17:12:41 localechooser: Generation complete.
Apr 16 17:12:41 localechooser: Generating locales (this might take a while)...
Apr 16 17:12:41 localechooser:   en_US.UTF-8
Apr 16 17:12:41 localechooser: ...
Apr 16 17:12:42 localechooser:  done
Apr 16 17:12:42 localechooser: Generation complete.
Apr 16 17:12:45 live-installer: update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Apr 16 17:12:45 live-installer: update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Apr 16 17:12:45 live-installer: update-initramfs: deferring update (trigger activated)
Apr 16 17:12:46 live-installer: Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
Apr 16 17:12:47 live-installer: update-initramfs: deferring update (trigger activated)
Apr 16 17:12:47 live-installer: Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
Apr 16 17:12:48 base-installer: info: kernel linux-signed-generic usable on amd64
Apr 16 17:12:48 base-installer: info: kernel linux-generic-hwe-16.04 usable on amd64
Apr 16 17:12:48 base-installer: info: kernel linux-generic usable on amd64
Apr 16 17:12:48 base-installer: info: kernel linux-virtual usable on amd64
Apr 16 17:12:48 base-installer: info: kernel linux-signed-image-generic usable on amd64
Apr 16 17:12:48 base-installer: info: kernel linux-image-extra-4.8.0-36-generic usable on amd64
Apr 16 17:12:48 base-installer: info: kernel linux-image-extra-4.4.0-62-generic usable on amd64
Apr 16 17:12:48 base-installer: info: kernel linux-image-generic-hwe-16.04 usable on amd64
Apr 16 17:12:48 base-installer: info: kernel linux-image-generic usable on amd64
Apr 16 17:12:48 base-installer: info: kernel linux-image-virtual usable on amd64
Apr 16 17:12:48 base-installer: info: kernel linux-signed-image-4.4.0-62-generic usable on amd64
Apr 16 17:12:48 base-installer: info: kernel linux-image-4.8.0-36-generic usable on amd64
Apr 16 17:12:48 base-installer: info: kernel linux-image-4.4.0-62-generic usable on amd64
Apr 16 17:12:48 base-installer: info: Found kernels 'linux-signed-generic,linux-generic-hwe-16.04,linux-generic,linux-virtual,linux-signed-image-generic,linux-image-extra-4.8.0-36-generic,linux-image-extra-4.4.0-62-generic,linux-image-generic-hwe-16.04,linux-image-generic,linux-image-virtual,linux-signed-image-4.4.0-62-generic,linux-image-4.8.0-36-generic,linux-image-4.4.0-62-generic'
Apr 16 17:12:48 base-installer: info: preseeded/current kernel: linux-generic-hwe-16.04
Apr 16 17:12:54 base-installer: info: Using kernel 'linux-generic'
Apr 16 17:12:54 base-installer: warning: Failed to get debconf answer 'base-installer/kernel/linux/initrd'.
Apr 16 17:12:54 base-installer: info: Setting do_initrd='yes'.
Apr 16 17:12:54 base-installer: info: Setting link_in_boot='no'.
Apr 16 17:12:55 in-target: Reading package lists...
Apr 16 17:12:55 in-target: 
Apr 16 17:12:55 in-target: Building dependency tree...
Apr 16 17:12:55 in-target: 
Apr 16 17:12:55 in-target: Reading state information...
Apr 16 17:12:55 in-target: busybox-initramfs is already the newest version (1:1.22.0-15ubuntu1).
Apr 16 17:12:55 in-target: 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Apr 16 17:12:55 in-target: Reading package lists...
Apr 16 17:12:55 in-target: 
Apr 16 17:12:55 in-target: Building dependency tree...
Apr 16 17:12:55 in-target: 
Apr 16 17:12:55 in-target: Reading state information...
Apr 16 17:12:55 in-target: initramfs-tools is already the newest version (0.122ubuntu8.8).
Apr 16 17:12:55 in-target: 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Apr 16 17:13:00 in-target: Reading package lists...
Apr 16 17:13:00 in-target: 
Apr 16 17:13:00 in-target: Building dependency tree...
Apr 16 17:13:00 in-target: 
Apr 16 17:13:00 in-target: Reading state information...
Apr 16 17:13:00 in-target: The following additional packages will be installed:
Apr 16 17:13:00 in-target:   crda iw libnl-3-200 libnl-genl-3-200 linux-firmware linux-headers-4.4.0-62
Apr 16 17:13:00 in-target:   linux-headers-4.4.0-62-generic linux-headers-generic
Apr 16 17:13:00 in-target:   linux-image-4.4.0-62-generic linux-image-extra-4.4.0-62-generic
Apr 16 17:13:00 in-target:   linux-image-generic wireless-regdb
Apr 16 17:13:00 in-target: Suggested packages:
Apr 16 17:13:00 in-target:   fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
Apr 16 17:13:00 in-target: Recommended packages:
Apr 16 17:13:00 in-target:   grub-pc | grub-efi-amd64 | grub-efi-ia32 | grub | lilo thermald
Apr 16 17:13:00 in-target: The following NEW packages will be installed:
Apr 16 17:13:00 in-target:   crda iw libnl-3-200 libnl-genl-3-200 linux-firmware linux-generic
Apr 16 17:13:00 in-target:   linux-headers-4.4.0-62 linux-headers-4.4.0-62-generic linux-headers-generic
Apr 16 17:13:00 in-target:   linux-image-4.4.0-62-generic linux-image-extra-4.4.0-62-generic
Apr 16 17:13:00 in-target:   linux-image-generic wireless-regdb
Apr 16 17:13:00 in-target: 0 upgraded, 13 newly installed, 0 to remove and 0 not upgraded.
Apr 16 17:13:00 in-target: Need to get 0 B/106 MB of archives.
Apr 16 17:13:00 in-target: After this operation, 453 MB of additional disk space will be used.
Apr 16 17:13:00 in-target: Get:1 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial/main amd64 libnl-3-200 amd64 3.2.27-1 [52.1 kB]
Apr 16 17:13:00 in-target: Get:2 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial/main amd64 libnl-genl-3-200 amd64 3.2.27-1 [11.2 kB]
Apr 16 17:13:00 in-target: Get:3 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial/main amd64 wireless-regdb all 2015.07.20-1ubuntu1 [9,058 B]
Apr 16 17:13:00 in-target: Get:4 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial/main amd64 iw amd64 3.17-1 [63.5 kB]
Apr 16 17:13:00 in-target: Get:5 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial/main amd64 crda amd64 3.13-1 [60.5 kB]
Apr 16 17:13:00 in-target: Get:6 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial/main amd64 linux-firmware all 1.157.8 [37.7 MB]
Apr 16 17:13:01 in-target: Get:7 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial/main amd64 linux-image-4.4.0-62-generic amd64 4.4.0-62.83 [21.3 MB]
Apr 16 17:13:03 in-target: Err:7 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial/main amd64 linux-image-4.4.0-62-generic amd64 4.4.0-62.83
Apr 16 17:13:03 in-target:   Hash Sum mismatch
Apr 16 17:13:03 in-target: Get:8 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial/main amd64 linux-image-extra-4.4.0-62-generic amd64 4.4.0-62.83 [36.3 MB]
Apr 16 17:13:07 in-target: Err:8 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial/main amd64 linux-image-extra-4.4.0-62-generic amd64 4.4.0-62.83
Apr 16 17:13:07 in-target:   Hash Sum mismatch
Apr 16 17:13:07 in-target: Get:9 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial/main amd64 linux-image-generic amd64 4.4.0.62.65 [2,290 B]
Apr 16 17:13:07 in-target: Get:10 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial/main amd64 linux-headers-4.4.0-62 all 4.4.0-62.83 [9,907 kB]
Apr 16 17:13:08 in-target: Get:11 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial/main amd64 linux-headers-4.4.0-62-generic amd64 4.4.0-62.83 [773 kB]
Apr 16 17:13:08 in-target: Get:12 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial/main amd64 linux-headers-generic amd64 4.4.0.62.65 [2,256 B]
Apr 16 17:13:08 in-target: Get:13 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial/main amd64 linux-generic amd64 4.4.0.62.65 [1,784 B]
Apr 16 17:13:08 in-target: E
Apr 16 17:13:08 in-target: : Failed to fetch cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8)/pool/main/l/linux/linux-image-4.4.0-62-generic_4.4.0-62.83_amd64.deb  Hash Sum mismatch
Apr 16 17:13:08 in-target: 
Apr 16 17:13:08 in-target: E: Failed to fetch cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8)/pool/main/l/linux/linux-image-extra-4.4.0-62-generic_4.4.0-62.83_amd64.deb  Hash Sum mismatch
Apr 16 17:13:08 in-target: 
Apr 16 17:13:08 in-target: E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
Apr 16 17:13:08 in-target: Reading package lists...
Apr 16 17:13:08 in-target: 
Apr 16 17:13:08 in-target: Building dependency tree...
Apr 16 17:13:08 in-target: 
Apr 16 17:13:08 in-target: Reading state information...
Apr 16 17:13:08 in-target: The following additional packages will be installed:
Apr 16 17:13:08 in-target:   linux-headers-4.4.0-62 linux-headers-4.4.0-62-generic
Apr 16 17:13:08 in-target: The following NEW packages will be installed:
Apr 16 17:13:08 in-target:   linux-headers-4.4.0-62 linux-headers-4.4.0-62-generic linux-headers-generic
Apr 16 17:13:08 in-target: 0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Apr 16 17:13:08 in-target: Need to get 0 B/10.7 MB of archives.
Apr 16 17:13:08 in-target: After this operation, 77.8 MB of additional disk space will be used.
Apr 16 17:13:08 in-target: Get:1 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial/main amd64 linux-headers-4.4.0-62 all 4.4.0-62.83 [9,907 kB]
Apr 16 17:13:09 in-target: Get:2 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial/main amd64 linux-headers-4.4.0-62-generic amd64 4.4.0-62.83 [773 kB]
Apr 16 17:13:09 in-target: Get:3 cdrom://Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8) xenial/main amd64 linux-headers-generic amd64 4.4.0.62.65 [2,256 B]
Apr 16 17:13:09 in-target: Selecting previously unselected package linux-headers-4.4.0-62.^M
Apr 16 17:13:09 in-target: (Reading database ... ^M
Apr 16 17:13:09 in-target: (Reading database ... 5%^M(Reading database ... 10%^M(Reading database ... 15%^M(Reading database ... 20%^M(Reading database ... 25%^M(Reading database ... 30%^M(Reading database ... 35%^M(Reading database ... 40%^M(Reading database ... 45%^M(Reading database ... 50%^M(Reading database ... 55%^M(Reading database ... 60%^M
Apr 16 17:13:09 in-target: (Reading database ... 65%^M(Reading database ... 70%^M
Apr 16 17:13:09 in-target: (Reading database ... 75%^M
Apr 16 17:13:09 in-target: (Reading database ... 80%^M
Apr 16 17:13:09 in-target: (Reading database ... 85%^M
Apr 16 17:13:09 in-target: (Reading database ... 90%^M
Apr 16 17:13:09 in-target: (Reading database ... 95%^M
Apr 16 17:13:09 in-target: (Reading database ... 100%^M(Reading database ... 10458 files and directories currently installed.)
Apr 16 17:13:09 in-target: ^M
Apr 16 17:13:09 in-target: Preparing to unpack .../linux-headers-4.4.0-62_4.4.0-62.83_all.deb ...^M
Apr 16 17:13:09 in-target: Unpacking linux-headers-4.4.0-62 (4.4.0-62.83) ...^M
Apr 16 17:13:17 in-target: Selecting previously unselected package linux-headers-4.4.0-62-generic.^M
Apr 16 17:13:17 in-target: Preparing to unpack .../linux-headers-4.4.0-62-generic_4.4.0-62.83_amd64.deb ...^M
Apr 16 17:13:17 in-target: Unpacking linux-headers-4.4.0-62-generic (4.4.0-62.83) ...^M
Apr 16 17:13:19 in-target: Selecting previously unselected package linux-headers-generic.^M
Apr 16 17:13:19 in-target: Preparing to unpack .../linux-headers-generic_4.4.0.62.65_amd64.deb ...^M
Apr 16 17:13:19 in-target: Unpacking linux-headers-generic (4.4.0.62.65) ...^M
Apr 16 17:13:19 in-target: Setting up linux-headers-4.4.0-62 (4.4.0-62.83) ...^M
Apr 16 17:13:20 in-target: Setting up linux-headers-4.4.0-62-generic (4.4.0-62.83) ...^M
Apr 16 17:13:20 in-target: Setting up linux-headers-generic (4.4.0.62.65) ...^M
Apr 16 17:13:21 base-installer: error: exiting on error base-installer/kernel/failed-install
Apr 16 17:13:32 main-menu[1109]: (process:23509): 0
Apr 16 17:13:32 main-menu[1109]: (process:23509): 0
Apr 16 17:13:32 main-menu[1109]: (process:23509): 0
Apr 16 17:13:32 main-menu[1109]: (process:23509): 0
Apr 16 17:13:32 main-menu[1109]: (process:23509): 0
Apr 16 17:13:32 main-menu[1109]: (process:23509): 0
Apr 16 17:13:32 main-menu[1109]: (process:23509): 0
Apr 16 17:13:32 main-menu[1109]: (process:23509): 0
Apr 16 17:13:32 main-menu[1109]: (process:23509): 0
Apr 16 17:13:32 main-menu[1109]: (process:23509): 0
Apr 16 17:13:32 main-menu[1109]: (process:23509): 0
Apr 16 17:13:32 main-menu[1109]: (process:23509): 0
Apr 16 17:13:32 main-menu[1109]: (process:23509): 0
Apr 16 17:13:32 main-menu[1109]: (process:23509): 0
Apr 16 17:13:32 main-menu[1109]: (process:23509): 0
Apr 16 17:13:32 main-menu[1109]: (process:23509): 0
Apr 16 17:13:32 main-menu[1109]: (process:23509): 0
Apr 16 17:13:32 main-menu[1109]: (process:23509): 0
Apr 16 17:13:32 main-menu[1109]: (process:23509): unknown udeb squashfs-modules
Apr 16 17:13:32 main-menu[1109]: WARNING **: Configuring 'live-installer' failed with error code 1
Apr 16 17:13:32 main-menu[1109]: WARNING **: Menu item 'live-installer' failed.
Apr 16 17:13:33 main-menu[1109]: INFO: Modifying debconf priority limit from 'medium' to 'low'
Apr 16 17:13:33 debconf: Setting debconf/priority to low
Apr 16 17:13:34 main-menu[1109]: INFO: Falling back to the package description for brltty-udeb
Apr 16 17:13:38 main-menu[1109]: INFO: Falling back to the package description for brltty-udeb
Apr 16 17:13:38 main-menu[1109]: INFO: Menu item 'save-logs' selected
```

---

### Post by TheFu on 2017-04-17
Thanks for the code tags, ajgreeny.

I don't have an answer from what is posted. Seems the networking isn't working or the install media isn't correct.
The "Hash Sum mismatch" is the clue for that.  Can you validate the media, please?

There are many ways to learn Linux server administration.
Using it daily is a great way, but really it is best to start with a Linux desktop version that runs a similar distro to get familiar with the environment. 

Laptops bring extra challenges for a server install.  Servers do not have any GUI. No video drivers will be installed. Servers do not use wifi, so no wifi drivers will be installed. Even if you have wired ethernet, sometimes the desktop or USB NICs require unusual drivers, which aren't automatically installed.

Another option is to use virtualization on a newer, more powerful, system.  Ubuntu server will install and run nicely with just 512MB of RAM, next to zero graphics, and since it is a VM, the actual hardware of the system isn't seen from "inside" - only the virtual hardware that the hypervisor provides through emulation.

The normal method to install ubuntu server is from an ISO. The ISO must be correctly burned to optical media or specifically placed onto a USB flash disk using a tool that allows correct booting.

Of course, you can do anything you put your mind towards. It is just that some paths will be easier and perhaps in a few months or years, performing the install with more skills will be easier?

BTW, it is hard to gauge your skill level from what has been written. A little of background, might help us tailor our responses to the correct level. How much Linux have you done?

---


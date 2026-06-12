---
title: "Ubuntu 7.10 lockups after recent software update"
date: 2008-02-22
forum: General Help
---

### Post by net4home on 2008-02-22
If this has been addressed someplace else I'm sorry to repost this.

I'm using Ubuntu 7.10 with a nVidia video driver, I know that it can cause problems, but I don't think that's what is causing my total lockups after the following was updated / upgraded yesterday.  

I noticed there was a nautilus update an evolution update and a few updates for some things to do with the CD-ROM.  After this ran my system started to freeze to a point where I couldn't log out, close windows, read mail or do anything.  It has happened today with just Firefox running, but I was able to restart the desktop and recover but when I start anything else like terminal, evolution, file browsing or even the Ubuntu Help.  It takes about 15 - 30 mins and it's frozen.  I can tell when it is starting as Firefox will start to respond slowly before everything goes dead.  

This has happened before to me when the software updates updated some language files for evolution.  I corrected it by uninstalling those packages, but I'm not able to uninstall some of these packages without removing alot of other programs.  Can anyone Help?  Below is the section of the dpkg.log file for the updates.  If something else is needed please let me know....

Thanks
Kevin 


2008-02-21 12:06:20 startup archives unpack
2008-02-21 12:06:40 upgrade libvolume-id0 113-0ubuntu16 113-0ubuntu17
2008-02-21 12:06:40 status half-configured libvolume-id0 113-0ubuntu16
2008-02-21 12:06:40 status unpacked libvolume-id0 113-0ubuntu16
2008-02-21 12:06:40 status half-installed libvolume-id0 113-0ubuntu16
2008-02-21 12:06:41 status half-installed libvolume-id0 113-0ubuntu16
2008-02-21 12:06:41 status unpacked libvolume-id0 113-0ubuntu17
2008-02-21 12:06:41 status unpacked libvolume-id0 113-0ubuntu17
2008-02-21 12:06:41 upgrade udev 113-0ubuntu16 113-0ubuntu17
2008-02-21 12:06:41 status half-configured udev 113-0ubuntu16
2008-02-21 12:06:41 status unpacked udev 113-0ubuntu16
2008-02-21 12:06:41 status half-installed udev 113-0ubuntu16
2008-02-21 12:06:42 status half-installed udev 113-0ubuntu16
2008-02-21 12:06:42 status unpacked udev 113-0ubuntu17
2008-02-21 12:06:42 status unpacked udev 113-0ubuntu17
2008-02-21 12:06:43 upgrade volumeid 113-0ubuntu16 113-0ubuntu17
2008-02-21 12:06:43 status half-configured volumeid 113-0ubuntu16
2008-02-21 12:06:43 status unpacked volumeid 113-0ubuntu16
2008-02-21 12:06:43 status half-installed volumeid 113-0ubuntu16
2008-02-21 12:06:43 status half-installed volumeid 113-0ubuntu16
2008-02-21 12:06:43 status unpacked volumeid 113-0ubuntu17
2008-02-21 12:06:43 status unpacked volumeid 113-0ubuntu17
2008-02-21 12:06:43 upgrade avahi-autoipd 0.6.20-2ubuntu3.2 0.6.20-2ubuntu3.3
2008-02-21 12:06:43 status half-configured avahi-autoipd 0.6.20-2ubuntu3.2
2008-02-21 12:06:43 status unpacked avahi-autoipd 0.6.20-2ubuntu3.2
2008-02-21 12:06:43 status half-installed avahi-autoipd 0.6.20-2ubuntu3.2
2008-02-21 12:06:44 status half-installed avahi-autoipd 0.6.20-2ubuntu3.2
2008-02-21 12:06:44 status unpacked avahi-autoipd 0.6.20-2ubuntu3.3
2008-02-21 12:06:44 status unpacked avahi-autoipd 0.6.20-2ubuntu3.3
2008-02-21 12:06:44 upgrade libavahi-common-data 0.6.20-2ubuntu3.2 0.6.20-2ubuntu3.3
2008-02-21 12:06:44 status half-configured libavahi-common-data 0.6.20-2ubuntu3.2
2008-02-21 12:06:44 status unpacked libavahi-common-data 0.6.20-2ubuntu3.2
2008-02-21 12:06:45 status half-installed libavahi-common-data 0.6.20-2ubuntu3.2
2008-02-21 12:06:45 status half-installed libavahi-common-data 0.6.20-2ubuntu3.2
2008-02-21 12:06:45 status unpacked libavahi-common-data 0.6.20-2ubuntu3.3
2008-02-21 12:06:45 status unpacked libavahi-common-data 0.6.20-2ubuntu3.3
2008-02-21 12:06:45 upgrade libavahi-common3 0.6.20-2ubuntu3.2 0.6.20-2ubuntu3.3
2008-02-21 12:06:45 status half-configured libavahi-common3 0.6.20-2ubuntu3.2
2008-02-21 12:06:45 status unpacked libavahi-common3 0.6.20-2ubuntu3.2
2008-02-21 12:06:46 status half-installed libavahi-common3 0.6.20-2ubuntu3.2
2008-02-21 12:06:46 status half-installed libavahi-common3 0.6.20-2ubuntu3.2
2008-02-21 12:06:46 status unpacked libavahi-common3 0.6.20-2ubuntu3.3
2008-02-21 12:06:46 status unpacked libavahi-common3 0.6.20-2ubuntu3.3
2008-02-21 12:06:46 upgrade libavahi-core5 0.6.20-2ubuntu3.2 0.6.20-2ubuntu3.3
2008-02-21 12:06:46 status half-configured libavahi-core5 0.6.20-2ubuntu3.2
2008-02-21 12:06:46 status unpacked libavahi-core5 0.6.20-2ubuntu3.2
2008-02-21 12:06:46 status half-installed libavahi-core5 0.6.20-2ubuntu3.2
2008-02-21 12:06:47 status half-installed libavahi-core5 0.6.20-2ubuntu3.2
2008-02-21 12:06:47 status unpacked libavahi-core5 0.6.20-2ubuntu3.3
2008-02-21 12:06:47 status unpacked libavahi-core5 0.6.20-2ubuntu3.3
2008-02-21 12:06:47 upgrade avahi-daemon 0.6.20-2ubuntu3.2 0.6.20-2ubuntu3.3
2008-02-21 12:06:47 status half-configured avahi-daemon 0.6.20-2ubuntu3.2
2008-02-21 12:06:48 status unpacked avahi-daemon 0.6.20-2ubuntu3.2
2008-02-21 12:06:48 status half-installed avahi-daemon 0.6.20-2ubuntu3.2
2008-02-21 12:06:49 status half-installed avahi-daemon 0.6.20-2ubuntu3.2
2008-02-21 12:06:50 status unpacked avahi-daemon 0.6.20-2ubuntu3.3
2008-02-21 12:06:50 status unpacked avahi-daemon 0.6.20-2ubuntu3.3
2008-02-21 12:06:50 upgrade libavahi-client3 0.6.20-2ubuntu3.2 0.6.20-2ubuntu3.3
2008-02-21 12:06:50 status half-configured libavahi-client3 0.6.20-2ubuntu3.2
2008-02-21 12:06:50 status unpacked libavahi-client3 0.6.20-2ubuntu3.2
2008-02-21 12:06:50 status half-installed libavahi-client3 0.6.20-2ubuntu3.2
2008-02-21 12:06:50 status half-installed libavahi-client3 0.6.20-2ubuntu3.2
2008-02-21 12:06:51 status unpacked libavahi-client3 0.6.20-2ubuntu3.3
2008-02-21 12:06:51 status unpacked libavahi-client3 0.6.20-2ubuntu3.3
2008-02-21 12:06:51 upgrade libavahi-compat-libdnssd1 0.6.20-2ubuntu3.2 0.6.20-2ubuntu3.3
2008-02-21 12:06:51 status half-configured libavahi-compat-libdnssd1 0.6.20-2ubuntu3.2
2008-02-21 12:06:51 status unpacked libavahi-compat-libdnssd1 0.6.20-2ubuntu3.2
2008-02-21 12:06:51 status half-installed libavahi-compat-libdnssd1 0.6.20-2ubuntu3.2
2008-02-21 12:06:51 status half-installed libavahi-compat-libdnssd1 0.6.20-2ubuntu3.2
2008-02-21 12:06:52 status unpacked libavahi-compat-libdnssd1 0.6.20-2ubuntu3.3
2008-02-21 12:06:52 status unpacked libavahi-compat-libdnssd1 0.6.20-2ubuntu3.3
2008-02-21 12:06:52 upgrade libavahi-glib1 0.6.20-2ubuntu3.2 0.6.20-2ubuntu3.3
2008-02-21 12:06:52 status half-configured libavahi-glib1 0.6.20-2ubuntu3.2
2008-02-21 12:06:52 status unpacked libavahi-glib1 0.6.20-2ubuntu3.2
2008-02-21 12:06:52 status half-installed libavahi-glib1 0.6.20-2ubuntu3.2
2008-02-21 12:06:52 status half-installed libavahi-glib1 0.6.20-2ubuntu3.2
2008-02-21 12:06:53 status unpacked libavahi-glib1 0.6.20-2ubuntu3.3
2008-02-21 12:06:53 status unpacked libavahi-glib1 0.6.20-2ubuntu3.3
2008-02-21 12:06:53 upgrade libavahi-qt3-1 0.6.20-2ubuntu3.2 0.6.20-2ubuntu3.3
2008-02-21 12:06:53 status half-configured libavahi-qt3-1 0.6.20-2ubuntu3.2
2008-02-21 12:06:53 status unpacked libavahi-qt3-1 0.6.20-2ubuntu3.2
2008-02-21 12:06:53 status half-installed libavahi-qt3-1 0.6.20-2ubuntu3.2
2008-02-21 12:06:53 status half-installed libavahi-qt3-1 0.6.20-2ubuntu3.2
2008-02-21 12:06:54 status unpacked libavahi-qt3-1 0.6.20-2ubuntu3.3
2008-02-21 12:06:54 status unpacked libavahi-qt3-1 0.6.20-2ubuntu3.3
2008-02-21 12:06:54 upgrade libcdio6 0.76-1ubuntu2 0.76-1ubuntu2.7.10.1
2008-02-21 12:06:54 status half-configured libcdio6 0.76-1ubuntu2
2008-02-21 12:06:54 status unpacked libcdio6 0.76-1ubuntu2
2008-02-21 12:06:54 status half-installed libcdio6 0.76-1ubuntu2
2008-02-21 12:06:54 status half-installed libcdio6 0.76-1ubuntu2
2008-02-21 12:06:55 status unpacked libcdio6 0.76-1ubuntu2.7.10.1
2008-02-21 12:06:55 status unpacked libcdio6 0.76-1ubuntu2.7.10.1
2008-02-21 12:06:55 upgrade libiso9660-4 0.76-1ubuntu2 0.76-1ubuntu2.7.10.1
2008-02-21 12:06:55 status half-configured libiso9660-4 0.76-1ubuntu2
2008-02-21 12:06:55 status unpacked libiso9660-4 0.76-1ubuntu2
2008-02-21 12:06:55 status half-installed libiso9660-4 0.76-1ubuntu2
2008-02-21 12:06:55 status half-installed libiso9660-4 0.76-1ubuntu2
2008-02-21 12:06:55 status unpacked libiso9660-4 0.76-1ubuntu2.7.10.1
2008-02-21 12:06:55 status unpacked libiso9660-4 0.76-1ubuntu2.7.10.1
2008-02-21 12:06:56 upgrade libnautilus-extension1 1:2.20.0-0ubuntu7 1:2.20.0-0ubuntu7.1
2008-02-21 12:06:56 status half-configured libnautilus-extension1 1:2.20.0-0ubuntu7
2008-02-21 12:06:56 status unpacked libnautilus-extension1 1:2.20.0-0ubuntu7
2008-02-21 12:06:56 status half-installed libnautilus-extension1 1:2.20.0-0ubuntu7
2008-02-21 12:06:56 status half-installed libnautilus-extension1 1:2.20.0-0ubuntu7
2008-02-21 12:06:56 status unpacked libnautilus-extension1 1:2.20.0-0ubuntu7.1
2008-02-21 12:06:56 status unpacked libnautilus-extension1 1:2.20.0-0ubuntu7.1
2008-02-21 12:06:56 upgrade libqt4-core 4.3.2-0ubuntu3.1 4.3.2-0ubuntu3.2
2008-02-21 12:06:56 status half-configured libqt4-core 4.3.2-0ubuntu3.1
2008-02-21 12:06:56 status unpacked libqt4-core 4.3.2-0ubuntu3.1
2008-02-21 12:06:56 status half-installed libqt4-core 4.3.2-0ubuntu3.1
2008-02-21 12:06:57 status half-installed libqt4-core 4.3.2-0ubuntu3.1
2008-02-21 12:06:57 status unpacked libqt4-core 4.3.2-0ubuntu3.2
2008-02-21 12:06:57 status unpacked libqt4-core 4.3.2-0ubuntu3.2
2008-02-21 12:06:58 upgrade libqt4-gui 4.3.2-0ubuntu3.1 4.3.2-0ubuntu3.2
2008-02-21 12:06:58 status half-configured libqt4-gui 4.3.2-0ubuntu3.1
2008-02-21 12:06:58 status unpacked libqt4-gui 4.3.2-0ubuntu3.1
2008-02-21 12:06:58 status half-installed libqt4-gui 4.3.2-0ubuntu3.1
2008-02-21 12:06:58 status half-installed libqt4-gui 4.3.2-0ubuntu3.1
2008-02-21 12:06:59 status unpacked libqt4-gui 4.3.2-0ubuntu3.2
2008-02-21 12:06:59 status unpacked libqt4-gui 4.3.2-0ubuntu3.2
2008-02-21 12:06:59 upgrade libqt4-sql 4.3.2-0ubuntu3.1 4.3.2-0ubuntu3.2
2008-02-21 12:06:59 status half-configured libqt4-sql 4.3.2-0ubuntu3.1
2008-02-21 12:07:00 status unpacked libqt4-sql 4.3.2-0ubuntu3.1
2008-02-21 12:07:00 status half-installed libqt4-sql 4.3.2-0ubuntu3.1
2008-02-21 12:07:00 status half-installed libqt4-sql 4.3.2-0ubuntu3.1
2008-02-21 12:07:00 status unpacked libqt4-sql 4.3.2-0ubuntu3.2
2008-02-21 12:07:00 status unpacked libqt4-sql 4.3.2-0ubuntu3.2
2008-02-21 12:07:00 upgrade libqt4-qt3support 4.3.2-0ubuntu3.1 4.3.2-0ubuntu3.2
2008-02-21 12:07:00 status half-configured libqt4-qt3support 4.3.2-0ubuntu3.1
2008-02-21 12:07:01 status unpacked libqt4-qt3support 4.3.2-0ubuntu3.1
2008-02-21 12:07:01 status half-installed libqt4-qt3support 4.3.2-0ubuntu3.1
2008-02-21 12:07:01 status half-installed libqt4-qt3support 4.3.2-0ubuntu3.1
2008-02-21 12:07:01 status unpacked libqt4-qt3support 4.3.2-0ubuntu3.2
2008-02-21 12:07:02 status unpacked libqt4-qt3support 4.3.2-0ubuntu3.2
2008-02-21 12:07:02 upgrade nautilus-data 1:2.20.0-0ubuntu7 1:2.20.0-0ubuntu7.1
2008-02-21 12:07:02 status half-configured nautilus-data 1:2.20.0-0ubuntu7
2008-02-21 12:07:19 status unpacked nautilus-data 1:2.20.0-0ubuntu7
2008-02-21 12:07:22 status half-installed nautilus-data 1:2.20.0-0ubuntu7
2008-02-21 12:07:23 status half-installed nautilus-data 1:2.20.0-0ubuntu7
2008-02-21 12:07:24 status unpacked nautilus-data 1:2.20.0-0ubuntu7.1
2008-02-21 12:07:24 status unpacked nautilus-data 1:2.20.0-0ubuntu7.1
2008-02-21 12:07:24 upgrade nautilus 1:2.20.0-0ubuntu7 1:2.20.0-0ubuntu7.1
2008-02-21 12:07:24 status half-configured nautilus 1:2.20.0-0ubuntu7
2008-02-21 12:07:24 status unpacked nautilus 1:2.20.0-0ubuntu7
2008-02-21 12:07:24 status half-installed nautilus 1:2.20.0-0ubuntu7
2008-02-21 12:07:25 status half-installed nautilus 1:2.20.0-0ubuntu7
2008-02-21 12:07:25 status unpacked nautilus 1:2.20.0-0ubuntu7.1
2008-02-21 12:07:26 status unpacked nautilus 1:2.20.0-0ubuntu7.1
2008-02-21 12:07:27 startup packages configure
2008-02-21 12:07:27 configure libvolume-id0 113-0ubuntu17 113-0ubuntu17
2008-02-21 12:07:27 status unpacked libvolume-id0 113-0ubuntu17
2008-02-21 12:07:28 status half-configured libvolume-id0 113-0ubuntu17
2008-02-21 12:07:28 status installed libvolume-id0 113-0ubuntu17
2008-02-21 12:07:28 configure volumeid 113-0ubuntu17 113-0ubuntu17
2008-02-21 12:07:28 status unpacked volumeid 113-0ubuntu17
2008-02-21 12:07:28 status half-configured volumeid 113-0ubuntu17
2008-02-21 12:07:28 status installed volumeid 113-0ubuntu17
2008-02-21 12:07:28 status triggers-pending initramfs-tools 0.85eubuntu20
2008-02-21 12:07:28 configure udev 113-0ubuntu17 113-0ubuntu17
2008-02-21 12:07:28 status unpacked udev 113-0ubuntu17
2008-02-21 12:07:29 status unpacked udev 113-0ubuntu17
2008-02-21 12:07:29 status unpacked udev 113-0ubuntu17
2008-02-21 12:07:29 status unpacked udev 113-0ubuntu17
2008-02-21 12:07:29 status unpacked udev 113-0ubuntu17
2008-02-21 12:07:29 status unpacked udev 113-0ubuntu17
2008-02-21 12:07:29 status unpacked udev 113-0ubuntu17
2008-02-21 12:07:29 status unpacked udev 113-0ubuntu17
2008-02-21 12:07:29 status unpacked udev 113-0ubuntu17
2008-02-21 12:07:30 status unpacked udev 113-0ubuntu17
2008-02-21 12:07:30 status unpacked udev 113-0ubuntu17
2008-02-21 12:07:30 status unpacked udev 113-0ubuntu17
2008-02-21 12:07:30 status unpacked udev 113-0ubuntu17
2008-02-21 12:07:30 status unpacked udev 113-0ubuntu17
2008-02-21 12:07:30 status unpacked udev 113-0ubuntu17
2008-02-21 12:07:30 status unpacked udev 113-0ubuntu17
2008-02-21 12:07:31 status unpacked udev 113-0ubuntu17
2008-02-21 12:07:31 status unpacked udev 113-0ubuntu17
2008-02-21 12:07:31 status half-configured udev 113-0ubuntu17
2008-02-21 12:07:31 status installed udev 113-0ubuntu17
2008-02-21 12:07:32 configure avahi-autoipd 0.6.20-2ubuntu3.3 0.6.20-2ubuntu3.3
2008-02-21 12:07:32 status unpacked avahi-autoipd 0.6.20-2ubuntu3.3
2008-02-21 12:07:32 status unpacked avahi-autoipd 0.6.20-2ubuntu3.3
2008-02-21 12:07:32 status unpacked avahi-autoipd 0.6.20-2ubuntu3.3
2008-02-21 12:07:32 status unpacked avahi-autoipd 0.6.20-2ubuntu3.3
2008-02-21 12:07:32 status unpacked avahi-autoipd 0.6.20-2ubuntu3.3
2008-02-21 12:07:32 status unpacked avahi-autoipd 0.6.20-2ubuntu3.3
2008-02-21 12:07:32 status half-configured avahi-autoipd 0.6.20-2ubuntu3.3
2008-02-21 12:07:33 status installed avahi-autoipd 0.6.20-2ubuntu3.3
2008-02-21 12:07:33 configure libavahi-common-data 0.6.20-2ubuntu3.3 0.6.20-2ubuntu3.3
2008-02-21 12:07:33 status unpacked libavahi-common-data 0.6.20-2ubuntu3.3
2008-02-21 12:07:33 status half-configured libavahi-common-data 0.6.20-2ubuntu3.3
2008-02-21 12:07:33 status installed libavahi-common-data 0.6.20-2ubuntu3.3
2008-02-21 12:07:33 configure libavahi-common3 0.6.20-2ubuntu3.3 0.6.20-2ubuntu3.3
2008-02-21 12:07:33 status unpacked libavahi-common3 0.6.20-2ubuntu3.3
2008-02-21 12:07:33 status half-configured libavahi-common3 0.6.20-2ubuntu3.3
2008-02-21 12:07:33 status installed libavahi-common3 0.6.20-2ubuntu3.3
2008-02-21 12:07:34 status triggers-pending libc6 2.6.1-1ubuntu10
2008-02-21 12:07:34 configure libavahi-core5 0.6.20-2ubuntu3.3 0.6.20-2ubuntu3.3
2008-02-21 12:07:34 status unpacked libavahi-core5 0.6.20-2ubuntu3.3
2008-02-21 12:07:34 status half-configured libavahi-core5 0.6.20-2ubuntu3.3
2008-02-21 12:07:34 status installed libavahi-core5 0.6.20-2ubuntu3.3
2008-02-21 12:07:34 configure avahi-daemon 0.6.20-2ubuntu3.3 0.6.20-2ubuntu3.3
2008-02-21 12:07:34 status unpacked avahi-daemon 0.6.20-2ubuntu3.3
2008-02-21 12:07:34 status unpacked avahi-daemon 0.6.20-2ubuntu3.3
2008-02-21 12:07:34 status unpacked avahi-daemon 0.6.20-2ubuntu3.3
2008-02-21 12:07:35 status unpacked avahi-daemon 0.6.20-2ubuntu3.3
2008-02-21 12:07:35 status unpacked avahi-daemon 0.6.20-2ubuntu3.3
2008-02-21 12:07:35 status unpacked avahi-daemon 0.6.20-2ubuntu3.3
2008-02-21 12:07:35 status unpacked avahi-daemon 0.6.20-2ubuntu3.3
2008-02-21 12:07:35 status unpacked avahi-daemon 0.6.20-2ubuntu3.3
2008-02-21 12:07:35 status half-configured avahi-daemon 0.6.20-2ubuntu3.3
2008-02-21 12:07:36 status installed avahi-daemon 0.6.20-2ubuntu3.3
2008-02-21 12:07:36 configure libavahi-client3 0.6.20-2ubuntu3.3 0.6.20-2ubuntu3.3
2008-02-21 12:07:36 status unpacked libavahi-client3 0.6.20-2ubuntu3.3
2008-02-21 12:07:36 status half-configured libavahi-client3 0.6.20-2ubuntu3.3
2008-02-21 12:07:36 status installed libavahi-client3 0.6.20-2ubuntu3.3
2008-02-21 12:07:37 configure libavahi-compat-libdnssd1 0.6.20-2ubuntu3.3 0.6.20-2ubuntu3.3
2008-02-21 12:07:37 status unpacked libavahi-compat-libdnssd1 0.6.20-2ubuntu3.3
2008-02-21 12:07:37 status half-configured libavahi-compat-libdnssd1 0.6.20-2ubuntu3.3
2008-02-21 12:07:37 status installed libavahi-compat-libdnssd1 0.6.20-2ubuntu3.3
2008-02-21 12:07:37 configure libavahi-glib1 0.6.20-2ubuntu3.3 0.6.20-2ubuntu3.3
2008-02-21 12:07:37 status unpacked libavahi-glib1 0.6.20-2ubuntu3.3
2008-02-21 12:07:37 status half-configured libavahi-glib1 0.6.20-2ubuntu3.3
2008-02-21 12:07:37 status installed libavahi-glib1 0.6.20-2ubuntu3.3
2008-02-21 12:07:37 configure libavahi-qt3-1 0.6.20-2ubuntu3.3 0.6.20-2ubuntu3.3
2008-02-21 12:07:37 status unpacked libavahi-qt3-1 0.6.20-2ubuntu3.3
2008-02-21 12:07:38 status half-configured libavahi-qt3-1 0.6.20-2ubuntu3.3
2008-02-21 12:07:38 status installed libavahi-qt3-1 0.6.20-2ubuntu3.3
2008-02-21 12:07:38 configure libcdio6 0.76-1ubuntu2.7.10.1 0.76-1ubuntu2.7.10.1
2008-02-21 12:07:38 status unpacked libcdio6 0.76-1ubuntu2.7.10.1
2008-02-21 12:07:38 status half-configured libcdio6 0.76-1ubuntu2.7.10.1
2008-02-21 12:07:38 status installed libcdio6 0.76-1ubuntu2.7.10.1
2008-02-21 12:07:38 configure libiso9660-4 0.76-1ubuntu2.7.10.1 0.76-1ubuntu2.7.10.1
2008-02-21 12:07:38 status unpacked libiso9660-4 0.76-1ubuntu2.7.10.1
2008-02-21 12:07:38 status half-configured libiso9660-4 0.76-1ubuntu2.7.10.1
2008-02-21 12:07:38 status installed libiso9660-4 0.76-1ubuntu2.7.10.1
2008-02-21 12:07:39 configure libnautilus-extension1 1:2.20.0-0ubuntu7.1 1:2.20.0-0ubuntu7.1
2008-02-21 12:07:39 status unpacked libnautilus-extension1 1:2.20.0-0ubuntu7.1
2008-02-21 12:07:39 status half-configured libnautilus-extension1 1:2.20.0-0ubuntu7.1
2008-02-21 12:07:39 status installed libnautilus-extension1 1:2.20.0-0ubuntu7.1
2008-02-21 12:07:39 configure libqt4-core 4.3.2-0ubuntu3.2 4.3.2-0ubuntu3.2
2008-02-21 12:07:39 status unpacked libqt4-core 4.3.2-0ubuntu3.2
2008-02-21 12:07:39 status half-configured libqt4-core 4.3.2-0ubuntu3.2
2008-02-21 12:07:39 status installed libqt4-core 4.3.2-0ubuntu3.2
2008-02-21 12:07:39 configure libqt4-gui 4.3.2-0ubuntu3.2 4.3.2-0ubuntu3.2
2008-02-21 12:07:39 status unpacked libqt4-gui 4.3.2-0ubuntu3.2
2008-02-21 12:07:39 status half-configured libqt4-gui 4.3.2-0ubuntu3.2
2008-02-21 12:07:40 status installed libqt4-gui 4.3.2-0ubuntu3.2
2008-02-21 12:07:40 configure libqt4-sql 4.3.2-0ubuntu3.2 4.3.2-0ubuntu3.2
2008-02-21 12:07:40 status unpacked libqt4-sql 4.3.2-0ubuntu3.2
2008-02-21 12:07:40 status half-configured libqt4-sql 4.3.2-0ubuntu3.2
2008-02-21 12:07:40 status installed libqt4-sql 4.3.2-0ubuntu3.2
2008-02-21 12:07:40 configure libqt4-qt3support 4.3.2-0ubuntu3.2 4.3.2-0ubuntu3.2
2008-02-21 12:07:40 status unpacked libqt4-qt3support 4.3.2-0ubuntu3.2
2008-02-21 12:07:40 status half-configured libqt4-qt3support 4.3.2-0ubuntu3.2
2008-02-21 12:07:40 status installed libqt4-qt3support 4.3.2-0ubuntu3.2
2008-02-21 12:07:40 configure nautilus-data 1:2.20.0-0ubuntu7.1 1:2.20.0-0ubuntu7.1
2008-02-21 12:07:40 status unpacked nautilus-data 1:2.20.0-0ubuntu7.1
2008-02-21 12:07:41 status half-configured nautilus-data 1:2.20.0-0ubuntu7.1
2008-02-21 12:07:52 status installed nautilus-data 1:2.20.0-0ubuntu7.1
2008-02-21 12:07:54 configure nautilus 1:2.20.0-0ubuntu7.1 1:2.20.0-0ubuntu7.1
2008-02-21 12:07:54 status unpacked nautilus 1:2.20.0-0ubuntu7.1
2008-02-21 12:07:54 status half-configured nautilus 1:2.20.0-0ubuntu7.1
2008-02-21 12:07:57 status installed nautilus 1:2.20.0-0ubuntu7.1
2008-02-21 12:07:58 trigproc initramfs-tools 0.85eubuntu20 0.85eubuntu20
2008-02-21 12:07:58 status half-configured initramfs-tools 0.85eubuntu20
2008-02-21 12:08:18 status installed initramfs-tools 0.85eubuntu20
2008-02-21 12:08:18 trigproc libc6 2.6.1-1ubuntu10 2.6.1-1ubuntu10
2008-02-21 12:08:18 status half-configured libc6 2.6.1-1ubuntu10
2008-02-21 12:08:41 status installed libc6 2.6.1-1ubuntu10

---

### Post by Sam Lars on 2008-02-22
Is there anything in syslog that lets you know what's going on?

---

### Post by Crafty Kisses on 2008-02-22
> **Sam Lars said:**
> Is there anything in syslog that lets you know what's going on?

Post the following output: ```
top
```

---

### Post by net4home on 2008-02-22
Thanks Sam I've looked and here is what I found.

There are a lot of DEBUG messages from the gdm and gdmgreater it also looks like I have at start up a lot of debug messages from NetworkManager about a new device has been added and a cupsd warning about needing to fix the application to use native API of Avahi.  

These are the debug messages from the gdm:
gdm[6046]: DEBUG: Attempting to parse key string: daemon/ServAuthDir=/var/lib/gdm
gdm[6046]: DEBUG: gdm_main: Here we go...
and they go on and on....

I did find with the utility top and htop that there was a process called trackerd that was running and taking up 100% of my first proc and almost 92% of the 3GBs of memory in my system.  I have removed this package and so far things are going well since I have up two terminal session two Firefox sessions a nautilus session as well as a gedit session and its been longer than 15 - 30 mins.  There also is no trackerd process running.  

If any one has any light to shed on this please feel free otherwise I'm considering this fixed.  

Thanks

---


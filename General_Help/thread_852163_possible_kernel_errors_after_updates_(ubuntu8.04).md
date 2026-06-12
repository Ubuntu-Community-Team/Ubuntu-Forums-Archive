---
title: "possible kernel errors after updates (ubuntu8.04)"
date: 2008-07-07
forum: General Help
---

### Post by plesset on 2008-07-07
I seem to have a new set of problems after installing some inconspicuous  packages this morning. The first thing I noticed was that FF3 began to crash immediately when I tried to open it. Perhaps naively I then tried to reboot, only to find it hang on the reboot with a lot of 
ominous error messages. I didn't catch them all but most seemed to be something like

"ata1.00 ... DRDY ERR"
"BMDMA"
"error UNC" 

When I boot it via liveCD, I can see all my disks and partitions 
(fdisk -l works) but it's like the kernel can't find some of them,
causing the boot to hang. I'm using the latest kernel, and have tried 
all the older ones I still have on the machine.  

Any help or suggestions will be most appreciated. 

- MP 




P.S. Here is an excerpt from my dpkg.log file:

2008-07-07 09:07:45 startup archives unpack
2008-07-07 09:08:02 upgrade python-apt 0.7.4ubuntu7 0.7.4ubuntu7.1
2008-07-07 09:08:02 status half-configured python-apt 0.7.4ubuntu7
2008-07-07 09:08:02 status unpacked python-apt 0.7.4ubuntu7
2008-07-07 09:08:02 status half-installed python-apt 0.7.4ubuntu7
2008-07-07 09:08:03 status half-installed python-apt 0.7.4ubuntu7
2008-07-07 09:08:03 status unpacked python-apt 0.7.4ubuntu7.1
2008-07-07 09:08:03 status unpacked python-apt 0.7.4ubuntu7.1
2008-07-07 09:08:03 upgrade gnome-cards-data 1:2.22.2.1-0ubuntu1 1:2.22.2.1-0ubuntu2
2008-07-07 09:08:03 status half-configured gnome-cards-data 1:2.22.2.1-0ubuntu1
2008-07-07 09:08:03 status unpacked gnome-cards-data 1:2.22.2.1-0ubuntu1
2008-07-07 09:08:03 status half-installed gnome-cards-data 1:2.22.2.1-0ubuntu1
2008-07-07 09:08:03 status half-installed gnome-cards-data 1:2.22.2.1-0ubuntu1
2008-07-07 09:08:03 status unpacked gnome-cards-data 1:2.22.2.1-0ubuntu2
2008-07-07 09:08:03 status unpacked gnome-cards-data 1:2.22.2.1-0ubuntu2
2008-07-07 09:08:03 upgrade gnome-games-data 1:2.22.2.1-0ubuntu1 1:2.22.2.1-0ubuntu2
2008-07-07 09:08:03 status half-configured gnome-games-data 1:2.22.2.1-0ubuntu1
2008-07-07 09:09:06 status unpacked gnome-games-data 1:2.22.2.1-0ubuntu1
2008-07-07 09:09:09 status half-installed gnome-games-data 1:2.22.2.1-0ubuntu1
2008-07-07 09:09:22 status half-installed gnome-games-data 1:2.22.2.1-0ubuntu1
2008-07-07 09:09:28 status unpacked gnome-games-data 1:2.22.2.1-0ubuntu2
2008-07-07 09:09:29 status unpacked gnome-games-data 1:2.22.2.1-0ubuntu2
2008-07-07 09:09:30 upgrade gtk2-engines-murrine 0.53.1-1ubuntu1 0.53.1-1ubuntu2
2008-07-07 09:09:30 status half-configured gtk2-engines-murrine 0.53.1-1ubuntu1
2008-07-07 09:09:30 status unpacked gtk2-engines-murrine 0.53.1-1ubuntu1
2008-07-07 09:09:30 status half-installed gtk2-engines-murrine 0.53.1-1ubuntu1
2008-07-07 09:09:30 status half-installed gtk2-engines-murrine 0.53.1-1ubuntu1
2008-07-07 09:09:30 status unpacked gtk2-engines-murrine 0.53.1-1ubuntu2
2008-07-07 09:09:30 status unpacked gtk2-engines-murrine 0.53.1-1ubuntu2
2008-07-07 09:09:30 upgrade gtk2-engines-ubuntulooks 0.9.12-11 0.9.12-12
2008-07-07 09:09:30 status half-configured gtk2-engines-ubuntulooks 0.9.12-11
2008-07-07 09:09:30 status unpacked gtk2-engines-ubuntulooks 0.9.12-11
2008-07-07 09:09:30 status half-installed gtk2-engines-ubuntulooks 0.9.12-11
2008-07-07 09:09:30 status half-installed gtk2-engines-ubuntulooks 0.9.12-11
2008-07-07 09:09:30 status unpacked gtk2-engines-ubuntulooks 0.9.12-12
2008-07-07 09:09:30 status unpacked gtk2-engines-ubuntulooks 0.9.12-12
2008-07-07 09:09:30 upgrade libpoppler2 0.6.4-1ubuntu2 0.6.4-1ubuntu3
2008-07-07 09:09:30 status half-configured libpoppler2 0.6.4-1ubuntu2
2008-07-07 09:09:30 status unpacked libpoppler2 0.6.4-1ubuntu2
2008-07-07 09:09:30 status half-installed libpoppler2 0.6.4-1ubuntu2
2008-07-07 09:09:35 status half-installed libpoppler2 0.6.4-1ubuntu2
2008-07-07 09:09:35 status unpacked libpoppler2 0.6.4-1ubuntu3
2008-07-07 09:09:36 status unpacked libpoppler2 0.6.4-1ubuntu3
2008-07-07 09:09:36 upgrade libpoppler-glib2 0.6.4-1ubuntu2 0.6.4-1ubuntu3
2008-07-07 09:09:36 status half-configured libpoppler-glib2 0.6.4-1ubuntu2
2008-07-07 09:09:36 status unpacked libpoppler-glib2 0.6.4-1ubuntu2
2008-07-07 09:09:36 status half-installed libpoppler-glib2 0.6.4-1ubuntu2
2008-07-07 09:09:36 status half-installed libpoppler-glib2 0.6.4-1ubuntu2
2008-07-07 09:09:36 status unpacked libpoppler-glib2 0.6.4-1ubuntu3
2008-07-07 09:09:36 status unpacked libpoppler-glib2 0.6.4-1ubuntu3
2008-07-07 09:09:36 install libsilc-1.1-2 <none> 1.1.5-1ubuntu1
2008-07-07 09:09:36 status half-installed libsilc-1.1-2 1.1.5-1ubuntu1
2008-07-07 09:09:36 status unpacked libsilc-1.1-2 1.1.5-1ubuntu1
2008-07-07 09:09:36 status unpacked libsilc-1.1-2 1.1.5-1ubuntu1
2008-07-07 09:09:36 upgrade pidgin 1:2.4.1-1ubuntu2.1 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:09:36 status half-configured pidgin 1:2.4.1-1ubuntu2.1
2008-07-07 09:09:42 status unpacked pidgin 1:2.4.1-1ubuntu2.1
2008-07-07 09:09:50 status half-installed pidgin 1:2.4.1-1ubuntu2.1
2008-07-07 09:09:51 status half-installed pidgin 1:2.4.1-1ubuntu2.1
2008-07-07 09:09:51 status unpacked pidgin 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:09:51 status unpacked pidgin 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:09:51 upgrade libpurple0 1:2.4.1-1ubuntu2.1 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:09:51 status half-configured libpurple0 1:2.4.1-1ubuntu2.1
2008-07-07 09:09:51 status unpacked libpurple0 1:2.4.1-1ubuntu2.1
2008-07-07 09:09:51 status half-installed libpurple0 1:2.4.1-1ubuntu2.1
2008-07-07 09:09:51 status half-installed libpurple0 1:2.4.1-1ubuntu2.1
2008-07-07 09:09:52 status unpacked libpurple0 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:09:52 status unpacked libpurple0 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:09:52 upgrade pidgin-data 1:2.4.1-1ubuntu2.1 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:09:52 status half-configured pidgin-data 1:2.4.1-1ubuntu2.1
2008-07-07 09:09:52 status unpacked pidgin-data 1:2.4.1-1ubuntu2.1
2008-07-07 09:09:52 status half-installed pidgin-data 1:2.4.1-1ubuntu2.1
2008-07-07 09:09:57 status half-installed pidgin-data 1:2.4.1-1ubuntu2.1
2008-07-07 09:09:58 status unpacked pidgin-data 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:09:58 status unpacked pidgin-data 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:09:58 upgrade libpurple-dev 1:2.4.1-1ubuntu2.1 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:09:58 status half-configured libpurple-dev 1:2.4.1-1ubuntu2.1
2008-07-07 09:09:58 status unpacked libpurple-dev 1:2.4.1-1ubuntu2.1
2008-07-07 09:09:58 status half-installed libpurple-dev 1:2.4.1-1ubuntu2.1
2008-07-07 09:09:58 status half-installed libpurple-dev 1:2.4.1-1ubuntu2.1
2008-07-07 09:09:58 status unpacked libpurple-dev 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:09:58 status unpacked libpurple-dev 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:09:58 upgrade pidgin-dev 1:2.4.1-1ubuntu2.1 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:09:58 status half-configured pidgin-dev 1:2.4.1-1ubuntu2.1
2008-07-07 09:10:19 status unpacked pidgin-dev 1:2.4.1-1ubuntu2.1
2008-07-07 09:10:19 status half-installed pidgin-dev 1:2.4.1-1ubuntu2.1
2008-07-07 09:10:19 status half-installed pidgin-dev 1:2.4.1-1ubuntu2.1
2008-07-07 09:10:20 status unpacked pidgin-dev 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:10:20 status unpacked pidgin-dev 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:10:20 upgrade poppler-utils 0.6.4-1ubuntu2 0.6.4-1ubuntu3
2008-07-07 09:10:20 status half-configured poppler-utils 0.6.4-1ubuntu2
2008-07-07 09:10:20 status unpacked poppler-utils 0.6.4-1ubuntu2
2008-07-07 09:10:20 status half-installed poppler-utils 0.6.4-1ubuntu2
2008-07-07 09:10:20 status half-installed poppler-utils 0.6.4-1ubuntu2
2008-07-07 09:10:20 status unpacked poppler-utils 0.6.4-1ubuntu3
2008-07-07 09:10:20 status unpacked poppler-utils 0.6.4-1ubuntu3
2008-07-07 09:10:20 upgrade update-notifier-common 0.70.7 0.70.8
2008-07-07 09:10:20 status half-configured update-notifier-common 0.70.7
2008-07-07 09:10:20 status unpacked update-notifier-common 0.70.7
2008-07-07 09:10:20 status half-installed update-notifier-common 0.70.7
2008-07-07 09:10:20 status half-installed update-notifier-common 0.70.7
2008-07-07 09:10:20 status unpacked update-notifier-common 0.70.8
2008-07-07 09:10:20 status unpacked update-notifier-common 0.70.8
2008-07-07 09:10:20 upgrade update-notifier 0.70.7 0.70.8
2008-07-07 09:10:20 status half-configured update-notifier 0.70.7
2008-07-07 09:10:25 status unpacked update-notifier 0.70.7
2008-07-07 09:10:29 status half-installed update-notifier 0.70.7
2008-07-07 09:10:29 status half-installed update-notifier 0.70.7
2008-07-07 09:10:30 status unpacked update-notifier 0.70.8
2008-07-07 09:10:30 status unpacked update-notifier 0.70.8
2008-07-07 09:10:30 upgrade xserver-xorg-video-intel 2:2.2.1-1ubuntu13.4 2:2.2.1-1ubuntu13.5
2008-07-07 09:10:30 status half-configured xserver-xorg-video-intel 2:2.2.1-1ubuntu13.4
2008-07-07 09:10:30 status unpacked xserver-xorg-video-intel 2:2.2.1-1ubuntu13.4
2008-07-07 09:10:30 status half-installed xserver-xorg-video-intel 2:2.2.1-1ubuntu13.4
2008-07-07 09:10:30 status half-installed xserver-xorg-video-intel 2:2.2.1-1ubuntu13.4
2008-07-07 09:10:30 status unpacked xserver-xorg-video-intel 2:2.2.1-1ubuntu13.5
2008-07-07 09:10:30 status unpacked xserver-xorg-video-intel 2:2.2.1-1ubuntu13.5
2008-07-07 09:10:31 startup packages configure
2008-07-07 09:10:31 configure python-apt 0.7.4ubuntu7.1 0.7.4ubuntu7.1
2008-07-07 09:10:31 status unpacked python-apt 0.7.4ubuntu7.1
2008-07-07 09:10:31 status half-configured python-apt 0.7.4ubuntu7.1
2008-07-07 09:10:31 status installed python-apt 0.7.4ubuntu7.1
2008-07-07 09:10:31 configure gnome-cards-data 1:2.22.2.1-0ubuntu2 1:2.22.2.1-0ubuntu2
2008-07-07 09:10:31 status unpacked gnome-cards-data 1:2.22.2.1-0ubuntu2
2008-07-07 09:10:31 status half-configured gnome-cards-data 1:2.22.2.1-0ubuntu2
2008-07-07 09:10:31 status installed gnome-cards-data 1:2.22.2.1-0ubuntu2
2008-07-07 09:10:31 configure gnome-games-data 1:2.22.2.1-0ubuntu2 1:2.22.2.1-0ubuntu2
2008-07-07 09:10:31 status unpacked gnome-games-data 1:2.22.2.1-0ubuntu2
2008-07-07 09:10:31 status half-configured gnome-games-data 1:2.22.2.1-0ubuntu2
2008-07-07 09:10:39 status installed gnome-games-data 1:2.22.2.1-0ubuntu2
2008-07-07 09:10:43 configure gtk2-engines-murrine 0.53.1-1ubuntu2 0.53.1-1ubuntu2
2008-07-07 09:10:43 status unpacked gtk2-engines-murrine 0.53.1-1ubuntu2
2008-07-07 09:10:43 status half-configured gtk2-engines-murrine 0.53.1-1ubuntu2
2008-07-07 09:10:43 status installed gtk2-engines-murrine 0.53.1-1ubuntu2
2008-07-07 09:10:43 configure gtk2-engines-ubuntulooks 0.9.12-12 0.9.12-12
2008-07-07 09:10:43 status unpacked gtk2-engines-ubuntulooks 0.9.12-12
2008-07-07 09:10:43 status half-configured gtk2-engines-ubuntulooks 0.9.12-12
2008-07-07 09:10:43 status installed gtk2-engines-ubuntulooks 0.9.12-12
2008-07-07 09:10:43 configure libpoppler2 0.6.4-1ubuntu3 0.6.4-1ubuntu3
2008-07-07 09:10:43 status unpacked libpoppler2 0.6.4-1ubuntu3
2008-07-07 09:10:43 status half-configured libpoppler2 0.6.4-1ubuntu3
2008-07-07 09:10:43 status installed libpoppler2 0.6.4-1ubuntu3
2008-07-07 09:10:43 status triggers-pending libc6 2.7-10ubuntu3
2008-07-07 09:10:43 configure libpoppler-glib2 0.6.4-1ubuntu3 0.6.4-1ubuntu3
2008-07-07 09:10:43 status unpacked libpoppler-glib2 0.6.4-1ubuntu3
2008-07-07 09:10:43 status half-configured libpoppler-glib2 0.6.4-1ubuntu3
2008-07-07 09:10:43 status installed libpoppler-glib2 0.6.4-1ubuntu3
2008-07-07 09:10:43 configure libsilc-1.1-2 1.1.5-1ubuntu1 1.1.5-1ubuntu1
2008-07-07 09:10:43 status unpacked libsilc-1.1-2 1.1.5-1ubuntu1
2008-07-07 09:10:43 status half-configured libsilc-1.1-2 1.1.5-1ubuntu1
2008-07-07 09:10:43 status installed libsilc-1.1-2 1.1.5-1ubuntu1
2008-07-07 09:10:43 configure pidgin-data 1:2.4.3-0ubuntu1~hardy1 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:10:43 status unpacked pidgin-data 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:10:44 status unpacked pidgin-data 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:10:44 status half-configured pidgin-data 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:10:44 status installed pidgin-data 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:10:44 configure libpurple0 1:2.4.3-0ubuntu1~hardy1 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:10:44 status unpacked libpurple0 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:10:44 status half-configured libpurple0 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:10:44 status installed libpurple0 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:10:44 configure pidgin 1:2.4.3-0ubuntu1~hardy1 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:10:44 status unpacked pidgin 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:10:44 status half-configured pidgin 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:10:47 status installed pidgin 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:10:51 configure libpurple-dev 1:2.4.3-0ubuntu1~hardy1 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:10:51 status unpacked libpurple-dev 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:10:51 status half-configured libpurple-dev 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:10:51 status installed libpurple-dev 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:10:51 configure pidgin-dev 1:2.4.3-0ubuntu1~hardy1 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:10:51 status unpacked pidgin-dev 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:10:51 status half-configured pidgin-dev 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:10:52 status installed pidgin-dev 1:2.4.3-0ubuntu1~hardy1
2008-07-07 09:10:52 configure poppler-utils 0.6.4-1ubuntu3 0.6.4-1ubuntu3
2008-07-07 09:10:52 status unpacked poppler-utils 0.6.4-1ubuntu3
2008-07-07 09:10:52 status half-configured poppler-utils 0.6.4-1ubuntu3
2008-07-07 09:10:52 status installed poppler-utils 0.6.4-1ubuntu3
2008-07-07 09:10:52 configure update-notifier-common 0.70.8 0.70.8
2008-07-07 09:10:52 status unpacked update-notifier-common 0.70.8
2008-07-07 09:10:52 status unpacked update-notifier-common 0.70.8
2008-07-07 09:10:52 status unpacked update-notifier-common 0.70.8
2008-07-07 09:10:52 status unpacked update-notifier-common 0.70.8
2008-07-07 09:10:52 status unpacked update-notifier-common 0.70.8
2008-07-07 09:10:52 status half-configured update-notifier-common 0.70.8
2008-07-07 09:10:52 status installed update-notifier-common 0.70.8
2008-07-07 09:10:52 configure update-notifier 0.70.8 0.70.8
2008-07-07 09:10:52 status unpacked update-notifier 0.70.8
2008-07-07 09:10:52 status unpacked update-notifier 0.70.8
2008-07-07 09:10:52 status half-configured update-notifier 0.70.8
2008-07-07 09:10:52 status installed update-notifier 0.70.8
2008-07-07 09:10:52 configure xserver-xorg-video-intel 2:2.2.1-1ubuntu13.5 2:2.2.1-1ubuntu13.5
2008-07-07 09:10:52 status unpacked xserver-xorg-video-intel 2:2.2.1-1ubuntu13.5
2008-07-07 09:10:52 status half-configured xserver-xorg-video-intel 2:2.2.1-1ubuntu13.5
2008-07-07 09:10:52 status installed xserver-xorg-video-intel 2:2.2.1-1ubuntu13.5
2008-07-07 09:10:52 trigproc libc6 2.7-10ubuntu3 2.7-10ubuntu3
2008-07-07 09:10:52 status half-configured libc6 2.7-10ubuntu3
2008-07-07 09:10:53 status installed libc6 2.7-10ubuntu3

---


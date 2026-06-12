---
title: "CPU Always 100%, why?"
date: 2015-08-27
forum: General Help
---

### Post by 171742 on 2015-08-27
Hi,

I got ubuntu 14.4 lts on 

[http://deals.epcusa.com/hp-compaq-6910p-hstnn-c31c-14-1-inch-notebook-windows-7-pro-32-bit-core-2-duo-2-0ghz-80-gb-2-gb-dvd-rw-grade-b-minor-cosmetic-wifi-windows-vista-business-coa](http://deals.epcusa.com/hp-compaq-6910p-hstnn-c31c-14-1-inch-notebook-windows-7-pro-32-bit-core-2-duo-2-0ghz-80-gb-2-gb-dvd-rw-grade-b-minor-cosmetic-wifi-windows-vista-business-coa).

The problem is right that, screenshots attached. Log also down. What is the cause?

I found this: 

[http://askubuntu.com/questions/176565/why-does-kworker-cpu-usage-get-so-high](http://askubuntu.com/questions/176565/why-does-kworker-cpu-usage-get-so-high)

but it goes way over my skill to fix. 

Any ideas?

Thanks!


LOG:

```
2015-08-11 15:16:42 startup packages remove
2015-08-11 15:16:42 status installed hddtemp:amd64 0.3-beta15-52
2015-08-11 15:16:44 remove hddtemp:amd64 0.3-beta15-52 <none>
2015-08-11 15:16:44 status half-configured hddtemp:amd64 0.3-beta15-52
2015-08-11 15:16:44 status half-installed hddtemp:amd64 0.3-beta15-52
2015-08-11 15:16:44 status triggers-pending man-db:amd64 2.6.7.1-1ubuntu1
2015-08-11 15:16:44 status config-files hddtemp:amd64 0.3-beta15-52
2015-08-11 15:16:44 status config-files hddtemp:amd64 0.3-beta15-52
2015-08-11 15:16:44 status installed psensor:amd64 0.8.0.3-1ubuntu3
2015-08-11 15:16:44 remove psensor:amd64 0.8.0.3-1ubuntu3 <none>
2015-08-11 15:16:44 status half-configured psensor:amd64 0.8.0.3-1ubuntu3
2015-08-11 15:16:44 status half-installed psensor:amd64 0.8.0.3-1ubuntu3
2015-08-11 15:16:44 status triggers-pending mime-support:all 3.54ubuntu1.1
2015-08-11 15:16:44 status triggers-pending gnome-menus:amd64 3.10.1-0ubuntu2
2015-08-11 15:16:44 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu1
2015-08-11 15:16:44 status half-installed psensor:amd64 0.8.0.3-1ubuntu3
2015-08-11 15:16:44 status triggers-pending bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-08-11 15:16:44 status half-installed psensor:amd64 0.8.0.3-1ubuntu3
2015-08-11 15:16:44 status triggers-pending gconf2:amd64 3.2.6-0ubuntu2
2015-08-11 15:16:44 status half-installed psensor:amd64 0.8.0.3-1ubuntu3
2015-08-11 15:16:44 status triggers-pending hicolor-icon-theme:all 0.13-1
2015-08-11 15:16:44 status half-installed psensor:amd64 0.8.0.3-1ubuntu3
2015-08-11 15:16:44 status config-files psensor:amd64 0.8.0.3-1ubuntu3
2015-08-11 15:16:44 status config-files psensor:amd64 0.8.0.3-1ubuntu3
2015-08-11 15:16:44 status installed psensor-common:all 0.8.0.3-1ubuntu3
2015-08-11 15:16:44 remove psensor-common:all 0.8.0.3-1ubuntu3 <none>
2015-08-11 15:16:44 status half-configured psensor-common:all 0.8.0.3-1ubuntu3
2015-08-11 15:16:44 status half-installed psensor-common:all 0.8.0.3-1ubuntu3
2015-08-11 15:16:44 status config-files psensor-common:all 0.8.0.3-1ubuntu3
2015-08-11 15:16:44 status config-files psensor-common:all 0.8.0.3-1ubuntu3
2015-08-11 15:16:44 status config-files psensor-common:all 0.8.0.3-1ubuntu3
2015-08-11 15:16:44 status not-installed psensor-common:all <none>
2015-08-11 15:16:44 trigproc man-db:amd64 2.6.7.1-1ubuntu1 <none>
2015-08-11 15:16:44 status half-configured man-db:amd64 2.6.7.1-1ubuntu1
2015-08-11 15:16:45 status installed man-db:amd64 2.6.7.1-1ubuntu1
2015-08-11 15:16:45 trigproc mime-support:all 3.54ubuntu1.1 <none>
2015-08-11 15:16:45 status half-configured mime-support:all 3.54ubuntu1.1
2015-08-11 15:16:45 status installed mime-support:all 3.54ubuntu1.1
2015-08-11 15:16:45 trigproc gnome-menus:amd64 3.10.1-0ubuntu2 <none>
2015-08-11 15:16:45 status half-configured gnome-menus:amd64 3.10.1-0ubuntu2
2015-08-11 15:16:45 status installed gnome-menus:amd64 3.10.1-0ubuntu2
2015-08-11 15:16:45 trigproc desktop-file-utils:amd64 0.22-1ubuntu1 <none>
2015-08-11 15:16:45 status half-configured desktop-file-utils:amd64 0.22-1ubuntu1
2015-08-11 15:16:45 status installed desktop-file-utils:amd64 0.22-1ubuntu1
2015-08-11 15:16:45 trigproc bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1 <none>
2015-08-11 15:16:45 status half-configured bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-08-11 15:16:45 status installed bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-08-11 15:16:45 trigproc gconf2:amd64 3.2.6-0ubuntu2 <none>
2015-08-11 15:16:45 status half-configured gconf2:amd64 3.2.6-0ubuntu2
2015-08-11 15:16:46 status installed gconf2:amd64 3.2.6-0ubuntu2
2015-08-11 15:16:46 trigproc hicolor-icon-theme:all 0.13-1 <none>
2015-08-11 15:16:46 status half-configured hicolor-icon-theme:all 0.13-1
2015-08-11 15:16:47 status installed hicolor-icon-theme:all 0.13-1
2015-08-15 00:45:32 startup archives unpack
2015-08-15 00:45:35 upgrade tzdata-java:all 2015d-0ubuntu0.14.04 2015f-0ubuntu0.14.04
2015-08-15 00:45:35 status half-configured tzdata-java:all 2015d-0ubuntu0.14.04
2015-08-15 00:45:35 status unpacked tzdata-java:all 2015d-0ubuntu0.14.04
2015-08-15 00:45:35 status half-installed tzdata-java:all 2015d-0ubuntu0.14.04
2015-08-15 00:45:35 status half-installed tzdata-java:all 2015d-0ubuntu0.14.04
2015-08-15 00:45:35 status unpacked tzdata-java:all 2015f-0ubuntu0.14.04
2015-08-15 00:45:35 status unpacked tzdata-java:all 2015f-0ubuntu0.14.04
2015-08-15 00:45:35 upgrade tzdata:all 2015d-0ubuntu0.14.04 2015f-0ubuntu0.14.04
2015-08-15 00:45:35 status half-configured tzdata:all 2015d-0ubuntu0.14.04
2015-08-15 00:45:35 status unpacked tzdata:all 2015d-0ubuntu0.14.04
2015-08-15 00:45:35 status half-installed tzdata:all 2015d-0ubuntu0.14.04
2015-08-15 00:45:36 status half-installed tzdata:all 2015d-0ubuntu0.14.04
2015-08-15 00:45:36 status unpacked tzdata:all 2015f-0ubuntu0.14.04
2015-08-15 00:45:36 status unpacked tzdata:all 2015f-0ubuntu0.14.04
2015-08-15 00:45:36 startup packages configure
2015-08-15 00:45:36 configure tzdata:all 2015f-0ubuntu0.14.04 <none>
2015-08-15 00:45:36 status unpacked tzdata:all 2015f-0ubuntu0.14.04
2015-08-15 00:45:36 status half-configured tzdata:all 2015f-0ubuntu0.14.04
2015-08-15 00:45:36 status installed tzdata:all 2015f-0ubuntu0.14.04
2015-08-15 00:45:37 startup archives unpack
2015-08-15 00:45:38 upgrade openssh-client:amd64 1:6.6p1-2ubuntu2 1:6.6p1-2ubuntu2.2
2015-08-15 00:45:38 status half-configured openssh-client:amd64 1:6.6p1-2ubuntu2
2015-08-15 00:45:38 status unpacked openssh-client:amd64 1:6.6p1-2ubuntu2
2015-08-15 00:45:38 status half-installed openssh-client:amd64 1:6.6p1-2ubuntu2
2015-08-15 00:45:38 status triggers-pending man-db:amd64 2.6.7.1-1ubuntu1
2015-08-15 00:45:39 status half-installed openssh-client:amd64 1:6.6p1-2ubuntu2
2015-08-15 00:45:39 status unpacked openssh-client:amd64 1:6.6p1-2ubuntu2.2
2015-08-15 00:45:39 status unpacked openssh-client:amd64 1:6.6p1-2ubuntu2.2
2015-08-15 00:45:39 upgrade firefox:amd64 39.0.3+build2-0ubuntu0.14.04.1 40.0+build4-0ubuntu0.14.04.1
2015-08-15 00:45:39 status half-configured firefox:amd64 39.0.3+build2-0ubuntu0.14.04.1
2015-08-15 00:45:39 status unpacked firefox:amd64 39.0.3+build2-0ubuntu0.14.04.1
2015-08-15 00:45:39 status half-installed firefox:amd64 39.0.3+build2-0ubuntu0.14.04.1
2015-08-15 00:45:39 status triggers-pending mime-support:all 3.54ubuntu1.1
2015-08-15 00:45:39 status triggers-pending gnome-menus:amd64 3.10.1-0ubuntu2
2015-08-15 00:45:39 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu1
2015-08-15 00:45:39 status half-installed firefox:amd64 39.0.3+build2-0ubuntu0.14.04.1
2015-08-15 00:45:39 status triggers-pending bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-08-15 00:45:39 status half-installed firefox:amd64 39.0.3+build2-0ubuntu0.14.04.1
2015-08-15 00:45:43 status half-installed firefox:amd64 39.0.3+build2-0ubuntu0.14.04.1
2015-08-15 00:45:44 status unpacked firefox:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-15 00:45:44 status unpacked firefox:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-15 00:45:44 upgrade firefox-locale-de:amd64 39.0.3+build2-0ubuntu0.14.04.1 40.0+build4-0ubuntu0.14.04.1
2015-08-15 00:45:44 status half-configured firefox-locale-de:amd64 39.0.3+build2-0ubuntu0.14.04.1
2015-08-15 00:45:44 status unpacked firefox-locale-de:amd64 39.0.3+build2-0ubuntu0.14.04.1
2015-08-15 00:45:44 status half-installed firefox-locale-de:amd64 39.0.3+build2-0ubuntu0.14.04.1
2015-08-15 00:45:44 status half-installed firefox-locale-de:amd64 39.0.3+build2-0ubuntu0.14.04.1
2015-08-15 00:45:44 status unpacked firefox-locale-de:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-15 00:45:44 status unpacked firefox-locale-de:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-15 00:45:44 upgrade firefox-locale-en:amd64 39.0.3+build2-0ubuntu0.14.04.1 40.0+build4-0ubuntu0.14.04.1
2015-08-15 00:45:44 status half-configured firefox-locale-en:amd64 39.0.3+build2-0ubuntu0.14.04.1
2015-08-15 00:45:44 status unpacked firefox-locale-en:amd64 39.0.3+build2-0ubuntu0.14.04.1
2015-08-15 00:45:44 status half-installed firefox-locale-en:amd64 39.0.3+build2-0ubuntu0.14.04.1
2015-08-15 00:45:44 status half-installed firefox-locale-en:amd64 39.0.3+build2-0ubuntu0.14.04.1
2015-08-15 00:45:44 status unpacked firefox-locale-en:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-15 00:45:44 status unpacked firefox-locale-en:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-15 00:45:45 upgrade flashplugin-installer:amd64 11.2.202.491ubuntu0.14.04.1 11.2.202.508ubuntu0.14.04.1
2015-08-15 00:45:45 status half-configured flashplugin-installer:amd64 11.2.202.491ubuntu0.14.04.1
2015-08-15 00:45:45 status unpacked flashplugin-installer:amd64 11.2.202.491ubuntu0.14.04.1
2015-08-15 00:45:45 status half-installed flashplugin-installer:amd64 11.2.202.491ubuntu0.14.04.1
2015-08-15 00:45:45 status triggers-pending update-notifier-common:all 0.154.1ubuntu1
2015-08-15 00:45:45 status half-installed flashplugin-installer:amd64 11.2.202.491ubuntu0.14.04.1
2015-08-15 00:45:45 status half-installed flashplugin-installer:amd64 11.2.202.491ubuntu0.14.04.1
2015-08-15 00:45:45 status unpacked flashplugin-installer:amd64 11.2.202.508ubuntu0.14.04.1
2015-08-15 00:45:45 status unpacked flashplugin-installer:amd64 11.2.202.508ubuntu0.14.04.1
2015-08-15 00:45:45 upgrade linux-firmware:all 1.127.14 1.127.15
2015-08-15 00:45:45 status half-configured linux-firmware:all 1.127.14
2015-08-15 00:45:45 status unpacked linux-firmware:all 1.127.14
2015-08-15 00:45:45 status half-installed linux-firmware:all 1.127.14
2015-08-15 00:45:49 status half-installed linux-firmware:all 1.127.14
2015-08-15 00:45:49 status unpacked linux-firmware:all 1.127.15
2015-08-15 00:45:49 status unpacked linux-firmware:all 1.127.15
2015-08-15 00:45:49 upgrade ssh-askpass-gnome:amd64 1:6.6p1-2ubuntu2 1:6.6p1-2ubuntu2.2
2015-08-15 00:45:49 status half-configured ssh-askpass-gnome:amd64 1:6.6p1-2ubuntu2
2015-08-15 00:45:49 status unpacked ssh-askpass-gnome:amd64 1:6.6p1-2ubuntu2
2015-08-15 00:45:49 status half-installed ssh-askpass-gnome:amd64 1:6.6p1-2ubuntu2
2015-08-15 00:45:49 status half-installed ssh-askpass-gnome:amd64 1:6.6p1-2ubuntu2
2015-08-15 00:45:49 status unpacked ssh-askpass-gnome:amd64 1:6.6p1-2ubuntu2.2
2015-08-15 00:45:49 status unpacked ssh-askpass-gnome:amd64 1:6.6p1-2ubuntu2.2
2015-08-15 00:45:49 upgrade xul-ext-ubufox:all 3.0-0ubuntu0.14.04.1 3.1-0ubuntu0.14.04.1
2015-08-15 00:45:49 status half-configured xul-ext-ubufox:all 3.0-0ubuntu0.14.04.1
2015-08-15 00:45:49 status unpacked xul-ext-ubufox:all 3.0-0ubuntu0.14.04.1
2015-08-15 00:45:49 status half-installed xul-ext-ubufox:all 3.0-0ubuntu0.14.04.1
2015-08-15 00:45:50 status half-installed xul-ext-ubufox:all 3.0-0ubuntu0.14.04.1
2015-08-15 00:45:50 status unpacked xul-ext-ubufox:all 3.1-0ubuntu0.14.04.1
2015-08-15 00:45:50 status unpacked xul-ext-ubufox:all 3.1-0ubuntu0.14.04.1
2015-08-15 00:45:50 trigproc man-db:amd64 2.6.7.1-1ubuntu1 2.6.7.1-1ubuntu1
2015-08-15 00:45:50 status half-configured man-db:amd64 2.6.7.1-1ubuntu1
2015-08-15 00:45:51 status installed man-db:amd64 2.6.7.1-1ubuntu1
2015-08-15 00:45:51 trigproc mime-support:all 3.54ubuntu1.1 3.54ubuntu1.1
2015-08-15 00:45:51 status half-configured mime-support:all 3.54ubuntu1.1
2015-08-15 00:45:51 status installed mime-support:all 3.54ubuntu1.1
2015-08-15 00:45:51 trigproc gnome-menus:amd64 3.10.1-0ubuntu2 3.10.1-0ubuntu2
2015-08-15 00:45:51 status half-configured gnome-menus:amd64 3.10.1-0ubuntu2
2015-08-15 00:45:51 status installed gnome-menus:amd64 3.10.1-0ubuntu2
2015-08-15 00:45:51 trigproc desktop-file-utils:amd64 0.22-1ubuntu1 0.22-1ubuntu1
2015-08-15 00:45:51 status half-configured desktop-file-utils:amd64 0.22-1ubuntu1
2015-08-15 00:45:51 status installed desktop-file-utils:amd64 0.22-1ubuntu1
2015-08-15 00:45:51 trigproc bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1 0.5.1+14.04.20140409-0ubuntu1
2015-08-15 00:45:51 status half-configured bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-08-15 00:45:51 status installed bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-08-15 00:45:51 trigproc update-notifier-common:all 0.154.1ubuntu1 0.154.1ubuntu1
2015-08-15 00:45:51 status half-configured update-notifier-common:all 0.154.1ubuntu1
2015-08-15 00:46:20 status installed update-notifier-common:all 0.154.1ubuntu1
2015-08-15 00:46:20 startup packages configure
2015-08-15 00:46:20 configure tzdata-java:all 2015f-0ubuntu0.14.04 <none>
2015-08-15 00:46:20 status unpacked tzdata-java:all 2015f-0ubuntu0.14.04
2015-08-15 00:46:20 status half-configured tzdata-java:all 2015f-0ubuntu0.14.04
2015-08-15 00:46:20 status installed tzdata-java:all 2015f-0ubuntu0.14.04
2015-08-15 00:46:20 configure openssh-client:amd64 1:6.6p1-2ubuntu2.2 <none>
2015-08-15 00:46:20 status unpacked openssh-client:amd64 1:6.6p1-2ubuntu2.2
2015-08-15 00:46:20 status unpacked openssh-client:amd64 1:6.6p1-2ubuntu2.2
2015-08-15 00:46:20 status unpacked openssh-client:amd64 1:6.6p1-2ubuntu2.2
2015-08-15 00:46:20 status half-configured openssh-client:amd64 1:6.6p1-2ubuntu2.2
2015-08-15 00:46:20 status installed openssh-client:amd64 1:6.6p1-2ubuntu2.2
2015-08-15 00:46:20 configure firefox:amd64 40.0+build4-0ubuntu0.14.04.1 <none>
2015-08-15 00:46:20 status unpacked firefox:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-15 00:46:20 status unpacked firefox:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-15 00:46:20 status unpacked firefox:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-15 00:46:20 status unpacked firefox:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-15 00:46:20 status unpacked firefox:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-15 00:46:20 status half-configured firefox:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-15 00:46:20 status installed firefox:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-15 00:46:20 configure firefox-locale-de:amd64 40.0+build4-0ubuntu0.14.04.1 <none>
2015-08-15 00:46:20 status unpacked firefox-locale-de:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-15 00:46:20 status half-configured firefox-locale-de:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-15 00:46:20 status installed firefox-locale-de:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-15 00:46:20 configure firefox-locale-en:amd64 40.0+build4-0ubuntu0.14.04.1 <none>
2015-08-15 00:46:20 status unpacked firefox-locale-en:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-15 00:46:20 status half-configured firefox-locale-en:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-15 00:46:20 status installed firefox-locale-en:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-15 00:46:20 configure flashplugin-installer:amd64 11.2.202.508ubuntu0.14.04.1 <none>
2015-08-15 00:46:20 status unpacked flashplugin-installer:amd64 11.2.202.508ubuntu0.14.04.1
2015-08-15 00:46:20 status half-configured flashplugin-installer:amd64 11.2.202.508ubuntu0.14.04.1
2015-08-15 00:46:21 status installed flashplugin-installer:amd64 11.2.202.508ubuntu0.14.04.1
2015-08-15 00:46:21 configure linux-firmware:all 1.127.15 <none>
2015-08-15 00:46:21 status unpacked linux-firmware:all 1.127.15
2015-08-15 00:46:21 status half-configured linux-firmware:all 1.127.15
2015-08-15 00:46:21 status installed linux-firmware:all 1.127.15
2015-08-15 00:46:21 configure ssh-askpass-gnome:amd64 1:6.6p1-2ubuntu2.2 <none>
2015-08-15 00:46:21 status unpacked ssh-askpass-gnome:amd64 1:6.6p1-2ubuntu2.2
2015-08-15 00:46:21 status half-configured ssh-askpass-gnome:amd64 1:6.6p1-2ubuntu2.2
2015-08-15 00:46:21 status installed ssh-askpass-gnome:amd64 1:6.6p1-2ubuntu2.2
2015-08-15 00:46:21 configure xul-ext-ubufox:all 3.1-0ubuntu0.14.04.1 <none>
2015-08-15 00:46:21 status unpacked xul-ext-ubufox:all 3.1-0ubuntu0.14.04.1
2015-08-15 00:46:21 status half-configured xul-ext-ubufox:all 3.1-0ubuntu0.14.04.1
2015-08-15 00:46:21 status installed xul-ext-ubufox:all 3.1-0ubuntu0.14.04.1
2015-08-18 17:30:41 startup archives unpack
2015-08-18 17:30:43 install gir1.2-gdesktopenums-3.0:amd64 <none> 3.10.1-0ubuntu1
2015-08-18 17:30:43 status half-installed gir1.2-gdesktopenums-3.0:amd64 3.10.1-0ubuntu1
2015-08-18 17:30:43 status unpacked gir1.2-gdesktopenums-3.0:amd64 3.10.1-0ubuntu1
2015-08-18 17:30:43 status unpacked gir1.2-gdesktopenums-3.0:amd64 3.10.1-0ubuntu1
2015-08-18 17:30:43 install gir1.2-gnomedesktop-3.0:amd64 <none> 3.8.4-0ubuntu3.1
2015-08-18 17:30:43 status half-installed gir1.2-gnomedesktop-3.0:amd64 3.8.4-0ubuntu3.1
2015-08-18 17:30:43 status unpacked gir1.2-gnomedesktop-3.0:amd64 3.8.4-0ubuntu3.1
2015-08-18 17:30:43 status unpacked gir1.2-gnomedesktop-3.0:amd64 3.8.4-0ubuntu3.1
2015-08-18 17:30:43 install gnome-shell-common:all <none> 3.10.4-0ubuntu5.2
2015-08-18 17:30:43 status half-installed gnome-shell-common:all 3.10.4-0ubuntu5.2
2015-08-18 17:30:43 status triggers-pending libglib2.0-0:i386 2.40.2-0ubuntu1
2015-08-18 17:30:43 status half-installed gnome-shell-common:all 3.10.4-0ubuntu5.2
2015-08-18 17:30:43 status triggers-pending libglib2.0-0:amd64 2.40.2-0ubuntu1
2015-08-18 17:30:43 status half-installed gnome-shell-common:all 3.10.4-0ubuntu5.2
2015-08-18 17:30:43 status triggers-pending gconf2:amd64 3.2.6-0ubuntu2
2015-08-18 17:30:43 status half-installed gnome-shell-common:all 3.10.4-0ubuntu5.2
2015-08-18 17:30:44 status unpacked gnome-shell-common:all 3.10.4-0ubuntu5.2
2015-08-18 17:30:44 status unpacked gnome-shell-common:all 3.10.4-0ubuntu5.2
2015-08-18 17:30:44 install gnome-tweak-tool:all <none> 3.10.1-2ubuntu1
2015-08-18 17:30:44 status half-installed gnome-tweak-tool:all 3.10.1-2ubuntu1
2015-08-18 17:30:44 status triggers-pending mime-support:all 3.54ubuntu1.1
2015-08-18 17:30:44 status triggers-pending gnome-menus:amd64 3.10.1-0ubuntu2
2015-08-18 17:30:44 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu1
2015-08-18 17:30:44 status half-installed gnome-tweak-tool:all 3.10.1-2ubuntu1
2015-08-18 17:30:44 status triggers-pending bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-08-18 17:30:44 status half-installed gnome-tweak-tool:all 3.10.1-2ubuntu1
2015-08-18 17:30:44 status triggers-pending hicolor-icon-theme:all 0.13-1
2015-08-18 17:30:44 status half-installed gnome-tweak-tool:all 3.10.1-2ubuntu1
2015-08-18 17:30:44 status unpacked gnome-tweak-tool:all 3.10.1-2ubuntu1
2015-08-18 17:30:44 status unpacked gnome-tweak-tool:all 3.10.1-2ubuntu1
2015-08-18 17:30:44 trigproc libglib2.0-0:i386 2.40.2-0ubuntu1 2.40.2-0ubuntu1
2015-08-18 17:30:44 status half-configured libglib2.0-0:i386 2.40.2-0ubuntu1
2015-08-18 17:30:44 status installed libglib2.0-0:i386 2.40.2-0ubuntu1
2015-08-18 17:30:44 trigproc libglib2.0-0:amd64 2.40.2-0ubuntu1 2.40.2-0ubuntu1
2015-08-18 17:30:44 status half-configured libglib2.0-0:amd64 2.40.2-0ubuntu1
2015-08-18 17:30:44 status installed libglib2.0-0:amd64 2.40.2-0ubuntu1
2015-08-18 17:30:44 trigproc gconf2:amd64 3.2.6-0ubuntu2 3.2.6-0ubuntu2
2015-08-18 17:30:44 status half-configured gconf2:amd64 3.2.6-0ubuntu2
2015-08-18 17:30:44 status installed gconf2:amd64 3.2.6-0ubuntu2
2015-08-18 17:30:44 trigproc mime-support:all 3.54ubuntu1.1 3.54ubuntu1.1
2015-08-18 17:30:44 status half-configured mime-support:all 3.54ubuntu1.1
2015-08-18 17:30:44 status installed mime-support:all 3.54ubuntu1.1
2015-08-18 17:30:44 trigproc gnome-menus:amd64 3.10.1-0ubuntu2 3.10.1-0ubuntu2
2015-08-18 17:30:44 status half-configured gnome-menus:amd64 3.10.1-0ubuntu2
2015-08-18 17:30:44 status installed gnome-menus:amd64 3.10.1-0ubuntu2
2015-08-18 17:30:44 trigproc desktop-file-utils:amd64 0.22-1ubuntu1 0.22-1ubuntu1
2015-08-18 17:30:44 status half-configured desktop-file-utils:amd64 0.22-1ubuntu1
2015-08-18 17:30:45 status installed desktop-file-utils:amd64 0.22-1ubuntu1
2015-08-18 17:30:45 trigproc bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1 0.5.1+14.04.20140409-0ubuntu1
2015-08-18 17:30:45 status half-configured bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-08-18 17:30:45 status installed bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-08-18 17:30:45 trigproc hicolor-icon-theme:all 0.13-1 0.13-1
2015-08-18 17:30:45 status half-configured hicolor-icon-theme:all 0.13-1
2015-08-18 17:30:46 status installed hicolor-icon-theme:all 0.13-1
2015-08-18 17:30:46 startup packages configure
2015-08-18 17:30:46 configure gir1.2-gdesktopenums-3.0:amd64 3.10.1-0ubuntu1 <none>
2015-08-18 17:30:46 status unpacked gir1.2-gdesktopenums-3.0:amd64 3.10.1-0ubuntu1
2015-08-18 17:30:46 status half-configured gir1.2-gdesktopenums-3.0:amd64 3.10.1-0ubuntu1
2015-08-18 17:30:46 status installed gir1.2-gdesktopenums-3.0:amd64 3.10.1-0ubuntu1
2015-08-18 17:30:46 configure gir1.2-gnomedesktop-3.0:amd64 3.8.4-0ubuntu3.1 <none>
2015-08-18 17:30:46 status unpacked gir1.2-gnomedesktop-3.0:amd64 3.8.4-0ubuntu3.1
2015-08-18 17:30:46 status half-configured gir1.2-gnomedesktop-3.0:amd64 3.8.4-0ubuntu3.1
2015-08-18 17:30:46 status installed gir1.2-gnomedesktop-3.0:amd64 3.8.4-0ubuntu3.1
2015-08-18 17:30:46 configure gnome-shell-common:all 3.10.4-0ubuntu5.2 <none>
2015-08-18 17:30:46 status unpacked gnome-shell-common:all 3.10.4-0ubuntu5.2
2015-08-18 17:30:46 status half-configured gnome-shell-common:all 3.10.4-0ubuntu5.2
2015-08-18 17:30:46 status installed gnome-shell-common:all 3.10.4-0ubuntu5.2
2015-08-18 17:30:46 configure gnome-tweak-tool:all 3.10.1-2ubuntu1 <none>
2015-08-18 17:30:46 status unpacked gnome-tweak-tool:all 3.10.1-2ubuntu1
2015-08-18 17:30:46 status half-configured gnome-tweak-tool:all 3.10.1-2ubuntu1
2015-08-18 17:30:46 status installed gnome-tweak-tool:all 3.10.1-2ubuntu1
2015-08-19 01:27:32 startup archives unpack
2015-08-19 01:27:34 upgrade libsnmp-base:all 5.7.2~dfsg-8.1ubuntu3 5.7.2~dfsg-8.1ubuntu3.1
2015-08-19 01:27:34 status half-configured libsnmp-base:all 5.7.2~dfsg-8.1ubuntu3
2015-08-19 01:27:34 status unpacked libsnmp-base:all 5.7.2~dfsg-8.1ubuntu3
2015-08-19 01:27:34 status half-installed libsnmp-base:all 5.7.2~dfsg-8.1ubuntu3
2015-08-19 01:27:34 status triggers-pending man-db:amd64 2.6.7.1-1ubuntu1
2015-08-19 01:27:34 status half-installed libsnmp-base:all 5.7.2~dfsg-8.1ubuntu3
2015-08-19 01:27:35 status unpacked libsnmp-base:all 5.7.2~dfsg-8.1ubuntu3.1
2015-08-19 01:27:35 status unpacked libsnmp-base:all 5.7.2~dfsg-8.1ubuntu3.1
2015-08-19 01:27:35 upgrade libsnmp30:amd64 5.7.2~dfsg-8.1ubuntu3 5.7.2~dfsg-8.1ubuntu3.1
2015-08-19 01:27:35 status half-configured libsnmp30:amd64 5.7.2~dfsg-8.1ubuntu3
2015-08-19 01:27:35 status unpacked libsnmp30:amd64 5.7.2~dfsg-8.1ubuntu3
2015-08-19 01:27:35 status half-installed libsnmp30:amd64 5.7.2~dfsg-8.1ubuntu3
2015-08-19 01:27:35 status half-installed libsnmp30:amd64 5.7.2~dfsg-8.1ubuntu3
2015-08-19 01:27:35 status unpacked libsnmp30:amd64 5.7.2~dfsg-8.1ubuntu3.1
2015-08-19 01:27:35 status unpacked libsnmp30:amd64 5.7.2~dfsg-8.1ubuntu3.1
2015-08-19 01:27:35 install linux-image-3.13.0-62-generic:amd64 <none> 3.13.0-62.102
2015-08-19 01:27:35 status half-installed linux-image-3.13.0-62-generic:amd64 3.13.0-62.102
2015-08-19 01:27:38 status unpacked linux-image-3.13.0-62-generic:amd64 3.13.0-62.102
2015-08-19 01:27:38 status unpacked linux-image-3.13.0-62-generic:amd64 3.13.0-62.102
2015-08-19 01:27:38 upgrade openssh-client:amd64 1:6.6p1-2ubuntu2.2 1:6.6p1-2ubuntu2.3
2015-08-19 01:27:38 status half-configured openssh-client:amd64 1:6.6p1-2ubuntu2.2
2015-08-19 01:27:38 status unpacked openssh-client:amd64 1:6.6p1-2ubuntu2.2
2015-08-19 01:27:38 status half-installed openssh-client:amd64 1:6.6p1-2ubuntu2.2
2015-08-19 01:27:39 status half-installed openssh-client:amd64 1:6.6p1-2ubuntu2.2
2015-08-19 01:27:39 status unpacked openssh-client:amd64 1:6.6p1-2ubuntu2.3
2015-08-19 01:27:39 status unpacked openssh-client:amd64 1:6.6p1-2ubuntu2.3
2015-08-19 01:27:39 install linux-image-extra-3.13.0-62-generic:amd64 <none> 3.13.0-62.102
2015-08-19 01:27:39 status half-installed linux-image-extra-3.13.0-62-generic:amd64 3.13.0-62.102
2015-08-19 01:27:48 status unpacked linux-image-extra-3.13.0-62-generic:amd64 3.13.0-62.102
2015-08-19 01:27:48 status unpacked linux-image-extra-3.13.0-62-generic:amd64 3.13.0-62.102
2015-08-19 01:27:49 upgrade linux-generic:amd64 3.13.0.61.68 3.13.0.62.69
2015-08-19 01:27:49 status half-configured linux-generic:amd64 3.13.0.61.68
2015-08-19 01:27:49 status unpacked linux-generic:amd64 3.13.0.61.68
2015-08-19 01:27:49 status half-installed linux-generic:amd64 3.13.0.61.68
2015-08-19 01:27:49 status half-installed linux-generic:amd64 3.13.0.61.68
2015-08-19 01:27:49 status unpacked linux-generic:amd64 3.13.0.62.69
2015-08-19 01:27:49 status unpacked linux-generic:amd64 3.13.0.62.69
2015-08-19 01:27:49 upgrade linux-image-generic:amd64 3.13.0.61.68 3.13.0.62.69
2015-08-19 01:27:49 status half-configured linux-image-generic:amd64 3.13.0.61.68
2015-08-19 01:27:49 status unpacked linux-image-generic:amd64 3.13.0.61.68
2015-08-19 01:27:49 status half-installed linux-image-generic:amd64 3.13.0.61.68
2015-08-19 01:27:49 status half-installed linux-image-generic:amd64 3.13.0.61.68
2015-08-19 01:27:49 status unpacked linux-image-generic:amd64 3.13.0.62.69
2015-08-19 01:27:49 status unpacked linux-image-generic:amd64 3.13.0.62.69
2015-08-19 01:27:49 install linux-headers-3.13.0-62:all <none> 3.13.0-62.102
2015-08-19 01:27:49 status half-installed linux-headers-3.13.0-62:all 3.13.0-62.102
2015-08-19 01:27:57 status unpacked linux-headers-3.13.0-62:all 3.13.0-62.102
2015-08-19 01:27:57 status unpacked linux-headers-3.13.0-62:all 3.13.0-62.102
2015-08-19 01:27:57 install linux-headers-3.13.0-62-generic:amd64 <none> 3.13.0-62.102
2015-08-19 01:27:57 status half-installed linux-headers-3.13.0-62-generic:amd64 3.13.0-62.102
2015-08-19 01:28:01 status unpacked linux-headers-3.13.0-62-generic:amd64 3.13.0-62.102
2015-08-19 01:28:01 status unpacked linux-headers-3.13.0-62-generic:amd64 3.13.0-62.102
2015-08-19 01:28:01 upgrade linux-headers-generic:amd64 3.13.0.61.68 3.13.0.62.69
2015-08-19 01:28:01 status half-configured linux-headers-generic:amd64 3.13.0.61.68
2015-08-19 01:28:01 status unpacked linux-headers-generic:amd64 3.13.0.61.68
2015-08-19 01:28:01 status half-installed linux-headers-generic:amd64 3.13.0.61.68
2015-08-19 01:28:01 status half-installed linux-headers-generic:amd64 3.13.0.61.68
2015-08-19 01:28:01 status unpacked linux-headers-generic:amd64 3.13.0.62.69
2015-08-19 01:28:01 status unpacked linux-headers-generic:amd64 3.13.0.62.69
2015-08-19 01:28:01 upgrade linux-libc-dev:amd64 3.13.0-61.100 3.13.0-62.102
2015-08-19 01:28:01 status half-configured linux-libc-dev:amd64 3.13.0-61.100
2015-08-19 01:28:01 status unpacked linux-libc-dev:amd64 3.13.0-61.100
2015-08-19 01:28:01 status half-installed linux-libc-dev:amd64 3.13.0-61.100
2015-08-19 01:28:02 status half-installed linux-libc-dev:amd64 3.13.0-61.100
2015-08-19 01:28:02 status unpacked linux-libc-dev:amd64 3.13.0-62.102
2015-08-19 01:28:02 status unpacked linux-libc-dev:amd64 3.13.0-62.102
2015-08-19 01:28:02 upgrade ssh-askpass-gnome:amd64 1:6.6p1-2ubuntu2.2 1:6.6p1-2ubuntu2.3
2015-08-19 01:28:02 status half-configured ssh-askpass-gnome:amd64 1:6.6p1-2ubuntu2.2
2015-08-19 01:28:02 status unpacked ssh-askpass-gnome:amd64 1:6.6p1-2ubuntu2.2
2015-08-19 01:28:02 status half-installed ssh-askpass-gnome:amd64 1:6.6p1-2ubuntu2.2
2015-08-19 01:28:02 status half-installed ssh-askpass-gnome:amd64 1:6.6p1-2ubuntu2.2
2015-08-19 01:28:02 status unpacked ssh-askpass-gnome:amd64 1:6.6p1-2ubuntu2.3
2015-08-19 01:28:02 status unpacked ssh-askpass-gnome:amd64 1:6.6p1-2ubuntu2.3
2015-08-19 01:28:02 trigproc man-db:amd64 2.6.7.1-1ubuntu1 2.6.7.1-1ubuntu1
2015-08-19 01:28:02 status half-configured man-db:amd64 2.6.7.1-1ubuntu1
2015-08-19 01:28:03 status installed man-db:amd64 2.6.7.1-1ubuntu1
2015-08-19 01:28:03 startup packages configure
2015-08-19 01:28:03 configure libsnmp-base:all 5.7.2~dfsg-8.1ubuntu3.1 <none>
2015-08-19 01:28:03 status unpacked libsnmp-base:all 5.7.2~dfsg-8.1ubuntu3.1
2015-08-19 01:28:03 status half-configured libsnmp-base:all 5.7.2~dfsg-8.1ubuntu3.1
2015-08-19 01:28:03 status installed libsnmp-base:all 5.7.2~dfsg-8.1ubuntu3.1
2015-08-19 01:28:03 configure libsnmp30:amd64 5.7.2~dfsg-8.1ubuntu3.1 <none>
2015-08-19 01:28:03 status unpacked libsnmp30:amd64 5.7.2~dfsg-8.1ubuntu3.1
2015-08-19 01:28:03 status half-configured libsnmp30:amd64 5.7.2~dfsg-8.1ubuntu3.1
2015-08-19 01:28:03 status installed libsnmp30:amd64 5.7.2~dfsg-8.1ubuntu3.1
2015-08-19 01:28:03 status triggers-pending libc-bin:amd64 2.19-0ubuntu6.6
2015-08-19 01:28:03 configure linux-image-3.13.0-62-generic:amd64 3.13.0-62.102 <none>
2015-08-19 01:28:03 status unpacked linux-image-3.13.0-62-generic:amd64 3.13.0-62.102
2015-08-19 01:28:03 status half-configured linux-image-3.13.0-62-generic:amd64 3.13.0-62.102
2015-08-19 01:29:19 status installed linux-image-3.13.0-62-generic:amd64 3.13.0-62.102
2015-08-19 01:29:19 configure openssh-client:amd64 1:6.6p1-2ubuntu2.3 <none>
2015-08-19 01:29:19 status unpacked openssh-client:amd64 1:6.6p1-2ubuntu2.3
2015-08-19 01:29:19 status unpacked openssh-client:amd64 1:6.6p1-2ubuntu2.3
2015-08-19 01:29:19 status unpacked openssh-client:amd64 1:6.6p1-2ubuntu2.3
2015-08-19 01:29:19 status half-configured openssh-client:amd64 1:6.6p1-2ubuntu2.3
2015-08-19 01:29:19 status installed openssh-client:amd64 1:6.6p1-2ubuntu2.3
2015-08-19 01:29:19 configure linux-image-extra-3.13.0-62-generic:amd64 3.13.0-62.102 <none>
2015-08-19 01:29:19 status unpacked linux-image-extra-3.13.0-62-generic:amd64 3.13.0-62.102
2015-08-19 01:29:19 status half-configured linux-image-extra-3.13.0-62-generic:amd64 3.13.0-62.102
2015-08-19 01:29:36 status installed linux-image-extra-3.13.0-62-generic:amd64 3.13.0-62.102
2015-08-19 01:29:36 configure linux-image-generic:amd64 3.13.0.62.69 <none>
2015-08-19 01:29:36 status unpacked linux-image-generic:amd64 3.13.0.62.69
2015-08-19 01:29:36 status half-configured linux-image-generic:amd64 3.13.0.62.69
2015-08-19 01:29:36 status installed linux-image-generic:amd64 3.13.0.62.69
2015-08-19 01:29:36 configure linux-headers-3.13.0-62:all 3.13.0-62.102 <none>
2015-08-19 01:29:36 status unpacked linux-headers-3.13.0-62:all 3.13.0-62.102
2015-08-19 01:29:36 status half-configured linux-headers-3.13.0-62:all 3.13.0-62.102
2015-08-19 01:29:36 status installed linux-headers-3.13.0-62:all 3.13.0-62.102
2015-08-19 01:29:36 configure linux-headers-3.13.0-62-generic:amd64 3.13.0-62.102 <none>
2015-08-19 01:29:36 status unpacked linux-headers-3.13.0-62-generic:amd64 3.13.0-62.102
2015-08-19 01:29:36 status half-configured linux-headers-3.13.0-62-generic:amd64 3.13.0-62.102
2015-08-19 01:29:37 status installed linux-headers-3.13.0-62-generic:amd64 3.13.0-62.102
2015-08-19 01:29:37 configure linux-headers-generic:amd64 3.13.0.62.69 <none>
2015-08-19 01:29:37 status unpacked linux-headers-generic:amd64 3.13.0.62.69
2015-08-19 01:29:37 status half-configured linux-headers-generic:amd64 3.13.0.62.69
2015-08-19 01:29:37 status installed linux-headers-generic:amd64 3.13.0.62.69
2015-08-19 01:29:37 configure linux-generic:amd64 3.13.0.62.69 <none>
2015-08-19 01:29:37 status unpacked linux-generic:amd64 3.13.0.62.69
2015-08-19 01:29:37 status half-configured linux-generic:amd64 3.13.0.62.69
2015-08-19 01:29:37 status installed linux-generic:amd64 3.13.0.62.69
2015-08-19 01:29:37 configure linux-libc-dev:amd64 3.13.0-62.102 <none>
2015-08-19 01:29:37 status unpacked linux-libc-dev:amd64 3.13.0-62.102
2015-08-19 01:29:37 status half-configured linux-libc-dev:amd64 3.13.0-62.102
2015-08-19 01:29:37 status installed linux-libc-dev:amd64 3.13.0-62.102
2015-08-19 01:29:37 configure ssh-askpass-gnome:amd64 1:6.6p1-2ubuntu2.3 <none>
2015-08-19 01:29:37 status unpacked ssh-askpass-gnome:amd64 1:6.6p1-2ubuntu2.3
2015-08-19 01:29:37 status half-configured ssh-askpass-gnome:amd64 1:6.6p1-2ubuntu2.3
2015-08-19 01:29:37 status installed ssh-askpass-gnome:amd64 1:6.6p1-2ubuntu2.3
2015-08-19 01:29:37 trigproc libc-bin:amd64 2.19-0ubuntu6.6 <none>
2015-08-19 01:29:37 status half-configured libc-bin:amd64 2.19-0ubuntu6.6
2015-08-19 01:29:37 status installed libc-bin:amd64 2.19-0ubuntu6.6
2015-08-22 08:47:20 startup archives unpack
2015-08-22 08:47:22 upgrade chromium-browser-l10n:all 43.0.2357.130-0ubuntu0.14.04.1.1092 44.0.2403.89-0ubuntu0.14.04.1.1095
2015-08-22 08:47:22 status half-configured chromium-browser-l10n:all 43.0.2357.130-0ubuntu0.14.04.1.1092
2015-08-22 08:47:22 status unpacked chromium-browser-l10n:all 43.0.2357.130-0ubuntu0.14.04.1.1092
2015-08-22 08:47:22 status half-installed chromium-browser-l10n:all 43.0.2357.130-0ubuntu0.14.04.1.1092
2015-08-22 08:47:23 status half-installed chromium-browser-l10n:all 43.0.2357.130-0ubuntu0.14.04.1.1092
2015-08-22 08:47:23 status unpacked chromium-browser-l10n:all 44.0.2403.89-0ubuntu0.14.04.1.1095
2015-08-22 08:47:23 status unpacked chromium-browser-l10n:all 44.0.2403.89-0ubuntu0.14.04.1.1095
2015-08-22 08:47:23 upgrade chromium-browser:amd64 43.0.2357.130-0ubuntu0.14.04.1.1092 44.0.2403.89-0ubuntu0.14.04.1.1095
2015-08-22 08:47:23 status half-configured chromium-browser:amd64 43.0.2357.130-0ubuntu0.14.04.1.1092
2015-08-22 08:47:23 status unpacked chromium-browser:amd64 43.0.2357.130-0ubuntu0.14.04.1.1092
2015-08-22 08:47:23 status half-installed chromium-browser:amd64 43.0.2357.130-0ubuntu0.14.04.1.1092
2015-08-22 08:47:23 status triggers-pending mime-support:all 3.54ubuntu1.1
2015-08-22 08:47:23 status triggers-pending gnome-menus:amd64 3.10.1-0ubuntu2
2015-08-22 08:47:23 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu1
2015-08-22 08:47:23 status half-installed chromium-browser:amd64 43.0.2357.130-0ubuntu0.14.04.1.1092
2015-08-22 08:47:23 status triggers-pending bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-08-22 08:47:23 status half-installed chromium-browser:amd64 43.0.2357.130-0ubuntu0.14.04.1.1092
2015-08-22 08:47:23 status triggers-pending hicolor-icon-theme:all 0.13-1
2015-08-22 08:47:23 status half-installed chromium-browser:amd64 43.0.2357.130-0ubuntu0.14.04.1.1092
2015-08-22 08:47:23 status triggers-pending man-db:amd64 2.6.7.1-1ubuntu1
2015-08-22 08:47:30 status half-installed chromium-browser:amd64 43.0.2357.130-0ubuntu0.14.04.1.1092
2015-08-22 08:47:30 status unpacked chromium-browser:amd64 44.0.2403.89-0ubuntu0.14.04.1.1095
2015-08-22 08:47:30 status unpacked chromium-browser:amd64 44.0.2403.89-0ubuntu0.14.04.1.1095
2015-08-22 08:47:30 upgrade chromium-codecs-ffmpeg-extra:amd64 43.0.2357.130-0ubuntu0.14.04.1.1092 44.0.2403.89-0ubuntu0.14.04.1.1095
2015-08-22 08:47:30 status half-configured chromium-codecs-ffmpeg-extra:amd64 43.0.2357.130-0ubuntu0.14.04.1.1092
2015-08-22 08:47:30 status unpacked chromium-codecs-ffmpeg-extra:amd64 43.0.2357.130-0ubuntu0.14.04.1.1092
2015-08-22 08:47:30 status half-installed chromium-codecs-ffmpeg-extra:amd64 43.0.2357.130-0ubuntu0.14.04.1.1092
2015-08-22 08:47:30 status half-installed chromium-codecs-ffmpeg-extra:amd64 43.0.2357.130-0ubuntu0.14.04.1.1092
2015-08-22 08:47:30 status unpacked chromium-codecs-ffmpeg-extra:amd64 44.0.2403.89-0ubuntu0.14.04.1.1095
2015-08-22 08:47:30 status unpacked chromium-codecs-ffmpeg-extra:amd64 44.0.2403.89-0ubuntu0.14.04.1.1095
2015-08-22 08:47:30 upgrade firefox:amd64 40.0+build4-0ubuntu0.14.04.1 40.0+build4-0ubuntu0.14.04.4
2015-08-22 08:47:30 status half-configured firefox:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-22 08:47:30 status unpacked firefox:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-22 08:47:30 status half-installed firefox:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-22 08:47:30 status half-installed firefox:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-22 08:47:30 status half-installed firefox:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-22 08:47:34 status half-installed firefox:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-22 08:47:34 status unpacked firefox:amd64 40.0+build4-0ubuntu0.14.04.4
2015-08-22 08:47:34 status unpacked firefox:amd64 40.0+build4-0ubuntu0.14.04.4
2015-08-22 08:47:34 upgrade firefox-locale-de:amd64 40.0+build4-0ubuntu0.14.04.1 40.0+build4-0ubuntu0.14.04.4
2015-08-22 08:47:34 status half-configured firefox-locale-de:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-22 08:47:34 status unpacked firefox-locale-de:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-22 08:47:34 status half-installed firefox-locale-de:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-22 08:47:34 status half-installed firefox-locale-de:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-22 08:47:34 status unpacked firefox-locale-de:amd64 40.0+build4-0ubuntu0.14.04.4
2015-08-22 08:47:34 status unpacked firefox-locale-de:amd64 40.0+build4-0ubuntu0.14.04.4
2015-08-22 08:47:35 upgrade firefox-locale-en:amd64 40.0+build4-0ubuntu0.14.04.1 40.0+build4-0ubuntu0.14.04.4
2015-08-22 08:47:35 status half-configured firefox-locale-en:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-22 08:47:35 status unpacked firefox-locale-en:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-22 08:47:35 status half-installed firefox-locale-en:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-22 08:47:35 status half-installed firefox-locale-en:amd64 40.0+build4-0ubuntu0.14.04.1
2015-08-22 08:47:35 status unpacked firefox-locale-en:amd64 40.0+build4-0ubuntu0.14.04.4
2015-08-22 08:47:35 status unpacked firefox-locale-en:amd64 40.0+build4-0ubuntu0.14.04.4
2015-08-22 08:47:35 trigproc mime-support:all 3.54ubuntu1.1 3.54ubuntu1.1
2015-08-22 08:47:35 status half-configured mime-support:all 3.54ubuntu1.1
2015-08-22 08:47:35 status installed mime-support:all 3.54ubuntu1.1
2015-08-22 08:47:35 trigproc gnome-menus:amd64 3.10.1-0ubuntu2 3.10.1-0ubuntu2
2015-08-22 08:47:35 status half-configured gnome-menus:amd64 3.10.1-0ubuntu2
2015-08-22 08:47:35 status installed gnome-menus:amd64 3.10.1-0ubuntu2
2015-08-22 08:47:35 trigproc desktop-file-utils:amd64 0.22-1ubuntu1 0.22-1ubuntu1
2015-08-22 08:47:35 status half-configured desktop-file-utils:amd64 0.22-1ubuntu1
2015-08-22 08:47:35 status installed desktop-file-utils:amd64 0.22-1ubuntu1
2015-08-22 08:47:35 trigproc bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1 0.5.1+14.04.20140409-0ubuntu1
2015-08-22 08:47:35 status half-configured bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-08-22 08:47:35 status installed bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-08-22 08:47:35 trigproc hicolor-icon-theme:all 0.13-1 0.13-1
2015-08-22 08:47:35 status half-configured hicolor-icon-theme:all 0.13-1
2015-08-22 08:47:36 status installed hicolor-icon-theme:all 0.13-1
2015-08-22 08:47:36 trigproc man-db:amd64 2.6.7.1-1ubuntu1 2.6.7.1-1ubuntu1
2015-08-22 08:47:36 status half-configured man-db:amd64 2.6.7.1-1ubuntu1
2015-08-22 08:47:37 status installed man-db:amd64 2.6.7.1-1ubuntu1
2015-08-22 08:47:37 startup packages configure
2015-08-22 08:47:37 configure chromium-codecs-ffmpeg-extra:amd64 44.0.2403.89-0ubuntu0.14.04.1.1095 <none>
2015-08-22 08:47:37 status unpacked chromium-codecs-ffmpeg-extra:amd64 44.0.2403.89-0ubuntu0.14.04.1.1095
2015-08-22 08:47:37 status half-configured chromium-codecs-ffmpeg-extra:amd64 44.0.2403.89-0ubuntu0.14.04.1.1095
2015-08-22 08:47:37 status installed chromium-codecs-ffmpeg-extra:amd64 44.0.2403.89-0ubuntu0.14.04.1.1095
2015-08-22 08:47:37 configure chromium-browser:amd64 44.0.2403.89-0ubuntu0.14.04.1.1095 <none>
2015-08-22 08:47:37 status unpacked chromium-browser:amd64 44.0.2403.89-0ubuntu0.14.04.1.1095
2015-08-22 08:47:37 status unpacked chromium-browser:amd64 44.0.2403.89-0ubuntu0.14.04.1.1095
2015-08-22 08:47:37 status unpacked chromium-browser:amd64 44.0.2403.89-0ubuntu0.14.04.1.1095
2015-08-22 08:47:37 status half-configured chromium-browser:amd64 44.0.2403.89-0ubuntu0.14.04.1.1095
2015-08-22 08:47:37 status installed chromium-browser:amd64 44.0.2403.89-0ubuntu0.14.04.1.1095
2015-08-22 08:47:37 configure chromium-browser-l10n:all 44.0.2403.89-0ubuntu0.14.04.1.1095 <none>
2015-08-22 08:47:37 status unpacked chromium-browser-l10n:all 44.0.2403.89-0ubuntu0.14.04.1.1095
2015-08-22 08:47:37 status half-configured chromium-browser-l10n:all 44.0.2403.89-0ubuntu0.14.04.1.1095
2015-08-22 08:47:37 status installed chromium-browser-l10n:all 44.0.2403.89-0ubuntu0.14.04.1.1095
2015-08-22 08:47:37 configure firefox:amd64 40.0+build4-0ubuntu0.14.04.4 <none>
2015-08-22 08:47:37 status unpacked firefox:amd64 40.0+build4-0ubuntu0.14.04.4
2015-08-22 08:47:37 status unpacked firefox:amd64 40.0+build4-0ubuntu0.14.04.4
2015-08-22 08:47:37 status unpacked firefox:amd64 40.0+build4-0ubuntu0.14.04.4
2015-08-22 08:47:37 status unpacked firefox:amd64 40.0+build4-0ubuntu0.14.04.4
2015-08-22 08:47:37 status unpacked firefox:amd64 40.0+build4-0ubuntu0.14.04.4
2015-08-22 08:47:37 status half-configured firefox:amd64 40.0+build4-0ubuntu0.14.04.4
2015-08-22 08:47:37 status installed firefox:amd64 40.0+build4-0ubuntu0.14.04.4
2015-08-22 08:47:37 configure firefox-locale-de:amd64 40.0+build4-0ubuntu0.14.04.4 <none>
2015-08-22 08:47:37 status unpacked firefox-locale-de:amd64 40.0+build4-0ubuntu0.14.04.4
2015-08-22 08:47:37 status half-configured firefox-locale-de:amd64 40.0+build4-0ubuntu0.14.04.4
2015-08-22 08:47:37 status installed firefox-locale-de:amd64 40.0+build4-0ubuntu0.14.04.4
2015-08-22 08:47:37 configure firefox-locale-en:amd64 40.0+build4-0ubuntu0.14.04.4 <none>
2015-08-22 08:47:37 status unpacked firefox-locale-en:amd64 40.0+build4-0ubuntu0.14.04.4
2015-08-22 08:47:37 status half-configured firefox-locale-en:amd64 40.0+build4-0ubuntu0.14.04.4
2015-08-22 08:47:37 status installed firefox-locale-en:amd64 40.0+build4-0ubuntu0.14.04.4
2015-08-26 09:00:58 startup archives unpack
2015-08-26 09:01:02 upgrade thunderbird-locale-de:amd64 1:31.8.0+build1-0ubuntu0.14.04.1 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:02 status half-configured thunderbird-locale-de:amd64 1:31.8.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:02 status unpacked thunderbird-locale-de:amd64 1:31.8.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:02 status half-installed thunderbird-locale-de:amd64 1:31.8.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:02 status half-installed thunderbird-locale-de:amd64 1:31.8.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:02 status unpacked thunderbird-locale-de:amd64 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:02 status unpacked thunderbird-locale-de:amd64 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:02 upgrade thunderbird-locale-en:amd64 1:31.8.0+build1-0ubuntu0.14.04.1 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:02 status half-configured thunderbird-locale-en:amd64 1:31.8.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:02 status unpacked thunderbird-locale-en:amd64 1:31.8.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:02 status half-installed thunderbird-locale-en:amd64 1:31.8.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:02 status half-installed thunderbird-locale-en:amd64 1:31.8.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:02 status unpacked thunderbird-locale-en:amd64 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:02 status unpacked thunderbird-locale-en:amd64 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:03 upgrade thunderbird:amd64 1:31.8.0+build1-0ubuntu0.14.04.1 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:03 status half-configured thunderbird:amd64 1:31.8.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:03 status unpacked thunderbird:amd64 1:31.8.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:03 status half-installed thunderbird:amd64 1:31.8.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:03 status triggers-pending man-db:amd64 2.6.7.1-1ubuntu1
2015-08-26 09:01:03 status triggers-pending mime-support:all 3.54ubuntu1.1
2015-08-26 09:01:03 status triggers-pending gnome-menus:amd64 3.10.1-0ubuntu2
2015-08-26 09:01:03 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu1
2015-08-26 09:01:03 status half-installed thunderbird:amd64 1:31.8.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:03 status triggers-pending bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-08-26 09:01:03 status half-installed thunderbird:amd64 1:31.8.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:07 status half-installed thunderbird:amd64 1:31.8.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:07 status unpacked thunderbird:amd64 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:07 status unpacked thunderbird:amd64 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:08 upgrade thunderbird-gnome-support:amd64 1:31.8.0+build1-0ubuntu0.14.04.1 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:08 status half-configured thunderbird-gnome-support:amd64 1:31.8.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:08 status unpacked thunderbird-gnome-support:amd64 1:31.8.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:08 status half-installed thunderbird-gnome-support:amd64 1:31.8.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:08 status half-installed thunderbird-gnome-support:amd64 1:31.8.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:08 status unpacked thunderbird-gnome-support:amd64 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:08 status unpacked thunderbird-gnome-support:amd64 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:08 upgrade thunderbird-locale-en-gb:all 1:31.8.0+build1-0ubuntu0.14.04.1 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:08 status half-configured thunderbird-locale-en-gb:all 1:31.8.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:08 status unpacked thunderbird-locale-en-gb:all 1:31.8.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:08 status half-installed thunderbird-locale-en-gb:all 1:31.8.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:08 status half-installed thunderbird-locale-en-gb:all 1:31.8.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:08 status unpacked thunderbird-locale-en-gb:all 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:08 status unpacked thunderbird-locale-en-gb:all 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:08 upgrade thunderbird-locale-en-us:all 1:31.8.0+build1-0ubuntu0.14.04.1 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:08 status half-configured thunderbird-locale-en-us:all 1:31.8.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:08 status unpacked thunderbird-locale-en-us:all 1:31.8.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:08 status half-installed thunderbird-locale-en-us:all 1:31.8.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:08 status half-installed thunderbird-locale-en-us:all 1:31.8.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:08 status unpacked thunderbird-locale-en-us:all 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:08 status unpacked thunderbird-locale-en-us:all 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:08 trigproc man-db:amd64 2.6.7.1-1ubuntu1 2.6.7.1-1ubuntu1
2015-08-26 09:01:08 status half-configured man-db:amd64 2.6.7.1-1ubuntu1
2015-08-26 09:01:09 status installed man-db:amd64 2.6.7.1-1ubuntu1
2015-08-26 09:01:09 trigproc mime-support:all 3.54ubuntu1.1 3.54ubuntu1.1
2015-08-26 09:01:09 status half-configured mime-support:all 3.54ubuntu1.1
2015-08-26 09:01:10 status installed mime-support:all 3.54ubuntu1.1
2015-08-26 09:01:10 trigproc gnome-menus:amd64 3.10.1-0ubuntu2 3.10.1-0ubuntu2
2015-08-26 09:01:10 status half-configured gnome-menus:amd64 3.10.1-0ubuntu2
2015-08-26 09:01:10 status installed gnome-menus:amd64 3.10.1-0ubuntu2
2015-08-26 09:01:10 trigproc desktop-file-utils:amd64 0.22-1ubuntu1 0.22-1ubuntu1
2015-08-26 09:01:10 status half-configured desktop-file-utils:amd64 0.22-1ubuntu1
2015-08-26 09:01:10 status installed desktop-file-utils:amd64 0.22-1ubuntu1
2015-08-26 09:01:10 trigproc bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1 0.5.1+14.04.20140409-0ubuntu1
2015-08-26 09:01:10 status half-configured bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-08-26 09:01:10 status installed bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-08-26 09:01:10 startup packages configure
2015-08-26 09:01:10 configure thunderbird:amd64 1:38.2.0+build1-0ubuntu0.14.04.1 <none>
2015-08-26 09:01:10 status unpacked thunderbird:amd64 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:10 status unpacked thunderbird:amd64 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:10 status unpacked thunderbird:amd64 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:10 status unpacked thunderbird:amd64 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:10 status half-configured thunderbird:amd64 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:10 status installed thunderbird:amd64 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:10 configure thunderbird-locale-de:amd64 1:38.2.0+build1-0ubuntu0.14.04.1 <none>
2015-08-26 09:01:10 status unpacked thunderbird-locale-de:amd64 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:10 status half-configured thunderbird-locale-de:amd64 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:10 status installed thunderbird-locale-de:amd64 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:10 configure thunderbird-locale-en:amd64 1:38.2.0+build1-0ubuntu0.14.04.1 <none>
2015-08-26 09:01:10 status unpacked thunderbird-locale-en:amd64 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:10 status half-configured thunderbird-locale-en:amd64 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:10 status installed thunderbird-locale-en:amd64 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:10 configure thunderbird-gnome-support:amd64 1:38.2.0+build1-0ubuntu0.14.04.1 <none>
2015-08-26 09:01:10 status unpacked thunderbird-gnome-support:amd64 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:10 status half-configured thunderbird-gnome-support:amd64 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:10 status installed thunderbird-gnome-support:amd64 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:10 configure thunderbird-locale-en-gb:all 1:38.2.0+build1-0ubuntu0.14.04.1 <none>
2015-08-26 09:01:10 status unpacked thunderbird-locale-en-gb:all 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:10 status half-configured thunderbird-locale-en-gb:all 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:10 status installed thunderbird-locale-en-gb:all 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:10 configure thunderbird-locale-en-us:all 1:38.2.0+build1-0ubuntu0.14.04.1 <none>
2015-08-26 09:01:10 status unpacked thunderbird-locale-en-us:all 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:10 status half-configured thunderbird-locale-en-us:all 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-26 09:01:10 status installed thunderbird-locale-en-us:all 1:38.2.0+build1-0ubuntu0.14.04.1
2015-08-27 10:52:49 startup archives unpack
2015-08-27 10:52:52 upgrade libgdk-pixbuf2.0-0:amd64 2.30.7-0ubuntu1 2.30.7-0ubuntu1.1
2015-08-27 10:52:52 status half-configured libgdk-pixbuf2.0-0:amd64 2.30.7-0ubuntu1
2015-08-27 10:52:52 status unpacked libgdk-pixbuf2.0-0:amd64 2.30.7-0ubuntu1
2015-08-27 10:52:52 status half-installed libgdk-pixbuf2.0-0:amd64 2.30.7-0ubuntu1
2015-08-27 10:52:52 status half-installed libgdk-pixbuf2.0-0:amd64 2.30.7-0ubuntu1
2015-08-27 10:52:52 status unpacked libgdk-pixbuf2.0-0:amd64 2.30.7-0ubuntu1.1
2015-08-27 10:52:52 status unpacked libgdk-pixbuf2.0-0:amd64 2.30.7-0ubuntu1.1
2015-08-27 10:52:53 upgrade libgdk-pixbuf2.0-common:all 2.30.7-0ubuntu1 2.30.7-0ubuntu1.1
2015-08-27 10:52:53 status half-configured libgdk-pixbuf2.0-common:all 2.30.7-0ubuntu1
2015-08-27 10:52:53 status unpacked libgdk-pixbuf2.0-common:all 2.30.7-0ubuntu1
2015-08-27 10:52:53 status half-installed libgdk-pixbuf2.0-common:all 2.30.7-0ubuntu1
2015-08-27 10:52:53 status half-installed libgdk-pixbuf2.0-common:all 2.30.7-0ubuntu1
2015-08-27 10:52:53 status unpacked libgdk-pixbuf2.0-common:all 2.30.7-0ubuntu1.1
2015-08-27 10:52:53 status unpacked libgdk-pixbuf2.0-common:all 2.30.7-0ubuntu1.1
2015-08-27 10:52:53 upgrade gir1.2-gdkpixbuf-2.0:amd64 2.30.7-0ubuntu1 2.30.7-0ubuntu1.1
2015-08-27 10:52:53 status half-configured gir1.2-gdkpixbuf-2.0:amd64 2.30.7-0ubuntu1
2015-08-27 10:52:53 status unpacked gir1.2-gdkpixbuf-2.0:amd64 2.30.7-0ubuntu1
2015-08-27 10:52:53 status half-installed gir1.2-gdkpixbuf-2.0:amd64 2.30.7-0ubuntu1
2015-08-27 10:52:53 status half-installed gir1.2-gdkpixbuf-2.0:amd64 2.30.7-0ubuntu1
2015-08-27 10:52:53 status unpacked gir1.2-gdkpixbuf-2.0:amd64 2.30.7-0ubuntu1.1
2015-08-27 10:52:53 status unpacked gir1.2-gdkpixbuf-2.0:amd64 2.30.7-0ubuntu1.1
2015-08-27 10:52:53 startup packages configure
2015-08-27 10:52:53 configure libgdk-pixbuf2.0-common:all 2.30.7-0ubuntu1.1 <none>
2015-08-27 10:52:53 status unpacked libgdk-pixbuf2.0-common:all 2.30.7-0ubuntu1.1
2015-08-27 10:52:53 status half-configured libgdk-pixbuf2.0-common:all 2.30.7-0ubuntu1.1
2015-08-27 10:52:53 status installed libgdk-pixbuf2.0-common:all 2.30.7-0ubuntu1.1
2015-08-27 10:52:53 configure libgdk-pixbuf2.0-0:amd64 2.30.7-0ubuntu1.1 <none>
2015-08-27 10:52:53 status unpacked libgdk-pixbuf2.0-0:amd64 2.30.7-0ubuntu1.1
2015-08-27 10:52:53 status half-configured libgdk-pixbuf2.0-0:amd64 2.30.7-0ubuntu1.1
2015-08-27 10:52:53 status installed libgdk-pixbuf2.0-0:amd64 2.30.7-0ubuntu1.1
2015-08-27 10:52:53 status triggers-pending libc-bin:amd64 2.19-0ubuntu6.6
2015-08-27 10:52:53 configure gir1.2-gdkpixbuf-2.0:amd64 2.30.7-0ubuntu1.1 <none>
2015-08-27 10:52:53 status unpacked gir1.2-gdkpixbuf-2.0:amd64 2.30.7-0ubuntu1.1
2015-08-27 10:52:53 status half-configured gir1.2-gdkpixbuf-2.0:amd64 2.30.7-0ubuntu1.1
2015-08-27 10:52:53 status installed gir1.2-gdkpixbuf-2.0:amd64 2.30.7-0ubuntu1.1
2015-08-27 10:52:53 trigproc libc-bin:amd64 2.19-0ubuntu6.6 <none>
2015-08-27 10:52:53 status half-configured libc-bin:amd64 2.19-0ubuntu6.6
2015-08-27 10:52:53 status installed libc-bin:amd64 2.19-0ubuntu6.6
2015-08-27 13:12:43 startup archives unpack
2015-08-27 13:12:54 install psensor-common:all <none> 0.8.0.3-1ubuntu3
2015-08-27 13:12:54 status half-installed psensor-common:all 0.8.0.3-1ubuntu3
2015-08-27 13:12:54 status unpacked psensor-common:all 0.8.0.3-1ubuntu3
2015-08-27 13:12:54 status unpacked psensor-common:all 0.8.0.3-1ubuntu3
2015-08-27 13:12:55 install psensor:amd64 0.8.0.3-1ubuntu3 0.8.0.3-1ubuntu3
2015-08-27 13:12:55 status half-installed psensor:amd64 0.8.0.3-1ubuntu3
2015-08-27 13:12:55 status triggers-pending hicolor-icon-theme:all 0.13-1
2015-08-27 13:12:55 status half-installed psensor:amd64 0.8.0.3-1ubuntu3
2015-08-27 13:12:55 status triggers-pending gconf2:amd64 3.2.6-0ubuntu2
2015-08-27 13:12:55 status half-installed psensor:amd64 0.8.0.3-1ubuntu3
2015-08-27 13:12:55 status triggers-pending mime-support:all 3.54ubuntu1.1
2015-08-27 13:12:55 status triggers-pending gnome-menus:amd64 3.10.1-0ubuntu2
2015-08-27 13:12:55 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu1
2015-08-27 13:12:55 status half-installed psensor:amd64 0.8.0.3-1ubuntu3
2015-08-27 13:12:55 status triggers-pending bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-08-27 13:12:55 status half-installed psensor:amd64 0.8.0.3-1ubuntu3
2015-08-27 13:12:55 status triggers-pending man-db:amd64 2.6.7.1-1ubuntu1
2015-08-27 13:12:56 status unpacked psensor:amd64 0.8.0.3-1ubuntu3
2015-08-27 13:12:56 status unpacked psensor:amd64 0.8.0.3-1ubuntu3
2015-08-27 13:12:57 install hddtemp:amd64 0.3-beta15-52 0.3-beta15-52
2015-08-27 13:12:57 status half-installed hddtemp:amd64 0.3-beta15-52
2015-08-27 13:12:57 status triggers-pending ureadahead:amd64 0.100.0-16
2015-08-27 13:12:57 status half-installed hddtemp:amd64 0.3-beta15-52
2015-08-27 13:12:57 status unpacked hddtemp:amd64 0.3-beta15-52
2015-08-27 13:12:57 status unpacked hddtemp:amd64 0.3-beta15-52
2015-08-27 13:12:57 trigproc hicolor-icon-theme:all 0.13-1 0.13-1
2015-08-27 13:12:57 status half-configured hicolor-icon-theme:all 0.13-1
2015-08-27 13:13:05 status installed hicolor-icon-theme:all 0.13-1
2015-08-27 13:13:05 trigproc gconf2:amd64 3.2.6-0ubuntu2 3.2.6-0ubuntu2
2015-08-27 13:13:05 status half-configured gconf2:amd64 3.2.6-0ubuntu2
2015-08-27 13:13:07 status installed gconf2:amd64 3.2.6-0ubuntu2
2015-08-27 13:13:07 trigproc mime-support:all 3.54ubuntu1.1 3.54ubuntu1.1
2015-08-27 13:13:07 status half-configured mime-support:all 3.54ubuntu1.1
2015-08-27 13:13:09 status installed mime-support:all 3.54ubuntu1.1
2015-08-27 13:13:09 trigproc gnome-menus:amd64 3.10.1-0ubuntu2 3.10.1-0ubuntu2
2015-08-27 13:13:09 status half-configured gnome-menus:amd64 3.10.1-0ubuntu2
2015-08-27 13:13:09 status installed gnome-menus:amd64 3.10.1-0ubuntu2
2015-08-27 13:13:09 trigproc desktop-file-utils:amd64 0.22-1ubuntu1 0.22-1ubuntu1
2015-08-27 13:13:09 status half-configured desktop-file-utils:amd64 0.22-1ubuntu1
2015-08-27 13:13:10 status installed desktop-file-utils:amd64 0.22-1ubuntu1
2015-08-27 13:13:10 trigproc bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1 0.5.1+14.04.20140409-0ubuntu1
2015-08-27 13:13:10 status half-configured bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-08-27 13:13:10 status installed bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-08-27 13:13:10 trigproc man-db:amd64 2.6.7.1-1ubuntu1 2.6.7.1-1ubuntu1
2015-08-27 13:13:10 status half-configured man-db:amd64 2.6.7.1-1ubuntu1
2015-08-27 13:13:15 status installed man-db:amd64 2.6.7.1-1ubuntu1
2015-08-27 13:13:15 trigproc ureadahead:amd64 0.100.0-16 0.100.0-16
2015-08-27 13:13:15 status half-configured ureadahead:amd64 0.100.0-16
2015-08-27 13:13:15 status installed ureadahead:amd64 0.100.0-16
2015-08-27 13:13:16 startup packages configure
2015-08-27 13:13:16 configure psensor-common:all 0.8.0.3-1ubuntu3 <none>
2015-08-27 13:13:16 status unpacked psensor-common:all 0.8.0.3-1ubuntu3
2015-08-27 13:13:16 status half-configured psensor-common:all 0.8.0.3-1ubuntu3
2015-08-27 13:13:16 status installed psensor-common:all 0.8.0.3-1ubuntu3
2015-08-27 13:13:16 configure psensor:amd64 0.8.0.3-1ubuntu3 <none>
2015-08-27 13:13:16 status unpacked psensor:amd64 0.8.0.3-1ubuntu3
2015-08-27 13:13:16 status unpacked psensor:amd64 0.8.0.3-1ubuntu3
2015-08-27 13:13:16 status half-configured psensor:amd64 0.8.0.3-1ubuntu3
2015-08-27 13:13:16 status installed psensor:amd64 0.8.0.3-1ubuntu3
2015-08-27 13:13:16 configure hddtemp:amd64 0.3-beta15-52 <none>
2015-08-27 13:13:16 status unpacked hddtemp:amd64 0.3-beta15-52
2015-08-27 13:13:16 status unpacked hddtemp:amd64 0.3-beta15-52
2015-08-27 13:13:16 status unpacked hddtemp:amd64 0.3-beta15-52
2015-08-27 13:13:16 status unpacked hddtemp:amd64 0.3-beta15-52
2015-08-27 13:13:16 status half-configured hddtemp:amd64 0.3-beta15-52
2015-08-27 13:13:34 status installed hddtemp:amd64 0.3-beta15-52
```

---

### Post by TheFu on 2015-08-27
Run top. Capture the text output.  What is at the "top"?  That is what is using the most CPU. If you don't know how to interpret it - post the TEXT here.  

BTW - Images and other documents are seldom desired here. Too many wasted bits - especially for low bandwidth people. I shouldn't have to load any program to view this stuff.

---

### Post by 171742 on 2015-08-31
```
top - 12:11:06 up 12 min,  2 users,  load average: 2,32, 2,60, 1,75
Tasks: 195 total,   1 running, 194 sleeping,   0 stopped,   0 zombie
%Cpu(s): 27,0 us,  9,9 sy,  0,0 ni, 63,0 id,  0,0 wa,  0,0 hi,  0,2 si,  0,0 st
KiB Mem:   4047964 total,  3103996 used,   943968 free,   201652 buffers
KiB Swap:  4192252 total,        0 used,  4192252 free.  1554204 cached Mem


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                              
 2537 o         20   0 1095988 107236  23904 S  18,1  2,6   2:14.91 chromium-browse                                                                      
 2429 o         20   0 1991416 250632 100112 S  13,1  6,2   3:40.05 chromium-browse                                                                      
 1257 root      20   0  248880  32468  16872 S  10,2  0,8   1:18.61 Xorg                                                                                 
 2574 o         20   0  701144  21612  15028 S   8,2  0,5   0:57.88 psensor                                                                              
 2959 o         20   0  661324  19840  12848 S   7,6  0,5   0:03.09 gnome-terminal                                                                       
 1737 o         20   0 1515952 141004  41348 S   3,9  3,5   1:09.43 compiz                                                                               
 2532 o         20   0 1140628 157372  22060 S   3,9  3,9   1:05.05 chromium-browse                                                                      
 1369 o         20   0  363348   4168   2888 S   2,0  0,1   0:04.53 ibus-daemon                                                                          
 1387 o         20   0  490520  17468  10544 S   1,3  0,4   0:01.80 ibus-ui-gtk3                                                                         
 2931 root      20   0       0      0      0 S   1,0  0,0   0:00.81 kworker/0:0                                                                          
 2987 o         20   0   30648   1720   1204 R   1,0  0,0   0:00.77 top                                                                                  
    7 root      20   0       0      0      0 S   0,7  0,0   0:04.34 rcu_sched                                                                            
   33 root      20   0       0      0      0 S   0,7  0,0   0:02.63 kworker/1:1                                                                          
 1822 o         20   0  436804  15236  11316 S   0,7  0,4   0:02.68 diodon                                                                               
  132 root      20   0       0      0      0 S   0,3  0,0   0:00.57 kworker/u4:4                                                                         
 1447 o         20   0  655200  20320  12068 S   0,3  0,5   0:06.85 unity-panel-ser                                                                      
 1595 o         20   0  206652   3320   2744 S   0,3  0,1   0:01.06 ibus-engine-sim                                                                      
 1787 o         20   0 1484076  46968  24528 S   0,3  1,2   0:20.11 nautilus                                                                             
 1865 o         20   0   20228    932    760 S   0,3  0,0   0:00.67 syndaemon                                                                            
 2120 root      20   0   73948   9192   4112 S   0,3  0,2   0:02.01 teamviewerd                                                                          
    1 root      20   0   33900   3288   1484 S   0,0  0,1   0:02.04 init                                                                                 
    2 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kthreadd                                                                             
    3 root      20   0       0      0      0 S   0,0  0,0   0:00.02 ksoftirqd/0                                                                          
    5 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/0:0H                                                                         
    6 root      20   0       0      0      0 S   0,0  0,0   0:00.34 kworker/u4:0                                                                         
    8 root      20   0       0      0      0 S   0,0  0,0   0:01.23 rcuos/0                                                                              
    9 root      20   0       0      0      0 S   0,0  0,0   0:01.38 rcuos/1                                                                              
   10 root      20   0       0      0      0 S   0,0  0,0   0:00.00 rcu_bh                                                                               
   11 root      20   0       0      0      0 S   0,0  0,0   0:00.00 rcuob/0                                                                              
   12 root      20   0       0      0      0 S   0,0  0,0   0:00.00 rcuob/1                                                                              
   13 root      rt   0       0      0      0 S   0,0  0,0   0:00.02 migration/0                                                                          
   14 root      rt   0       0      0      0 S   0,0  0,0   0:00.01 watchdog/0                                                                           
   15 root      rt   0       0      0      0 S   0,0  0,0   0:00.01 watchdog/1                                                                           
   16 root      rt   0       0      0      0 S   0,0  0,0   0:00.01 migration/1                                                                          
   17 root      20   0       0      0      0 S   0,0  0,0   0:00.15 ksoftirqd/1                                                                          
   19 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/1:0H                                                                         
   20 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 khelper                                                                              
   21 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kdevtmpfs                                                                            
   22 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 netns                                                                                
   23 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 writeback                                                                            
   24 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kintegrityd
```

---

### Post by TheFu on 2015-08-31
Appears to be 63% idle.  Chromium is a hog - it is using over 3G of RAM on your system alone. There are simpler browsers that use less resources - dillo is one, but does have limitations.

What CPU does the machine have? **head -n 10 /proc/cpuinfo** would be helpful.

---

### Post by v3.xx on 2015-08-31
Have you checked for optional video drivers?

---

### Post by 171742 on 2015-08-31
No, how to do so?

---

### Post by 171742 on 2015-08-31
Yes, but this never happened before, so isnt it unlikely?

---

### Post by HermanAB on 2015-08-31
That looks normal for someone using the Chrome browser.

The moral of the story is to kill Chrome and use pretty much any other browser.

---

### Post by 171742 on 2015-09-02
Hi,

Firefox is even slower. So my PC is too old?

BR

---

### Post by CantankRus on 2015-09-02
Install inxi (sysinfo script)...
```
sudo apt-get install inxi
```
and post your terminal output of...
```
inxi -b
```

---

### Post by TheFu on 2015-09-02
> **171742 said:**
> Hi,

Firefox is even slower. So my PC is too old?

BR

We've asked for some facts. Will you please provide them so we can help?
There are ways to make things feel faster and to offload some work that isn't necessary. Whether that will work or not depends on your hardware.

Please post the requested data.

---

### Post by 171742 on 2015-09-02
System:    Host: o-HP-Compaq-6910p-KL536AV Kernel: 3.13.0-62-generic x86_64 (64 bit) 
           Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   System: Hewlett-Packard (portable) product: HP Compaq 6910p (KL536AV) version: F.17
           Mobo: Hewlett-Packard model: 30C1 version: KBC Version 68.36
           Bios: Hewlett-Packard version: 68MCD Ver. F.17 date: 11/04/2008
CPU:       Dual core Intel Core2 Duo CPU T8300 (-MCP-) clocked at 800.00 MHz 
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RV516/M64-S [Mobility Radeon X2300] 
           X.Org: 1.15.1 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1440x900@60.0hz 
           GLX Renderer: Gallium 0.4 on ATI RV515 GLX Version: 2.1 Mesa 10.1.3
Network:   Card-1: Intel PRO/Wireless 4965 AG or AGN [Kedron] Network Connection driver: iwl4965 
           Card-2: Intel 82566MM Gigabit Network Connection driver: e1000e 
Drives:    HDD Total Size: 120.0GB (73.2% used)
Info:      Processes: 209 Uptime: 6:33 Memory: 2281.1/3953.1MB Client: Shell (bash) inxi: 1.9.17 
o@o-HP-Compaq-6910p-KL536AV:~$

---

### Post by TheFu on 2015-09-02
Not the fastest C2D machine.  Says 800Mhz, but that CPU can go to 2.4Ghz. Could be normal for it to run slow when not busy. Can you make it increase the CPU speed?  Passmark is 1480 ... not exactly hot by standards for today, but very acceptable for normal desktop use with a lighter GUI.

Ok - because it is a laptop, to make a machine like this faster, the only real choice is to use a lighter GUI like XFCE or LXDE and remove the stock Unity GUI. Everything will feel faster.  There is an easy-to-follow how to over a howtogeek.

My netbook has a passmark of 1548 - about the same and runs great, but not with Unity.

Lastly, if you could please use "code tags" for output above (just edit that post). That would be helpful. It will make things line up nicely.

---

### Post by 171742 on 2015-09-02
Thanks! So that means my pc is crap. But are these alternatives as easy to handle? Ubuntu is already pushing my limits sometimes.n

---

### Post by Doug S on 2015-09-02
> **TheFu said:**
> Says 800Mhz, but that CPU can go to 2.4Ghz. Could be normal for it to run slow when not busy. Can you make it increase the CPU speed? +1. Back to basics. Show that your CPU does frequency scaling properly, as perhaps it is somehow using the acpi-cpufreq scaling driver in powersave mode. Do:```
$ grep MHz /proc/cpuinfo
```both with no load and with significant load.

---

### Post by monkeybrain20122 on 2015-09-02
> **171742 said:**
> Hi,

Firefox is even slower. So my PC is too old?

BR

Chrome/Chromium is 'fast' because it uses a lot of ram. :) You can cut down ram use if you don't open many tabs.

---


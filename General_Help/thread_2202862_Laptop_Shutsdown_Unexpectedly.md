---
title: "Laptop Shutsdown Unexpectedly"
date: 2014-01-31
forum: General Help
---

### Post by borgward on 2014-01-31
My laptop began shutting down unexpectedly after the next to the last update. It shuts down as soon as I close my laptop, whether on powersupply or battery. Battery is good. I booted to the DVD I installed from, and the laptop does not shutdown after I close the laptop, whether it is connected to the power supply or running on battery. I think this behavior is due to the next to the last update.

---

### Post by ajgreeny on 2014-01-31
What version of ubuntu and what was included in the last update?

Are you sure the laptop is not overheating, or is it happening only when you close the laptop?

Can you also check what are the power management settings for when you close the lid.

---

### Post by borgward on 2014-01-31
Mint Nadia 14.1 Don't know what was included in the last update. How to find out.

It is not overheating. It shuts down as soon as I close my laptop. Where to find record of temperatures?

The power management settings for when running on battery or when Plugged in are Suspend.

---

### Post by ajgreeny on 2014-02-01
Run the command ```
grep -iw upgrade /var/log/dpkg.log.1 && grep -iw upgrade /var/log/dpkg.log
``` in terminal to see a list by date of what has been upgraded on your system.  If you get an error message saying one or other of those dpkg.log files does not exist just edit the command to remove one half of it and keep just the file that does exist. That may give some clue to your problem.

---

### Post by borgward on 2014-02-01
No errors indicated.

---

### Post by ajgreeny on 2014-02-02
So what were the latest updates?

---

### Post by borgward on 2014-02-02
tom@tom-Inspiron-1520 ~ $ grep -iw upgrade /var/log/dpkg.log.1 && grep -iw upgrade /var/log/dpkg.log
2014-01-09 09:57:34 upgrade libdrm2:amd64 2.4.43-0ubuntu0.2 2.4.46-1ubuntu0.0.1
2014-01-09 09:57:35 upgrade libdrm2:i386 2.4.43-0ubuntu0.2 2.4.46-1ubuntu0.0.1
2014-01-09 09:57:39 upgrade libdrm-nouveau1a:amd64 2.4.43-0ubuntu0.2 2.4.46-1ubuntu0.0.1
2014-01-09 09:57:40 upgrade libdrm-radeon1:i386 2.4.43-0ubuntu0.2 2.4.46-1ubuntu0.0.1
2014-01-09 09:57:40 upgrade libdrm-radeon1:amd64 2.4.43-0ubuntu0.2 2.4.46-1ubuntu0.0.1
2014-01-09 09:57:44 upgrade libkms1:amd64 2.4.43-0ubuntu0.2 2.4.46-1ubuntu0.0.1
2014-01-09 09:57:44 upgrade libprocps0:amd64 1:3.3.3-2ubuntu3.2 1:3.3.3-2ubuntu3.3
2014-01-09 09:57:45 upgrade libcurl3-gnutls:amd64 7.27.0-1ubuntu1.4 7.27.0-1ubuntu1.7
2014-01-09 09:57:46 upgrade gnome-keyring:amd64 3.6.1-0ubuntu1 3.6.1-0ubuntu1.1
2014-01-09 09:57:48 upgrade libcurl3:i386 7.27.0-1ubuntu1.4 7.27.0-1ubuntu1.7
2014-01-09 09:57:49 upgrade libcurl3:amd64 7.27.0-1ubuntu1.4 7.27.0-1ubuntu1.7
2014-01-09 09:57:57 upgrade libnss3-1d:amd64 3.14.3-0ubuntu0.12.10.1 3.15.3.1-0ubuntu0.12.10.1
2014-01-09 09:57:57 upgrade libnss3:amd64 3.14.3-0ubuntu0.12.10.1 3.15.3.1-0ubuntu0.12.10.1
2014-01-09 09:57:58 upgrade libnss3:i386 3.14.3-0ubuntu0.12.10.1 3.15.3.1-0ubuntu0.12.10.1
2014-01-09 09:58:02 upgrade libcurl3-nss:amd64 7.27.0-1ubuntu1.4 7.27.0-1ubuntu1.7
2014-01-09 09:58:03 upgrade libdrm-intel1:i386 2.4.43-0ubuntu0.2 2.4.46-1ubuntu0.0.1
2014-01-09 09:58:03 upgrade libdrm-intel1:amd64 2.4.43-0ubuntu0.2 2.4.46-1ubuntu0.0.1
2014-01-09 09:58:07 upgrade libdrm-nouveau2:i386 2.4.43-0ubuntu0.2 2.4.46-1ubuntu0.0.1
2014-01-09 09:58:08 upgrade libdrm-nouveau2:amd64 2.4.43-0ubuntu0.2 2.4.46-1ubuntu0.0.1
2014-01-09 09:58:11 upgrade libjpeg-turbo8:i386 1.2.1-0ubuntu2 1.2.1-0ubuntu2.12.10.1
2014-01-09 09:58:12 upgrade libjpeg-turbo8:amd64 1.2.1-0ubuntu2 1.2.1-0ubuntu2.12.10.1
2014-01-09 09:58:15 upgrade libpam-gnome-keyring:amd64 3.6.1-0ubuntu1 3.6.1-0ubuntu1.1
2014-01-09 09:58:16 upgrade libpixman-1-0:i386 0.26.0-3 0.30.2-1ubuntu0.0.0.1
2014-01-09 09:58:17 upgrade libpixman-1-0:amd64 0.26.0-3 0.30.2-1ubuntu0.0.0.1
2014-01-09 09:58:21 upgrade libqt4-test:amd64 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:58:21 upgrade libqt4-test:i386 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:58:22 upgrade libqtcore4:i386 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:58:23 upgrade libqtcore4:amd64 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:58:28 upgrade libqt4-sql-mysql:i386 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:58:28 upgrade libqt4-qt3support:i386 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:58:29 upgrade libqt4-qt3support:amd64 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:58:30 upgrade libqt4-designer:amd64 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:58:32 upgrade libqt4-designer:i386 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:58:33 upgrade libqt4-script:amd64 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:58:34 upgrade libqt4-script:i386 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:58:34 upgrade libqt4-dbus:amd64 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:58:35 upgrade libqt4-dbus:i386 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:58:36 upgrade libqt4-xml:amd64 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:58:36 upgrade libqt4-xml:i386 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:58:41 upgrade libqtgui4:amd64 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:58:42 upgrade libqtgui4:i386 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:58:44 upgrade libqt4-declarative:amd64 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:58:45 upgrade libqt4-declarative:i386 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:58:46 upgrade libqt4-network:amd64 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:58:46 upgrade libqt4-network:i386 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:58:51 upgrade libqt4-sql:amd64 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:58:51 upgrade libqt4-sql:i386 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:58:55 upgrade libqt4-xmlpatterns:amd64 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:58:56 upgrade libqt4-xmlpatterns:i386 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:59:02 upgrade libqt4-help:amd64 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:59:02 upgrade libqt4-scripttools:i386 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:59:03 upgrade libqt4-scripttools:amd64 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:59:07 upgrade libqt4-opengl:i386 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:59:07 upgrade libqt4-opengl:amd64 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:59:11 upgrade libqt4-svg:i386 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:59:12 upgrade libqt4-svg:amd64 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:59:16 upgrade libqt4-sql-sqlite:amd64 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:59:16 upgrade qdbus:amd64 4:4.8.3+dfsg-0ubuntu3.1 4:4.8.3+dfsg-0ubuntu3.2
2014-01-09 09:59:17 upgrade samba:amd64 2:3.6.6-3ubuntu5.2 2:3.6.6-3ubuntu5.3
2014-01-09 09:59:20 upgrade libwbclient0:amd64 2:3.6.6-3ubuntu5.2 2:3.6.6-3ubuntu5.3
2014-01-09 09:59:21 upgrade smbclient:amd64 2:3.6.6-3ubuntu5.2 2:3.6.6-3ubuntu5.3
2014-01-09 09:59:23 upgrade samba-common:all 2:3.6.6-3ubuntu5.2 2:3.6.6-3ubuntu5.3
2014-01-09 09:59:24 upgrade procps:amd64 1:3.3.3-2ubuntu3.2 1:3.3.3-2ubuntu3.3
2014-01-09 09:59:25 upgrade samba-common-bin:amd64 2:3.6.6-3ubuntu5.2 2:3.6.6-3ubuntu5.3
2014-01-09 09:59:26 upgrade libsmbclient:amd64 2:3.6.6-3ubuntu5.2 2:3.6.6-3ubuntu5.3
2014-01-09 09:59:27 upgrade gpgv:amd64 1.4.11-3ubuntu4.3 1.4.11-3ubuntu4.4
2014-01-09 09:59:34 upgrade gnupg:amd64 1.4.11-3ubuntu4.3 1.4.11-3ubuntu4.4
2014-01-09 09:59:41 upgrade rsyslog:amd64 5.8.6-1ubuntu9.2 5.8.6-1ubuntu9.3
2014-01-09 09:59:43 upgrade iproute:amd64 20120521-3ubuntu1 20120521-3ubuntu1.1
2014-01-09 09:59:44 upgrade duplicity:amd64 0.6.19-0ubuntu2.2 0.6.19-0ubuntu2.3
2014-01-09 09:59:45 upgrade firefox:amd64 25.0+build3-0ubuntu0.12.10.1 26.0+build2-0ubuntu0.12.10.2
2014-01-09 09:59:49 upgrade firefox-locale-en:amd64 25.0+build3-0ubuntu0.12.10.1 26.0+build2-0ubuntu0.12.10.2
2014-01-09 09:59:50 upgrade libgimp2.0:amd64 2.8.2-1ubuntu1.1 2.8.2-1ubuntu1.2
2014-01-09 09:59:51 upgrade gimp-data:all 2.8.2-1ubuntu1.1 2.8.2-1ubuntu1.2
2014-01-09 09:59:53 upgrade gimp:amd64 2.8.2-1ubuntu1.1 2.8.2-1ubuntu1.2
2014-01-09 09:59:56 upgrade libxfont1:amd64 1:1.4.5-2 1:1.4.5-2ubuntu0.12.10.1
2014-01-09 09:59:56 upgrade mint-flashplugin-11:amd64 11.2.202.280 11.2.202.332
2014-01-09 09:59:58 upgrade pm-utils:all 1.4.1-9 1.4.1-9fix.ubuntu12.10
2014-01-09 09:59:59 upgrade thunderbird:amd64 1:24.1.0+build1-0ubuntu0.12.10.1 1:24.2.0+build1-0ubuntu0.12.10.1
2014-01-09 10:00:02 upgrade thunderbird-gnome-support:amd64 1:24.1.0+build1-0ubuntu0.12.10.1 1:24.2.0+build1-0ubuntu0.12.10.1
2014-01-09 10:00:03 upgrade unzip:amd64 6.0-7ubuntu1 6.0-7ubuntu1.1
2014-01-09 10:00:04 upgrade xserver-common:all 2:1.13.0-0ubuntu6.4 2:1.13.0-0ubuntu6.5
2014-01-09 10:00:05 upgrade xserver-xephyr:amd64 2:1.13.0-0ubuntu6.4 2:1.13.0-0ubuntu6.5
2014-01-09 22:19:40 upgrade libssl1.0.0:i386 1.0.1c-3ubuntu2.5 1.0.1c-3ubuntu2.6
2014-01-09 22:19:41 upgrade libssl1.0.0:amd64 1.0.1c-3ubuntu2.5 1.0.1c-3ubuntu2.6
2014-01-09 22:19:48 upgrade openssl:amd64 1.0.1c-3ubuntu2.5 1.0.1c-3ubuntu2.6
2014-01-25 22:35:56 upgrade base-files:amd64 6.5ubuntu11 6.5ubuntu12
2014-01-25 22:36:29 upgrade libdbus-1-3:i386 1.6.4-1ubuntu4 1.6.4-1ubuntu4.1
2014-01-25 22:36:30 upgrade libdbus-1-3:amd64 1.6.4-1ubuntu4 1.6.4-1ubuntu4.1
2014-01-25 22:36:34 upgrade mountall:amd64 2.42 2.42ubuntu0.4
2014-01-25 22:36:35 upgrade libdbus-glib-1-2:i386 0.100-1 0.100-1ubuntu0.1
2014-01-25 22:36:35 upgrade libdbus-glib-1-2:amd64 0.100-1 0.100-1ubuntu0.1
2014-01-25 22:36:41 upgrade printer-driver-hpijs:amd64 3.12.6-3ubuntu4.2 3.12.6-3ubuntu4.3
2014-01-25 22:36:42 upgrade printer-driver-postscript-hp:all 3.12.6-3ubuntu4.2 3.12.6-3ubuntu4.3
2014-01-25 22:36:43 upgrade libsane-hpaio:amd64 3.12.6-3ubuntu4.2 3.12.6-3ubuntu4.3
2014-01-25 22:36:43 upgrade hplip:amd64 3.12.6-3ubuntu4.2 3.12.6-3ubuntu4.3
2014-01-25 22:36:44 upgrade libhpmud0:amd64 3.12.6-3ubuntu4.2 3.12.6-3ubuntu4.3
2014-01-25 22:36:45 upgrade libcupsmime1:amd64 1.6.1-0ubuntu11.4 1.6.1-0ubuntu11.5
2014-01-25 22:36:46 upgrade cups:amd64 1.6.1-0ubuntu11.4 1.6.1-0ubuntu11.5
2014-01-25 22:36:48 upgrade cups-bsd:amd64 1.6.1-0ubuntu11.4 1.6.1-0ubuntu11.5
2014-01-25 22:36:49 upgrade cups-client:amd64 1.6.1-0ubuntu11.4 1.6.1-0ubuntu11.5
2014-01-25 22:36:50 upgrade libcups2:amd64 1.6.1-0ubuntu11.4 1.6.1-0ubuntu11.5
2014-01-25 22:36:50 upgrade libcups2:i386 1.6.1-0ubuntu11.4 1.6.1-0ubuntu11.5
2014-01-25 22:37:00 upgrade cups-common:all 1.6.1-0ubuntu11.4 1.6.1-0ubuntu11.5
2014-01-25 22:37:01 upgrade libcupsimage2:amd64 1.6.1-0ubuntu11.4 1.6.1-0ubuntu11.5
2014-01-25 22:37:01 upgrade libcupsimage2:i386 1.6.1-0ubuntu11.4 1.6.1-0ubuntu11.5
2014-01-25 22:37:05 upgrade hplip-data:all 3.12.6-3ubuntu4.2 3.12.6-3ubuntu4.3
2014-01-25 22:37:06 upgrade libcupsppdc1:amd64 1.6.1-0ubuntu11.4 1.6.1-0ubuntu11.5
2014-01-25 22:37:07 upgrade cups-ppdc:amd64 1.6.1-0ubuntu11.4 1.6.1-0ubuntu11.5
2014-01-25 22:37:08 upgrade printer-driver-hpcups:amd64 3.12.6-3ubuntu4.2 3.12.6-3ubuntu4.3
2014-01-25 22:37:09 upgrade python-dbus-dev:all 1.1.1-1 1.1.1-1ubuntu0.1
2014-01-25 22:37:09 upgrade python-dbus:amd64 1.1.1-1 1.1.1-1ubuntu0.1
2014-01-25 22:37:10 upgrade libcupscgi1:amd64 1.6.1-0ubuntu11.4 1.6.1-0ubuntu11.5
2014-01-25 22:37:11 upgrade mysql-common:all 5.5.34-0ubuntu0.12.10.1 5.5.35-0ubuntu0.12.10.1
2014-01-25 22:37:11 upgrade libmysqlclient18:i386 5.5.34-0ubuntu0.12.10.1 5.5.35-0ubuntu0.12.10.1
2014-01-25 22:37:12 upgrade libnspr4:i386 4.9.5-0ubuntu0.12.10.1 4.9.5-0ubuntu0.12.10.2
2014-01-25 22:37:13 upgrade libnspr4:amd64 4.9.5-0ubuntu0.12.10.1 4.9.5-0ubuntu0.12.10.2
2014-01-25 22:37:18 upgrade libnss3-1d:amd64 3.15.3.1-0ubuntu0.12.10.1 3.15.4-0ubuntu0.12.10.1
2014-01-25 22:37:19 upgrade libnss3:i386 3.15.3.1-0ubuntu0.12.10.1 3.15.4-0ubuntu0.12.10.1
2014-01-25 22:37:20 upgrade libnss3:amd64 3.15.3.1-0ubuntu0.12.10.1 3.15.4-0ubuntu0.12.10.1
2014-01-25 22:37:23 upgrade openjdk-7-jre:amd64 7u25-2.3.10-1ubuntu0.12.10.2 7u51-2.4.4-0ubuntu0.12.10.2
2014-01-25 22:37:25 upgrade icedtea-7-jre-jamvm:amd64 7u25-2.3.10-1ubuntu0.12.10.2 7u51-2.4.4-0ubuntu0.12.10.2
2014-01-25 22:37:25 upgrade openjdk-7-jre-headless:amd64 7u25-2.3.10-1ubuntu0.12.10.2 7u51-2.4.4-0ubuntu0.12.10.2
2014-01-25 22:37:28 upgrade bind9-host:amd64 1:9.8.1.dfsg.P1-4.2ubuntu3.3 1:9.8.1.dfsg.P1-4.2ubuntu3.4
2014-01-25 22:37:29 upgrade dnsutils:amd64 1:9.8.1.dfsg.P1-4.2ubuntu3.3 1:9.8.1.dfsg.P1-4.2ubuntu3.4
2014-01-25 22:37:30 upgrade libisc83:amd64 1:9.8.1.dfsg.P1-4.2ubuntu3.3 1:9.8.1.dfsg.P1-4.2ubuntu3.4
2014-01-25 22:37:30 upgrade libdns81:amd64 1:9.8.1.dfsg.P1-4.2ubuntu3.3 1:9.8.1.dfsg.P1-4.2ubuntu3.4
2014-01-25 22:37:31 upgrade libisccc80:amd64 1:9.8.1.dfsg.P1-4.2ubuntu3.3 1:9.8.1.dfsg.P1-4.2ubuntu3.4
2014-01-25 22:37:31 upgrade libisccfg82:amd64 1:9.8.1.dfsg.P1-4.2ubuntu3.3 1:9.8.1.dfsg.P1-4.2ubuntu3.4
2014-01-25 22:37:32 upgrade liblwres80:amd64 1:9.8.1.dfsg.P1-4.2ubuntu3.3 1:9.8.1.dfsg.P1-4.2ubuntu3.4
2014-01-25 22:37:35 upgrade libbind9-80:amd64 1:9.8.1.dfsg.P1-4.2ubuntu3.3 1:9.8.1.dfsg.P1-4.2ubuntu3.4
2014-01-25 22:37:35 upgrade dbus:amd64 1.6.4-1ubuntu4 1.6.4-1ubuntu4.1
2014-01-25 22:37:36 upgrade python3-dbus:amd64 1.1.1-1 1.1.1-1ubuntu0.1
2014-01-25 22:37:37 upgrade dbus-x11:amd64 1.6.4-1ubuntu4 1.6.4-1ubuntu4.1
2014-01-25 22:37:38 upgrade hpijs:all 3.12.6-3ubuntu4.2 3.12.6-3ubuntu4.3
2014-01-25 22:37:39 upgrade linux-firmware:all 1.95 1.95.1
2014-01-25 22:37:41 upgrade linux-generic:amd64 3.5.0.17.19 3.5.0.45.61
2014-01-25 22:37:41 upgrade linux-libc-dev:amd64 3.5.0-17.28 3.5.0-45.68
2014-01-25 22:37:43 upgrade linux-sound-base:all 1.0.25+dfsg-0ubuntu3 1.0.25+dfsg-0ubuntu3.1
2014-01-25 22:37:43 upgrade openjdk-7-jre-lib:all 7u25-2.3.10-1ubuntu0.12.10.2 7u51-2.4.4-0ubuntu0.12.10.2
2014-01-25 22:37:44 upgrade xserver-xorg-core:amd64 2:1.13.0-0ubuntu6 2:1.13.0-0ubuntu6.5
2014-01-25 22:37:45 upgrade xserver-xorg-video-intel:amd64 2:2.20.9-0ubuntu2 2:2.20.9-0ubuntu2.3
2014-01-25 22:37:46 upgrade xserver-xorg-video-nouveau:amd64 1:1.0.2-0ubuntu3 1:1.0.3-0ubuntu0.2
2014-01-25 22:37:46 upgrade xserver-xorg-video-openchrome:amd64 1:0.3.1-0ubuntu1 1:0.3.1-0ubuntu1.12.10.1

No errrors.

---


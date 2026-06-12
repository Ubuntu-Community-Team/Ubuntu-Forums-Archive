---
title: "xubuntu 14.04.4 places query"
date: 2017-02-20
forum: General Help
---

### Post by smokeyone2 on 2017-02-20
Hello

I am getting used to using Xubuntu when suddenly a load of folders and files have appeared in my Xubuntu/Places directory.

Where as before all the Places directory contained was Documents Downloads Videos Pictures Music it now contains
items like .bcast .cache .config .dbus .gconf etc etc  perhaps 50 folders & files -

Any ideas please why this has happened

Thanks

---

### Post by ajgreeny on 2017-02-20
No clue at this stage what has happened, but have a look at the hidden file in your home called **.gtk-bookmarks** which will show you if they are your own user bookmarks or system added.  If they are included in that list you can simply delete them from that simple text file.

Have you inadvertently at some time dragged highlighted folders into the left hand side-pane of thunar when trying to drag and drop a folder into another folder?

---

### Post by smokeyone2 on 2017-02-20
Thank you for your advice - system added bookmarks - but other strange things have happened it seems.
Comments files appear to have been added all over the place, screen resolution has decided to change, thumbnails are now tiny
and my bookmarks from Quipzilla have vanished.

An automatic update maybe !

Thanks again

---

### Post by vasa1 on 2017-02-20
Run```
sudo apt-get update
```and if all looks okay, run```
sudo apt-get upgrade
```
If there's anything untoward, post the entire contents here using code tags.

As for recent automatic updates, you could post the output of```
grep "status installed" /var/log/dpkg.log.1 /var/log/dpkg.log | sort -u -k5 | sort -k1
```
That'll list what has been updated on your system.

Also, have you rebooted your system?

---

### Post by smokeyone2 on 2017-02-20
Thanks for the advice -

Have run sudo apt-get update & sudo apt-get upgrade & rebooted but the problem persists.
Could list 
```
grep "status installed" /var/log/dpkg.log.1 /var/log/dpkg.log | sort -u -k5 | sort -k1
```

but the list is a mile long.
If you wish me to post I will of course but it starts like this

```
xubuntu@xubuntu:~/Desktop$ grep "status installed" /var/log/dpkg.log.1 /var/log/dpkg.log | sort -u -k5 | sort -k1
/var/log/dpkg.log.1:2017-01-30 06:57:03 status installed vivaldi-stable:amd64 1.6.689.46-1
/var/log/dpkg.log.1:2017-01-30 06:57:25 status installed desktop-file-utils:amd64 0.22-1ubuntu1
/var/log/dpkg.log.1:2017-01-30 06:57:25 status installed gnome-menus:amd64 3.10.1-0ubuntu2
/var/log/dpkg.log.1:2017-01-30 06:57:25 status installed mime-support:all 3.54ubuntu1.1
/var/log/dpkg.log.1:2017-01-30 07:03:04 status installed man-db:amd64 2.6.7.1-1u
```

Also just to mention other odd signs - my email client mislaid it's files - still on the system thank goodness - but was not associated with them. All fonts
have gone extra small and cursor right clicking on the desktop produces a tiny screen of open new window etc etc. Now thinking about a fresh install !

Thanks again

---

### Post by Impavidus on 2017-02-20
> **smokeyone2 said:**
> 
Where as before all the Places directory contained was Documents Downloads Videos Pictures Music it now contains
items like .bcast .cache .config .dbus .gconf etc etc  perhaps 50 folders & files -


Your places always contained .cache, .dbus etc. They were just hidden. Files and directories starting with . are by default hidden, so for some reason they are now no longer. So don't delete them, as that will cause more problems.

As for your other problems, and what caused it to happen, I've no idea. Or did those problems only appear after you began messing with those newly appeared directories?

---

### Post by ajgreeny on 2017-02-20
A variation of the command shown by vasa1 will show us exactly what has been upgraded on your system recently in date order, rather than everything that is now installed.
```
grep -i " upgrade " /var/log/dpkg.log.1 /var/log/dpkg.log
```
and another similar command 
```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log
```
will show all additional packages that have been installed recently.

Give that a try, though I somehow doubt that there will be anything that immediately springs to light, but if you can relate the output of those commands to the date when you first saw this problem it might help give a clue.

---

### Post by smokeyone2 on 2017-02-20
Thank you all for the help -

```
xubuntu@xubuntu:~/Desktop$ grep -i " upgrade " /var/log/dpkg.log.1 /var/log/dpkg.log
/var/log/dpkg.log:2017-02-20 10:06:46 upgrade base-files:amd64 7.2ubuntu5.4 7.2ubuntu5.5
/var/log/dpkg.log:2017-02-20 10:07:13 upgrade mount:amd64 2.20.1-5.1ubuntu20.7 2.20.1-5.1ubuntu20.9
/var/log/dpkg.log:2017-02-20 10:07:15 upgrade tar:amd64 1.27.1-1 1.27.1-1ubuntu0.1
/var/log/dpkg.log:2017-02-20 10:07:20 upgrade lsb-base:all 4.1+Debian11ubuntu6.1 4.1+Debian11ubuntu6.2
/var/log/dpkg.log:2017-02-20 10:07:22 upgrade tzdata-java:all 2016f-0ubuntu0.14.04 2016j-0ubuntu0.14.04
/var/log/dpkg.log:2017-02-20 10:07:23 upgrade tzdata:all 2016f-0ubuntu0.14.04 2016j-0ubuntu0.14.04
/var/log/dpkg.log:2017-02-20 10:07:26 upgrade util-linux:amd64 2.20.1-5.1ubuntu20.7 2.20.1-5.1ubuntu20.9
/var/log/dpkg.log:2017-02-20 10:07:30 upgrade libapt-pkg4.12:amd64 1.0.1ubuntu2.14 1.0.1ubuntu2.17
/var/log/dpkg.log:2017-02-20 10:07:33 upgrade gpgv:amd64 1.4.16-1ubuntu2.3 1.4.16-1ubuntu2.4
/var/log/dpkg.log:2017-02-20 10:07:35 upgrade gnupg:amd64 1.4.16-1ubuntu2.3 1.4.16-1ubuntu2.4
/var/log/dpkg.log:2017-02-20 10:07:38 upgrade apt:amd64 1.0.1ubuntu2.14 1.0.1ubuntu2.17
/var/log/dpkg.log:2017-02-20 10:07:43 upgrade bsdutils:amd64 1:2.20.1-5.1ubuntu20.7 1:2.20.1-5.1ubuntu20.9
/var/log/dpkg.log:2017-02-20 10:07:47 upgrade libuuid1:amd64 2.20.1-5.1ubuntu20.7 2.20.1-5.1ubuntu20.9
/var/log/dpkg.log:2017-02-20 10:07:49 upgrade libblkid1:amd64 2.20.1-5.1ubuntu20.7 2.20.1-5.1ubuntu20.9
/var/log/dpkg.log:2017-02-20 10:07:51 upgrade libmount1:amd64 2.20.1-5.1ubuntu20.7 2.20.1-5.1ubuntu20.9
/var/log/dpkg.log:2017-02-20 10:07:53 upgrade libapt-inst1.5:amd64 1.0.1ubuntu2.14 1.0.1ubuntu2.17
/var/log/dpkg.log:2017-02-20 10:07:53 upgrade libgcrypt11:amd64 1.5.3-2ubuntu4.3 1.5.3-2ubuntu4.4
/var/log/dpkg.log:2017-02-20 10:07:54 upgrade libgnutls-openssl27:amd64 2.12.23-12ubuntu2.5 2.12.23-12ubuntu2.6
/var/log/dpkg.log:2017-02-20 10:07:55 upgrade libgnutls26:amd64 2.12.23-12ubuntu2.5 2.12.23-12ubuntu2.6
/var/log/dpkg.log:2017-02-20 10:07:56 upgrade python3.4:amd64 3.4.3-1ubuntu1~14.04.3 3.4.3-1ubuntu1~14.04.5
/var/log/dpkg.log:2017-02-20 10:07:57 upgrade python3.4-minimal:amd64 3.4.3-1ubuntu1~14.04.3 3.4.3-1ubuntu1~14.04.5
/var/log/dpkg.log:2017-02-20 10:07:58 upgrade libpython3.4:amd64 3.4.3-1ubuntu1~14.04.3 3.4.3-1ubuntu1~14.04.5
/var/log/dpkg.log:2017-02-20 10:07:59 upgrade libpython3.4-stdlib:amd64 3.4.3-1ubuntu1~14.04.3 3.4.3-1ubuntu1~14.04.5
/var/log/dpkg.log:2017-02-20 10:08:00 upgrade libssl1.0.0:amd64 1.0.1f-1ubuntu2.19 1.0.1f-1ubuntu2.22
/var/log/dpkg.log:2017-02-20 10:08:01 upgrade libpython3.4-minimal:amd64 3.4.3-1ubuntu1~14.04.3 3.4.3-1ubuntu1~14.04.5
/var/log/dpkg.log:2017-02-20 10:08:02 upgrade ntpdate:amd64 1:4.2.6.p5+dfsg-3ubuntu2.14.04.8 1:4.2.6.p5+dfsg-3ubuntu2.14.04.10
/var/log/dpkg.log:2017-02-20 10:08:03 upgrade libdbus-1-3:amd64 1.6.18-0ubuntu4.3 1.6.18-0ubuntu4.5
/var/log/dpkg.log:2017-02-20 10:08:04 upgrade udev:amd64 204-5ubuntu20.19 204-5ubuntu20.24
/var/log/dpkg.log:2017-02-20 10:08:05 upgrade libudev1:amd64 204-5ubuntu20.19 204-5ubuntu20.24
/var/log/dpkg.log:2017-02-20 10:08:06 upgrade libk5crypto3:amd64 1.12+dfsg-2ubuntu5.2 1.12+dfsg-2ubuntu5.3
/var/log/dpkg.log:2017-02-20 10:08:07 upgrade libgssapi-krb5-2:amd64 1.12+dfsg-2ubuntu5.2 1.12+dfsg-2ubuntu5.3
/var/log/dpkg.log:2017-02-20 10:08:07 upgrade libkrb5-3:amd64 1.12+dfsg-2ubuntu5.2 1.12+dfsg-2ubuntu5.3
/var/log/dpkg.log:2017-02-20 10:08:08 upgrade libkrb5support0:amd64 1.12+dfsg-2ubuntu5.2 1.12+dfsg-2ubuntu5.3
/var/log/dpkg.log:2017-02-20 10:08:09 upgrade libidn11:amd64 1.28-1ubuntu2 1.28-1ubuntu2.1
/var/log/dpkg.log:2017-02-20 10:08:09 upgrade libcurl3-gnutls:amd64 7.35.0-1ubuntu2.7 7.35.0-1ubuntu2.10
/var/log/dpkg.log:2017-02-20 10:08:10 upgrade libpam-systemd:amd64 204-5ubuntu20.19 204-5ubuntu20.24
/var/log/dpkg.log:2017-02-20 10:08:11 upgrade systemd-services:amd64 204-5ubuntu20.19 204-5ubuntu20.24
/var/log/dpkg.log:2017-02-20 10:08:12 upgrade libsystemd-daemon0:amd64 204-5ubuntu20.19 204-5ubuntu20.24
/var/log/dpkg.log:2017-02-20 10:08:13 upgrade libapparmor1:amd64 2.8.95~2430-0ubuntu5.3 2.10.95-0ubuntu2.5~14.04.1
/var/log/dpkg.log:2017-02-20 10:08:13 upgrade libsystemd-login0:amd64 204-5ubuntu20.19 204-5ubuntu20.24
/var/log/dpkg.log:2017-02-20 10:08:14 upgrade dbus:amd64 1.6.18-0ubuntu4.3 1.6.18-0ubuntu4.5
/var/log/dpkg.log:2017-02-20 10:08:15 upgrade chromium-browser-l10n:all 51.0.2704.79-0ubuntu0.14.04.1.1121 53.0.2785.143-0ubuntu0.14.04.1.1145
/var/log/dpkg.log:2017-02-20 10:08:17 upgrade libfontconfig1:amd64 2.11.0-0ubuntu4.1 2.11.0-0ubuntu4.2
/var/log/dpkg.log:2017-02-20 10:08:18 upgrade fontconfig-config:all 2.11.0-0ubuntu4.1 2.11.0-0ubuntu4.2
/var/log/dpkg.log:2017-02-20 10:08:19 upgrade libgdk-pixbuf2.0-0:amd64 2.30.7-0ubuntu1.2 2.30.7-0ubuntu1.6
/var/log/dpkg.log:2017-02-20 10:08:20 upgrade libgdk-pixbuf2.0-common:all 2.30.7-0ubuntu1.2 2.30.7-0ubuntu1.6
/var/log/dpkg.log:2017-02-20 10:08:20 upgrade libnss3-nssdb:all 2:3.23-0ubuntu0.14.04.1 2:3.26.2-0ubuntu0.14.04.3
/var/log/dpkg.log:2017-02-20 10:08:21 upgrade libnss3:amd64 2:3.23-0ubuntu0.14.04.1 2:3.26.2-0ubuntu0.14.04.3
/var/log/dpkg.log:2017-02-20 10:08:22 upgrade chromium-browser:amd64 51.0.2704.79-0ubuntu0.14.04.1.1121 53.0.2785.143-0ubuntu0.14.04.1.1145
/var/log/dpkg.log:2017-02-20 10:08:30 upgrade chromium-codecs-ffmpeg-extra:amd64 51.0.2704.79-0ubuntu0.14.04.1.1121 53.0.2785.143-0ubuntu0.14.04.1.1145
/var/log/dpkg.log:2017-02-20 10:08:30 upgrade libp11-kit-gnome-keyring:amd64 3.10.1-1ubuntu4.2 3.10.1-1ubuntu4.3
/var/log/dpkg.log:2017-02-20 10:08:31 upgrade dbus-x11:amd64 1.6.18-0ubuntu4.3 1.6.18-0ubuntu4.5
/var/log/dpkg.log:2017-02-20 10:08:32 upgrade gnome-keyring:amd64 3.10.1-1ubuntu4.2 3.10.1-1ubuntu4.3
/var/log/dpkg.log:2017-02-20 10:08:33 upgrade libgudev-1.0-0:amd64 1:204-5ubuntu20.19 1:204-5ubuntu20.24
/var/log/dpkg.log:2017-02-20 10:08:34 upgrade gstreamer0.10-plugins-good:amd64 0.10.31-3+nmu1ubuntu5 0.10.31-3+nmu1ubuntu5.2
/var/log/dpkg.log:2017-02-20 10:08:35 upgrade imagemagick-common:all 8:6.7.7.10-6ubuntu3.1 8:6.7.7.10-6ubuntu3.3
/var/log/dpkg.log:2017-02-20 10:08:36 upgrade libavutil52:amd64 6:9.18-0ubuntu0.14.04.1 6:9.20-0ubuntu0.14.04.1
/var/log/dpkg.log:2017-02-20 10:08:36 upgrade libavcodec54:amd64 6:9.18-0ubuntu0.14.04.1 6:9.20-0ubuntu0.14.04.1
/var/log/dpkg.log:2017-02-20 10:08:38 upgrade libavformat54:amd64 6:9.18-0ubuntu0.14.04.1 6:9.20-0ubuntu0.14.04.1
/var/log/dpkg.log:2017-02-20 10:08:38 upgrade libavdevice53:amd64 6:9.18-0ubuntu0.14.04.1 6:9.20-0ubuntu0.14.04.1
/var/log/dpkg.log:2017-02-20 10:08:39 upgrade libavresample1:amd64 6:9.18-0ubuntu0.14.04.1 6:9.20-0ubuntu0.14.04.1
/var/log/dpkg.log:2017-02-20 10:08:40 upgrade libswscale2:amd64 6:9.18-0ubuntu0.14.04.1 6:9.20-0ubuntu0.14.04.1
/var/log/dpkg.log:2017-02-20 10:08:41 upgrade libavfilter3:amd64 6:9.18-0ubuntu0.14.04.1 6:9.20-0ubuntu0.14.04.1
/var/log/dpkg.log:2017-02-20 10:08:41 upgrade libav-tools:amd64 6:9.18-0ubuntu0.14.04.1 6:9.20-0ubuntu0.14.04.1
/var/log/dpkg.log:2017-02-20 10:08:43 upgrade libavahi-common-data:amd64 0.6.31-4ubuntu1 0.6.31-4ubuntu1.1
/var/log/dpkg.log:2017-02-20 10:08:43 upgrade libavahi-common3:amd64 0.6.31-4ubuntu1 0.6.31-4ubuntu1.1
/var/log/dpkg.log:2017-02-20 10:08:44 upgrade libavahi-client3:amd64 0.6.31-4ubuntu1 0.6.31-4ubuntu1.1
/var/log/dpkg.log:2017-02-20 10:08:45 upgrade libavahi-core7:amd64 0.6.31-4ubuntu1 0.6.31-4ubuntu1.1
/var/log/dpkg.log:2017-02-20 10:08:46 upgrade libavahi-glib1:amd64 0.6.31-4ubuntu1 0.6.31-4ubuntu1.1
/var/log/dpkg.log:2017-02-20 10:08:48 upgrade libcurl3:amd64 7.35.0-1ubuntu2.7 7.35.0-1ubuntu2.10
/var/log/dpkg.log:2017-02-20 10:08:48 upgrade libxpm4:amd64 1:3.5.10-1 1:3.5.10-1ubuntu0.1
/var/log/dpkg.log:2017-02-20 10:08:49 upgrade libgd3:amd64 2.1.0-3ubuntu0.2 2.1.0-3ubuntu0.5
/var/log/dpkg.log:2017-02-20 10:08:50 upgrade libgstreamer1.0-0:amd64 1.2.4-0ubuntu1 1.2.4-0ubuntu1.1
/var/log/dpkg.log:2017-02-20 10:08:51 upgrade libharfbuzz0b:amd64 0.9.27-1ubuntu1 0.9.27-1ubuntu1.1
/var/log/dpkg.log:2017-02-20 10:08:52 upgrade libharfbuzz-icu0:amd64 0.9.27-1ubuntu1 0.9.27-1ubuntu1.1
/var/log/dpkg.log:2017-02-20 10:08:52 upgrade libnettle4:amd64 2.7.1-1ubuntu0.1 2.7.1-1ubuntu0.2
/var/log/dpkg.log:2017-02-20 10:08:53 upgrade libhogweed2:amd64 2.7.1-1ubuntu0.1 2.7.1-1ubuntu0.2
/var/log/dpkg.log:2017-02-20 10:08:54 upgrade libmagickwand5:amd64 8:6.7.7.10-6ubuntu3.1 8:6.7.7.10-6ubuntu3.3
/var/log/dpkg.log:2017-02-20 10:08:54 upgrade libmagickcore5-extra:amd64 8:6.7.7.10-6ubuntu3.1 8:6.7.7.10-6ubuntu3.3
/var/log/dpkg.log:2017-02-20 10:08:55 upgrade libmagickcore5:amd64 8:6.7.7.10-6ubuntu3.1 8:6.7.7.10-6ubuntu3.3
/var/log/dpkg.log:2017-02-20 10:08:56 upgrade mysql-common:all 5.5.50-0ubuntu0.14.04.1 5.5.54-0ubuntu0.14.04.1
/var/log/dpkg.log:2017-02-20 10:08:57 upgrade libmysqlclient18:amd64 5.5.50-0ubuntu0.14.04.1 5.5.54-0ubuntu0.14.04.1
/var/log/dpkg.log:2017-02-20 10:08:57 upgrade libnl-route-3-200:amd64 3.2.21-1ubuntu3 3.2.21-1ubuntu4
/var/log/dpkg.log:2017-02-20 10:08:58 upgrade libnl-genl-3-200:amd64 3.2.21-1ubuntu3 3.2.21-1ubuntu4
/var/log/dpkg.log:2017-02-20 10:08:59 upgrade libnl-3-200:amd64 3.2.21-1ubuntu3 3.2.21-1ubuntu4
/var/log/dpkg.log:2017-02-20 10:08:59 upgrade libpam-gnome-keyring:amd64 3.10.1-1ubuntu4.2 3.10.1-1ubuntu4.3
/var/log/dpkg.log:2017-02-20 10:09:00 upgrade libpcsclite1:amd64 1.8.10-1ubuntu1 1.8.10-1ubuntu1.1
/var/log/dpkg.log:2017-02-20 10:09:01 upgrade python2.7:amd64 2.7.6-8ubuntu0.2 2.7.6-8ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:09:02 upgrade libpython2.7:amd64 2.7.6-8ubuntu0.2 2.7.6-8ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:09:02 upgrade libpython2.7-stdlib:amd64 2.7.6-8ubuntu0.2 2.7.6-8ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:09:04 upgrade python2.7-minimal:amd64 2.7.6-8ubuntu0.2 2.7.6-8ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:09:05 upgrade libpython2.7-minimal:amd64 2.7.6-8ubuntu0.2 2.7.6-8ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:09:06 upgrade ghostscript:amd64 9.10~dfsg-0ubuntu10.4 9.10~dfsg-0ubuntu10.6
/var/log/dpkg.log:2017-02-20 10:09:06 upgrade ghostscript-x:amd64 9.10~dfsg-0ubuntu10.4 9.10~dfsg-0ubuntu10.6
/var/log/dpkg.log:2017-02-20 10:09:07 upgrade libgs9-common:all 9.10~dfsg-0ubuntu10.4 9.10~dfsg-0ubuntu10.6
/var/log/dpkg.log:2017-02-20 10:09:08 upgrade libgs9:amd64 9.10~dfsg-0ubuntu10.4 9.10~dfsg-0ubuntu10.6
/var/log/dpkg.log:2017-02-20 10:09:09 upgrade libspectre1:amd64 0.2.7-2ubuntu1.1 0.2.7-2ubuntu1.2
/var/log/dpkg.log:2017-02-20 10:09:10 upgrade libwbclient0:amd64 2:4.3.9+dfsg-0ubuntu0.14.04.3 2:4.3.11+dfsg-0ubuntu0.14.04.4
/var/log/dpkg.log:2017-02-20 10:09:11 upgrade klibc-utils:amd64 2.0.3-0ubuntu1.14.04.1 2.0.3-0ubuntu1.14.04.2
/var/log/dpkg.log:2017-02-20 10:09:11 upgrade libklibc:amd64 2.0.3-0ubuntu1.14.04.1 2.0.3-0ubuntu1.14.04.2
/var/log/dpkg.log:2017-02-20 10:09:12 upgrade initramfs-tools:all 0.103ubuntu4.4 0.103ubuntu4.6
/var/log/dpkg.log:2017-02-20 10:09:13 upgrade initramfs-tools-bin:amd64 0.103ubuntu4.4 0.103ubuntu4.6
/var/log/dpkg.log:2017-02-20 10:09:17 upgrade openjdk-7-jre:amd64 7u101-2.6.6-0ubuntu0.14.04.1 7u121-2.6.8-1ubuntu0.14.04.3
/var/log/dpkg.log:2017-02-20 10:09:19 upgrade openjdk-7-jre-headless:amd64 7u101-2.6.6-0ubuntu0.14.04.1 7u121-2.6.8-1ubuntu0.14.04.3
/var/log/dpkg.log:2017-02-20 10:09:24 upgrade python-crypto:amd64 2.6.1-4build1 2.6.1-4ubuntu0.2
/var/log/dpkg.log:2017-02-20 10:09:26 upgrade libsmbclient:amd64 2:4.3.9+dfsg-0ubuntu0.14.04.3 2:4.3.11+dfsg-0ubuntu0.14.04.4
/var/log/dpkg.log:2017-02-20 10:09:26 upgrade smbclient:amd64 2:4.3.9+dfsg-0ubuntu0.14.04.3 2:4.3.11+dfsg-0ubuntu0.14.04.4
/var/log/dpkg.log:2017-02-20 10:09:27 upgrade samba-common-bin:amd64 2:4.3.9+dfsg-0ubuntu0.14.04.3 2:4.3.11+dfsg-0ubuntu0.14.04.4
/var/log/dpkg.log:2017-02-20 10:09:28 upgrade python-samba:amd64 2:4.3.9+dfsg-0ubuntu0.14.04.3 2:4.3.11+dfsg-0ubuntu0.14.04.4
/var/log/dpkg.log:2017-02-20 10:09:29 upgrade samba-libs:amd64 2:4.3.9+dfsg-0ubuntu0.14.04.3 2:4.3.11+dfsg-0ubuntu0.14.04.4
/var/log/dpkg.log:2017-02-20 10:09:31 upgrade samba-common:all 2:4.3.9+dfsg-0ubuntu0.14.04.3 2:4.3.11+dfsg-0ubuntu0.14.04.4
/var/log/dpkg.log:2017-02-20 10:09:32 upgrade ubuntu-drivers-common:amd64 1:0.2.91.11 1:0.2.91.12
/var/log/dpkg.log:2017-02-20 10:09:33 upgrade lsb-release:all 4.1+Debian11ubuntu6.1 4.1+Debian11ubuntu6.2
/var/log/dpkg.log:2017-02-20 10:09:34 upgrade ubuntu-release-upgrader-gtk:all 1:0.220.8 1:0.220.9
/var/log/dpkg.log:2017-02-20 10:09:35 upgrade ubuntu-release-upgrader-core:all 1:0.220.8 1:0.220.9
/var/log/dpkg.log:2017-02-20 10:09:36 upgrade update-manager:all 1:0.196.14 1:0.196.22
/var/log/dpkg.log:2017-02-20 10:09:37 upgrade python3-distupgrade:all 1:0.220.8 1:0.220.9
/var/log/dpkg.log:2017-02-20 10:09:37 upgrade python3-update-manager:all 1:0.196.14 1:0.196.22
/var/log/dpkg.log:2017-02-20 10:09:38 upgrade update-manager-core:all 1:0.196.14 1:0.196.22
/var/log/dpkg.log:2017-02-20 10:09:39 upgrade update-notifier:amd64 0.154.1ubuntu1 0.154.1ubuntu2
/var/log/dpkg.log:2017-02-20 10:09:40 upgrade update-notifier-common:all 0.154.1ubuntu1 0.154.1ubuntu2
/var/log/dpkg.log:2017-02-20 10:09:41 upgrade gstreamer1.0-plugins-bad-videoparsers:amd64 1.2.4-1~ubuntu1 1.2.4-1~ubuntu1.1
/var/log/dpkg.log:2017-02-20 10:09:42 upgrade gstreamer1.0-plugins-bad-faad:amd64 1.2.4-1~ubuntu1 1.2.4-1~ubuntu1.1
/var/log/dpkg.log:2017-02-20 10:09:42 upgrade gstreamer1.0-plugins-bad:amd64 1.2.4-1~ubuntu1 1.2.4-1~ubuntu1.1
/var/log/dpkg.log:2017-02-20 10:09:43 upgrade gstreamer1.0-plugins-good:amd64 1.2.4-1~ubuntu1 1.2.4-1~ubuntu1.3
/var/log/dpkg.log:2017-02-20 10:09:44 upgrade libgstreamer-plugins-good1.0-0:amd64 1.2.4-1~ubuntu1 1.2.4-1~ubuntu1.3
/var/log/dpkg.log:2017-02-20 10:09:45 upgrade libgstreamer-plugins-bad1.0-0:amd64 1.2.4-1~ubuntu1 1.2.4-1~ubuntu1.1
/var/log/dpkg.log:2017-02-20 10:09:45 upgrade libgme0:amd64 0.5.5-2 0.5.5-2ubuntu0.14.04.1
/var/log/dpkg.log:2017-02-20 10:09:46 upgrade libupnp6:amd64 1:1.6.17-1.2 1:1.6.17-1.2+deb7u2build0.14.04.1
/var/log/dpkg.log:2017-02-20 10:09:47 upgrade apt-utils:amd64 1.0.1ubuntu2.14 1.0.1ubuntu2.17
/var/log/dpkg.log:2017-02-20 10:09:47 upgrade init-system-helpers:all 1.14 1.14ubuntu1
/var/log/dpkg.log:2017-02-20 10:09:48 upgrade isc-dhcp-client:amd64 4.2.4-7ubuntu12.5 4.2.4-7ubuntu12.8
/var/log/dpkg.log:2017-02-20 10:09:51 upgrade isc-dhcp-common:amd64 4.2.4-7ubuntu12.5 4.2.4-7ubuntu12.8
/var/log/dpkg.log:2017-02-20 10:09:51 upgrade sudo:amd64 1.8.9p5-1ubuntu1.2 1.8.9p5-1ubuntu1.3
/var/log/dpkg.log:2017-02-20 10:09:52 upgrade vim-tiny:amd64 2:7.4.052-1ubuntu3 2:7.4.052-1ubuntu3.1
/var/log/dpkg.log:2017-02-20 10:09:53 upgrade vim-common:amd64 2:7.4.052-1ubuntu3 2:7.4.052-1ubuntu3.1
/var/log/dpkg.log:2017-02-20 10:09:54 upgrade accountsservice:amd64 0.6.35-0ubuntu7.2 0.6.35-0ubuntu7.3
/var/log/dpkg.log:2017-02-20 10:09:55 upgrade libaccountsservice0:amd64 0.6.35-0ubuntu7.2 0.6.35-0ubuntu7.3
/var/log/dpkg.log:2017-02-20 10:09:56 upgrade libapparmor-perl:amd64 2.8.95~2430-0ubuntu5.3 2.10.95-0ubuntu2.5~14.04.1
/var/log/dpkg.log:2017-02-20 10:09:56 upgrade apparmor:amd64 2.8.95~2430-0ubuntu5.3 2.10.95-0ubuntu2.5~14.04.1
/var/log/dpkg.log:2017-02-20 10:09:57 upgrade apt-transport-https:amd64 1.0.1ubuntu2.14 1.0.1ubuntu2.17
/var/log/dpkg.log:2017-02-20 10:09:58 upgrade bind9-host:amd64 1:9.9.5.dfsg-3ubuntu0.8 1:9.9.5.dfsg-3ubuntu0.13
/var/log/dpkg.log:2017-02-20 10:09:59 upgrade dnsutils:amd64 1:9.9.5.dfsg-3ubuntu0.8 1:9.9.5.dfsg-3ubuntu0.13
/var/log/dpkg.log:2017-02-20 10:09:59 upgrade libisc95:amd64 1:9.9.5.dfsg-3ubuntu0.8 1:9.9.5.dfsg-3ubuntu0.13
/var/log/dpkg.log:2017-02-20 10:10:00 upgrade libdns100:amd64 1:9.9.5.dfsg-3ubuntu0.8 1:9.9.5.dfsg-3ubuntu0.13
/var/log/dpkg.log:2017-02-20 10:10:01 upgrade libisccc90:amd64 1:9.9.5.dfsg-3ubuntu0.8 1:9.9.5.dfsg-3ubuntu0.13
/var/log/dpkg.log:2017-02-20 10:10:01 upgrade libisccfg90:amd64 1:9.9.5.dfsg-3ubuntu0.8 1:9.9.5.dfsg-3ubuntu0.13
/var/log/dpkg.log:2017-02-20 10:10:02 upgrade liblwres90:amd64 1:9.9.5.dfsg-3ubuntu0.8 1:9.9.5.dfsg-3ubuntu0.13
/var/log/dpkg.log:2017-02-20 10:10:03 upgrade libbind9-90:amd64 1:9.9.5.dfsg-3ubuntu0.8 1:9.9.5.dfsg-3ubuntu0.13
/var/log/dpkg.log:2017-02-20 10:10:03 upgrade krb5-locales:all 1.12+dfsg-2ubuntu5.2 1.12+dfsg-2ubuntu5.3
/var/log/dpkg.log:2017-02-20 10:10:04 upgrade openssh-client:amd64 1:6.6p1-2ubuntu2.7 1:6.6p1-2ubuntu2.8
/var/log/dpkg.log:2017-02-20 10:10:05 upgrade openssl:amd64 1.0.1f-1ubuntu2.19 1.0.1f-1ubuntu2.22
/var/log/dpkg.log:2017-02-20 10:10:06 upgrade uuid-runtime:amd64 2.20.1-5.1ubuntu20.7 2.20.1-5.1ubuntu20.9
/var/log/dpkg.log:2017-02-20 10:10:07 upgrade grub-pc:amd64 2.02~beta2-9ubuntu1.11 2.02~beta2-9ubuntu1.12
/var/log/dpkg.log:2017-02-20 10:10:07 upgrade grub-pc-bin:amd64 2.02~beta2-9ubuntu1.11 2.02~beta2-9ubuntu1.12
/var/log/dpkg.log:2017-02-20 10:10:08 upgrade grub2-common:amd64 2.02~beta2-9ubuntu1.11 2.02~beta2-9ubuntu1.12
/var/log/dpkg.log:2017-02-20 10:10:09 upgrade grub-common:amd64 2.02~beta2-9ubuntu1.11 2.02~beta2-9ubuntu1.12
/var/log/dpkg.log:2017-02-20 10:10:10 upgrade python3-problem-report:all 2.14.1-0ubuntu3.21 2.14.1-0ubuntu3.23
/var/log/dpkg.log:2017-02-20 10:10:11 upgrade python3-apport:all 2.14.1-0ubuntu3.21 2.14.1-0ubuntu3.23
/var/log/dpkg.log:2017-02-20 10:10:12 upgrade apport:all 2.14.1-0ubuntu3.21 2.14.1-0ubuntu3.23
/var/log/dpkg.log:2017-02-20 10:10:14 upgrade apport-gtk:all 2.14.1-0ubuntu3.21 2.14.1-0ubuntu3.23
/var/log/dpkg.log:2017-02-20 10:10:14 upgrade avahi-autoipd:amd64 0.6.31-4ubuntu1 0.6.31-4ubuntu1.1
/var/log/dpkg.log:2017-02-20 10:10:15 upgrade avahi-daemon:amd64 0.6.31-4ubuntu1 0.6.31-4ubuntu1.1
/var/log/dpkg.log:2017-02-20 10:10:16 upgrade avahi-utils:amd64 0.6.31-4ubuntu1 0.6.31-4ubuntu1.1
/var/log/dpkg.log:2017-02-20 10:10:17 upgrade cinelerra-cv:amd64 1:2.3.git.20160731-0~ppa1~trusty2 1:2.3.git.20170212-0~ppa1~trusty1
/var/log/dpkg.log:2017-02-20 10:10:19 upgrade libguicast1-cv:amd64 1:2.3.git.20160731-0~ppa1~trusty2 1:2.3.git.20170212-0~ppa1~trusty1
/var/log/dpkg.log:2017-02-20 10:10:19 upgrade libmpeg3cine-cv:amd64 1:2.3.git.20160731-0~ppa1~trusty2 1:2.3.git.20170212-0~ppa1~trusty1
/var/log/dpkg.log:2017-02-20 10:10:20 upgrade libquicktimecine-cv:amd64 1:2.3.git.20160731-0~ppa1~trusty2 1:2.3.git.20170212-0~ppa1~trusty1
/var/log/dpkg.log:2017-02-20 10:10:21 upgrade dkms:all 2.2.0.3-1.1ubuntu5.14.04.7 2.2.0.3-1.1ubuntu5.14.04.9
/var/log/dpkg.log:2017-02-20 10:10:22 upgrade file-roller:amd64 3.10.2.1-0ubuntu4.1 3.10.2.1-0ubuntu4.2
/var/log/dpkg.log:2017-02-20 10:10:23 upgrade firefox-locale-en:amd64 47.0+build3-0ubuntu0.14.04.1 51.0.1+build2-0ubuntu0.14.04.2
/var/log/dpkg.log:2017-02-20 10:10:24 upgrade fontconfig:amd64 2.11.0-0ubuntu4.1 2.11.0-0ubuntu4.2
/var/log/dpkg.log:2017-02-20 10:10:27 upgrade gir1.2-gdkpixbuf-2.0:amd64 2.30.7-0ubuntu1.2 2.30.7-0ubuntu1.6
/var/log/dpkg.log:2017-02-20 10:10:28 upgrade gir1.2-gstreamer-1.0:amd64 1.2.4-0ubuntu1 1.2.4-0ubuntu1.1
/var/log/dpkg.log:2017-02-20 10:10:28 upgrade gir1.2-gudev-1.0:amd64 1:204-5ubuntu20.19 1:204-5ubuntu20.24
/var/log/dpkg.log:2017-02-20 10:10:29 upgrade gstreamer0.10-pulseaudio:amd64 0.10.31-3+nmu1ubuntu5 0.10.31-3+nmu1ubuntu5.2
/var/log/dpkg.log:2017-02-20 10:10:29 upgrade gstreamer1.0-pulseaudio:amd64 1.2.4-1~ubuntu1 1.2.4-1~ubuntu1.3
/var/log/dpkg.log:2017-02-20 10:10:30 upgrade gstreamer1.0-tools:amd64 1.2.4-0ubuntu1 1.2.4-0ubuntu1.1
/var/log/dpkg.log:2017-02-20 10:10:31 upgrade icoutils:amd64 0.31.0-2 0.31.0-2+deb8u2build0.14.04.1
/var/log/dpkg.log:2017-02-20 10:10:31 upgrade imagemagick:amd64 8:6.7.7.10-6ubuntu3.1 8:6.7.7.10-6ubuntu3.3
/var/log/dpkg.log:2017-02-20 10:10:32 upgrade libakonadi-kcal4:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:33 upgrade libmicroblog4:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:34 upgrade libktnef4:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:34 upgrade libkcal4:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:35 upgrade libakonadi-calendar4:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:36 upgrade libkcalutils4:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:37 upgrade libkalarmcal2:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:38 upgrade libkpimidentities4:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:38 upgrade libakonadi-contact4:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:39 upgrade libkpimutils4:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:40 upgrade libkabc4:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:40 upgrade libkresources4:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:41 upgrade kdepimlibs-kio-plugins:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:42 upgrade libkldap4:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:43 upgrade libkcalcore4:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:43 upgrade libkpimtextedit4:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:44 upgrade libkholidays4:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:45 upgrade libakonadi-socialutils4:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:46 upgrade mysql-server-core-5.5:amd64 5.5.50-0ubuntu0.14.04.1 5.5.54-0ubuntu0.14.04.1
/var/log/dpkg.log:2017-02-20 10:10:47 upgrade mysql-client-core-5.5:amd64 5.5.50-0ubuntu0.14.04.1 5.5.54-0ubuntu0.14.04.1
/var/log/dpkg.log:2017-02-20 10:10:48 upgrade akonadi-server:amd64 1.12.1-0ubuntu1.1 1.12.1-0ubuntu1.2
/var/log/dpkg.log:2017-02-20 10:10:49 upgrade akonadi-backend-mysql:all 1.12.1-0ubuntu1.1 1.12.1-0ubuntu1.2
/var/log/dpkg.log:2017-02-20 10:10:50 upgrade libakonadiprotocolinternals1:amd64 1.12.1-0ubuntu1.1 1.12.1-0ubuntu1.2
/var/log/dpkg.log:2017-02-20 10:10:50 upgrade libmailtransport4:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:51 upgrade libakonadi-kmime4:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:52 upgrade libakonadi-kde4:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:53 upgrade libakonadi-notes4:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:54 upgrade libkmbox4:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:54 upgrade libkimap4:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:55 upgrade libkmime4:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:56 upgrade libakonadi-kabc4:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:58 upgrade libqgpgme1:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:59 upgrade libgpgme++2:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:10:59 upgrade libgweather-common:all 3.10.2-0ubuntu2 3.10.2-0ubuntu3
/var/log/dpkg.log:2017-02-20 10:11:00 upgrade libgweather-3-6:amd64 3.10.2-0ubuntu2 3.10.2-0ubuntu3
/var/log/dpkg.log:2017-02-20 10:11:01 upgrade libkontactinterface4:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:11:02 upgrade libkxmlrpcclient4:amd64 4:4.13.3-0ubuntu0.2 4:4.13.3-0ubuntu0.3
/var/log/dpkg.log:2017-02-20 10:11:03 upgrade libservlet3.0-java:all 7.0.52-1ubuntu0.6 7.0.52-1ubuntu0.9
/var/log/dpkg.log:2017-02-20 10:11:03 upgrade whoopsie:amd64 0.2.24.6ubuntu2 0.2.24.6ubuntu3
/var/log/dpkg.log:2017-02-20 10:11:04 upgrade libwhoopsie0:amd64 0.2.24.6ubuntu2 0.2.24.6ubuntu3
/var/log/dpkg.log:2017-02-20 10:11:05 upgrade linux-firmware:all 1.127.22 1.127.23
/var/log/dpkg.log:2017-02-20 10:11:17 upgrade linux-headers-generic:amd64 3.13.0.92.99 3.13.0.109.117
/var/log/dpkg.log:2017-02-20 10:11:24 upgrade linux-image-generic:amd64 3.13.0.92.99 3.13.0.109.117
/var/log/dpkg.log:2017-02-20 10:11:25 upgrade linux-libc-dev:amd64 3.13.0-92.139 3.13.0-109.156
/var/log/dpkg.log:2017-02-20 10:11:26 upgrade python-pil:amd64 2.3.0-1ubuntu3 2.3.0-1ubuntu3.3
/var/log/dpkg.log:2017-02-20 10:11:27 upgrade python-imaging:all 2.3.0-1ubuntu3 2.3.0-1ubuntu3.3
/var/log/dpkg.log:2017-02-20 10:11:31 upgrade python3-crypto:amd64 2.6.1-4build1 2.6.1-4ubuntu0.2
/var/log/dpkg.log:2017-02-20 10:11:32 upgrade software-center:all 13.10-0ubuntu4.1 13.10-0ubuntu4.2
/var/log/dpkg.log:2017-02-20 10:11:33 upgrade thunderbird-locale-en:amd64 1:45.2.0+build1-0ubuntu0.14.04.3 1:45.7.0+build1-0ubuntu0.14.04.1
/var/log/dpkg.log:2017-02-20 10:11:34 upgrade thunderbird:amd64 1:45.2.0+build1-0ubuntu0.14.04.3 1:45.7.0+build1-0ubuntu0.14.04.1
/var/log/dpkg.log:2017-02-20 10:11:39 upgrade thunderbird-locale-en-us:all 1:45.2.0+build1-0ubuntu0.14.04.3 1:45.7.0+build1-0ubuntu0.14.04.1
/var/log/dpkg.log:2017-02-20 10:11:40 upgrade xserver-xorg-video-intel:amd64 2:2.99.910-0ubuntu1.6 2:2.99.910-0ubuntu1.7
/var/log/dpkg.log:2017-02-20 14:01:24 upgrade libmm-glib0:amd64 1.0.0-2ubuntu1 1.0.0-2ubuntu1.1
/var/log/dpkg.log:2017-02-20 14:01:25 upgrade libnautilus-extension1a:amd64 1:3.10.1-0ubuntu8 1:3.10.1-0ubuntu9.11
/var/log/dpkg.log:2017-02-20 14:01:26 upgrade modemmanager:amd64 1.0.0-2ubuntu1 1.0.0-2ubuntu1.1
/var/log/dpkg.log:2017-02-20 14:01:27 upgrade mugshot:all 0.2.3-1 0.2.5-0ubuntu0.1
/var/log/dpkg.log:2017-02-20 14:01:28 upgrade nautilus-data:all 1:3.10.1-0ubuntu8 1:3.10.1-0ubuntu9.11
/var/log/dpkg.log:2017-02-20 14:01:29 upgrade xfdesktop4:amd64 4.11.6-1ubuntu1 4.11.8-0ubuntu0.1
/var/log/dpkg.log:2017-02-20 14:01:30 upgrade xfdesktop4-data:all 4.11.6-1ubuntu1 4.11.8-0ubuntu0.1
/var/log/dpkg.log:2017-02-20 14:01:31 upgrade oneconf-common:all 0.3.7 0.3.7.14.04.1
/var/log/dpkg.log:2017-02-20 14:01:32 upgrade python3-oneconf:all 0.3.7 0.3.7.14.04.1
/var/log/dpkg.log:2017-02-20 14:01:33 upgrade oneconf:all 0.3.7 0.3.7.14.04.1
/var/log/dpkg.log:2017-02-20 14:01:34 upgrade python-oneconf:all 0.3.7 0.3.7.14.04.1
xubuntu@xubuntu:~/Desktop$
```

---

### Post by vasa1 on 2017-02-20
So you also have kde components!

---

### Post by ajgreeny on 2017-02-20
Wow!
Was today the first time you have upgraded all your packages as there seems to be 243 that were all upgraded today, an unusually large number, unless you installed the OS only today and this is the first update?

Personally, I would not worry about the kde libs that you have as I am certain they will not be affecting this problem; I have a few KDE applications that always bring with them a lot of other library files etc etc that do no damage, so I can see no reason why your situation should be different from mine in that respect.  Things can get a bit convoluted if you have full installation of more than one DE version, eg ubuntu-desktop and kubuntu-desktop on the same OS, but just a few kde applications should not cause problems.

---

### Post by smokeyone2 on 2017-02-20
Should I try and delete the Ubuntu desktop setip .....still stuck with odd goings on & tiny fonts/thumbnails etc

---

### Post by ajgreeny on 2017-02-20
NO. 
Don't start deleting things just yet without trying to figure out what has gone wrong, and what it was that you did, and I suspect it must be something done by you, that caused this very strange situation.

I'm not even sure what you mean by "delete the ubuntu desktop setup" as you started this thread saying this was Xubuntu 14.04.

Are you even certain that you are looking at thunar with Places, ie Bookmarks and system Places as well, showing in the left hand pane and not in Tree mode? 
For Places use Ctrl+B and for Tree mode use Ctrl+E.

---

### Post by Kris_M on 2017-02-20
reading this I wonder if the OP didn't simply, by mistake, hit Ctrl-H, and maybe a few other shortcuts...

---

### Post by smokeyone2 on 2017-02-21
I may have hit a key by mistake but surely not Ctrl+ something else - two keys together !
Clean install might be the answer .....

---

### Post by ajgreeny on 2017-02-21
I don't think this is likely to help but try renaming the various (three?) xfce4 folders, one by one, in your home .config folder, as well as the thunar folder also in .config to see if that removes this problem for you.

---

### Post by smokeyone2 on 2017-02-22
Thank you for the suggestion - but still no luck. I seem to recall that I had less trouble installing Xubuntu from scratch than I do now so a clean install might be the easiest solution.
Thanks again

---

### Post by Keith_Helms on 2017-02-22
Go into the View menu in File Manager (Places) and uncheck "Show Hidden Files".

---

### Post by speartip on 2017-02-22
I agree with Keith_Helms.
It seems that all you have done is revealed the hidden files & folders.
Those listed in #1 are perfectly normal. 
Just follow Keiths advice and all should be ok.

---

### Post by ajgreeny on 2017-02-22
> **Keith_Helms said:**
> Go into the View menu in File Manager (Places) and uncheck "Show Hidden Files".
Showing hidden files and folders has nothing to do with what is included in the Places menu, ie your file manager Bookmarks as far as I am aware; I _always_ show hidden files and folders in my file managers, whichever one I am using, and have never seen this problem on any of my systems.

---

### Post by speartip on 2017-02-22
@ajgreeny.
If you read post 1 again, the op refers to his places "directory", which judging by what's in it is his home directory. 
All the extras in their he refers to are simply hidden files & folders.
IMO Keith is correct, just unticking "show hidden files" should resolve his problem.

---

### Post by ajgreeny on 2017-02-22
> **speartip said:**
> @ajgreeny.
If you read post 1 again, the op refers to his places "directory", which judging by what's in it is his home directory. 
All the extras in their he refers to are simply hidden files & folders.
IMO Keith is correct, just unticking "show hidden files" should resolve his problem.
Sorry, but I don't know what or where this places "directory" is, as there is no such thing in my system.

However, just to add to my, and I imagine your confusion I have just found that according to a bug filed at [https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1280641](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1280641) there is a potential problem as the file which now contains all your thunar bookmarks, ie, what shows in the Places pane in thunar is now **~/.config/gtk-3.0/bookmarks** and the old version **~/.gtk-bookmarks** is now no longer needed nor working.

@ smokeyone2
What exactly did you mean by > I am getting used to using Xubuntu when suddenly a load of folders and files have appeared in my Xubuntu/Places directory.Is this the Places panel applet? In my system that applet uses the **~/.config/gtk-3.0/bookmarks** file for its contents. so have a look at that file in your system, if it exists in 14.04.

---

### Post by mörgæs on 2017-02-23
> **smokeyone2 said:**
> ...so a clean install might be the easiest solution.


Yes, you have to consider that 14.04 has only two months left of support anyway and that 16.04.2 finally is available. 

Even if this were a perfectly working system I would say that now was a good time to move on.

---


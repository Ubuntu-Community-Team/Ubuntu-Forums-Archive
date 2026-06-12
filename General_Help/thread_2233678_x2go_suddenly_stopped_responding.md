---
title: "x2go suddenly stopped responding"
date: 2014-07-10
forum: General Help
---

### Post by kelsey3 on 2014-07-10
Hi,

I am running Ubuntu server 14.04 with XFCE4 and all of a sudden x2go stopped working.

When I try to connect each time I see the following in my auth.log and the client just hangs.

Jul 10 14:29:51 box sshd[2554]: pam_unix(sshd:session): session opened for user kelsey by (uid=0)
Jul 10 14:30:40 box sshd[2554]: pam_unix(sshd:session): session closed for user kelsey

I can rdp into the box over VNC and ssh still works.

I have tried the client on mac and windows and also purged x2goserver and opensh and reinstalled but still no joy.

The pyhoca-gui client also didn't work.

I am at a bit of a loss as to how to troubleshoot further so any help appreciated.

---

### Post by kelsey3 on 2014-07-11
I was looking through my apt history logs and I think I started getting this problem after running apt-get dist-upgrade

Maybe it is something to do with the libpam updates...


Start-Date: 2014-07-05  22:57:22
Commandline: apt-get dist-upgrade
Upgrade:  gir1.2-dbusmenu-glib-0.4:amd64 (12.10.3+14.04.20140319-0ubuntu1,  12.10.3+14.04.20140612-0ubuntu1), libsystemd-login0:amd64  (204-5ubuntu20.2, 204-5ubuntu20.3), intel-gpu-tools:amd64 (1.3-0ubuntu2,  1.3-0ubuntu2.1), libnm-gtk0:amd64 (0.9.8.8-0ubuntu4.1,  0.9.8.8-0ubuntu4.2), systemd-services:amd64 (204-5ubuntu20.2,  204-5ubuntu20.3), libnautilus-extension1a:amd64 (3.10.1-0ubuntu9.1,  3.10.1-0ubuntu9.2), libboost-date-time1.54.0:amd64 (1.54.0-4ubuntu3,  1.54.0-4ubuntu3.1), libboost-system1.54.0:amd64 (1.54.0-4ubuntu3,  1.54.0-4ubuntu3.1), libsystemd-daemon0:amd64 (204-5ubuntu20.2,  204-5ubuntu20.3), libgudev-1.0-0:amd64 (204-5ubuntu20.2,  204-5ubuntu20.3), libdbusmenu-gtk4:amd64  (12.10.3+14.04.20140319-0ubuntu1, 12.10.3+14.04.20140612-0ubuntu1),  libpam-systemd:amd64 (204-5ubuntu20.2, 204-5ubuntu20.3),  sabnzbdplus-theme-smpl:amd64 (0.7.17-0ubuntu1~jcfp1~trusty,  0.7.18~rc1-0ubuntu1~jcfp1~trusty), shotwell-common:amd64  (0.18.0-0ubuntu4, 0.18.0-0ubuntu4.1), udev:amd64 (204-5ubuntu20.2,  204-5ubuntu20.3), shotwell:amd64 (0.18.0-0ubuntu4, 0.18.0-0ubuntu4.1),  libdbusmenu-gtk3-4:amd64 (12.10.3+14.04.20140319-0ubuntu1,  12.10.3+14.04.20140612-0ubuntu1), network-manager-gnome:amd64  (0.9.8.8-0ubuntu4.1, 0.9.8.8-0ubuntu4.2), libnm-gtk-common:amd64  (0.9.8.8-0ubuntu4.1, 0.9.8.8-0ubuntu4.2), libdbusmenu-glib4:amd64  (12.10.3+14.04.20140319-0ubuntu1, 12.10.3+14.04.20140612-0ubuntu1),  gir1.2-gudev-1.0:amd64 (204-5ubuntu20.2, 204-5ubuntu20.3),  sabnzbdplus-theme-classic:amd64 (0.7.17-0ubuntu1~jcfp1~trusty,  0.7.18~rc1-0ubuntu1~jcfp1~trusty), sabnzbdplus:amd64  (0.7.17-0ubuntu1~jcfp1~trusty, 0.7.18~rc1-0ubuntu1~jcfp1~trusty),  libudev1:amd64 (204-5ubuntu20.2, 204-5ubuntu20.3), libudev1:i386  (204-5ubuntu20.2, 204-5ubuntu20.3), nautilus:amd64 (3.10.1-0ubuntu9.1,  3.10.1-0ubuntu9.2), libboost-iostreams1.54.0:amd64 (1.54.0-4ubuntu3,  1.54.0-4ubuntu3.1), libsystemd-journal0:amd64 (204-5ubuntu20.2,  204-5ubuntu20.3), nautilus-data:amd64 (3.10.1-0ubuntu9.1,  3.10.1-0ubuntu9.2), sabnzbdplus-theme-plush:amd64  (0.7.17-0ubuntu1~jcfp1~trusty, 0.7.18~rc1-0ubuntu1~jcfp1~trusty),  gnome-settings-daemon-schemas:amd64 (3.8.6.1-0ubuntu11.1,  3.8.6.1-0ubuntu11.2)
End-Date: 2014-07-05  22:57:44

Start-Date: 2014-07-06  07:54:15
Upgrade:  linux-image-extra-3.13.0-30-generic:amd64 (3.13.0-30.54, 3.13.0-30.55),  linux-image-3.13.0-30-generic:amd64 (3.13.0-30.54, 3.13.0-30.55),  linux-headers-3.13.0-30-generic:amd64 (3.13.0-30.54, 3.13.0-30.55),  linux-headers-3.13.0-30:amd64 (3.13.0-30.54, 3.13.0-30.55),  linux-libc-dev:amd64 (3.13.0-30.54, 3.13.0-30.55)
End-Date: 2014-07-06  07:55:25

---

### Post by kelsey3 on 2014-07-15
I just noticed I am getting this error on the server after the client hangs for a while but not sure if it's related:

Jul 15 15:31:17 box console-kit-daemon[1424]: GLib-CRITICAL: Source ID 1308 was not found when attempting to remove it

---

### Post by kelsey3 on 2014-07-25
I figure this out...

I have two nics in the box with two Internet connections. In order to force rtorrent traffic over one connection I set the tos setting in rtorrent to be 0x08 and added an ip rule for that tos.

Apparently this affected x2go as it was coming in over the over connection and this ip rule seemed to break it. I changed the hex tos value and everything works.

---


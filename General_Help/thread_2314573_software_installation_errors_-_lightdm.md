---
title: "software installation errors - lightdm"
date: 2016-02-22
forum: General Help
---

### Post by andy-andyward on 2016-02-22
Can anybody help please, I'm out of my depth :confused: and somewhat frightened of messing with lightdm

I have a pretty new (clean) installation of 15.10 having failed to get the upgrade from 14.04 to work.
Everything appeared OK until (I think) I installed the drivers for my panasonic mb-2030 (printer and scanner all work fine), from that point on (again, I think) I get errors on software upgrades with lightdm complaining.
Problems arise in software updater, synaptec and muon (if I am in Plasma).
Several aps have installed OK despite the error message about lightdm but I can't get clamav to install properly!
Also, I did not try to install samba until after the panasonic drivers and it did not go well either [IMG]http://ubuntuforums.org/images/icons/icon9.png[/IMG]
I have removed the panasonic drivers as per the instructions from panasonic and deleted the printer from cups.
I have also removed samba.

I have tried apt-get update - this worked fine

apt-get upgrade threw multiple errors and suggested using apt-get autoremove which also threw multiple errors referencing panasonic and lightdm


--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
AUTOREMOVE
```
andrew@Front:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  attr glib-networking:i386 kde-l10n-engb libaio1 libasn1-8-heimdal:i386 libasound2:i386 libatk-bridge2.0-0:i386
  libatk1.0-0:i386 libatspi2.0-0:i386 libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
  libboost-filesystem1.58.0:i386 libboost-system1.58.0:i386 libbsd0:i386 libcairo-gobject2:i386 libcairo2:i386
  libcolord2:i386 libcups2:i386 libcurl3:i386 libdatrie1:i386 libdbus-1-3:i386 libdbus-glib-1-2:i386
  libdbusmenu-glib4:i386 libdbusmenu-gtk3-4:i386 libdbusmenu-gtk4:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libegl1-mesa:i386 libelf1:i386 libexpat1:i386
  libffi6:i386 libfontconfig1:i386 libfreetype6:i386 libgbm1:i386 libgconf-2-4:i386 libgdk-pixbuf2.0-0:i386
  libgl1-mesa-dri:i386 libglib2.0-0:i386 libgmp10:i386 libgnutls-deb0-28:i386 libgraphite2-3:i386 libgssapi-krb5-2:i386
  libgssapi3-heimdal:i386 libgtk2.0-0:i386 libharfbuzz0b:i386 libhcrypto4-heimdal:i386 libhdb9-heimdal
  libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386 libhogweed4:i386 libhx509-5-heimdal:i386 libicu55:i386
  libidn11:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386 libjson-glib-1.0-0:i386 libk5crypto3:i386
  libkdc2-heimdal libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386 libkrb5support0:i386 liblcms2-2:i386
  libldap-2.4-2:i386 libllvm3.5v5 libllvm3.6v5:i386 libmirclient9:i386 libmircommon5:i386 libmirprotobuf3:i386
  libmspack0 libnettle6:i386 libnspr4:i386 libnss3:i386 libp11-kit0:i386 libpango-1.0-0:i386 libpango1.0-0:i386
  libpangocairo-1.0-0:i386 libpangoft2-1.0-0:i386 libpangox-1.0-0:i386 libpangoxft-1.0-0:i386 libpciaccess0:i386
  libpixman-1-0:i386 libpng12-0:i386 libprotobuf-lite9v5:i386 libproxy1v5:i386 librest-0.7-0:i386
  libroken18-heimdal:i386 librtmp1:i386 libsasl2-2:i386 libsasl2-modules:i386 libsasl2-modules-db:i386
  libsoup-gnome2.4-1:i386 libsoup2.4-1:i386 libsqlite3-0:i386 libssl1.0.0:i386 libstdc++6:i386 libtasn1-6:i386
  libtext-csv-perl libtext-csv-xs-perl libthai0:i386 libtiff5:i386 libtxc-dxtn-s2tc0:i386 libwayland-client0:i386
  libwayland-cursor0:i386 libwayland-egl1-mesa:i386 libwayland-server0:i386 libwind0-heimdal:i386 libx11-6:i386
  libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcb-xfixes0:i386
  libxcb1:i386 libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386
  libxft2:i386 libxi6:i386 libxinerama1:i386 libxkbcommon0:i386 libxml2:i386 libxrandr2:i386 libxrender1:i386
  libxss1:i386 libxtst6:i386 linux-headers-4.2.0-16 linux-headers-4.2.0-16-generic linux-image-4.2.0-16-generic
  linux-image-extra-4.2.0-16-generic python-dnspython samba-dsdb-modules samba-vfs-modules tdb-tools
0 to upgrade, 0 to newly install, 144 to remove and 0 not to upgrade.
1 not fully installed or removed.
After this operation, 556 MB disk space will be freed.

Do you want to continue? [Y/n] y
(Reading database ... 301658 files and directories currently installed.)
Removing attr (1:2.4.47-2) ...
Removing librest-0.7-0:i386 (0.7.93-1) ...
Removing libsoup-gnome2.4-1:i386 (2.50.0-2debian1) ...
Removing libsoup2.4-1:i386 (2.50.0-2debian1) ...
Removing glib-networking:i386 (2.46.0-1) ...
Removing kde-l10n-engb (4:15.08.2-0ubuntu1) ...
Removing samba-vfs-modules (2:4.1.17+dfsg-4ubuntu3.2) ...
Removing libaio1:amd64 (0.3.110-1) ...
Removing libcurl3:i386 (7.43.0-1ubuntu2.1) ...
Removing libldap-2.4-2:i386 (2.4.41+dfsg-1ubuntu2) ...
Removing libgssapi3-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Removing libheimntlm0-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Removing libkrb5-26-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Removing libhx509-5-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Removing libasound2:i386 (1.0.29-0ubuntu1) ...
Removing libatk-bridge2.0-0:i386 (2.16.0-1ubuntu1) ...
Removing libgtk2.0-0:i386 (2.24.28-1ubuntu1.1) ...
Removing libdbusmenu-gtk4:i386 (12.10.3+15.04.20150410.2-0ubuntu1) ...
Removing libatspi2.0-0:i386 (2.16.0-1ubuntu1) ...
Removing libcups2:i386 (2.1.0-4ubuntu3) ...
Removing libavahi-client3:i386 (0.6.31-4ubuntu4) ...
Removing libavahi-common3:i386 (0.6.31-4ubuntu4) ...
Removing libavahi-common-data:i386 (0.6.31-4ubuntu4) ...
Removing libmirclient9:i386 (0.17.0+15.10.20151008.2-0ubuntu1) ...
Removing libmircommon5:i386 (0.17.0+15.10.20151008.2-0ubuntu1) ...
Removing libboost-filesystem1.58.0:i386 (1.58.0+dfsg-3.1ubuntu1) ...
Removing libboost-system1.58.0:i386 (1.58.0+dfsg-3.1ubuntu1) ...
Removing libwayland-egl1-mesa:i386 (11.0.2-1ubuntu4) ...
Removing libegl1-mesa:i386 (11.0.2-1ubuntu4) ...
Removing libgbm1:i386 (11.0.2-1ubuntu4) ...
Removing libgl1-mesa-dri:i386 (11.0.2-1ubuntu4) ...
Removing libllvm3.6v5:i386 (1:3.6.2-1) ...
Removing libedit2:i386 (3.1-20150325-1ubuntu1) ...
Removing libbsd0:i386 (0.7.0-2) ...
Removing libcairo-gobject2:i386 (1.14.2-2ubuntu2) ...
Removing libpango1.0-0:i386 (1.36.8-3) ...
Removing libpangocairo-1.0-0:i386 (1.36.8-3) ...
Removing libcairo2:i386 (1.14.2-2ubuntu2) ...
Removing libcolord2:i386 (1.2.11-0ubuntu2) ...
Removing libpangoxft-1.0-0:i386 (1.36.8-3) ...
Removing libpangox-1.0-0:i386 (0.0.2-5) ...
Removing libgconf-2-4:i386 (3.2.6-3ubuntu5) ...
Removing libdbus-glib-1-2:i386 (0.104-1build1) ...
Removing libdbus-1-3:i386 (1.10.0-1ubuntu1) ...
Removing libdbusmenu-gtk3-4:i386 (12.10.3+15.04.20150410.2-0ubuntu1) ...
Removing libdbusmenu-glib4:i386 (12.10.3+15.04.20150410.2-0ubuntu1) ...
Removing libdrm-amdgpu1:i386 (2.4.64-1) ...
Removing libdrm-intel1:i386 (2.4.64-1) ...
Removing libdrm-nouveau2:i386 (2.4.64-1) ...
Removing libdrm-radeon1:i386 (2.4.64-1) ...
Removing libdrm2:i386 (2.4.64-1) ...
Removing libelf1:i386 (0.163-4ubuntu1) ...
Removing libxft2:i386 (2.3.2-1) ...
Removing libpangoft2-1.0-0:i386 (1.36.8-3) ...
Removing libfontconfig1:i386 (2.11.1-0ubuntu6) ...
Removing libexpat1:i386 (2.1.0-7) ...
Removing libwayland-server0:i386 (1.8.1-1) ...
Removing libwayland-cursor0:i386 (1.8.1-1) ...
Removing libwayland-client0:i386 (1.8.1-1) ...
Removing libharfbuzz0b:i386 (1.0.1-1build2) ...
Removing libfreetype6:i386 (2.5.2-4ubuntu2) ...
Removing libgdk-pixbuf2.0-0:i386 (2.32.1-1) ...
Removing libjson-glib-1.0-0:i386 (1.0.4-2) ...
Removing librtmp1:i386 (2.4+20150115.gita107cef-1build1) ...
Removing libgnutls-deb0-28:i386 (3.3.15-5ubuntu2) ...
Removing libhogweed4:i386 (3.1.1-4ubuntu0.1) ...
Removing libgmp10:i386 (2:6.0.0+dfsg-7) ...
Removing libgraphite2-3:i386 (1.2.4-3ubuntu1.1) ...
Removing libgssapi-krb5-2:i386 (1.13.2+dfsg-2ubuntu0.1) ...
Removing libhcrypto4-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Removing libkdc2-heimdal:amd64 (1.6~rc2+dfsg-10ubuntu1) ...
Removing libhdb9-heimdal:amd64 (1.6~rc2+dfsg-10ubuntu1) ...
Removing libheimbase1-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Removing libxml2:i386 (2.9.2+zdfsg1-4ubuntu0.3) ...
Removing libicu55:i386 (55.1-4ubuntu1) ...
Removing libidn11:i386 (1.28-1ubuntu2) ...
Removing libtiff5:i386 (4.0.3-12.3ubuntu2) ...
Removing libjbig0:i386 (2.1-3.1) ...
Removing libjpeg8:i386 (8c-2ubuntu8) ...
Removing libjpeg-turbo8:i386 (1.3.0-0ubuntu2) ...
Removing libkrb5-3:i386 (1.13.2+dfsg-2ubuntu0.1) ...
Removing libk5crypto3:i386 (1.13.2+dfsg-2ubuntu0.1) ...
Removing libkeyutils1:i386 (1.5.9-5ubuntu1) ...
Removing libkrb5support0:i386 (1.13.2+dfsg-2ubuntu0.1) ...
Removing liblcms2-2:i386 (2.6-3ubuntu2) ...
Removing libllvm3.5v5:amd64 (1:3.5.2-2) ...
Removing libmirprotobuf3:i386 (0.17.0+15.10.20151008.2-0ubuntu1) ...
Removing libmspack0:amd64 (0.5-1) ...
Removing libnettle6:i386 (3.1.1-4ubuntu0.1) ...
Removing libnss3:i386 (2:3.21-0ubuntu0.15.10.1) ...
Removing libnspr4:i386 (2:4.10.10-0ubuntu0.15.10.1) ...
Removing libp11-kit0:i386 (0.23.1-3) ...
Removing libpciaccess0:i386 (0.13.4-1) ...
Removing libpixman-1-0:i386 (0.32.6-3) ...
Removing libpng12-0:i386 (1.2.51-0ubuntu3.15.10.2) ...
Removing libprotobuf-lite9v5:i386 (2.6.1-1.2) ...
Removing libproxy1v5:i386 (0.4.11-4ubuntu3~gcc5.3) ...
Removing libwind0-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Removing libsasl2-2:i386 (2.1.26.dfsg1-14) ...
Removing libsasl2-modules:i386 (2.1.26.dfsg1-14) ...
Removing libsasl2-modules-db:i386 (2.1.26.dfsg1-14) ...
Removing libsqlite3-0:i386 (3.8.11.1-1) ...
Removing libssl1.0.0:i386 (1.0.2d-0ubuntu1.3) ...
Removing libtxc-dxtn-s2tc0:i386 (0~git20131104-1.1) ...
Removing libstdc++6:i386 (5.2.1-22ubuntu2) ...
Removing libtasn1-6:i386 (4.5-2) ...
Removing libtext-csv-perl (1.33-1) ...
Removing libtext-csv-xs-perl (1.19-1) ...
Removing libxtst6:i386 (2:1.2.2-1) ...
Removing libxss1:i386 (1:1.2.2-1) ...
Removing libx11-xcb1:i386 (2:1.6.3-1ubuntu2) ...
Removing libxcb-xfixes0:i386 (1.11-0ubuntu1) ...
Removing libxcb-shm0:i386 (1.11-0ubuntu1) ...
Removing libxcb-dri2-0:i386 (1.11-0ubuntu1) ...
Removing libxcb-render0:i386 (1.11-0ubuntu1) ...
Removing libxcomposite1:i386 (1:0.4.4-1) ...
Removing libxcursor1:i386 (1:1.1.14-1) ...
Removing libxdamage1:i386 (1:1.1.4-2) ...
Removing libxrandr2:i386 (2:1.5.0-1) ...
Removing libxfixes3:i386 (1:5.0.1-2) ...
Removing libxi6:i386 (2:1.7.4-1) ...
Removing libxinerama1:i386 (2:1.1.3-1) ...
Removing libxkbcommon0:i386 (0.5.0-1ubuntu2) ...
Removing libxrender1:i386 (1:0.9.9-0ubuntu1) ...
Removing linux-headers-4.2.0-16-generic (4.2.0-16.19) ...
Removing linux-headers-4.2.0-16 (4.2.0-16.19) ...
Removing linux-image-extra-4.2.0-16-generic (4.2.0-16.19) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
update-initramfs: Generating /boot/initrd.img-4.2.0-16-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-27-generic
Found initrd image: /boot/initrd.img-4.2.0-27-generic
Found linux image: /boot/vmlinuz-4.2.0-25-generic
Found initrd image: /boot/initrd.img-4.2.0-25-generic
Found linux image: /boot/vmlinuz-4.2.0-16-generic
Found initrd image: /boot/initrd.img-4.2.0-16-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Removing linux-image-4.2.0-16-generic (4.2.0-16.19) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
update-initramfs: Deleting /boot/initrd.img-4.2.0-16-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-27-generic
Found initrd image: /boot/initrd.img-4.2.0-27-generic
Found linux image: /boot/vmlinuz-4.2.0-25-generic
Found initrd image: /boot/initrd.img-4.2.0-25-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Removing python-dnspython (1.12.0-1) ...
Removing samba-dsdb-modules (2:4.1.17+dfsg-4ubuntu3.2) ...
Removing tdb-tools (1.3.5-1) ...
Removing libasn1-8-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Removing libatk1.0-0:i386 (2.16.0-2build1) ...
Removing libpango-1.0-0:i386 (1.36.8-3) ...
Removing libthai0:i386 (0.1.22-2) ...
Removing libdatrie1:i386 (0.2.9-2) ...
Removing libglib2.0-0:i386 (2.46.1-1) ...
Removing libroken18-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Removing libxext6:i386 (2:1.3.3-1) ...
Removing libffi6:i386 (3.2.1-3) ...
Removing libx11-6:i386 (2:1.6.3-1ubuntu2) ...
Removing libxcb1:i386 (1.11-0ubuntu1) ...
Removing libxau6:i386 (1:1.0.8-1) ...
Removing libxdmcp6:i386 (1:1.1.2-1) ...
Processing triggers for man-db (2.7.4-1) ...
Processing triggers for libc-bin (2.21-0ubuntu4.1) ...
Setting up lightdm (1.16.7-0ubuntu1) ...
insserv: warning: script 'S80panasoniclpd-init' missing LSB tags and overrides
insserv: warning: script 'panasoniclpd-init' missing LSB tags and overrides
insserv: There is a loop between service grub-common and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service grub-common if started
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: There is a loop between service grub-common and urandom if started
insserv:  loop involving service urandom at depth 4
insserv:  loop involving service hwclock at depth 3
insserv: There is a loop at service panasoniclpd-init if started
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: There is a loop between service panasoniclpd-init and dns-clean if started
insserv:  loop involving service dns-clean at depth 1
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package lightdm (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 lightdm
E: Sub-process /usr/bin/dpkg returned an error code (1)
andrew@Front:~$ 
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
APT-GET UPGRADE

```
andrew@Front:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... The following packages were automatically installed and are no longer required:
  attr glib-networking:i386 kde-l10n-engb libaio1 libasn1-8-heimdal:i386
  libasound2:i386 libatk-bridge2.0-0:i386 libatk1.0-0:i386 libatspi2.0-0:i386
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
  libboost-filesystem1.58.0:i386 libboost-system1.58.0:i386 libbsd0:i386
  libcairo-gobject2:i386 libcairo2:i386 libcolord2:i386 libcups2:i386
  libcurl3:i386 libdatrie1:i386 libdbus-1-3:i386 libdbus-glib-1-2:i386
  libdbusmenu-glib4:i386 libdbusmenu-gtk3-4:i386 libdbusmenu-gtk4:i386
  libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386
  libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libegl1-mesa:i386
  libelf1:i386 libexpat1:i386 libffi6:i386 libfontconfig1:i386
  libfreetype6:i386 libgbm1:i386 libgconf-2-4:i386 libgdk-pixbuf2.0-0:i386
  libgl1-mesa-dri:i386 libglib2.0-0:i386 libgmp10:i386 libgnutls-deb0-28:i386
  libgraphite2-3:i386 libgssapi-krb5-2:i386 libgssapi3-heimdal:i386
  libgtk2.0-0:i386 libharfbuzz0b:i386 libhcrypto4-heimdal:i386 libhdb9-heimdal
  libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386 libhogweed4:i386
  libhx509-5-heimdal:i386 libicu55:i386 libidn11:i386 libjbig0:i386
  libjpeg-turbo8:i386 libjpeg8:i386 libjson-glib-1.0-0:i386 libk5crypto3:i386
  libkdc2-heimdal libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386
  libkrb5support0:i386 liblcms2-2:i386 libldap-2.4-2:i386 libllvm3.5v5
  libllvm3.6v5:i386 libmirclient9:i386 libmircommon5:i386 libmirprotobuf3:i386
  libmspack0 libnettle6:i386 libnspr4:i386 libnss3:i386 libp11-kit0:i386
  libpango-1.0-0:i386 libpango1.0-0:i386 libpangocairo-1.0-0:i386
  libpangoft2-1.0-0:i386 libpangox-1.0-0:i386 libpangoxft-1.0-0:i386
  libpciaccess0:i386 libpixman-1-0:i386 libpng12-0:i386
  libprotobuf-lite9v5:i386 libproxy1v5:i386 librest-0.7-0:i386
  libroken18-heimdal:i386 librtmp1:i386 libsasl2-2:i386 libsasl2-modules:i386
  libsasl2-modules-db:i386 libsoup-gnome2.4-1:i386 libsoup2.4-1:i386
  libsqlite3-0:i386 libssl1.0.0:i386 libstdc++6:i386 libtasn1-6:i386
  libtext-csv-perl libtext-csv-xs-perl libthai0:i386 libtiff5:i386
  libtxc-dxtn-s2tc0:i386 libwayland-client0:i386 libwayland-cursor0:i386
  libwayland-egl1-mesa:i386 libwayland-server0:i386 libwind0-heimdal:i386
  libx11-6:i386 libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386
  libxcb-render0:i386 libxcb-shm0:i386 libxcb-xfixes0:i386 libxcb1:i386
  libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386
  libxext6:i386 libxfixes3:i386 libxft2:i386 libxi6:i386 libxinerama1:i386
  libxkbcommon0:i386 libxml2:i386 libxrandr2:i386 libxrender1:i386
  libxss1:i386 libxtst6:i386 linux-headers-4.2.0-16
  linux-headers-4.2.0-16-generic linux-image-4.2.0-16-generic
  linux-image-extra-4.2.0-16-generic python-dnspython samba-dsdb-modules
  samba-vfs-modules tdb-tools
Use 'apt-get autoremove' to remove them.
Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.

Do you want to continue? [Y/n] y
Setting up lightdm (1.16.7-0ubuntu1) ...
insserv: warning: script 'S80panasoniclpd-init' missing LSB tags and overrides
insserv: warning: script 'panasoniclpd-init' missing LSB tags and overrides
insserv: There is a loop between service grub-common and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service grub-common if started
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: There is a loop between service grub-common and urandom if started
insserv:  loop involving service urandom at depth 4
insserv:  loop involving service hwclock at depth 3
insserv: There is a loop at service panasoniclpd-init if started
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: There is a loop between service panasoniclpd-init and dns-clean if started
insserv:  loop involving service dns-clean at depth 1
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package lightdm (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 lightdm
E: Sub-process /usr/bin/dpkg returned an error code (1)
andrew@Front:~$ 
```

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Thanks ... Andy

---

### Post by v3.xx on 2016-02-22
I don't know, looks pretty bad from here.  And its safe to say that your driver install did it.  You may be able to access your system at the grub boot screen by going to recovery mode and then remove that driver.

Please post a link to this driver.  Thanks

PS
Please use code tags
```
AUTOREMOVE
andrew@Front:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED
attr glib-networking:i386 kde-l10n-engb libaio1 libasn1-8-heimdal:i386 libasound2:i386 libatk-bridge2.0-0:i386
libatk1.0-0:i386 libatspi2.0-0:i386 libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
libboost-filesystem1.58.0:i386 libboost-system1.58.0:i386 libbsd0:i386 libcairo-gobject2:i386 libcairo2:i386
libcolord2:i386 libcups2:i386 libcurl3:i386 libdatrie1:i386 libdbus-1-3:i386 libdbus-glib-1-2:i386
libdbusmenu-glib4:i386 libdbusmenu-gtk3-4:i386 libdbusmenu-gtk4:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386
libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libegl1-mesa:i386 libelf1:i386 libexpat1:i386
libffi6:i386 libfontconfig1:i386 libfreetype6:i386 libgbm1:i386 libgconf-2-4:i386 libgdk-pixbuf2.0-0:i386
libgl1-mesa-dri:i386 libglib2.0-0:i386 libgmp10:i386 libgnutls-deb0-28:i386 libgraphite2-3:i386 libgssapi-krb5-2:i386
libgssapi3-heimdal:i386 libgtk2.0-0:i386 libharfbuzz0b:i386 libhcrypto4-heimdal:i386 libhdb9-heimdal
libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386 libhogweed4:i386 libhx509-5-heimdal:i386 libicu55:i386
libidn11:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386 libjson-glib-1.0-0:i386 libk5crypto3:i386
libkdc2-heimdal libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386 libkrb5support0:i386 liblcms2-2:i386
libldap-2.4-2:i386 libllvm3.5v5 libllvm3.6v5:i386 libmirclient9:i386 libmircommon5:i386 libmirprotobuf3:i386
libmspack0 libnettle6:i386 libnspr4:i386 libnss3:i386 libp11-kit0:i386 libpango-1.0-0:i386 libpango1.0-0:i386
libpangocairo-1.0-0:i386 libpangoft2-1.0-0:i386 libpangox-1.0-0:i386 libpangoxft-1.0-0:i386 libpciaccess0:i386
libpixman-1-0:i386 libpng12-0:i386 libprotobuf-lite9v5:i386 libproxy1v5:i386 librest-0.7-0:i386
libroken18-heimdal:i386 librtmp1:i386 libsasl2-2:i386 libsasl2-modules:i386 libsasl2-modules-db:i386
libsoup-gnome2.4-1:i386 libsoup2.4-1:i386 libsqlite3-0:i386 libssl1.0.0:i386 libstdc++6:i386 libtasn1-6:i386
libtext-csv-perl libtext-csv-xs-perl libthai0:i386 libtiff5:i386 libtxc-dxtn-s2tc0:i386 libwayland-client0:i386
libwayland-cursor0:i386 libwayland-egl1-mesa:i386 libwayland-server0:i386 libwind0-heimdal:i386 libx11-6:i386
libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcb-xfixes0:i386
libxcb1:i386 libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386
libxft2:i386 libxi6:i386 libxinerama1:i386 libxkbcommon0:i386 libxml2:i386 libxrandr2:i386 libxrender1:i386
libxss1:i386 libxtst6:i386 linux-headers-4.2.0-16 linux-headers-4.2.0-16-generic linux-image-4.2.0-16-generic
linux-image-extra-4.2.0-16-generic python-dnspython samba-dsdb-modules samba-vfs-modules tdb-tools
0 to upgrade, 0 to newly install, 144 to remove and 0 not to upgrade.
1 not fully installed or removed.
After this operation, 556 MB disk space will be freed.


Do you want to continue? [Y/n] y
(Reading database ... 301658 files and directories currently installed.)
Removing attr (1:2.4.47-2) ...
Removing librest-0.7-0:i386 (0.7.93-1) ...
Removing libsoup-gnome2.4-1:i386 (2.50.0-2debian1) ...
Removing libsoup2.4-1:i386 (2.50.0-2debian1) ...
Removing glib-networking:i386 (2.46.0-1) ...
Removing kde-l10n-engb (4:15.08.2-0ubuntu1) ...
Removing samba-vfs-modules (2:4.1.17+dfsg-4ubuntu3.2) ...
Removing libaio1:amd64 (0.3.110-1) ...
Removing libcurl3:i386 (7.43.0-1ubuntu2.1) ...
Removing libldap-2.4-2:i386 (2.4.41+dfsg-1ubuntu2) ...
Removing libgssapi3-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Removing libheimntlm0-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Removing libkrb5-26-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Removing libhx509-5-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Removing libasound2:i386 (1.0.29-0ubuntu1) ...
Removing libatk-bridge2.0-0:i386 (2.16.0-1ubuntu1) ...
Removing libgtk2.0-0:i386 (2.24.28-1ubuntu1.1) ...
Removing libdbusmenu-gtk4:i386 (12.10.3+15.04.20150410.2-0ubuntu1) ...
Removing libatspi2.0-0:i386 (2.16.0-1ubuntu1) ...
Removing libcups2:i386 (2.1.0-4ubuntu3) ...
Removing libavahi-client3:i386 (0.6.31-4ubuntu4) ...
Removing libavahi-common3:i386 (0.6.31-4ubuntu4) ...
Removing libavahi-common-data:i386 (0.6.31-4ubuntu4) ...
Removing libmirclient9:i386 (0.17.0+15.10.20151008.2-0ubuntu1) ...
Removing libmircommon5:i386 (0.17.0+15.10.20151008.2-0ubuntu1) ...
Removing libboost-filesystem1.58.0:i386 (1.58.0+dfsg-3.1ubuntu1) ...
Removing libboost-system1.58.0:i386 (1.58.0+dfsg-3.1ubuntu1) ...
Removing libwayland-egl1-mesa:i386 (11.0.2-1ubuntu4) ...
Removing libegl1-mesa:i386 (11.0.2-1ubuntu4) ...
Removing libgbm1:i386 (11.0.2-1ubuntu4) ...
Removing libgl1-mesa-dri:i386 (11.0.2-1ubuntu4) ...
Removing libllvm3.6v5:i386 (1:3.6.2-1) ...
Removing libedit2:i386 (3.1-20150325-1ubuntu1) ...
Removing libbsd0:i386 (0.7.0-2) ...
Removing libcairo-gobject2:i386 (1.14.2-2ubuntu2) ...
Removing libpango1.0-0:i386 (1.36.8-3) ...
Removing libpangocairo-1.0-0:i386 (1.36.8-3) ...
Removing libcairo2:i386 (1.14.2-2ubuntu2) ...
Removing libcolord2:i386 (1.2.11-0ubuntu2) ...
Removing libpangoxft-1.0-0:i386 (1.36.8-3) ...
Removing libpangox-1.0-0:i386 (0.0.2-5) ...
Removing libgconf-2-4:i386 (3.2.6-3ubuntu5) ...
Removing libdbus-glib-1-2:i386 (0.104-1build1) ...
Removing libdbus-1-3:i386 (1.10.0-1ubuntu1) ...
Removing libdbusmenu-gtk3-4:i386 (12.10.3+15.04.20150410.2-0ubuntu1) ...
Removing libdbusmenu-glib4:i386 (12.10.3+15.04.20150410.2-0ubuntu1) ...
Removing libdrm-amdgpu1:i386 (2.4.64-1) ...
Removing libdrm-intel1:i386 (2.4.64-1) ...
Removing libdrm-nouveau2:i386 (2.4.64-1) ...
Removing libdrm-radeon1:i386 (2.4.64-1) ...
Removing libdrm2:i386 (2.4.64-1) ...
Removing libelf1:i386 (0.163-4ubuntu1) ...
Removing libxft2:i386 (2.3.2-1) ...
Removing libpangoft2-1.0-0:i386 (1.36.8-3) ...
Removing libfontconfig1:i386 (2.11.1-0ubuntu6) ...
Removing libexpat1:i386 (2.1.0-7) ...
Removing libwayland-server0:i386 (1.8.1-1) ...
Removing libwayland-cursor0:i386 (1.8.1-1) ...
Removing libwayland-client0:i386 (1.8.1-1) ...
Removing libharfbuzz0b:i386 (1.0.1-1build2) ...
Removing libfreetype6:i386 (2.5.2-4ubuntu2) ...
Removing libgdk-pixbuf2.0-0:i386 (2.32.1-1) ...
Removing libjson-glib-1.0-0:i386 (1.0.4-2) ...
Removing librtmp1:i386 (2.4+20150115.gita107cef-1build1) ...
Removing libgnutls-deb0-28:i386 (3.3.15-5ubuntu2) ...
Removing libhogweed4:i386 (3.1.1-4ubuntu0.1) ...
Removing libgmp10:i386 (2:6.0.0+dfsg-7) ...
Removing libgraphite2-3:i386 (1.2.4-3ubuntu1.1) ...
Removing libgssapi-krb5-2:i386 (1.13.2+dfsg-2ubuntu0.1) ...
Removing libhcrypto4-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Removing libkdc2-heimdal:amd64 (1.6~rc2+dfsg-10ubuntu1) ...
Removing libhdb9-heimdal:amd64 (1.6~rc2+dfsg-10ubuntu1) ...
Removing libheimbase1-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Removing libxml2:i386 (2.9.2+zdfsg1-4ubuntu0.3) ...
Removing libicu55:i386 (55.1-4ubuntu1) ...
Removing libidn11:i386 (1.28-1ubuntu2) ...
Removing libtiff5:i386 (4.0.3-12.3ubuntu2) ...
Removing libjbig0:i386 (2.1-3.1) ...
Removing libjpeg8:i386 (8c-2ubuntu8) ...
Removing libjpeg-turbo8:i386 (1.3.0-0ubuntu2) ...
Removing libkrb5-3:i386 (1.13.2+dfsg-2ubuntu0.1) ...
Removing libk5crypto3:i386 (1.13.2+dfsg-2ubuntu0.1) ...
Removing libkeyutils1:i386 (1.5.9-5ubuntu1) ...
Removing libkrb5support0:i386 (1.13.2+dfsg-2ubuntu0.1) ...
Removing liblcms2-2:i386 (2.6-3ubuntu2) ...
Removing libllvm3.5v5:amd64 (1:3.5.2-2) ...
Removing libmirprotobuf3:i386 (0.17.0+15.10.20151008.2-0ubuntu1) ...
Removing libmspack0:amd64 (0.5-1) ...
Removing libnettle6:i386 (3.1.1-4ubuntu0.1) ...
Removing libnss3:i386 (2:3.21-0ubuntu0.15.10.1) ...
Removing libnspr4:i386 (2:4.10.10-0ubuntu0.15.10.1) ...
Removing libp11-kit0:i386 (0.23.1-3) ...
Removing libpciaccess0:i386 (0.13.4-1) ...
Removing libpixman-1-0:i386 (0.32.6-3) ...
Removing libpng12-0:i386 (1.2.51-0ubuntu3.15.10.2) ...
Removing libprotobuf-lite9v5:i386 (2.6.1-1.2) ...
Removing libproxy1v5:i386 (0.4.11-4ubuntu3~gcc5.3) ...
Removing libwind0-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Removing libsasl2-2:i386 (2.1.26.dfsg1-14) ...
Removing libsasl2-modules:i386 (2.1.26.dfsg1-14) ...
Removing libsasl2-modules-db:i386 (2.1.26.dfsg1-14) ...
Removing libsqlite3-0:i386 (3.8.11.1-1) ...
Removing libssl1.0.0:i386 (1.0.2d-0ubuntu1.3) ...
Removing libtxc-dxtn-s2tc0:i386 (0~git20131104-1.1) ...
Removing libstdc++6:i386 (5.2.1-22ubuntu2) ...
Removing libtasn1-6:i386 (4.5-2) ...
Removing libtext-csv-perl (1.33-1) ...
Removing libtext-csv-xs-perl (1.19-1) ...
Removing libxtst6:i386 (2:1.2.2-1) ...
Removing libxss1:i386 (1:1.2.2-1) ...
Removing libx11-xcb1:i386 (2:1.6.3-1ubuntu2) ...
Removing libxcb-xfixes0:i386 (1.11-0ubuntu1) ...
Removing libxcb-shm0:i386 (1.11-0ubuntu1) ...
Removing libxcb-dri2-0:i386 (1.11-0ubuntu1) ...
Removing libxcb-render0:i386 (1.11-0ubuntu1) ...
Removing libxcomposite1:i386 (1:0.4.4-1) ...
Removing libxcursor1:i386 (1:1.1.14-1) ...
Removing libxdamage1:i386 (1:1.1.4-2) ...
Removing libxrandr2:i386 (2:1.5.0-1) ...
Removing libxfixes3:i386 (1:5.0.1-2) ...
Removing libxi6:i386 (2:1.7.4-1) ...
Removing libxinerama1:i386 (2:1.1.3-1) ...
Removing libxkbcommon0:i386 (0.5.0-1ubuntu2) ...
Removing libxrender1:i386 (1:0.9.9-0ubuntu1) ...
Removing linux-headers-4.2.0-16-generic (4.2.0-16.19) ...
Removing linux-headers-4.2.0-16 (4.2.0-16.19) ...
Removing linux-image-extra-4.2.0-16-generic (4.2.0-16.19) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
update-initramfs: Generating /boot/initrd.img-4.2.0-16-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-27-generic
Found initrd image: /boot/initrd.img-4.2.0-27-generic
Found linux image: /boot/vmlinuz-4.2.0-25-generic
Found initrd image: /boot/initrd.img-4.2.0-25-generic
Found linux image: /boot/vmlinuz-4.2.0-16-generic
Found initrd image: /boot/initrd.img-4.2.0-16-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Removing linux-image-4.2.0-16-generic (4.2.0-16.19) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
update-initramfs: Deleting /boot/initrd.img-4.2.0-16-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-27-generic
Found initrd image: /boot/initrd.img-4.2.0-27-generic
Found linux image: /boot/vmlinuz-4.2.0-25-generic
Found initrd image: /boot/initrd.img-4.2.0-25-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Removing python-dnspython (1.12.0-1) ...
Removing samba-dsdb-modules (2:4.1.17+dfsg-4ubuntu3.2) ...
Removing tdb-tools (1.3.5-1) ...
Removing libasn1-8-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Removing libatk1.0-0:i386 (2.16.0-2build1) ...
Removing libpango-1.0-0:i386 (1.36.8-3) ...
Removing libthai0:i386 (0.1.22-2) ...
Removing libdatrie1:i386 (0.2.9-2) ...
Removing libglib2.0-0:i386 (2.46.1-1) ...
Removing libroken18-heimdal:i386 (1.6~rc2+dfsg-10ubuntu1) ...
Removing libxext6:i386 (2:1.3.3-1) ...
Removing libffi6:i386 (3.2.1-3) ...
Removing libx11-6:i386 (2:1.6.3-1ubuntu2) ...
Removing libxcb1:i386 (1.11-0ubuntu1) ...
Removing libxau6:i386 (1:1.0.8-1) ...
Removing libxdmcp6:i386 (1:1.1.2-1) ...
Processing triggers for man-db (2.7.4-1) ...
Processing triggers for libc-bin (2.21-0ubuntu4.1) ...
Setting up lightdm (1.16.7-0ubuntu1) ...
insserv: warning: script 'S80panasoniclpd-init' missing LSB tags and overrides
insserv: warning: script 'panasoniclpd-init' missing LSB tags and overrides
insserv: There is a loop between service grub-common and procps if started
insserv: loop involving service procps at depth 2
insserv: loop involving service udev at depth 1
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service grub-common if started
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: loop involving service networking at depth 4
insserv: There is a loop between service grub-common and urandom if started
insserv: loop involving service urandom at depth 4
insserv: loop involving service hwclock at depth 3
insserv: There is a loop at service panasoniclpd-init if started
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: There is a loop between service panasoniclpd-init and dns-clean if started
insserv: loop involving service dns-clean at depth 1
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package lightdm (--configure):
subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
lightdm
E: Sub-process /usr/bin/dpkg returned an error code (1)
andrew@Front:~$

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
APT-GET UPGRADE



andrew@Front:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... The following packages were automatically installed and are no longer required:
attr glib-networking:i386 kde-l10n-engb libaio1 libasn1-8-heimdal:i386
libasound2:i386 libatk-bridge2.0-0:i386 libatk1.0-0:i386 libatspi2.0-0:i386
libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
libboost-filesystem1.58.0:i386 libboost-system1.58.0:i386 libbsd0:i386
libcairo-gobject2:i386 libcairo2:i386 libcolord2:i386 libcups2:i386
libcurl3:i386 libdatrie1:i386 libdbus-1-3:i386 libdbus-glib-1-2:i386
libdbusmenu-glib4:i386 libdbusmenu-gtk3-4:i386 libdbusmenu-gtk4:i386
libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386
libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libegl1-mesa:i386
libelf1:i386 libexpat1:i386 libffi6:i386 libfontconfig1:i386
libfreetype6:i386 libgbm1:i386 libgconf-2-4:i386 libgdk-pixbuf2.0-0:i386
libgl1-mesa-dri:i386 libglib2.0-0:i386 libgmp10:i386 libgnutls-deb0-28:i386
libgraphite2-3:i386 libgssapi-krb5-2:i386 libgssapi3-heimdal:i386
libgtk2.0-0:i386 libharfbuzz0b:i386 libhcrypto4-heimdal:i386 libhdb9-heimdal
libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386 libhogweed4:i386
libhx509-5-heimdal:i386 libicu55:i386 libidn11:i386 libjbig0:i386
libjpeg-turbo8:i386 libjpeg8:i386 libjson-glib-1.0-0:i386 libk5crypto3:i386
libkdc2-heimdal libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386
libkrb5support0:i386 liblcms2-2:i386 libldap-2.4-2:i386 libllvm3.5v5
libllvm3.6v5:i386 libmirclient9:i386 libmircommon5:i386 libmirprotobuf3:i386
libmspack0 libnettle6:i386 libnspr4:i386 libnss3:i386 libp11-kit0:i386
libpango-1.0-0:i386 libpango1.0-0:i386 libpangocairo-1.0-0:i386
libpangoft2-1.0-0:i386 libpangox-1.0-0:i386 libpangoxft-1.0-0:i386
libpciaccess0:i386 libpixman-1-0:i386 libpng12-0:i386
libprotobuf-lite9v5:i386 libproxy1v5:i386 librest-0.7-0:i386
libroken18-heimdal:i386 librtmp1:i386 libsasl2-2:i386 libsasl2-modules:i386
libsasl2-modules-db:i386 libsoup-gnome2.4-1:i386 libsoup2.4-1:i386
libsqlite3-0:i386 libssl1.0.0:i386 libstdc++6:i386 libtasn1-6:i386
libtext-csv-perl libtext-csv-xs-perl libthai0:i386 libtiff5:i386
libtxc-dxtn-s2tc0:i386 libwayland-client0:i386 libwayland-cursor0:i386
libwayland-egl1-mesa:i386 libwayland-server0:i386 libwind0-heimdal:i386
libx11-6:i386 libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386
libxcb-render0:i386 libxcb-shm0:i386 libxcb-xfixes0:i386 libxcb1:i386
libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386
libxext6:i386 libxfixes3:i386 libxft2:i386 libxi6:i386 libxinerama1:i386
libxkbcommon0:i386 libxml2:i386 libxrandr2:i386 libxrender1:i386
libxss1:i386 libxtst6:i386 linux-headers-4.2.0-16
linux-headers-4.2.0-16-generic linux-image-4.2.0-16-generic
linux-image-extra-4.2.0-16-generic python-dnspython samba-dsdb-modules
samba-vfs-modules tdb-tools
Use 'apt-get autoremove' to remove them.
Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.


Do you want to continue? [Y/n] y
Setting up lightdm (1.16.7-0ubuntu1) ...
insserv: warning: script 'S80panasoniclpd-init' missing LSB tags and overrides
insserv: warning: script 'panasoniclpd-init' missing LSB tags and overrides
insserv: There is a loop between service grub-common and procps if started
insserv: loop involving service procps at depth 2
insserv: loop involving service udev at depth 1
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service grub-common if started
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: loop involving service networking at depth 4
insserv: There is a loop between service grub-common and urandom if started
insserv: loop involving service urandom at depth 4
insserv: loop involving service hwclock at depth 3
insserv: There is a loop at service panasoniclpd-init if started
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: There is a loop between service panasoniclpd-init and dns-clean if started
insserv: loop involving service dns-clean at depth 1
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting panasoniclpd-init depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package lightdm (--configure):
subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
lightdm
E: Sub-process /usr/bin/dpkg returned an error code (1)
andrew@Front:~$
```

---

### Post by andy-andyward on 2016-02-22
Hi, yes, I was feeling pretty glum about my chances of avoiding a(nother) rebuild.

Here's the link to the drivers - all the documentation, scripts etc. are in the also there.

[http://panasonic.net/pcc/support/fax/common/table/linuxdriver.html#SD](http://panasonic.net/pcc/support/fax/common/table/linuxdriver.html#SD)

I can access my system OK, am I correct that you're advising I try the driver removal pre-system load via grub?

Cheers ... Andy

---

### Post by v3.xx on 2016-02-22
Here's my findings Andy

Not having the scanner I cannot test the driver, but I did load the 64bit version without issue.

[ATTACH=CONFIG]267434[/ATTACH]

So I really don't know where you went wrong, but yes, try going to recovery mode and removing it.  I also did this with the uninstall script provided.

And you say this is also a version upgrade to 15.10 which could mean that this is a upgrade gone wrong.

---

### Post by andy-andyward on 2016-02-22
Hi again,
No, I gave up trying to do the upgrade to 15.10 and had to do a full install from CD.
Not sure what happens with the uninstall script, it all finished OK and cups reflected that the config files were gone when I went into it to remove the printer.
I'll try the recovery mode removal - thanks.

---

### Post by andy-andyward on 2016-02-23
Seems to be sorted out now, while checking at the path to try removing the driver in recovery I found that none of the files (especially uninstall-driver) were present and then I realised that the scanner stuff was all still there.  I ran the scanner uninstall, apt-get update, apt-get autoremove, reboot and then apt-get upgrade and everything now appears to be working.  I have subsequently installed clamav, calmscan etc. which I wasn't able to do before,
Thanks loads for your help

---

### Post by v3.xx on 2016-02-23
Good show :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---


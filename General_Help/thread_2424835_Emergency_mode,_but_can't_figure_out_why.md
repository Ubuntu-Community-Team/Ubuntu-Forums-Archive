---
title: "Emergency mode, but can't figure out why"
date: 2019-08-15
forum: General Help
---

### Post by freedombacon on 2019-08-15
Ubuntu 18.04 no longer boots after I installed updates and removed a  failed hard drive. It keeps going to emergency mode, but there doesn't  seem to be anything wrong. I initially thought it was a hardware  problem, so I reset the UEFI and disconnected drives I don't need. That  didn't help, and I can boot 19.04 from USB without problem. I checked  the filesystems and they are all clean. CMOS battery is also good.

Latest updates installed:
```

Start-Date: 2019-08-13  15:20:15
Commandline: apt-get dist-upgrade
Requested-By: avz (1001)
Install:  linux-headers-4.15.0-58-generic:amd64 (4.15.0-58.64, automatic),  linux-modules-extra-4.15.0-58-generic:amd64 (4.15.0-58.64, automatic),  linux-headers-4.15.0-58:amd64 (4.15.0-58.64, automatic),  linux-modules-4.15.0-58-generic:amd64 (4.15.0-58.64, automatic),  xdg-desktop-portal-gtk:amd64 (1.0.2-0ubuntu1.1, automatic),  linux-image-4.15.0-58-generic:amd64 (4.15.0-58.64, automatic),  xdg-desktop-portal:amd64 (1.0.3-0ubuntu0.2, automatic)
Upgrade:  milou:amd64 (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1), vlc-bin:amd64  (3.0.4-1ubuntu0.2, 3.0.7.1-0ubuntu18.04.1),  libreoffice-style-breeze:amd64 (1:6.0.7-0ubuntu0.18.04.7,  1:6.0.7-0ubuntu0.18.04.8), libreoffice-math:amd64  (1:6.0.7-0ubuntu0.18.04.7, 1:6.0.7-0ubuntu0.18.04.8),  vlc-plugin-video-output:amd64 (3.0.4-1ubuntu0.2,  3.0.7.1-0ubuntu18.04.1), libkwinglutils11:amd64 (4:5.12.7-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), libkf5config-data:amd64 (5.44.0-0ubuntu1,  5.44.0-0ubuntu1.1), plasma-workspace:amd64 (4:5.12.7-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), libtaskmanager6:amd64 (4:5.12.7-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), poppler-utils:amd64 (0.62.0-2ubuntu2.9,  0.62.0-2ubuntu2.10), gstreamer1.0-alsa:amd64  (1.14.4-1ubuntu1.1~ubuntu18.04.1, 1.14.5-0ubuntu1~18.04.1),  libplasma-geolocation-interface5:amd64 (4:5.12.7-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), liboxygenstyle5-5:amd64 (4:5.12.7-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), language-pack-gnome-en:amd64 (1:18.04+20180712,  1:18.04+20190718), libksignalplotter7:amd64 (4:5.12.7-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), linux-headers-generic:amd64 (4.15.0.54.56,  4.15.0.58.60), gir1.2-gtk-3.0:amd64 (3.22.30-1ubuntu3,  3.22.30-1ubuntu4), libpowerdevilui5:amd64 (4:5.12.7-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), kde-cli-tools:amd64 (4:5.12.7-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), kde-config-gtk-style:amd64 (4:5.12.5-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), linux-libc-dev:amd64 (4.15.0-54.58, 4.15.0-58.64),  gstreamer1.0-plugins-base-apps:amd64 (1.14.4-1ubuntu1.1~ubuntu18.04.1,  1.14.5-0ubuntu1~18.04.1), libldap-2.4-2:amd64 (2.4.45+dfsg-1ubuntu1.2,  2.4.45+dfsg-1ubuntu1.3), python3-software-properties:amd64  (0.96.24.32.9, 0.96.24.32.11), vlc-plugin-samba:amd64 (3.0.4-1ubuntu0.2,  3.0.7.1-0ubuntu18.04.1), bluedevil:amd64 (4:5.12.7-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), openssl:amd64 (1.1.1-1ubuntu2.1~18.04.3,  1.1.1-1ubuntu2.1~18.04.4), kde-config-gtk-style-preview:amd64  (4:5.12.5-0ubuntu0.1, 4:5.12.8-0ubuntu0.1), breeze-cursor-theme:amd64  (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1), sane-utils:amd64  (1.0.27-1~experimental3ubuntu2, 1.0.27-1~experimental3ubuntu2.1),  plasma-nm:amd64 (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1),  plasma-pa:amd64 (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1),  libegl-mesa0:amd64 (19.0.2-1ubuntu1.1~18.04.1,  19.0.2-1ubuntu1.1~18.04.2), libreoffice-gtk3:amd64  (1:6.0.7-0ubuntu0.18.04.7, 1:6.0.7-0ubuntu0.18.04.8),  libpam-kwallet-common:amd64 (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1),  plasma-dataengines-addons:amd64 (4:5.12.7-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), libreoffice-java-common:amd64  (1:6.0.7-0ubuntu0.18.04.7, 1:6.0.7-0ubuntu0.18.04.8),  vlc-plugin-qt:amd64 (3.0.4-1ubuntu0.2, 3.0.7.1-0ubuntu18.04.1),  libsystemd0:amd64 (237-3ubuntu10.24, 237-3ubuntu10.25),  libgtk-3-common:amd64 (3.22.30-1ubuntu3, 3.22.30-1ubuntu4),  gstreamer1.0-tools:amd64 (1.14.4-1~ubuntu18.04.1,  1.14.5-0ubuntu1~18.04.1), linux-image-generic:amd64 (4.15.0.54.56,  4.15.0.58.60), libreoffice-base:amd64 (1:6.0.7-0ubuntu0.18.04.7,  1:6.0.7-0ubuntu0.18.04.8), libgtk-3-0:amd64 (3.22.30-1ubuntu3,  3.22.30-1ubuntu4), gstreamer1.0-plugins-good:amd64  (1.14.4-1ubuntu1~ubuntu18.04.1, 1.14.5-0ubuntu1~18.04.1), libgs9:amd64  (9.26~dfsg+0-0ubuntu0.18.04.9, 9.26~dfsg+0-0ubuntu0.18.04.10),  libreoffice-core:amd64 (1:6.0.7-0ubuntu0.18.04.7,  1:6.0.7-0ubuntu0.18.04.8), libprocesscore7:amd64 (4:5.12.7-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), libglapi-mesa:amd64 (19.0.2-1ubuntu1.1~18.04.1,  19.0.2-1ubuntu1.1~18.04.2), kwin-style-breeze:amd64  (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1), kwin-data:amd64  (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1), ksshaskpass:amd64  (4:5.12.6-0ubuntu0.1, 4:5.12.8-0ubuntu0.1),  plasma-wallpapers-addons:amd64 (4:5.12.7-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), libreoffice-style-oxygen:amd64  (1:6.0.7-0ubuntu0.18.04.7, 1:6.0.7-0ubuntu0.18.04.8), libebml4v5:amd64  (1.3.5-2, 1.3.5-2ubuntu0.1), fonts-noto-cjk:amd64 (1:20170601+repack1-2,  1:20190409+repack1-0ubuntu0.18.04), libkf5sysguard-bin:amd64  (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1), iputils-arping:amd64  (3:20161105-1ubuntu2, 3:20161105-1ubuntu3), systemsettings:amd64  (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1), vlc-plugin-skins2:amd64  (3.0.4-1ubuntu0.2, 3.0.7.1-0ubuntu18.04.1),  language-selector-common:amd64 (0.188.2, 0.188.3),  plasma-discover-common:amd64 (5.12.7-0ubuntu0.1, 5.12.8-0ubuntu0.1),  libpoppler-qt5-1:amd64 (0.62.0-2ubuntu2.9, 0.62.0-2ubuntu2.10),  vlc-plugin-visualization:amd64 (3.0.4-1ubuntu0.2,  3.0.7.1-0ubuntu18.04.1), virtualbox-guest-additions-iso:amd64  (5.2.18-1~ubuntu18.04.1, 5.2.32-1~ubuntu18.04.1), vlc-l10n:amd64  (3.0.4-1ubuntu0.2, 3.0.7.1-0ubuntu18.04.1), kde-style-breeze:amd64  (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1), libkf5configcore5:amd64  (5.44.0-0ubuntu1, 5.44.0-0ubuntu1.1), libsox3:amd64 (14.4.2-3,  14.4.2-3ubuntu0.18.04.1), usb-creator-common:amd64 (0.3.5ubuntu18.04.1,  0.3.5ubuntu18.04.2), ubuntu-standard:amd64 (1.417.1, 1.417.3),  kmenuedit:amd64 (4:5.12.6-0ubuntu0.1, 4:5.12.8-0ubuntu0.1),  khotkeys:amd64 (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1),  plasma-discover:amd64 (5.12.7-0ubuntu0.1, 5.12.8-0ubuntu0.1),  ubuntu-desktop:amd64 (1.417.1, 1.417.3), libreoffice-kde:amd64  (1:6.0.7-0ubuntu0.18.04.7, 1:6.0.7-0ubuntu0.18.04.8),  libxatracker2:amd64 (19.0.2-1ubuntu1.1~18.04.1,  19.0.2-1ubuntu1.1~18.04.2), breeze:amd64 (4:5.12.7-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), vlc-plugin-notify:amd64 (3.0.4-1ubuntu0.2,  3.0.7.1-0ubuntu18.04.1), libvlc5:amd64 (3.0.4-1ubuntu0.2,  3.0.7.1-0ubuntu18.04.1), iputils-tracepath:amd64 (3:20161105-1ubuntu2,  3:20161105-1ubuntu3), kde-style-oxygen-qt5:amd64 (4:5.12.7-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), virtualbox-dkms:amd64  (5.2.18-dfsg-2~ubuntu18.04.5, 5.2.32-dfsg-0~ubuntu18.04.1),  gstreamer1.0-plugins-bad:amd64 (1.14.4-1ubuntu1~ubuntu18.04.1,  1.14.5-0ubuntu1~18.04.1), udev:amd64 (237-3ubuntu10.24,  237-3ubuntu10.25), usb-creator-gtk:amd64 (0.3.5ubuntu18.04.1,  0.3.5ubuntu18.04.2), libegl1-mesa:amd64 (19.0.2-1ubuntu1.1~18.04.1,  19.0.2-1ubuntu1.1~18.04.2), gstreamer1.0-plugins-base:amd64  (1.14.4-1ubuntu1.1~ubuntu18.04.1, 1.14.5-0ubuntu1~18.04.1),  ubuntu-server:amd64 (1.417.1, 1.417.3), language-pack-en:amd64  (1:18.04+20180712, 1:18.04+20190718), plasma-desktop:amd64  (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1), kactivitymanagerd:amd64  (5.12.7-0ubuntu0.1, 5.12.8-0ubuntu0.1), libsox-fmt-alsa:amd64 (14.4.2-3,  14.4.2-3ubuntu0.18.04.1), libwavpack1:amd64 (5.1.0-2ubuntu1.3,  5.1.0-2ubuntu1.4), software-properties-gtk:amd64 (0.96.24.32.9,  0.96.24.32.11), dkms:amd64 (2.3-3ubuntu9.3, 2.3-3ubuntu9.5),  python3-uno:amd64 (1:6.0.7-0ubuntu0.18.04.7, 1:6.0.7-0ubuntu0.18.04.8),  virtualbox:amd64 (5.2.18-dfsg-2~ubuntu18.04.5,  5.2.32-dfsg-0~ubuntu18.04.1), openjdk-11-jre-headless:amd64  (11.0.3+7-1ubuntu2~18.04.1, 11.0.4+11-1ubuntu2~18.04.3),  user-manager:amd64 (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1),  linux-signed-generic:amd64 (4.15.0.54.56, 4.15.0.58.60),  kde-style-breeze-qt4:amd64 (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1),  libgstreamer-plugins-good1.0-0:amd64 (1.14.4-1ubuntu1~ubuntu18.04.1,  1.14.5-0ubuntu1~18.04.1), libvlccore9:amd64 (3.0.4-1ubuntu0.2,  3.0.7.1-0ubuntu18.04.1), libudev1:amd64 (237-3ubuntu10.24,  237-3ubuntu10.25), libkwineffects11:amd64 (4:5.12.7-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), plasma-vault:amd64 (5.12.7-0ubuntu0.1,  5.12.8-0ubuntu0.1), libvlc-bin:amd64 (3.0.4-1ubuntu0.2,  3.0.7.1-0ubuntu18.04.1), plasma-desktop-data:amd64 (4:5.12.7-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), powerdevil-data:amd64 (4:5.12.7-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), libksgrd7:amd64 (4:5.12.7-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), gstreamer1.0-pulseaudio:amd64  (1.14.4-1ubuntu1~ubuntu18.04.1, 1.14.5-0ubuntu1~18.04.1), libgbm1:amd64  (19.0.2-1ubuntu1.1~18.04.1, 19.0.2-1ubuntu1.1~18.04.2),  libkworkspace5-5:amd64 (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1),  libkf5configgui5:amd64 (5.44.0-0ubuntu1, 5.44.0-0ubuntu1.1),  thunderbird-gnome-support:amd64 (1:60.7.2+build2-0ubuntu0.18.04.1,  1:60.8.0+build1-0ubuntu0.18.04.1), libreoffice-style-galaxy:amd64  (1:6.0.7-0ubuntu0.18.04.7, 1:6.0.7-0ubuntu0.18.04.8),  libreoffice-base-core:amd64 (1:6.0.7-0ubuntu0.18.04.7,  1:6.0.7-0ubuntu0.18.04.8), kwin-addons:amd64 (4:5.12.7-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), software-properties-kde:amd64 (0.96.24.32.9,  0.96.24.32.11), kde-cli-tools-data:amd64 (4:5.12.7-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), ubuntu-minimal:amd64 (1.417.1, 1.417.3),  libinput-bin:amd64 (1.10.4-1, 1.10.4-1ubuntu0.18.04.1),  plasma-runners-addons:amd64 (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1),  libreoffice-ogltrans:amd64 (1:6.0.7-0ubuntu0.18.04.7,  1:6.0.7-0ubuntu0.18.04.8), gstreamer1.0-gtk3:amd64  (1.14.4-1ubuntu1~ubuntu18.04.1, 1.14.5-0ubuntu1~18.04.1),  oxygen-sounds:amd64 (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1),  mysql-client-core-5.7:amd64 (5.7.26-0ubuntu0.18.04.1,  5.7.27-0ubuntu0.18.04.1), libsane1:amd64 (1.0.27-1~experimental3ubuntu2,  1.0.27-1~experimental3ubuntu2.1), libreoffice-impress:amd64  (1:6.0.7-0ubuntu0.18.04.7, 1:6.0.7-0ubuntu0.18.04.8),  libkscreenlocker5:amd64 (5.12.7-0ubuntu0.1, 5.12.8-0ubuntu0.1),  libpam-kwallet4:amd64 (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1),  libpam-kwallet5:amd64 (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1),  libgtk-3-bin:amd64 (3.22.30-1ubuntu3, 3.22.30-1ubuntu4),  sddm-theme-breeze:amd64 (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1),  libnss-myhostname:amd64 (237-3ubuntu10.24, 237-3ubuntu10.25), sox:amd64  (14.4.2-3, 14.4.2-3ubuntu0.18.04.1), libgstreamer-gl1.0-0:amd64  (1.14.4-1ubuntu1.1~ubuntu18.04.1, 1.14.5-0ubuntu1~18.04.1),  libmspack0:amd64 (0.6-3ubuntu0.2, 0.6-3ubuntu0.3), kinfocenter:amd64  (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1), systemd-sysv:amd64  (237-3ubuntu10.24, 237-3ubuntu10.25), firefox-locale-en:amd64  (67.0.4+build1-0ubuntu0.18.04.1, 68.0.1+build1-0ubuntu0.18.04.1),  openjdk-11-jre:amd64 (11.0.3+7-1ubuntu2~18.04.1,  11.0.4+11-1ubuntu2~18.04.3), libldap-common:amd64  (2.4.45+dfsg-1ubuntu1.2, 2.4.45+dfsg-1ubuntu1.3),  libwayland-egl1-mesa:amd64 (19.0.2-1ubuntu1.1~18.04.1,  19.0.2-1ubuntu1.1~18.04.2), libkf5screen-bin:amd64 (4:5.12.4-0ubuntu1,  4:5.12.8-0ubuntu0.1), ure:amd64 (6.0.7-0ubuntu0.18.04.7,  6.0.7-0ubuntu0.18.04.8), kwrited:amd64 (4:5.12.6-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), libkf5screen7:amd64 (4:5.12.4-0ubuntu1,  4:5.12.8-0ubuntu0.1), libreoffice-sdbc-hsqldb:amd64  (1:6.0.7-0ubuntu0.18.04.7, 1:6.0.7-0ubuntu0.18.04.8),  libreoffice-writer:amd64 (1:6.0.7-0ubuntu0.18.04.7,  1:6.0.7-0ubuntu0.18.04.8), vlc:amd64 (3.0.4-1ubuntu0.2,  3.0.7.1-0ubuntu18.04.1), libpam-systemd:amd64 (237-3ubuntu10.24,  237-3ubuntu10.25), libgstreamer-plugins-base1.0-0:amd64  (1.14.4-1ubuntu1.1~ubuntu18.04.1, 1.14.5-0ubuntu1~18.04.1),  libgail-3-0:amd64 (3.22.30-1ubuntu3, 3.22.30-1ubuntu4), vlc-data:amd64  (3.0.4-1ubuntu0.2, 3.0.7.1-0ubuntu18.04.1), libreoffice-common:amd64  (1:6.0.7-0ubuntu0.18.04.7, 1:6.0.7-0ubuntu0.18.04.8),  libreoffice-kde4:amd64 (1:6.0.7-0ubuntu0.18.04.7,  1:6.0.7-0ubuntu0.18.04.8), gstreamer1.0-x:amd64  (1.14.4-1ubuntu1.1~ubuntu18.04.1, 1.14.5-0ubuntu1~18.04.1),  ghostscript:amd64 (9.26~dfsg+0-0ubuntu0.18.04.9,  9.26~dfsg+0-0ubuntu0.18.04.10), libcolorcorrect5:amd64  (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1), systemd:amd64  (237-3ubuntu10.24, 237-3ubuntu10.25), gir1.2-gst-plugins-base-1.0:amd64  (1.14.4-1ubuntu1.1~ubuntu18.04.1, 1.14.5-0ubuntu1~18.04.1),  ghostscript-x:amd64 (9.26~dfsg+0-0ubuntu0.18.04.9,  9.26~dfsg+0-0ubuntu0.18.04.10), libgl1-mesa-dri:amd64  (19.0.2-1ubuntu1.1~18.04.1, 19.0.2-1ubuntu1.1~18.04.2), kwin-x11:amd64  (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1), drkonqi:amd64  (5.12.7-0ubuntu0.1, 5.12.8-0ubuntu0.1), ksysguard-data:amd64  (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1), iputils-ping:amd64  (3:20161105-1ubuntu2, 3:20161105-1ubuntu3), libmysqlclient20:amd64  (5.7.26-0ubuntu0.18.04.1, 5.7.27-0ubuntu0.18.04.1), libnss-systemd:amd64  (237-3ubuntu10.24, 237-3ubuntu10.25), libgs9-common:amd64  (9.26~dfsg+0-0ubuntu0.18.04.9, 9.26~dfsg+0-0ubuntu0.18.04.10),  thunderbird:amd64 (1:60.7.2+build2-0ubuntu0.18.04.1,  1:60.8.0+build1-0ubuntu0.18.04.1), libkwin4-effect-builtins1:amd64  (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1),  vlc-plugin-video-splitter:amd64 (3.0.4-1ubuntu0.2,  3.0.7.1-0ubuntu18.04.1), ksysguardd:amd64 (4:5.12.7-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), gstreamer1.0-libav:amd64  (1.14.4-0ubuntu1~ubuntu18.04.1, 1.14.5-0ubuntu1~18.04.1),  libgl1-mesa-glx:amd64 (19.0.2-1ubuntu1.1~18.04.1,  19.0.2-1ubuntu1.1~18.04.2), libkf5config-bin:amd64 (5.44.0-0ubuntu1,  5.44.0-0ubuntu1.1), libsane-common:amd64 (1.0.27-1~experimental3ubuntu2,  1.0.27-1~experimental3ubuntu2.1), fonts-opensymbol:amd64  (2:102.10+LibO6.0.7-0ubuntu0.18.04.7,  2:102.10+LibO6.0.7-0ubuntu0.18.04.8), libnss3:amd64 (2:3.35-2ubuntu2.2,  2:3.35-2ubuntu2.3), libkfontinstui5:amd64 (4:5.12.7-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), virtualbox-qt:amd64 (5.2.18-dfsg-2~ubuntu18.04.5,  5.2.32-dfsg-0~ubuntu18.04.1), firefox:amd64  (67.0.4+build1-0ubuntu0.18.04.1, 68.0.1+build1-0ubuntu0.18.04.1),  libreoffice-pdfimport:amd64 (1:6.0.7-0ubuntu0.18.04.7,  1:6.0.7-0ubuntu0.18.04.8), uno-libs3:amd64 (6.0.7-0ubuntu0.18.04.7,  6.0.7-0ubuntu0.18.04.8), gir1.2-gstreamer-1.0:amd64  (1.14.4-1~ubuntu18.04.1, 1.14.5-0ubuntu1~18.04.1), kscreen:amd64  (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1),  libreoffice-style-tango:amd64 (1:6.0.7-0ubuntu0.18.04.7,  1:6.0.7-0ubuntu0.18.04.8), tmux:amd64 (2.6-3ubuntu0.1, 2.6-3ubuntu0.2),  gtk-update-icon-cache:amd64 (3.22.30-1ubuntu3, 3.22.30-1ubuntu4),  mesa-vdpau-drivers:amd64 (19.0.2-1ubuntu1.1~18.04.1,  19.0.2-1ubuntu1.1~18.04.2), linux-firmware:amd64 (1.173.8, 1.173.9),  libssl1.1:amd64 (1.1.1-1ubuntu2.1~18.04.3, 1.1.1-1ubuntu2.1~18.04.4),  language-selector-gnome:amd64 (0.188.2, 0.188.3), libsox-fmt-base:amd64  (14.4.2-3, 14.4.2-3ubuntu0.18.04.1), libkfontinst5:amd64  (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1), vlc-plugin-base:amd64  (3.0.4-1ubuntu0.2, 3.0.7.1-0ubuntu18.04.1), libreoffice-gnome:amd64  (1:6.0.7-0ubuntu0.18.04.7, 1:6.0.7-0ubuntu0.18.04.8),  libkf5sysguard-data:amd64 (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1),  kde-config-screenlocker:amd64 (5.12.7-0ubuntu0.1, 5.12.8-0ubuntu0.1),  khotkeys-data:amd64 (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1),  libexiv2-14:amd64 (0.25-3.1ubuntu0.18.04.2, 0.25-3.1ubuntu0.18.04.3),  libpoppler-glib8:amd64 (0.62.0-2ubuntu2.9, 0.62.0-2ubuntu2.10),  libreoffice-calc:amd64 (1:6.0.7-0ubuntu0.18.04.7,  1:6.0.7-0ubuntu0.18.04.8), libpoppler73:amd64 (0.62.0-2ubuntu2.9,  0.62.0-2ubuntu2.10), kdeplasma-addons-data:amd64 (4:5.12.7-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), liboxygenstyleconfig5-5:amd64  (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1), libkwinxrenderutils11:amd64  (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1), thunderbird-locale-en:amd64  (1:60.7.2+build2-0ubuntu0.18.04.1, 1:60.8.0+build1-0ubuntu0.18.04.1),  patch:amd64 (2.7.6-2ubuntu1, 2.7.6-2ubuntu1.1),  plasma-look-and-feel-org-kde-breezedark-desktop:amd64  (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1),  libgstreamer-plugins-bad1.0-0:amd64 (1.14.4-1ubuntu1~ubuntu18.04.1,  1.14.5-0ubuntu1~18.04.1), libgstreamer1.0-0:amd64  (1.14.4-1~ubuntu18.04.1, 1.14.5-0ubuntu1~18.04.1), linux-generic:amd64  (4.15.0.54.56, 4.15.0.58.60), breeze-gtk-theme:amd64 (5.12.7-0ubuntu0.1,  5.12.8-0ubuntu0.1), powerdevil:amd64 (4:5.12.7-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), mysql-server-core-5.7:amd64  (5.7.26-0ubuntu0.18.04.1, 5.7.27-0ubuntu0.18.04.1),  libpowerdevilcore2:amd64 (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1),  libprocessui7:amd64 (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1),  ksysguard:amd64 (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1),  libreoffice-base-drivers:amd64 (1:6.0.7-0ubuntu0.18.04.7,  1:6.0.7-0ubuntu0.18.04.8), kwin-common:amd64 (4:5.12.7-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), qml-module-qtquick-controls-styles-breeze:amd64  (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1), gstreamer1.0-gl:amd64  (1.14.4-1ubuntu1.1~ubuntu18.04.1, 1.14.5-0ubuntu1~18.04.1),  libreoffice-draw:amd64 (1:6.0.7-0ubuntu0.18.04.7,  1:6.0.7-0ubuntu0.18.04.8), plasma-widgets-addons:amd64  (4:5.12.7-0ubuntu0.1, 4:5.12.8-0ubuntu0.1), libinput10:amd64 (1.10.4-1,  1.10.4-1ubuntu0.18.04.1), libreoffice-avmedia-backend-gstreamer:amd64  (1:6.0.7-0ubuntu0.18.04.7, 1:6.0.7-0ubuntu0.18.04.8),  mesa-va-drivers:amd64 (19.0.2-1ubuntu1.1~18.04.1,  19.0.2-1ubuntu1.1~18.04.2), base-files:amd64 (10.1ubuntu2.4,  10.1ubuntu2.6), libglx-mesa0:amd64 (19.0.2-1ubuntu1.1~18.04.1,  19.0.2-1ubuntu1.1~18.04.2), libweather-ion7:amd64 (4:5.12.7-0ubuntu0.1,  4:5.12.8-0ubuntu0.1), software-properties-common:amd64 (0.96.24.32.9,  0.96.24.32.11)
End-Date: 2019-08-13  15:26:56
```

Why  doesn't this boot? What should I look for in the journal? If this is a  hardware problem, what part could it be? Did one of these updates break  it?

---

### Post by Bashing-om on 2019-08-15
freedombacon; Hello -

> 
Why doesn't this boot? What should I look for in the journal? If this is a hardware problem, what part could it be? Did one of these updates break it?


No telling at this point what is not going on - let's do some diagnostic commands and try and isolate.
Post back:
```

sudo blkid -c /dev/null -o list
cat /etc/fstab
sudo lshw -C display ##where I can accept "unclaimed" as the booting is in recovery - I am interested in identifying the hardware

```


[INDENT][INDENT]see where we go from here
[/INDENT][/INDENT]

---

### Post by freedombacon on 2019-08-15
Thanks for the quick reply.

blkid
```
device     fs_type label    mount point    UUID

/dev/nvme0n1
                            (in use)       
/dev/nvme0n1p1
           crypto_LUKS      (in use)       512a15ce-c0b1-4892-ae3a-9bef0da89a66
/dev/sda1  ext2             (not mounted)  ea56d16d-a783-4d9b-b4db-47629bb10206
/dev/sda5  crypto_LUKS      (not mounted)  6044518b-b0d1-417a-a510-95d93f06ca9e
/dev/sdb1  vfat             /boot/efi      BD1D-011C
/dev/sdb2  ext4             /boot          2b186b5f-f572-49f2-97c7-e98a2b934996
/dev/sdb3  crypto_LUKS      (in use)       c7dba435-cee3-4171-abb5-fff6b0ac36ae
/dev/sdc1  crypto_LUKS      (in use)       b6d468db-9fe5-4c36-9e54-9393153818d2
/dev/sdd1  crypto_LUKS      (in use)       8f3721a1-eac1-4add-9935-68981fa16dfd
/dev/mapper/sda3_crypt
           LVM2_member      (in use)       tpf3HG-jWZO-GYh3-bQRE-iMd7-NOV7-U6Mwo9
/dev/mapper/hostname--vg-swap_1
           swap             [SWAP]         2225110f-f10e-415d-953a-6beca9a28325
/dev/mapper/hostname--vg-root
           ext4             /              99a00e10-e6aa-475f-b6ca-18f55220a36b
/dev/mapper/hostname--vg-usr
           ext4             /usr           636cbba1-506f-42c6-bda9-1d43d0c03147
/dev/mapper/hostname--vg-var
           ext4             /var           bfe91b39-83d3-4c48-8560-7616159bdadd
/dev/mapper/hostname--vg-opt
           ext4             /opt           d8afb181-a3e0-474d-ac6b-2a2d14af7864
/dev/mapper/hostname--vg-tmp
           ext4             /tmp           21efee3f-1acb-4113-8bcf-98ee316f6181
/dev/mapper/ironwolf
           ext4             /mnt/ironwolf  a89e8a55-9703-4130-aa4e-12022c74a2fa
/dev/mapper/terascale
           ext4             /home          9dc1d3db-64a6-4cd3-801e-29fb0063f41c
/dev/mapper/970evo
           ext4             /mnt/970evo    4d84e87c-d6c1-406b-8323-e8e8c43c9b89
```

fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/hostname--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=2b186b5f-f572-49f2-97c7-e98a2b934996 /boot           ext4    defaults        0       2
# /boot/efi was on /dev/sda1 during installation
UUID=BD1D-011C  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/hostname--vg-opt /opt            ext4    defaults        0       2
/dev/mapper/hostname--vg-tmp /tmp            ext4    defaults        0       2
/dev/mapper/hostname--vg-usr /usr            ext4    defaults        0       2
/dev/mapper/hostname--vg-var /var            ext4    defaults        0       2
/dev/mapper/hostname--vg-swap_1 none            swap    sw              0       0
# /home on seagate terascale
/dev/mapper/terascale /home     ext4     defaults        0       0
# WD Re FAILED
#/dev/mapper/wdre /mnt/wdre      ext4     defaults        0       0
# WD Red 
/dev/mapper/wdred /mnt/wdred    xfs     defaults        0       0
# WD Black  Combined to RAID mdblack
#/dev/mapper/wdblack1 /mnt/black1 ext4    defaults       0       0
# WD Black  Combined to RAID mdblack
#/dev/mapper/wdblack2 /mnt/black2 ext4    defaults        0       0
# Seagate Ironwolf
/dev/mapper/ironwolf /mnt/ironwolf ext4  defaults       0        0
# Samsung 970 EVO
/dev/mapper/970evo /mnt/970evo ext4 defaults,lazytime,nodev,journal_checksum,discard 0 0
# WD Blacks in RAID1
#/dev/mapper/vg-mdblack/lv-mdblack /mnt/mdblack ext4 defaults 0 0
```

lshw
```
  *-display                 
       description: VGA compatible controller
       product: Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:55 memory:d0000000-dfffffff memory:fbe20000-fbe3ffff ioport:e000(size=256) memory:c0000-dffff
```

---

### Post by Bashing-om on 2019-08-15
freedombacon; Welp -

I see nothing here to point to an error in mounting - but I do not have the experience with encryption and such to have an opinion :(

However - the practice of using the UUIDs rather than a directory location is highly encouraged in the fstab file.
```

sysop@x1804mini:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=1460de17-30e4-4566-b181-18c17b62887a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=5cd50446-1330-4130-a521-1ea936c9fc2a /home           ext4    defaults        0       2
# /var was on /dev/sdb3 during installation
UUID=69b1f02a-5e00-415e-ab75-78fdd63f72a3 /var            ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=8d4743bc-8e47-4650-b5fd-1ea904d4ecda none            swap    sw              0       0
sysop@x1804mini:~$ 

```

Not much help -
[INDENT][INDENT]maybe a push in the right direction 
[/INDENT][/INDENT]

---

### Post by freedombacon on 2019-08-16
The UUIDs aren't necessary in fstab in this case. Correct, they do make sure a partition is mounted in the correct place. When partitions are encrypted, the UUIDs go in /etc/crypttab. There is also a name for the filesystem there, so the friendly name /dev/mapper/example is always correct. LVM is similar, where the name of the volume is part of its metadata, so the device name in fstab is always correctly mounted.

---

### Post by hanzomon4 on 2019-08-18
Was the failed drive in your fstab? I think that can cause a drop to initramfs shell.

---

### Post by freedombacon on 2019-08-18
I finally figured out how to get it to boot. It turns out that one of the LVs was being created with a different device name than I originally created. It's still not clear why this was enough of emergency to stop the boot. Technically, this computer only needs one drive to get to the login screen. Are there different options I should be using in fstab/crypttab/mdadm/etc...? If this had booted the way it was supposed to, I would have been able to find this problem a lot sooner.

---


---
title: "libsdl2-dev screws over my Ubuntu 22.04 installation"
date: 2022-05-16
forum: General Help
---

### Post by fpi1337 on 2022-05-16
Hi guys, I've opened this thread because I've encountered a critical issue when it comes to installing libsdl2-dev under Ubuntu 22.04 (using apt). Whenever I choose to install it, apt removes the majority of the mandatory packages like for example the GNOME DE and many other stuff. I even can't access my system anymore and I'm force to reinstall 22.04. Has anyone succeeded in installing libsdl2-dev? It's not the first time that there's a problem with that package. I've already experienced this almost a year ago under 21.03(?) and posted that issue here.

Does someone know how to solve this?

---

### Post by him610 on 2022-05-16
On my LTS 22.04 system,* libsdl2-dev* is installed automatically at installation. There is no need to install it manually; same goes for LTS 20.04.4.

---

### Post by fpi1337 on 2022-05-17
First of all, thank you for your reply!

It's weird because I just reinstalled 22.04 again but libsdl2-dev wasn't installed automatically on my system. I have to install it myself. But if I try to install it, the following output occurs:

```
fpi@fpi-VPCEH3J1E:~$ sudo apt-get install libsdl2-dev
Paketlisten werden gelesen… Fertig
Abhängigkeitsbaum wird aufgebaut… Fertig
Statusinformationen werden eingelesen… Fertig
Die folgenden Pakete wurden automatisch installiert und werden nicht mehr benötigt:
  acl apg aptdaemon-data apturl-common bluez-obexd bolt busybox-initramfs
  chromium-codecs-ffmpeg-extra colord-data desktop-file-utils dns-root-data
  dnsmasq-base fdisk gdisk genisoimage gir1.2-accountsservice-1.0 gir1.2-adw-1
  gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdm-1.0 gir1.2-geoclue-2.0 gir1.2-gnomebluetooth-3.0 gir1.2-goa-1.0
  gir1.2-graphene-1.0 gir1.2-gst-plugins-base-1.0 gir1.2-gtk-4.0
  gir1.2-gudev-1.0 gir1.2-gweather-3.0 gir1.2-javascriptcoregtk-4.0
  gir1.2-json-1.0 gir1.2-mutter-10 gir1.2-nm-1.0 gir1.2-nma-1.0 gir1.2-rb-3.0
  gir1.2-rsvg-2.0 gir1.2-snapd-1 gir1.2-soup-2.4 gir1.2-udisks-2.0
  gir1.2-unity-7.0 gir1.2-upowerglib-1.0 gir1.2-vte-2.91 gir1.2-webkit2-4.0
  gkbd-capplet gnome-bluetooth-3-common gnome-bluetooth-common
  gnome-control-center-faces gnome-online-accounts gnome-session-common
  gnome-settings-daemon-common gnome-shell-common gstreamer1.0-pipewire
  gstreamer1.0-vaapi gvfs-common gvfs-libs hplip-data initramfs-tools-bin
  klibc-utils libadwaita-1-0 libatasmart4 libatomic1:i386 libblockdev-crypto2
  libblockdev-fs2 libblockdev-loop2 libblockdev-part-err2 libblockdev-part2
  libblockdev-swap2 libblockdev-utils2 libblockdev2 libbluetooth3 libbsd0:i386
  libcdio-cdda2 libcdio-paranoia2 libcolord-gtk1 libcolorhug2 libcue2
  libdmapsharing-3.0-2 libdrm-amdgpu1:i386 libdrm-nouveau2:i386
  libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libelf1:i386 libexpat1:i386
  libfdisk1 libffi8:i386 libflashrom1 libfprint-2-2 libfreerdp-server2-2
  libftdi1-2 libfwupd2 libfwupdplugin5 libgcab-1.0-0 libgdm1 libgif7
  libglapi-mesa:i386 libglvnd0:i386 libgnome-autoar-0-0 libgnome-bg-4-1
  libgnome-bluetooth-3.0-13 libgnome-bluetooth13 libgnome-desktop-4-1
  libgnomekbd-common libgnomekbd8 libgoa-backend-1.0-1 libgpod-common libgpod4
  libgsf-1-114 libgsf-1-common libgsound0 libgssdp-1.2-0
  libgstreamer-plugins-bad1.0-0 libgupnp-1.2-1 libgupnp-av-1.0-3
  libgupnp-dlna-2.0-4 libgusb2 libhpmud0 libicu70:i386 libieee1284-3
  libimagequant0 libimobiledevice6 libjcat1 libklibc libldb2 liblirc-client0
  libllvm13:i386 libmbim-glib4 libmbim-proxy libmd0:i386 libmtp-common
  libmtp-runtime libmtp9 libmutter-10-0 libndp0 libnetplan0 libnfs13 libnm0
  libnma-common libnma0 libnvidia-cfg1-390 libnvidia-common-390
  libnvidia-compute-390:i386 libnvidia-decode-390 libnvidia-decode-390:i386
  libnvidia-encode-390 libnvidia-encode-390:i386 libnvidia-fbc1-390
  libnvidia-gl-390 libnvidia-gl-390:i386 libnvidia-ifr1-390
  libparted-fs-resize0 libpipewire-0.3-0 libpipewire-0.3-common
  libpipewire-0.3-modules libpkcs11-helper1 libplist3 libplymouth5
  libqmi-glib5 libqmi-proxy libraqm0 librhythmbox-core10 librygel-core-2.6-2
  librygel-db-2.6-2 librygel-renderer-2.6-2 librygel-server-2.6-2
  libsane-common libsane-hpaio libsbc1 libsensors5:i386 libsgutils2-2
  libsmbclient libsmbios-c2 libsnmp-base libsnmp40 libspa-0.2-modules
  libstdc++6:i386 libsysmetrics1 libtalloc2 libtcl8.6 libteamdctl0 libtevent0
  libudisks2-0 libusbmuxd6 libva-wayland2 libvncserver1 libvolume-key1
  libvulkan1:i386 libwayland-client0:i386 libwbclient0 libx11-6:i386
  libx11-xcb1:i386 libxatracker2 libxau6:i386 libxcb-dri2-0:i386
  libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-icccm4 libxcb-image0
  libxcb-keysyms1 libxcb-present0:i386 libxcb-randr0:i386 libxcb-render-util0
  libxcb-res0 libxcb-shm0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386
  libxcb-xkb1 libxcb-xv0 libxcb1:i386 libxcvt0 libxdmcp6:i386 libxext6:i386
  libxfixes3:i386 libxfont2 libxkbcommon-x11-0 libxklavier16 libxml2:i386
  libxnvctrl0 libxshmfence1:i386 libxvmc1 libxxf86vm1:i386 linux-sound-base
  mesa-vulkan-drivers:i386 mobile-broadband-provider-info mutter-common
  nautilus-data nvidia-compute-utils-390 nvidia-kernel-source-390
  nvidia-utils-390 openvpn pipewire pipewire-bin pipewire-media-session
  power-profiles-daemon ppp pptp-linux printer-driver-hpcups
  printer-driver-postscript-hp python3-certifi python3-chardet python3-click
  python3-colorama python3-dateutil python3-debconf python3-debian
  python3-defer python3-ldb python3-macaroonbakery python3-mako
  python3-markupsafe python3-netifaces python3-olefile python3-pil
  python3-protobuf python3-pymacaroons python3-renderpm python3-reportlab
  python3-reportlab-accel python3-requests python3-rfc3339
  python3-software-properties python3-talloc python3-tz python3-xkit
  rhythmbox-data rygel samba-libs sane-airscan switcheroo-control tcl tcl8.6
  tracker tracker-extract tracker-miner-fs ubuntu-advantage-desktop-daemon
  update-notifier-common usb-modeswitch usb-modeswitch-data usbmuxd x11-apps
  x11-session-utils x11-xkb-utils xbitmaps xcvt xdg-desktop-portal xfonts-base
  xfonts-encodings xfonts-scalable xfonts-utils xinit xinput xserver-common
  xserver-xephyr xserver-xorg-legacy xwayland zstd
Verwenden Sie »sudo apt autoremove«, um sie zu entfernen.
Die folgenden zusätzlichen Pakete werden installiert:
  dbus-x11 gnome-control-center-data libasound2-dev libblkid-dev libc-dev-bin
  libc-devtools libc6-dev libcrypt-dev libdbus-1-dev libdecor-0-0
  libdecor-0-plugin-1-cairo libegl-dev libegl1-mesa-dev libffi-dev libgl-dev
  libgles-dev libgles1 libglib2.0-dev libglib2.0-dev-bin libglu1-mesa-dev
  libglvnd-core-dev libglvnd-dev libglx-dev libibus-1.0-dev libice-dev
  libmount-dev libnsl-dev libopengl-dev libpcre16-3 libpcre2-16-0 libpcre2-dev
  libpcre2-posix3 libpcre3-dev libpcre32-3 libpcrecpp0v5 libpthread-stubs0-dev
  libpulse-dev libsdl2-2.0-0 libselinux1-dev libsepol-dev libsm-dev
  libsndio-dev libsndio7.0 libtirpc-dev libudev-dev libudev1 libwayland-bin
  libwayland-dev libx11-dev libxau-dev libxcb1-dev libxcursor-dev libxdmcp-dev
  libxext-dev libxfixes-dev libxi-dev libxinerama-dev libxkbcommon-dev
  libxrandr-dev libxrender-dev libxss-dev libxt-dev libxv-dev libxxf86vm-dev
  linux-libc-dev manpages-dev python3-distutils python3-software-properties
  rpcsvc-proto uuid-dev x11proto-dev xorg-sgml-doctools xtrans-dev zlib1g-dev
Vorgeschlagene Pakete:
  libasound2-doc glibc-doc libgirepository1.0-dev libglib2.0-doc libxml2-utils
  libice-doc libsm-doc sndiod libwayland-doc libx11-doc libxcb-doc libxext-doc
  libxt-doc
Empfohlene Pakete:
  unattended-upgrades
Die folgenden Pakete werden ENTFERNT:
  alsa-base aptdaemon apturl bluez brltty colord dbus-user-session fprintd
  friendly-recovery fwupd gdm3 gnome-bluetooth gnome-control-center
  gnome-disk-utility gnome-initial-setup gnome-power-manager
  gnome-remote-desktop gnome-session-bin gnome-settings-daemon gnome-shell
  gnome-shell-extension-appindicator gnome-shell-extension-desktop-icons-ng
  gnome-shell-extension-ubuntu-dock gnome-startup-applications
  gstreamer1.0-packagekit gvfs gvfs-backends gvfs-daemons gvfs-fuse hplip
  initramfs-tools initramfs-tools-core language-selector-gnome libnss-systemd
  libpam-fprintd libpam-systemd libsane1 libtss2-esys-3.0.2-0 libtss2-mu0
  libtss2-sys1 libtss2-tcti-cmd0 libtss2-tcti-device0 libtss2-tcti-mssim0
  libtss2-tcti-swtpm0 libu2f-udev media-player-info modemmanager nautilus
  nautilus-share netplan.io network-manager
  network-manager-config-connectivity-ubuntu network-manager-gnome
  network-manager-openvpn network-manager-openvpn-gnome network-manager-pptp
  network-manager-pptp-gnome nvidia-settings packagekit packagekit-tools
  pkexec plymouth plymouth-label plymouth-theme-spinner
  plymouth-theme-ubuntu-text policykit-1 polkitd pulseaudio-module-bluetooth
  python3-aptdaemon python3-aptdaemon.gtk3widgets rhythmbox
  rhythmbox-plugin-alternative-toolbar rhythmbox-plugins rtkit sane-utils
  screen-resolution-extra simple-scan snapd software-properties-common
  software-properties-gtk systemd-oomd systemd-timesyncd tpm-udev
  ubuntu-desktop ubuntu-desktop-minimal ubuntu-drivers-common ubuntu-minimal
  ubuntu-release-upgrader-gtk ubuntu-session ubuntu-standard udev udisks2
  update-manager update-notifier upower usb-creator-common usb-creator-gtk
  xdg-desktop-portal-gnome xdg-desktop-portal-gtk xorg xserver-xorg
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-libinput
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-amdgpu
  xserver-xorg-video-ati xserver-xorg-video-fbdev xserver-xorg-video-intel
  xserver-xorg-video-nouveau xserver-xorg-video-nvidia-390
  xserver-xorg-video-qxl xserver-xorg-video-radeon xserver-xorg-video-vesa
  xserver-xorg-video-vmware
Die folgenden NEUEN Pakete werden installiert:
  dbus-x11 libasound2-dev libblkid-dev libc-dev-bin libc-devtools libc6-dev
  libcrypt-dev libdbus-1-dev libdecor-0-0 libdecor-0-plugin-1-cairo libegl-dev
  libegl1-mesa-dev libffi-dev libgl-dev libgles-dev libgles1 libglib2.0-dev
  libglib2.0-dev-bin libglu1-mesa-dev libglvnd-core-dev libglvnd-dev
  libglx-dev libibus-1.0-dev libice-dev libmount-dev libnsl-dev libopengl-dev
  libpcre16-3 libpcre2-16-0 libpcre2-dev libpcre2-posix3 libpcre3-dev
  libpcre32-3 libpcrecpp0v5 libpthread-stubs0-dev libpulse-dev libsdl2-2.0-0
  libsdl2-dev libselinux1-dev libsepol-dev libsm-dev libsndio-dev libsndio7.0
  libtirpc-dev libudev-dev libwayland-bin libwayland-dev libx11-dev libxau-dev
  libxcb1-dev libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev libxi-dev
  libxinerama-dev libxkbcommon-dev libxrandr-dev libxrender-dev libxss-dev
  libxt-dev libxv-dev libxxf86vm-dev linux-libc-dev manpages-dev
  python3-distutils rpcsvc-proto uuid-dev x11proto-dev xorg-sgml-doctools
  xtrans-dev zlib1g-dev
Die folgenden Pakete werden aktualisiert (Upgrade):
  gnome-control-center-data libudev1 python3-software-properties
3 aktualisiert, 72 neu installiert, 116 zu entfernen und 59 nicht aktualisiert.
Es müssen noch 17,1 MB von 17,6 MB an Archiven heruntergeladen werden.
Nach dieser Operation werden 133 MB Plattenplatz freigegeben.
Möchten Sie fortfahren? [J/n] 

```

Although, it's in german, you can see that apt wants to remove a bunch of mandatory packages. And that's totally weird. Maybe someone else has an idea how to avoid this?


best regards

---

### Post by fpi1337 on 2022-05-17
It turns out, that upgrading the existing packages "fixed" this bug. When I installed my Ubuntu, I checked the "download updates while installing"-checkbox. But I didn't know that I have to install the downloaded packages manually. After upgrading the packages with the update manager, libsdl2-dev could be installed without any problems.

---

### Post by Impavidus on 2022-05-17
The **59 nicht aktualisiert** gives it away. For 59 packages there were upgrades available. When you install something new, it may depend on the latest version of some libraries. If you haven't upgraded your other software, that may depend on an older version of those libraries, leading to some package version conflict. apt "solves" this by installing the stuff you requested and removing the conflicting stuff. So, before installing anything new, make sure the existing packages are all up to date.

BTW, libsdl2-dev is indeed not installed by default, at least not on my Xubuntu 21.10 system. I installed it from the repos to compile a game from source. Most people don't need -dev packages, as they are for compiling your own stuff.

---

### Post by fpi1337 on 2022-05-17
> **Impavidus said:**
> The **59 nicht aktualisiert** gives it away. For 59 packages there were upgrades available. When you install something new, it may depend on the latest version of some libraries. If you haven't upgraded your other software, that may depend on an older version of those libraries, leading to some package version conflict. apt "solves" this by installing the stuff you requested and removing the conflicting stuff. So, before installing anything new, make sure the existing packages are all up to date.

BTW, libsdl2-dev is indeed not installed by default, at least not on my Xubuntu 21.10 system. I installed it from the repos to compile a game from source. Most people don't need -dev packages, as they are for compiling your own stuff.

Thanks for clarifying! To be honest, I'm not used to updating since I mostly use point releases. These conflicts don't occur (mostly) when running a point release. I completely ignored that 22.04 hasn't a point release yet, so updating my packages is mandatory for functionality.

And yes indeed, mostly you don't need libsdl2-dev but you in my case I wanted to compile a game from source. I also needed it to compile my own Citra Emulator build, so it's a pretty common thing to have it on my systems. But yeah, point releases.. :P

---

### Post by frederick0 on 2022-05-17
Thanks for sharing the help, I am new here and this thread is really helpful for me.

---

### Post by fpi1337 on 2022-05-17
> **frederick0 said:**
> Thanks for sharing the help, I am new here and this thread is really helpful for me.

Glad that this helps and that I'm not the only who that experienced that issue!

---


---
title: "Updates to 12.04 32bit are causing OpenGL issues"
date: 2012-10-26
forum: General Help
---

### Post by Sidner on 2012-10-26
Hey guys. I'm having the following issue, but first a little background. I have a working program that uses OpenGL, made on an Ubuntu 12.04 32bit a couple of weeks ago. Since then, I've tried Ubuntu 12.10 and come back to 12.04 due to some issues with OpenGL as well. I though "well, it worked on 12.04, so it must be work again". It does, on a fresh install, after installing the OpenGL dev libraries (freeglut3, libglui-dev and libglew1.6-dev). I installed Gnome3 and, after all the updates it did (kernel included), it still worked. What happens is, after installing some more updates to Ubuntu (which I'll show below), OpenGL starts crashing in a weird way. Instead of loading the correct textures for each material, it loads the last loaded texture on some materials! And the materials to which it does seems random to me. It must be one of the following updates that is causing the issue, but I really don't want to install one by one and see which one crashes, causing me to do a clean install all over again...

The updates are the following:

```

sidner@sidner-pc:~$ sudo apt-get upgrade
[sudo] password for sidner: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  ginn libgrip0 libunity-2d-private0 libunity-core-5.0-5 unity unity-2d-common unity-2d-panel unity-2d-shell unity-2d-spread unity-common
  unity-services
The following packages will be upgraded:
  accountsservice apparmor apport apport-gtk apport-symptoms apt apt-transport-https apt-utils aptdaemon aptdaemon-data bind9-host coreutils cups
  cups-bsd cups-client cups-common cups-ppdc dbus dbus-x11 dnsutils eog evince evince-common firefox firefox-globalmenu firefox-gnome-support
  fontconfig fontconfig-config ghostscript ghostscript-cups ghostscript-x gir1.2-javascriptcoregtk-3.0 gir1.2-rb-3.0 gir1.2-totem-1.0
  gir1.2-webkit-3.0 glib-networking glib-networking-common glib-networking-services gnome-control-center gnome-control-center-data gnome-media gnupg
  gpgv grub-common grub-pc grub-pc-bin grub2-common gvfs gvfs-backends gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs isc-dhcp-client
  isc-dhcp-common jockey-common jockey-gtk landscape-client-ui-install libaccountsservice0 libapt-inst1.4 libapt-pkg4.12 libart-2.0-2 libbind9-80
  libc-bin libc-dev-bin libc6 libc6-dev libcups2 libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libdbus-1-3 libdns81 libevince3-3
  libfontconfig1 libgl1-mesa-dri libgnome-control-center1 libgnome2-common libgs9 libgs9-common libisc83 libisccc80 libisccfg82
  libjavascriptcoregtk-3.0-0 libldap-2.4-2 liblwres80 libnux-2.0-0 libnux-2.0-common libparted0debian1 librhythmbox-core5 libssl1.0.0 libtotem0
  libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libxatracker1 libxcb-dri2-0 libxcb-glx0 libxcb-render0 libxcb-shape0 libxcb-shm0 libxml2 libxslt1.1
  linux-firmware linux-libc-dev login lsb-base lsb-release multiarch-support ntfs-3g nux-tools nvidia-common onboard openssl parted passwd
  policykit-1-gnome python-apport python-aptdaemon python-aptdaemon.gtk3widgets python-aptdaemon.pkcompat python-gst0.10 python-libxml2
  python-problem-report python-software-properties resolvconf rhythmbox rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder
  rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins sessioninstaller software-center software-properties-common
  software-properties-gtk totem totem-common totem-mozilla totem-plugins transmission-common transmission-gtk tzdata ubuntu-keyring unity-2d
  unity-greeter update-manager update-manager-core update-notifier update-notifier-common wpasupplicant x11-utils xdiagnose xserver-common
  xserver-xorg-core xserver-xorg-input-synaptics xserver-xorg-input-wacom xserver-xorg-video-intel xterm
162 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.

```

All and any help is appreciated. I'm not upgrading anything till I have this sorted out or at least a clue...

Thank you.

---

### Post by dino99 on 2012-10-26
run that program in debug mode or at least into a terminal to see the output. Might be a version issue due to some upgrades. If you remember the date of the suddent problem, then you can check the updates history inside synaptic for example.

---

### Post by Sidner on 2012-10-27
> **dino99 said:**
> run that program in debug mode or at least into a terminal to see the output. Might be a version issue due to some upgrades. If you remember the date of the suddent problem, then you can check the updates history inside synaptic for example.

Well, I am, since I wrote the program. :P The output all checks out. I'm printing out all the materials and textures that are being applied at any given moment and they all check out...but the ones on the screen don't... :( First time the problem happened was when I switched from 12.04 32bit to 12.10 64bit. Might be one of the updates comes by default on the new release?

---


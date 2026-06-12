---
title: "sudo apt autoremove just bricked my machine - why?"
date: 2020-04-30
forum: General Help
---

### Post by GhX6GZMB on 2020-04-30
I always thought autoremove was relatively harmless. But after an apt update and upgrade I ran apt autoremove. It deleted hundreds of files, and my laptop is now bricked.

How can this happen, and what can I do prevent this in the future?

Fortunately, I have a backup, but when I restore this, I'll probably have the same thing happening next time.

Suggestions, anyone?

Thank You.

---

### Post by VMC on 2020-04-30
Sometimes when you delete a critical piece of program, it then wants to remove all related programs. Do you recall what you deleted to spark the autoremove?

---

### Post by CelticWarrior on 2020-04-30
It's very rare but happens.
The typical cause is a messed up sources list and/or things we wrongly uninstalled. Without knowing the history before that unfortunate event this is all anyone can say about it.

---

### Post by sgage on 2020-04-30
First of all, you didn't 'brick' your machine. You broke the OS. Bricking means that something has borked the firmware on your computer or device to the point that nothing can be done with it - it's as useful as a brick.

What I would do is boot with a live usb or dvd, get my files backed up somewhere, and reinstall. Trying to piece together exactly what happened can be impossible and very fiddly - just reinstall, and you'll save a lot of time and aggravation.

---

### Post by GhX6GZMB on 2020-04-30
Thank You for your replies. 
Using Timeshift I just resurrected my setup and my machine is running again.
I have a wonderfully stable setup with just two users and have had no problems at all until now. I use Muon for installation and removal of programs, this has always worked perfectly.

I regularly do a sudo apt update + upgrade with no issues. Today I decided to do a sudo apt autoremove on top. This has never been a problem before.

This was the output:
```
macro@macro-pc:~$ sudo apt autoremoveReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  2048-qt acpi-support acpid alsa-base apport apport-symptoms apt-config-icons-hidpi apt-config-icons-large apt-config-icons-large-hidpi
  apt-xapian-index arc-theme bluedevil bluez bluez-cups bolt breeze-cursor-theme catdoc cdparanoia cdrdao cdrskin chafa compton
  compton-conf dc dvd+rw-tools fcitx5-module-quickphrase-editor fonts-freefont-ttf fonts-kacst fonts-kacst-one fonts-khmeros-core fonts-lao
  fonts-lklug-sinhala fonts-noto-cjk fonts-sil-abyssinica fonts-sil-padauk fonts-symbola fonts-thai-tlwg fonts-tibetan-machine
  fonts-tlwg-garuda fonts-tlwg-garuda-ttf fonts-tlwg-kinnari fonts-tlwg-kinnari-ttf fonts-tlwg-laksaman fonts-tlwg-laksaman-ttf
  fonts-tlwg-loma fonts-tlwg-loma-ttf fonts-tlwg-mono fonts-tlwg-mono-ttf fonts-tlwg-norasi fonts-tlwg-norasi-ttf fonts-tlwg-purisa
  fonts-tlwg-purisa-ttf fonts-tlwg-sawasdee fonts-tlwg-sawasdee-ttf fonts-tlwg-typewriter fonts-tlwg-typewriter-ttf fonts-tlwg-typist
  fonts-tlwg-typist-ttf fonts-tlwg-typo fonts-tlwg-typo-ttf fonts-tlwg-umpush fonts-tlwg-umpush-ttf fonts-tlwg-waree fonts-tlwg-waree-ttf
  fwupd fwupd-signed genisoimage geoclue-2.0 gir1.2-udisks-2.0 git git-man gnome-accessibility-themes gnome-themes-extra
  gnome-themes-extra-data growisofs gstreamer1.0-gtk3 gtk2-engines-murrine gtk2-engines-pixbuf haveged htop iio-sensor-proxy im-config
  imagemagick-6-common inputattach k3b k3b-data kactivities-bin kactivitymanagerd kcalc kde-cli-tools kde-cli-tools-data kde-style-breeze
  kerneloops kpackagelauncherqml kpackagetool5 laptop-detect liba52-0.7.4 libabw-0.1-1 libao-common libao4 libappstreamqt2 libaribb24-0
  libaudio2 libbasicusageenvironment1 libburn4 libcddb2 libcdr-0.1-1 libchafa0 libcolamd2 libconfig9 libdc1394-22 libdca0 libdjvulibre-text
  libdjvulibre21 libdvbpsi10 libdvdnav4 libdvdread4 libe-book-0.1-1 libebml4v5 libegl1-mesa libepub0 libepubgen-0.1-1 liberror-perl
  libetonyek-0.1-1 libevent-2.1-6 libexiv2-14 libfaad2 libfcitx-config4 libfcitx-core0 libfcitx-gclient1 libfcitx-qt5-1 libfcitx-qt5-data
  libfcitx-utils0 libflac++6v5 libfreehand-0.1-1 libfwupd2 libgcab-1.0-0 libgettextpo0 libgles2 libglu1-mesa libgroupsock8 libhavege1
  libiso9660-11 libixml10 libk3b7 libk3b7-extracodecs libkate1 libkf5activities5 libkf5bluezqt-data libkf5bluezqt6 libkf5calendarevents5
  libkf5cddb-data libkf5cddb5 libkf5declarative-data libkf5declarative5 libkf5filemetadata-bin libkf5filemetadata-data libkf5filemetadata3
  libkf5kcmutils-data libkf5kcmutils5 libkf5kirigami2-5 libkf5networkmanagerqt6 libkf5newstuff-data libkf5newstuff5 libkf5newstuffcore5
  libkf5notifyconfig-data libkf5notifyconfig5 libkf5package-data libkf5package5 libkf5plasma5 libkf5plasmaquick5 libkf5quickaddons5
  libkf5style5 libkf5su-bin libkf5su-data libkf5su5 libkworkspace5-5 liblirc-client0 liblivemedia64 liblqr-1-0 liblua5.2-0 libmad0
  libmagickcore-6.q16-6 libmagickwand-6.q16-6 libmatroska6v5 libmicrodns0 libmimetic0v5 libminiupnpc17 libminizip1 libmpcdec6 libmpeg2-4
  libmspub-0.1-1 libmusicbrainz5cc2v5 libmwaw-0.3-3 libnatpmp1 liboath0 libodfgen-0.1-1 libopenmpt-modplug1 libpackagekitqt5-1
  libpagemaker-0.0-0 libperl4-corelibs-perl libphonon4qt5-4 libpipewire-0.2-1 libplacebo7 libpoppler-qt5-1 libpresage-data libpresage1v5
  libprotobuf-lite17 libproxy-tools libqapt3 libqapt3-runtime libqca-qt5-2 libqca-qt5-2-plugins libqgpgme7 libqrencode4 libqt4-dbus
  libqt4-declarative libqt4-network libqt4-script libqt4-sql libqt4-sql-mysql libqt4-xml libqt4-xmlpatterns libqt5concurrent5
  libqt5designer5 libqt5help5 libqt5keychain1 libqt5multimedia5 libqt5positioning5 libqt5quickcontrols2-5 libqt5quicktemplates2-5
  libqt5quickwidgets5 libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5webchannel5 libqt5webengine-data libqt5webenginecore5
  libqt5webenginewidgets5 libqt5webkit5 libqtcore4 libqtdbus4 libqtgui4 libre2-5 libreoffice-base-core libreoffice-calc libreoffice-draw
  libreoffice-gtk3 libreoffice-impress libreoffice-math libreoffice-writer libresid-builder0c2a libsbc1 libsdl-image1.2 libsdl1.2debian
  libsidplay2 libsmbios-c2 libsnapd-qt1 libsndio7.0 libspatialaudio0 libspectre1 libssh2-1 libsuitesparseconfig5 libsynctex2
  libtinyxml2.6.2v5 libu2f-udev libupnp13 libusageenvironment3 libva-wayland2 libvcdinfo0 libvisio-0.1-1 libvlc-bin libvlc5 libvlccore9
  libvncclient1 libwhoopsie0 libwpd-0.10-10 libwpg-0.3-3 libwps-0.4-4 libxapian30 libxatracker2 libxcb-composite0 libxcb-damage0 libxcb-xv0
  libxfont2 libxmlb1 libxvmc1 linux-headers-5.3.0-18 linux-headers-5.3.0-18-generic linux-image-5.3.0-18-generic
  linux-modules-5.3.0-18-generic linux-modules-extra-5.3.0-18-generic linux-sound-base lp-solve lubuntu-default-settings lxqt-admin
  lxqt-admin-l10n memtest86+ mesa-vulkan-drivers mscompress mtools muon neofetch nm-tray noblenote oathtool ofono pass pass-extension-otp
  pastebinit patch pcmciautils phonon4qt5 phonon4qt5-backend-vlc plasma-discover plasma-discover-backend-snap plasma-discover-common
  plasma-framework policykit-desktop-privileges presage printer-driver-brlaser printer-driver-c2esp printer-driver-foo2zjs
  printer-driver-foo2zjs-common printer-driver-m2300w printer-driver-min12xxw printer-driver-pnm2ppa printer-driver-ptouch
  printer-driver-pxljr printer-driver-sag-gdi printer-driver-splix pulseaudio-module-bluetooth pwgen python3-apport
  python3-dbus.mainloop.pyqt5 python3-debian python3-problem-report python3-pyqt5 python3-requests-unixsocket python3-sip
  python3-software-properties python3-systemd python3-xapian python3-xkit qapt-deb-installer qdbus qml-module-org-kde-bluezqt
  qml-module-org-kde-kconfig qml-module-org-kde-kcoreaddons qml-module-org-kde-kio qml-module-org-kde-kirigami2
  qml-module-org-kde-kquickcontrols qml-module-org-kde-kquickcontrolsaddons qml-module-org-kde-newstuff qml-module-org-kde-qqc2desktopstyle
  qml-module-qtgraphicaleffects qml-module-qtqml-models2 qml-module-qtquick-controls qml-module-qtquick-controls2
  qml-module-qtquick-dialogs qml-module-qtquick-layouts qml-module-qtquick-privatewidgets qml-module-qtquick-templates2
  qml-module-qtquick-window2 qml-module-qtquick2 qpdfview qpdfview-djvu-plugin qpdfview-ps-plugin qpdfview-translations qrencode qtchooser
  qtcore4-l10n qtpass quassel quassel-data rfkill sbsigntool screengrab sddm sddm-theme-lubuntu secureboot-db skanlite
  software-properties-common software-properties-qt spice-vdagent syslinux syslinux-common syslinux-legacy transmission-common
  transmission-qt tree trojita trojita-data trojita-l10n ttf-ancient-fonts-symbola ttf-ubuntu-font-family ubuntu-drivers-common
  ubuntu-release-upgrader-qt unattended-upgrades usb-creator-common usb-creator-kde vcdimager vlc vlc-bin vlc-data vlc-l10n
  vlc-plugin-access-extra vlc-plugin-base vlc-plugin-notify vlc-plugin-qt vlc-plugin-samba vlc-plugin-skins2 vlc-plugin-svg
  vlc-plugin-video-output vlc-plugin-video-splitter vlc-plugin-visualization whoopsie wodim x11-apps x11-session-utils xbitmaps xclip
  xdg-desktop-portal xdg-desktop-portal-kde xfonts-base xfonts-encodings xfonts-scalable xfonts-utils xinit xinput xorg xserver-common
  xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-libinput xserver-xorg-input-wacom xserver-xorg-legacy
  xserver-xorg-video-all xserver-xorg-video-amdgpu xserver-xorg-video-ati xserver-xorg-video-fbdev xserver-xorg-video-intel
  xserver-xorg-video-nouveau xserver-xorg-video-qxl xserver-xorg-video-radeon xserver-xorg-video-vesa xserver-xorg-video-vmware zsync
0 upgraded, 0 newly installed, 449 to remove and 0 not upgraded.
After this operation, 1.233 MB disk space will be freed.
Do you want to continue? [Y/n] 
```

Unfortunately I pressed "Y" here. After that, my PC was dead. I'm at my wit's end and afraid to use this command again.

Ideas anyone?

Thank You.

---

### Post by VMC on 2020-04-30
Run *muon*, and click on history. Look back at what you did prior to this scenario.

---

### Post by GhX6GZMB on 2020-05-01
Thanks, but apparently the problem is too old for the Muon history.

I have a suspicion, though.
My PC is set up with US-English language, but German Locale. This combination does not exist in the UTF-8 list.
This would firstly explain why my machine is installed with a plethora of Indian, Tamil, Thai, Vietnamese etc. fonts and no Western ones.
Secondly, why deleting these fonts and installing Western fonts creates problems, even using sudo apt fc-cache.
There are conflicts galore here.

Any suggestions for a good font manager for Lubuntu, please? In the Muon listings I find nothing.

Thank You.

---


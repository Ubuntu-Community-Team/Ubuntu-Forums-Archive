---
title: "sudo apt autoremove made system not bootable"
date: 2021-04-03
forum: General Help
---

### Post by Brent_Santin on 2021-04-03
Hi,

I use my computer for music recording. I recently bought a new computer and installed Lubuntu 20.04 on it. As part of setting up the computer I install a low-latency core to improve timing for audio recording.
The command I use is:

[B]sudo apt-get install linux-lowlatency

[/B]No problem there. The installation of the new core worked well and I could reboot.  However, I did notice that the output of the installation process identified packages that are "no longer required" and recommended that they could be removed with "sudo apt autoremove".
I did execute this command and afterward found my computer would not boot any longer. 

The splash screen for Lubuntu would show up for about 20 seconds, then the screen would go black. This much was normal.
Normally, after about 15 seconds in the black screen, the mouse pointer would show up followed by the desktop a very short time later.

The problem now was that the black screen (no mouse pointer) would never go away and the desktop would never be reached.

I restored my system from a backup and installed the low-latency core again, but this time I did *not* execute the "sudo apt autoremove" and will not, as I am terrified it will make my system unbootable again.

I'm trying to understand what happened.

Here is a log of what the low latency core said was removable:
[B]
```

brent@tower-i5:~$  sudo apt-get install linux-lowlatency
[sudo] password for brent: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  2048-qt acpi-support acpid alsa-base apport
  apport-symptoms apt-config-icons-hidpi
  apt-config-icons-large apt-config-icons-large-hidpi
  aptdaemon arc-theme bluedevil bluez-cups bolt
  breeze-cursor-theme cdrdao cdrskin chafa compton
  compton-conf dc dvd+rw-tools fcitx fcitx-bin
  fcitx-config-common fcitx-config-gtk fcitx-data
  fcitx-frontend-all fcitx-frontend-gtk2 fcitx-frontend-gtk3
  fcitx-frontend-qt5 fcitx-module-dbus fcitx-module-kimpanel
  fcitx-module-lua fcitx-module-x11 fcitx-modules
  fcitx-ui-classic fcitx5-module-quickphrase-editor
  fonts-font-awesome fonts-kacst fonts-kacst-one
  fonts-khmeros-core fonts-lao fonts-lato
  fonts-lklug-sinhala fonts-noto-cjk fonts-sil-abyssinica
  fonts-sil-padauk fonts-symbola fonts-thai-tlwg
  fonts-tibetan-machine fonts-tlwg-garuda
  fonts-tlwg-garuda-ttf fonts-tlwg-kinnari
  fonts-tlwg-kinnari-ttf fonts-tlwg-laksaman
  fonts-tlwg-laksaman-ttf fonts-tlwg-loma
  fonts-tlwg-loma-ttf fonts-tlwg-mono fonts-tlwg-mono-ttf
  fonts-tlwg-norasi fonts-tlwg-norasi-ttf fonts-tlwg-purisa
  fonts-tlwg-purisa-ttf fonts-tlwg-sawasdee
  fonts-tlwg-sawasdee-ttf fonts-tlwg-typewriter
  fonts-tlwg-typewriter-ttf fonts-tlwg-typist
  fonts-tlwg-typist-ttf fonts-tlwg-typo fonts-tlwg-typo-ttf
  fonts-tlwg-umpush fonts-tlwg-umpush-ttf fonts-tlwg-waree
  fonts-tlwg-waree-ttf fwupd fwupd-signed gir1.2-soup-2.4
  gir1.2-udisks-2.0 glib-networking:i386
  gnome-accessibility-themes gnome-themes-extra
  gnome-themes-extra-data growisofs gstreamer1.0-x:i386
  gtk2-engines-murrine haveged htop inputattach
  javascript-common k3b k3b-data k3b-i18n kcalc
  kde-style-breeze kerneloops laptop-detect libaa1:i386
  libappstreamqt2 libavc1394-0:i386 libburn4 libcaca0:i386    
  libchafa0 libchromaprint-tools libconfig9 libcupsimage2     
  libdiscid0 libdv4:i386 libevent-2.1-7 libfcitx-config4      
  libfcitx-core0 libfcitx-gclient1 libfcitx-qt5-1             
  libfcitx-qt5-data libfcitx-utils0 libfwupd2
  libfwupdplugin1 libgcab-1.0-0 libgettextpo0
  libgstreamer-plugins-good1.0-0
  libgstreamer-plugins-good1.0-0:i386 libgudev-1.0-0:i386
  libgutenprint-common libgutenprint9 libhavege1
  libiec61883-0:i386 libiso9660-11 libjs-jquery
  libjs-modernizr libjs-sphinxdoc libjs-underscore libk3b7
  libk3b7-extracodecs libkf5cddb-data libkf5cddb5
  libkf5networkmanagerqt6 libkf5style5 libmarkdown2
  libmimetic0v5 libminiupnpc17 libminizip1
  libmusicbrainz5cc2v5 libnatpmp1 liboath0 libopusfile0
  libpackagekitqt5-1 libperl4-corelibs-perl
  libpipewire-0.2-1 libpresage-data libpresage1v5
  libproxy1v5:i386 libqapt3 libqapt3-runtime libqgpgme7
  libqrencode4 libqt5keychain1 libqt5script5
  libqt5webengine-data libqt5webenginecore5
  libqt5webenginewidgets5 libraw1394-11:i386 libre2-5
  libsamplerate0:i386 libsbc1 libshout3:i386 libslang2:i386
  libsmbios-c2 libsnapd-qt1 libsoup2.4-1:i386 libtag1v5:i386
  libtag1v5-vanilla:i386 libtinyxml2.6.2v5 libtss2-esys0
  libu2f-udev libvcdinfo0 libvncclient1 libwhoopsie0
  libxatracker2 libxfont2 libxmlb1 libxv1:i386 libxvmc1
  linux-sound-base lubuntu-default-settings
  lubuntu-update-notifier lxqt-admin lxqt-admin-l10n
  memtest86+ mscompress mtools muon neofetch nm-tray
  noblenote oathtool ofono pass pass-extension-otp
  pastebinit pavucontrol-qt-l10n pcmciautils plasma-discover
  plasma-discover-backend-fwupd plasma-discover-backend-snap
  plasma-discover-common policykit-desktop-privileges
  presage printer-driver-brlaser printer-driver-c2esp
  printer-driver-foo2zjs printer-driver-foo2zjs-common
  printer-driver-gutenprint printer-driver-m2300w
  printer-driver-min12xxw printer-driver-pnm2ppa
  printer-driver-ptouch printer-driver-pxljr
  printer-driver-sag-gdi printer-driver-splix pwgen
  python3-apport python3-aptdaemon python3-click
  python3-colorama python3-debconf python3-defer
  python3-feedparser python3-libdiscid
  python3-musicbrainzngs python3-mutagen
  python3-problem-report python3-pyqt5.qtmultimedia
  python3-requests-unixsocket python3-software-properties
  python3-systemd python3-xkit qapt-deb-installer
  qml-module-org-kde-kcoreaddons qml-module-org-kde-kio
  qml-module-org-kde-qqc2desktopstyle qrencode qtpass
  quassel quassel-data rfkill screengrab sddm
  sddm-theme-lubuntu software-properties-common
  software-properties-qt sphinx-rtd-theme-common
  spice-vdagent syslinux syslinux-common syslinux-legacy
  tpm-udev transmission-common transmission-qt tree trojita
  trojita-data trojita-l10n ttf-ancient-fonts-symbola
  ttf-ubuntu-font-family ubuntu-drivers-common
  ubuntu-release-upgrader-qt unattended-upgrades
  update-notifier-common usb-creator-common usb-creator-kde
  vcdimager vlc vlc-bin vlc-l10n vlc-plugin-access-extra
  vlc-plugin-notify vlc-plugin-qt vlc-plugin-samba
  vlc-plugin-skins2 vlc-plugin-svg vlc-plugin-video-splitter
  vlc-plugin-visualization whoopsie x11-apps
  x11-session-utils xbitmaps xclip xdg-desktop-portal
  xdg-desktop-portal-kde xfonts-base xfonts-efont-unicode
  xfonts-efont-unicode-ib xfonts-encodings xfonts-scalable
  xfonts-utils xinit xinput xorg xserver-common xserver-xorg
  xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-libinput xserver-xorg-input-wacom
  xserver-xorg-legacy xserver-xorg-video-all
  xserver-xorg-video-amdgpu xserver-xorg-video-ati
  xserver-xorg-video-fbdev xserver-xorg-video-intel
  xserver-xorg-video-nouveau xserver-xorg-video-qxl
  xserver-xorg-video-radeon xserver-xorg-video-vesa
  xserver-xorg-video-vmware zsync
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-headers-5.4.0-70 linux-headers-5.4.0-70-lowlatency
  linux-headers-lowlatency linux-image-5.4.0-70-lowlatency
  linux-image-lowlatency linux-modules-5.4.0-70-lowlatency
Suggested packages:
  fdutils linux-doc | linux-source-5.4.0 linux-tools
The following NEW packages will be installed:
  linux-headers-5.4.0-70 linux-headers-5.4.0-70-lowlatency
  linux-headers-lowlatency linux-image-5.4.0-70-lowlatency
  linux-image-lowlatency linux-lowlatency
  linux-modules-5.4.0-70-lowlatency
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 75.4 MB of archives.
After this operation, 377 MB of additional disk space will be used.
Do you want to continue? [Y/n]

```


[/B] The output of "sudo apt autoremove" showed more packages were to be removed:[B]

```

brent@tower-i5:~$ sudo apt autoremove
[sudo] password for brent: 
Sorry, try again.
[sudo] password for brent: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  2048-qt acpi-support acpid alsa-base apport
  apport-symptoms apt-config-icons-hidpi
  apt-config-icons-large apt-config-icons-large-hidpi
  aptdaemon arc-theme bluedevil bluez-cups bolt
  breeze-cursor-theme cdrdao cdrskin chafa compton
  compton-conf dc dvd+rw-tools fcitx fcitx-bin
  fcitx-config-common fcitx-config-gtk fcitx-data
  fcitx-frontend-all fcitx-frontend-gtk2 fcitx-frontend-gtk3
  fcitx-frontend-qt5 fcitx-module-dbus fcitx-module-kimpanel
  fcitx-module-lua fcitx-module-x11 fcitx-modules
  fcitx-ui-classic fcitx5-module-quickphrase-editor
  fonts-font-awesome fonts-kacst fonts-kacst-one
  fonts-khmeros-core fonts-lao fonts-lato
  fonts-lklug-sinhala fonts-noto-cjk fonts-sil-abyssinica
  fonts-sil-padauk fonts-symbola fonts-thai-tlwg
  fonts-tibetan-machine fonts-tlwg-garuda
  fonts-tlwg-garuda-ttf fonts-tlwg-kinnari
  fonts-tlwg-kinnari-ttf fonts-tlwg-laksaman
  fonts-tlwg-laksaman-ttf fonts-tlwg-loma
  fonts-tlwg-loma-ttf fonts-tlwg-mono fonts-tlwg-mono-ttf
  fonts-tlwg-norasi fonts-tlwg-norasi-ttf fonts-tlwg-purisa
  fonts-tlwg-purisa-ttf fonts-tlwg-sawasdee
  fonts-tlwg-sawasdee-ttf fonts-tlwg-typewriter
  fonts-tlwg-typewriter-ttf fonts-tlwg-typist
  fonts-tlwg-typist-ttf fonts-tlwg-typo fonts-tlwg-typo-ttf
  fonts-tlwg-umpush fonts-tlwg-umpush-ttf fonts-tlwg-waree
  fonts-tlwg-waree-ttf fwupd fwupd-signed gir1.2-soup-2.4
  gir1.2-udisks-2.0 glib-networking:i386
  gnome-accessibility-themes gnome-themes-extra
  gnome-themes-extra-data growisofs gstreamer1.0-x:i386
  gtk2-engines-murrine haveged htop inputattach
  javascript-common k3b k3b-data k3b-i18n kcalc
  kde-style-breeze kerneloops laptop-detect libaa1:i386       
  libappstreamqt2 libavc1394-0:i386 libburn4 libcaca0:i386    
  libchafa0 libchromaprint-tools libconfig9 libcupsimage2     
  libdiscid0 libdv4:i386 libevent-2.1-7 libfcitx-config4      
  libfcitx-core0 libfcitx-gclient1 libfcitx-qt5-1
  libfcitx-qt5-data libfcitx-utils0 libfwupd2
  libfwupdplugin1 libgcab-1.0-0 libgettextpo0
  libgstreamer-plugins-good1.0-0
  libgstreamer-plugins-good1.0-0:i386 libgudev-1.0-0:i386
  libgutenprint-common libgutenprint9 libhavege1
  libiec61883-0:i386 libiso9660-11 libjs-jquery
  libjs-modernizr libjs-sphinxdoc libjs-underscore libk3b7
  libk3b7-extracodecs libkf5cddb-data libkf5cddb5
  libkf5networkmanagerqt6 libkf5style5 libmarkdown2
  libmimetic0v5 libminiupnpc17 libminizip1
  libmusicbrainz5cc2v5 libnatpmp1 liboath0 libopusfile0
  libpackagekitqt5-1 libperl4-corelibs-perl
  libpipewire-0.2-1 libpresage-data libpresage1v5
  libproxy1v5:i386 libqapt3 libqapt3-runtime libqgpgme7
  libqrencode4 libqt5keychain1 libqt5script5
  libqt5webengine-data libqt5webenginecore5
  libqt5webenginewidgets5 libraw1394-11:i386 libre2-5
  libsamplerate0:i386 libsbc1 libshout3:i386 libslang2:i386
  libsmbios-c2 libsnapd-qt1 libsoup2.4-1:i386 libtag1v5:i386
  libtag1v5-vanilla:i386 libtinyxml2.6.2v5 libtss2-esys0
  libu2f-udev libvcdinfo0 libvncclient1 libwhoopsie0
  libxatracker2 libxfont2 libxmlb1 libxv1:i386 libxvmc1
  linux-sound-base lubuntu-default-settings
  lubuntu-update-notifier lxqt-admin lxqt-admin-l10n
  memtest86+ mscompress mtools muon neofetch nm-tray
  noblenote oathtool ofono pass pass-extension-otp
  pastebinit pavucontrol-qt-l10n pcmciautils plasma-discover
  plasma-discover-backend-fwupd plasma-discover-backend-snap
  plasma-discover-common policykit-desktop-privileges
  presage printer-driver-brlaser printer-driver-c2esp
  printer-driver-foo2zjs printer-driver-foo2zjs-common
  printer-driver-gutenprint printer-driver-m2300w
  printer-driver-min12xxw printer-driver-pnm2ppa
  printer-driver-ptouch printer-driver-pxljr
  printer-driver-sag-gdi printer-driver-splix pwgen
  python3-apport python3-aptdaemon python3-click
  python3-colorama python3-debconf python3-defer
  python3-feedparser python3-libdiscid
  python3-musicbrainzngs python3-mutagen
  python3-problem-report python3-pyqt5.qtmultimedia
  python3-requests-unixsocket python3-software-properties
  python3-systemd python3-xkit qapt-deb-installer
  qml-module-org-kde-kcoreaddons qml-module-org-kde-kio
  qml-module-org-kde-qqc2desktopstyle qrencode qtpass
  quassel quassel-data rfkill screengrab sddm
  sddm-theme-lubuntu software-properties-common
  software-properties-qt sphinx-rtd-theme-common
  spice-vdagent syslinux syslinux-common syslinux-legacy
  tpm-udev transmission-common transmission-qt tree trojita
  trojita-data trojita-l10n ttf-ancient-fonts-symbola
  ttf-ubuntu-font-family ubuntu-drivers-common
  ubuntu-release-upgrader-qt unattended-upgrades
  update-notifier-common usb-creator-common usb-creator-kde
  vcdimager vlc vlc-bin vlc-l10n vlc-plugin-access-extra
  vlc-plugin-notify vlc-plugin-qt vlc-plugin-samba
  vlc-plugin-skins2 vlc-plugin-svg vlc-plugin-video-splitter
  vlc-plugin-visualization whoopsie x11-apps
  x11-session-utils xbitmaps xclip xdg-desktop-portal
  xdg-desktop-portal-kde xfonts-base xfonts-efont-unicode
  xfonts-efont-unicode-ib xfonts-encodings xfonts-scalable
  xfonts-utils xinit xinput xorg xserver-common xserver-xorg
  xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-libinput xserver-xorg-input-wacom
  xserver-xorg-legacy xserver-xorg-video-all
  xserver-xorg-video-amdgpu xserver-xorg-video-ati
  xserver-xorg-video-fbdev xserver-xorg-video-intel
  xserver-xorg-video-nouveau xserver-xorg-video-qxl
  xserver-xorg-video-radeon xserver-xorg-video-vesa
  xserver-xorg-video-vmware zsync
0 upgraded, 0 newly installed, 318 to remove and 0 not upgraded.
After this operation, 582 MB disk space will be freed.
Do you want to continue? [Y/n] 
```

[/B] It seems like some very important packages (i.e. video driver, etc.) are being removed. What gives?[B]
I am a long-time Linux user, but a novice on the technical side, so please forgive my lack of knowledge.
Any help would be appreciated, as I think at some point I would like to remove unused packages...but SAFELY! Thanks.

Thanks.

[/B]

---

### Post by CatKiller on 2021-04-03
> **Brent_Santin said:**
> I did execute this command and afterward found my computer would not boot any longer.

From the list of packages, that was a bad plan, as you found.

Installing linux-lowlatency doesn't, by itself, cause the package conflicts that would remove those important packages; I've done it myself many times. I suspect that you've removed something else previously that's put your computer in this state.

---

### Post by deadflowr on 2021-04-03
The output suggests that at some point prior to the commands you had remove a vital piece of software somehow.
As the command removed the xserver packages it's understandable that no muse or anything shows up, since those rely on the xserver for graphics.
You might be able to fix it if you can switch consoles.
Try ctrl + alt + F2, or F3
and see if you get a prompt.
If a prompt shows login as your user.
And try installing the lubuntu-desktop package
Try
```
sudo apt update
sudo apt install lubuntu-desktop
or 
sudo apt install --reinstall lubuntu-desktop
```
If it installed, I'd just try a quick reboot.
(sudo reboot should work from that prompt.)

The only issue that might come up is networking as I have not parsed the removed package list enough to gather whether any important networking pieces were removed or not.
But it doesn't seem like there is.

---

### Post by Impavidus on 2021-04-03
For some reason, a lot of packages were erroneously marked as automatically installed instead of manually (many packages installed during initial installation of the OS are marked as manually installed), or some metapackages depending on a lot of useful software were removed. Is there any clue in /var/log/dpkg.log?

Have you considered Ubuntu Studio? It comes with software for audio processing and the low-latency kernel, so less stuff to do after the initial installation of the OS.

---

### Post by Brent_Santin on 2021-04-03
> **deadflowr said:**
> You might be able to fix it if you can switch consoles.
Try ctrl + alt + F2, or F3
and see if you get a prompt.
If a prompt shows login as your user.
And try installing the lubuntu-desktop package
Try
```
sudo apt update
sudo apt install lubuntu-desktop
or 
sudo apt install --reinstall lubuntu-desktop
```
If it installed, I'd just try a quick reboot.
(sudo reboot should work from that prompt.)

The only issue that might come up is networking as I have not parsed the removed package list enough to gather whether any important networking pieces were removed or not.
But it doesn't seem like there is.

Okay, I was successfully able to do carry out the instructions you suggested above, and rebooted the system. I am also on the internet (posting this) so I assume at least that part of networking still works.
What would you suggest as the next step?  Is there any way to check if this fixed the problem?

By the way. I ran "sudo apt update again" (BUT DID NOT CONFIRM THE ACTION) and the output was _much shorter_:

```

brent@tower-i5:~$ sudo apt autoremove
[sudo] password for brent: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  fonts-font-awesome fonts-lato gir1.2-soup-2.4
  glib-networking:i386 gstreamer1.0-x:i386 javascript-common
  libaa1:i386 libavc1394-0:i386 libcaca0:i386
  libchromaprint-tools libdiscid0 libdv4:i386
  libgstreamer-plugins-good1.0-0
  libgstreamer-plugins-good1.0-0:i386 libgudev-1.0-0:i386
  libiec61883-0:i386 libjs-jquery libjs-modernizr
  libjs-sphinxdoc libjs-underscore libopusfile0
  libproxy1v5:i386 libraw1394-11:i386 libsamplerate0:i386
  libshout3:i386 libslang2:i386 libsoup2.4-1:i386
  libtag1v5:i386 libtag1v5-vanilla:i386 libxv1:i386
  python3-feedparser python3-libdiscid
  python3-musicbrainzngs python3-mutagen
  python3-pyqt5.qtmultimedia sphinx-rtd-theme-common
0 upgraded, 0 newly installed, 36 to remove and 0 not upgraded.
After this operation, 26.7 MB disk space will be freed.
Do you want to continue? [Y/n] 

```

Thanks.

---

### Post by deadflowr on 2021-04-03
Your options are 

1) Ignore it and not run the autoremove command.
(But this might not last long as the list will grow longer over time.)

2) Painstakingly try removing each package listed one at a time and see if anything causes issues again.

3) Just throw caution to the wind and run the autoremove command and hope for the best.


I don't see anything that might be problematic in the output listed,
but that doesn't mean there isn't.

---

### Post by Brent_Santin on 2021-04-03
Okay. I will probably backup (disk image) then try sudo apt autoremove again.

I wonder if the problem was caused by me having to remove LibreOffice (the one that was included in the Lubuntu 20.04 installation) and reinstall. This is due to a known bug whereby printing to PDFs results in a blank page.
I followed the instructions [in this thread here (link).]("https://ask.libreoffice.org/en/question/264506/export-directly-to-pdf-only-produces-a-blank-page/")

> 
[B] Complete deinstall
[/B]
 dpkg --list | awk '/ii/&&/libreoffice/{print $2}' | sudo xargs apt --yes purge
sudo apt --yes autoremove
sudo rm -r /usr/lib/libreoffice/* [B]

Reinstall
[/B]
 sudo apt update --yes
sudo apt install libreoffice libreoffice-gtk3 libreoffice-sdbc-hsqldb libreoffice-help-en-us

I wonder if that stripped any important components then reinstalled them with the "manual" flag.

---

### Post by Brent_Santin on 2021-04-03
I'm happy to report, deadflowr, that your advice seems to be the solution. After carrying out your instructions in post #3 and doing a "sudo apt remove" with the shorter list that resulted, my system rebooted fine and my system now shows:

```

brent@tower-i5:~$ sudo apt autoremove
[sudo] password for brent: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
brent@tower-i5:~$ 

```

Which seems like it's a good thing to me? RIght?

The only "problem" with my system now is the buggy PDF export in LibreOffice (which is a noted problem in a french Lubuntu 20.04 install). The buggy version of Libreoffice was re-installed when I did the reinstall of Lubuntu desktop. I'm loathe to re-implement  the solution found online as I believe that might have caused the problem in the first place.

---

### Post by ajgreeny on 2021-04-03
Before I run the autoremove command I **always** run it using the ***-s*** option (simulate) so that I have plenty of time to read the list of packages that would be removed without the ***-s***.

I do this because there have been times when third party packages that I need to keep would have been removed during the autoremove action.

---

### Post by guiverc on 2021-04-03
Your issue with LibreOffice seems to be the issue listed in the Lubuntu 20.04 LTS release notes. Did you try what is suggested there?

[https://lubuntu.me/focal-2-released/](https://lubuntu.me/focal-2-released/)

> **LibreOffice Exporting Documents as a PDF**

 There is a [bug]("https://bugs.documentfoundation.org/show_bug.cgi?id=125234#c11")  where certain fonts do not render in exported PDF documents. As a  workaround, LibreOffice applications can be launched from the  command line with the following environment variable  SAL_VCL_QT5_USE_CAIRO=true. For example, to launch writer issue  SAL_VCL_QT5_USE_CAIRO=true libreoffice –writer.



---

### Post by Brent_Santin on 2021-04-03
Thank you so much guiverc for pointing me toward this workaround. That will certainly save me a lot of work and stress. Thank you, thank you, thank you (to all of you)!

---

### Post by turtles on 2021-04-05
autoremove seems badly broken.
For example it seems to want to remove the current running kernel if you've installed a new one, but have not booted to it yet.
However it never seems to really get the old kernels I am long past out of /boot
I am not sure if there is a file like the 'world' file in Gentoo where you can put package you never want to auto remove.

---


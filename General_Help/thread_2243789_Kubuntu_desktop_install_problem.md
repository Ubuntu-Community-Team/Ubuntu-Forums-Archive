---
title: "Kubuntu desktop install problem"
date: 2014-09-11
forum: General Help
---

### Post by xerox5555 on 2014-09-11
I tried:
```
$ sudo apt-get install kubuntu-desktop 
```
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kubuntu-desktop : Depends: ark but it is not going to be installed
                   Depends: audiocd-kio but it is not going to be installed
                   Depends: dolphin but it is not going to be installed
                   Depends: gstreamer0.10-qapt but it is not going to be installed
                   Depends: kde-window-manager but it is not going to be installed
                   Depends: kde-workspace but it is not going to be installed
                   Depends: kde-zeroconf but it is not going to be installed
                   Depends: kdepasswd but it is not going to be installed
                   Depends: khelpcenter4 but it is not going to be installed
                   Depends: klipper but it is not going to be installed
                   Depends: kmix but it is not going to be installed
                   Depends: konsole but it is not going to be installed
                   Depends: ksnapshot but it is not going to be installed
                   Depends: ksysguard but it is not going to be installed
                   Depends: lightdm-kde-greeter but it is not going to be installed
                   Depends: okular but it is not going to be installed
                   Depends: plasma-desktop but it is not going to be installed
                   Depends: plasma-netbook but it is not going to be installed
                   Depends: pm-utils but it is not going to be installed
                   Depends: software-properties-kde but it is not going to be installed
                   Depends: systemsettings but it is not going to be installed
                   Recommends: about-distro but it is not going to be installed
                   Recommends: akregator but it is not going to be installed
                   Recommends: amarok but it is not going to be installed
                   Recommends: apport-kde but it is not going to be installed
                   Recommends: apturl-kde but it is not going to be installed
                   Recommends: baloo but it is not going to be installed
                   Recommends: bluedevil but it is not going to be installed
                   Recommends: cdrdao but it is not going to be installed
                   Recommends: colord-kde but it is not going to be installed
                   Recommends: cryptsetup but it is not going to be installed
                   Recommends: dragonplayer but it is not going to be installed
                   Recommends: gnupg-agent
                   Recommends: gpgsm
                   Recommends: gstreamer1.0-pulseaudio but it is not going to be installed
                   Recommends: gwenview but it is not going to be installed
                   Recommends: ibus-qt4 but it is not going to be installed
                   Recommends: k3b but it is not going to be installed
                   Recommends: kaccessible but it is not going to be installed
                   Recommends: kaddressbook but it is not going to be installed
                   Recommends: kamera but it is not going to be installed
                   Recommends: kate but it is not going to be installed
                   Recommends: kcalc but it is not going to be installed
                   Recommends: kde-baseapps-bin but it is not going to be installed
                   Recommends: kde-config-gtk-style but it is not going to be installed
                   Recommends: kde-config-tablet but it is not going to be installed
                   Recommends: kde-config-whoopsie but it is not going to be installed
                   Recommends: kde-telepathy but it is not going to be installed
                   Recommends: kde-touchpad but it is not going to be installed
                   Recommends: kdegraphics-strigi-analyzer but it is not going to be installed
                   Recommends: kdenetwork-filesharing but it is not going to be installed
                   Recommends: partitionmanager but it is not going to be installed
                   Recommends: phonon-backend-gstreamer but it is not going to be installed
                   Recommends: pinentry-qt4 but it is not going to be installed
                   Recommends: plasma-nm but it is not going to be installed
                   Recommends: plasma-runner-telepathy-contact but it is not going to be installed
                   Recommends: plasma-widget-folderview but it is not going to be installed
                   Recommends: plasma-widget-kimpanel but it is not going to be installed
                   Recommends: plasma-widget-menubar but it is not going to be installed
                   Recommends: plasma-widgets-addons but it is not going to be installed
                   Recommends: plymouth-theme-kubuntu-logo but it is not going to be installed
                   Recommends: plymouth-theme-kubuntu-text but it is not going to be installed
                   Recommends: polkit-kde-1 but it is not going to be installed
                   Recommends: print-manager but it is not going to be installed
                   Recommends: pulseaudio-module-bluetooth but it is not going to be installed
                   Recommends: python-qt4-dbus but it is not going to be installed
                   Recommends: qapt-deb-installer but it is not going to be installed
                   Recommends: quassel but it is not going to be installed
                   Recommends: skanlite but it is not going to be installed
                   Recommends: ttf-oxygen-font-family but it is not going to be installed
                   Recommends: usb-creator-kde but it is not going to be installed
                   Recommends: user-manager but it is not going to be installed
 libasound2-plugins : Depends: libpulse0 (>= 1:0.99.1) but it is not going to be installed
 libespeak1 : Depends: libpulse0 (>= 1:0.99.1) but it is not going to be installed
 libestools2.1 : Depends: libpulse0 (>= 1:0.99.1) but it is not going to be installed
 libfreerdp-plugins-standard : Depends: libpulse0 (>= 1:0.99.1) but it is not going to be installed
 libmediastreamer-base3 : Depends: libpulse0 (>= 1:0.99.1) but it is not going to be installed
 libphonon4 : Depends: libpulse0 (>= 1:0.99.1) but it is not going to be installed
 libpulse-mainloop-glib0 : Depends: libpulse0 (>= 1:0.99.1) but it is not going to be installed
 libpulsedsp : Depends: libpulse0 (>= 1:0.99.1) but it is not going to be installed
 libqtmultimediakit1 : Depends: libpulse0 (>= 1:0.99.1) but it is not going to be installed
 libsdl1.2debian : Depends: libpulse0 (>= 1:0.99.1) but it is not going to be installed
 openjdk-7-jre : Depends: libpulse0 (>= 1:0.99.1) but it is not going to be installed
                 Recommends: libgconf2-4 but it is not going to be installed
                 Recommends: fonts-dejavu-extra but it is not going to be installed
 pulseaudio : Depends: libpulse0 (= 1:4.0-0ubuntu11) but it is not going to be installed
              Recommends: pulseaudio-module-x11 but it is not going to be installed
              Recommends: gstreamer0.10-pulseaudio but it is not going to be installed
              Recommends: pulseaudio-utils
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

After;
```
sudo apt-get -f install
```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  anthy-common fonts-lmodern libanthy0 libgfortran3 libmaa3 libserf-1-1
  libsvn1 lmodern tex-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libpulse0
The following NEW packages will be installed:
  libpulse0
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
231 not fully installed or removed.
Need to get 0 B/225 kB of archives.
After this operation, 871 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
(Reading database ... 200257 files and directories currently installed.)
Preparing to unpack .../libpulse0_1%3a4.0-0ubuntu11_amd64.deb ...
Unpacking libpulse0:amd64 (1:4.0-0ubuntu11) ...
dpkg: error processing archive /var/cache/apt/archives/libpulse0_1%3a4.0-0ubuntu11_amd64.deb (--unpack):
 trying to overwrite shared '/etc/pulse/client.conf', which is different from other instances of package libpulse0:amd64
Errors were encountered while processing:
 /var/cache/apt/archives/libpulse0_1%3a4.0-0ubuntu11_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

i cant install kubuntu-desktop. how am i fix this problem?

---


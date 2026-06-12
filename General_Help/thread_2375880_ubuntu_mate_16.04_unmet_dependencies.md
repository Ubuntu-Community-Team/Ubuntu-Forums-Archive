---
title: "ubuntu mate 16.04: unmet dependencies"
date: 2017-10-28
forum: General Help
---

### Post by erotavlas on 2017-10-28
Hi,
I have a problem that I cannot solve under ubuntu mate 16.04 64 bit.
I just executed a small script in order to install mega.nz tools:
```
#!/bin/bash

architecture=$(uname -m)
apt-get install megatools gdebi -y --force-yes --quiet
arch="i386"
if [[ $architecture = "x86_64" ]]; then
    arch="amd64"
fi
versionID="$(cat /etc/*-release | grep "DISTRIB_RELEASE=" | cut -d "=" -f2)"
megasync="megasync-xUbuntu_${versionID}_$arch.deb"
wget "https://mega.nz/linux/MEGAsync/xUbuntu_$versionID/$arch/$megasync"
gdebi "$megasync" -n
rm -rf "$megasync"
```

The script installed successfully gdebi, megatools and megasync and after that started to update a lot of packages.
Now, I get unmet dependencies and I cannot solved them.
I already tried with apt-get install -f without success. These are the first rows of the output:
```

sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies.
 account-plugin-facebook : Depends: libaccount-plugin-generic-oauth but it is not installed or
                                    ubuntu-system-settings-online-accounts but it is not installed
 account-plugin-flickr : Depends: libaccount-plugin-generic-oauth but it is not installed or
                                  ubuntu-system-settings-online-accounts but it is not installed
 account-plugin-google : Depends: libaccount-plugin-google but it is not installed or
                                  ubuntu-system-settings-online-accounts but it is not installed
 adduser : Depends: perl-base (>= 5.6.0) but it is not installed
           Depends: passwd (>= 1:4.1.5.1-1.1ubuntu6) but it is not installed
 adwaita-icon-theme : Depends: libgtk-3-bin but it is not installed
                      Depends: librsvg2-common but it is not installed
 alsa-base : Depends: kmod (>= 17-1) but it is not installed
             Depends: udev but it is not installed
             Recommends: alsa-utils but it is not installed
 apparmor:amd64 : Depends: python3:any
 apport : Depends: python3 but it is not installed
          Depends: python3-gi but it is not installed
          Depends: gir1.2-glib-2.0 (>= 1.29.17) but it is not installed
          Recommends: policykit-1 but it is not installed
          Recommends: python3-systemd but it is not installed
 apport-gtk : Depends: python3 but it is not installed
              Depends: gir1.2-gtk-3.0 (>= 3.1.90) but it is not installed
              Depends: gir1.2-wnck-3.0 but it is not installed
              Depends: python3-gi but it is not installed
              Depends: procps but it is not installed
              Depends: x-terminal-emulator
              Recommends: update-notifier
              Recommends: gdb but it is not installed or
                          gdb-minimal but it is not installable
 apt : Depends: gpgv but it is not installed or
                gpgv2 but it is not installed
       Depends: gnupg but it is not installed or
                gnupg2 but it is not installed
 aptdaemon : Depends: python3 but it is not installed
             Depends: python3:any (>= 3.2~)
             Depends: gir1.2-glib-2.0 but it is not installed
             Depends: python3-gi but it is not installed
             Depends: policykit-1 but it is not installed
             Recommends: lintian but it is not installed
 apturl:amd64 : Depends: python3:any (>= 3.3.2-2~)
                Depends: software-properties-gtk:amd64 but it is not installable
                Depends: python3-aptdaemon:amd64 but it is not installable
                Depends: python3-aptdaemon.gtk3widgets:amd64 but it is not installable
 apturl-common:amd64 : Depends: python3:any (>= 3.3.2-2~)
                       Depends: python3-update-manager:amd64 but it is not installable
 asciidoc : Depends: python (>= 2.4) but it is not installed
            Depends: python:any (>= 2.6.6-7~)
            Recommends: dblatex but it is not installed
            Recommends: docbook-utils but it is not installed
            Recommends: libxml2-utils but it is not installed
            Recommends: xmlto but it is not installed
 aspell-en : Depends: aspell (>= 0.60.3-2) but it is not installed
 aspell-it : Depends: aspell but it is not installed
 atril:amd64 : Depends: atril-common:amd64 (>= 1.12.2-1) but it is not installable
               Depends: mate-desktop-common:amd64 but it is not installable
 audacity:amd64 : Depends: audacity-data:amd64 (= 2.1.2-1) but it is not installable
 avahi-discover : Depends: python:any (< 2.8)
                  Depends: python:any (>= 2.7.5-5~)
                  Depends: python-avahi but it is not installed
                  Depends: python-dbus but it is not installed
                  Depends: python-gtk2 (>= 2.8.6-2) but it is not installed
                  Depends: python-glade2 but it is not installed
                  Depends: avahi-daemon but it is not installed
 bash-completion : PreDepends: dpkg (>= 1.15.7.2~) but it is not installed
                   Depends: bash (>= 3.2) but it is not installed
 bless : Depends: mono-runtime (>= 3.0~) but it is not installed
         Depends: libglade2.0-cil (>= 2.12.10-1ubuntu1) but it is not installed
         Depends: libglib2.0-cil (>= 2.12.10-1ubuntu1) but it is not installed
         Depends: libgtk2.0-cil (>= 2.12.10-1ubuntu1) but it is not installed
         Depends: rarian-compat but it is not installed or
                  scrollkeeper
 blueman:amd64 : Depends: gnome-icon-theme:amd64 but it is not installable
 borgbackup:amd64 : Depends: python3-pkg-resources:amd64 but it is not installable
 brasero:amd64 : Depends: brasero-common:amd64 (= 3.12.1-1ubuntu3~16.04) but it is not installable
 brasero-common : Depends: dconf-gsettings-backend but it is not installed or
                           gsettings-backend


```
Do you have any suggestions?
Thank you

---

### Post by erotavlas on 2017-10-28
I tried to remove the first package with sudo dpkg -r account-plugin-facebook account-plugin-flicker account-plugin-google.
The command sudo apt-get -f install gives at the end
```
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
```
and asks me to remove system packages.

```

sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies.
 adduser : Depends: perl-base (>= 5.6.0) but it is not installed
           Depends: passwd (>= 1:4.1.5.1-1.1ubuntu6) but it is not installed
 adwaita-icon-theme : Depends: libgtk-3-bin but it is not installed
                      Depends: librsvg2-common but it is not installed
 alsa-base : Depends: kmod (>= 17-1) but it is not installed
             Depends: udev but it is not installed
             Recommends: alsa-utils but it is not installed
 apparmor:amd64 : Depends: python3:any
 apport : Depends: python3 but it is not installed
          Depends: python3-gi but it is not installed
          Depends: gir1.2-glib-2.0 (>= 1.29.17) but it is not installed
          Recommends: policykit-1 but it is not installed
          Recommends: python3-systemd but it is not installed
 apport-gtk : Depends: python3 but it is not installed
              Depends: gir1.2-gtk-3.0 (>= 3.1.90) but it is not installed
              Depends: gir1.2-wnck-3.0 but it is not installed
              Depends: python3-gi but it is not installed
              Depends: procps but it is not installed
              Depends: x-terminal-emulator
              Recommends: update-notifier
              Recommends: gdb but it is not installed or
                          gdb-minimal but it is not installable
 apt : Depends: gpgv but it is not installed or
                gpgv2 but it is not installed
       Depends: gnupg but it is not installed or
                gnupg2 but it is not installed
 aptdaemon : Depends: python3 but it is not installed
             Depends: python3:any (>= 3.2~)
             Depends: gir1.2-glib-2.0 but it is not installed
             Depends: python3-gi but it is not installed
             Depends: policykit-1 but it is not installed
             Recommends: lintian but it is not installed
 apturl:amd64 : Depends: python3:any (>= 3.3.2-2~)
                Depends: software-properties-gtk:amd64 but it is not installable
                Depends: python3-aptdaemon:amd64 but it is not installable
                Depends: python3-aptdaemon.gtk3widgets:amd64 but it is not installable
 apturl-common:amd64 : Depends: python3:any (>= 3.3.2-2~)
                       Depends: python3-update-manager:amd64 but it is not installable
 asciidoc : Depends: python (>= 2.4) but it is not installed
            Depends: python:any (>= 2.6.6-7~)
            Recommends: dblatex but it is not installed
            Recommends: docbook-utils but it is not installed
            Recommends: libxml2-utils but it is not installed
            Recommends: xmlto but it is not installed
 aspell-en : Depends: aspell (>= 0.60.3-2) but it is not installed
 aspell-it : Depends: aspell but it is not installed
 atril:amd64 : Depends: atril-common:amd64 (>= 1.12.2-1) but it is not installable
               Depends: mate-desktop-common:amd64 but it is not installable
 audacity:amd64 : Depends: audacity-data:amd64 (= 2.1.2-1) but it is not installable
 avahi-discover : Depends: python:any (< 2.8)
                  Depends: python:any (>= 2.7.5-5~)
                  Depends: python-avahi but it is not installed
                  Depends: python-dbus but it is not installed
                  Depends: python-gtk2 (>= 2.8.6-2) but it is not installed
                  Depends: python-glade2 but it is not installed
                  Depends: avahi-daemon but it is not installed
 bash-completion : PreDepends: dpkg (>= 1.15.7.2~) but it is not installed
                   Depends: bash (>= 3.2) but it is not installed
 bless : Depends: mono-runtime (>= 3.0~) but it is not installed
         Depends: libglade2.0-cil (>= 2.12.10-1ubuntu1) but it is not installed
         Depends: libglib2.0-cil (>= 2.12.10-1ubuntu1) but it is not installed
         Depends: libgtk2.0-cil (>= 2.12.10-1ubuntu1) but it is not installed
         Depends: rarian-compat but it is not installed or
                  scrollkeeper
 blueman:amd64 : Depends: gnome-icon-theme:amd64 but it is not installable
 borgbackup:amd64 : Depends: python3-pkg-resources:amd64 but it is not installable
 brasero:amd64 : Depends: brasero-common:amd64 (= 3.12.1-1ubuntu3~16.04) but it is not installable
 brasero-common : Depends: dconf-gsettings-backend but it is not installed or
                           gsettings-backend
 ca-certificates : Depends: openssl (>= 1.0.0) but it is not installed
 ca-certificates-java : Depends: openjdk-7-jre-headless (>= 7~u3-2.1.1~pre1-1) but it is not installable or
                                 java7-runtime-headless
                        Depends: libnss3 (>= 3.12.9+ckbi-1.82-0ubuntu3~) but it is not installed
 ca-certificates-mono : Depends: mono-runtime (>= 2.10.1) but it is not installed
 caja-common : Depends: dconf-gsettings-backend but it is not installed or
                        gsettings-backend
 caja-gksu:amd64 : Depends: caja-extensions-common:amd64 (= 1.12.0-1) but it is not installable
 caja-open-terminal:amd64 : Depends: caja-extensions-common:amd64 (= 1.12.0-1) but it is not installable
 caja-sendto:amd64 : Depends: caja-extensions-common:amd64 (= 1.12.0-1) but it is not installable
 caja-wallpaper:amd64 : Depends: caja-extensions-common:amd64 (= 1.12.0-1) but it is not installable
 cheese:amd64 : Depends: gnome-video-effects:amd64 but it is not installable
                Recommends: nautilus-sendto:amd64 but it is not installable
 cheese-common : Depends: dconf-gsettings-backend but it is not installed or
                          gsettings-backend
 clamav-base : Depends: logrotate but it is not installed
               Recommends: clamav but it is not installed
 clamav-daemon:amd64 : Depends: clamav-base:amd64 (= 0.99.2+dfsg-0ubuntu0.16.04.2) but it is not installable
 clamav-freshclam:amd64 : Depends: clamav-base:amd64 (>= 0.99.2+dfsg-0ubuntu0.16.04.2) but it is not installable
 clamdscan:amd64 : Depends: clamav-base:amd64 (= 0.99.2+dfsg-0ubuntu0.16.04.2) but it is not installable
 clamtk : Depends: perl but it is not installed
          Depends: clamav (>= 0.95) but it is not installed
          Depends: clamav-freshclam (>= 0.95) but it is not installed or
                   clamav-data
          Depends: libgtk2-perl (>= 2:1.241) but it is not installed
          Depends: liblocale-gettext-perl but it is not installed
          Depends: cron or
                   cron-daemon
 cli-common : Depends: perl but it is not installed
 cmake:amd64 : Depends: cmake-data:amd64 (= 3.5.1-1ubuntu3) but it is not installable
 colord:amd64 : Depends: colord-data:amd64 but it is not installable
 compiz : Depends: compiz-core (>= 1:0.9.12.2+16.04.20160823-0ubuntu1) but it is not installed
          Depends: compiz-plugins-default (>= 1:0.9.12.2+16.04.20160823-0ubuntu1) but it is not installed
          Depends: compiz-gnome but it is not installed
 compiz-gnome:amd64 : Depends: gnome-settings-daemon-schemas:amd64 (>= 3.4.2-0ubuntu9) but it is not installable
 console-setup-linux : Depends: kbd (>= 1.15-1ubuntu3) but it is not installed
 debconf : PreDepends: perl-base (>= 5.6.1-4) but it is not installed
           Recommends: apt-utils (>= 0.5.1) but it is not installed
 debconf-i18n : Depends: liblocale-gettext-perl but it is not installed
                Depends: libtext-iconv-perl but it is not installed
                Depends: libtext-charwidth-perl but it is not installed
 deja-dup-backend-cloudfiles : Depends: deja-dup but it is not installed
                               Depends: duplicity but it is not installed
 deja-dup-backend-gvfs : Depends: deja-dup but it is not installed
                         Depends: duplicity but it is not installed
                         Depends: gvfs-backends but it is not installed
                         Depends: python-gi but it is not installed
 deja-dup-backend-s3 : Depends: deja-dup but it is not installed
                       Depends: duplicity but it is not installed
 deja-dup-caja : Depends: python-caja but it is not installed
                 Depends: gir1.2-caja but it is not installed
                 Depends: caja but it is not installed
                 Depends: gir1.2-gtk-2.0 but it is not installed
                 Depends: deja-dup but it is not installed
 dh-python : Depends: python3:any (>= 3.3.2-2~)
 dictionaries-common : Depends: libtext-iconv-perl but it is not installed
 dkms : Depends: kmod but it is not installed or
                 kldutils but it is not installable
        Depends: gcc but it is not installed
        Depends: coreutils (>= 7.4) but it is not installed
        Depends: patch but it is not installed
        Recommends: fakeroot
        Recommends: menu but it is not installed or
                    sudo
 dpkg-dev : Depends: bzip2 but it is not installed
            Depends: xz-utils but it is not installed
            Depends: patch (>= 2.7) but it is not installed
            Depends: make
            Depends: binutils but it is not installed
            Depends: base-files (>= 5.0.0) but it is not installed
            Recommends: gcc but it is not installed or
                        c-compiler
            Recommends: build-essential but it is not installed
            Recommends: fakeroot
            Recommends: gnupg but it is not installed or
                        gnupg2 but it is not installed
            Recommends: gpgv but it is not installed or
                        gpgv2 but it is not installed
            Recommends: libalgorithm-merge-perl but it is not installed
 duplicity:amd64 : Depends: python-lockfile:amd64 (> 1:0.9) but it is not installable
 engrampa:amd64 : Depends: engrampa-common:amd64 (= 1.12.0-2) but it is not installable
                  Recommends: mate-icon-theme:amd64 but it is not installable
 engrampa-common : Depends: dconf-gsettings-backend but it is not installed or
                            gsettings-backend
 enigmail : Depends: gnupg-agent but it is not installed
            Depends: gnupg (>= 2) but it is not installed or
                     gnupg2 but it is not installed
            Depends: thunderbird (>= 38.0) but it is not installed or
                     seamonkey (>= 2.35) but it is not installable
            Recommends: pinentry-x11
 eom:amd64 : Depends: eom-common:amd64 (= 1.12.2-2) but it is not installable
             Depends: mate-desktop-common:amd64 but it is not installable
 evolution-data-server-common : Depends: dconf-gsettings-backend but it is not installed or
                                         gsettings-backend
 filezilla:amd64 : Depends: filezilla-common:amd64 (= 3.15.0.2-1ubuntu1) but it is not installable
 flashplugin-installer:amd64 : Depends: update-notifier-common:amd64 (>= 0.119ubuntu2) but it is not installable
 folder-color-caja : Depends: python-caja but it is not installed
                     Depends: gir1.2-caja but it is not installed
                     Depends: caja but it is not installed
                     Depends: gir1.2-gtk-2.0 but it is not installed
                     Depends: python:any (< 2.8)
                     Depends: python:any (>= 2.7~)
 folder-color-common : Depends: gvfs-bin but it is not installed
                       Depends: libgtk2.0-bin but it is not installed
                       Depends: python:any (< 2.8)
                       Depends: python:any (>= 2.7~)
 fonts-horai-umefont : PreDepends: dpkg (>= 1.15.6~) but it is not installed
 fonts-kacst : PreDepends: dpkg (>= 1.15.6~) but it is not installed
 fonts-kacst-one : PreDepends: dpkg (>= 1.15.6~) but it is not installed
 fonts-lato : PreDepends: dpkg (>= 1.15.6~) but it is not installed
 fonts-nanum : PreDepends: dpkg (>= 1.15.7.2) but it is not installed
 fonts-sil-abyssinica : PreDepends: dpkg (>= 1.15.6~) but it is not installed
 fonts-takao-pgothic : PreDepends: dpkg (>= 1.15.6~) but it is not installed
 fonts-unfonts-core : PreDepends: dpkg (>= 1.15.7.2) but it is not installed
 foomatic-db-compressed-ppds : Depends: python3 but it is not installed
                               Depends: xz-utils but it is not installed
                               Recommends: cups-filters (>= 1.0.42) but it is not installed or
                                           foomatic-filters (>= 4.0)
                               Recommends: ghostscript but it is not installed
                               Recommends: cups but it is not installed
                               Recommends: cups-client but it is not installed
 friendly-recovery : Depends: upstart but it is not installed or
                              systemd-sysv but it is not installed
                     Depends: whiptail but it is not installed
                     Recommends: gettext-base but it is not installed
 gconf2:amd64 : Depends: python3:any
 gdebi : Depends: python3:any (>= 3.3.2-2~)
         Depends: gir1.2-gtk-3.0 but it is not installed
         Depends: gir1.2-vte-2.91 but it is not installed
         Depends: python3-gi but it is not installed
         Depends: gksu but it is not installed
         Recommends: libgtk2-perl but it is not installed
         Recommends: shared-mime-info but it is not installed
         Recommends: lintian but it is not installed
 gdebi-core : Depends: python3:any (>= 3.3.2-2~)
              Depends: python3-apt but it is not installed
              Depends: file but it is not installed
 gedit:amd64 : Depends: python3:any (>= 3.3.2-2~)
               Depends: gedit-common:amd64 (>= 3.18) but it is not installable
               Depends: gedit-common:amd64 (< 3.19) but it is not installable
 gedit-common : Depends: dconf-gsettings-backend but it is not installed or
                         gsettings-backend
                Recommends: gedit but it is not installed
 ghostscript:amd64 : Depends: gsfonts:amd64 (>= 6.0-1) but it is not installable
 gimp:amd64 : Depends: gimp-data:amd64 (>= 2.8.16) but it is not installable
              Depends: gimp-data:amd64 (<= 2.8.16-z) but it is not installable
              Depends: python:any (>= 2.6.6-7~)
 gimp-help-it : Depends: gimp-helpbrowser but it is not installable or
                         www-browser
 git:amd64 : Depends: liberror-perl:amd64 but it is not installable
 gnome-icon-theme : Depends: libgtk-3-bin but it is not installed
                    Depends: librsvg2-common but it is not installed
 gnome-orca : Depends: dconf-gsettings-backend but it is not installed or
                       gsettings-backend
              Depends: python3:any (>= 3.3.2-2~)
              Depends: gir1.2-glib-2.0 but it is not installed
              Depends: gir1.2-gtk-3.0 (>= 3.6.2) but it is not installed
              Depends: gir1.2-pango-1.0 but it is not installed
              Depends: gir1.2-wnck-3.0 but it is not installed
              Depends: python3-brlapi (>= 0.5.1) but it is not installed
              Depends: python3-cairo but it is not installed
              Depends: python3-gi (>= 3.10) but it is not installed
              Depends: speech-dispatcher (>= 0.8) but it is not installed
              Recommends: xbrlapi but it is not installed
              Recommends: libgail-common but it is not installed
 gnome-settings-daemon-schemas : Depends: dconf-gsettings-backend but it is not installed or
                                          gsettings-backend
 gnome-video-effects : Depends: gstreamer1.0-plugins-good but it is not installed
 gnuplot-x11:amd64 : Depends: gnuplot-data:amd64 (= 4.6.6-3) but it is not installable
 gobject-introspection:amd64 : Depends: python:any
                               Depends: python-mako:amd64 but it is not installable
 grub2-themes-ubuntu-mate : Depends: grub-common (>= 2) but it is not installed
 gsettings-desktop-schemas : Depends: dconf-gsettings-backend but it is not installed or
                                      gsettings-backend
 gsettings-ubuntu-schemas : Depends: dconf-gsettings-backend but it is not installed or
                                     gsettings-backend
 gufw : Depends: python:any (>= 2.6.6-7~)
        Depends: gir1.2-gtk-3.0 but it is not installed
        Depends: policykit-1 but it is not installed
        Depends: python-netifaces but it is not installed
        Depends: gir1.2-webkit-3.0 but it is not installed
        Depends: python-gi but it is not installed
 gvfs-common : Depends: desktop-file-utils but it is not installed
               Recommends: gvfs but it is not installed
 hexchat:amd64 : Depends: hexchat-common:amd64 (= 2.10.2-1ubuntu3) but it is not installable
                 Recommends: hexchat-plugins:amd64 but it is not installable
                 Recommends: hexchat-perl:amd64 but it is not installable
                 Recommends: hexchat-python:amd64 but it is not installable
 hplip:amd64 : Depends: hplip-data:amd64 (= 3.16.3+repack0-1) but it is not installable
               Depends: python3-pexpect:amd64 but it is not installable
               Depends: python3-reportlab:amd64 but it is not installable
               Recommends: printer-driver-postscript-hp:amd64 but it is not installable
 hplip-data : Depends: xz-utils but it is not installed
              Depends: python3:any (>= 3.3.2-2~)
 hwdata : Depends: usbutils but it is not installed
          Depends: pciutils but it is not installed
 icoutils:amd64 : Depends: libwww-perl:amd64 but it is not installable
 im-config : Depends: gettext-base but it is not installed
             Depends: zenity but it is not installed or
                      kde-baseapps-bin but it is not installed or
                      whiptail but it is not installed
             Recommends: whiptail but it is not installed
 imagemagick-common : PreDepends: dpkg (>= 1.15.7.2) but it is not installed
 init-system-helpers : Depends: perl-base (>= 5.20.1-3) but it is not installed
 initramfs-tools-core : Depends: initramfs-tools-bin (= 0.122ubuntu8.9) but it is not installed
                        Depends: busybox-initramfs (>= 1:1.13.3-1ubuntu5) but it is not installed
                        Depends: klibc-utils (>= 2.0.4-7~) but it is not installed
                        Depends: cpio but it is not installed
                        Depends: kmod but it is not installed or
                                 module-init-tools but it is not installed
                        Depends: udev but it is not installed
 inkscape:amd64 : Depends: python:any (>= 2.7.5-5~)
                  Recommends: libimage-magick-perl:amd64 but it is not installable
 inxi : Depends: bash (>= 3.0) but it is not installed
        Depends: gawk but it is not installed
        Depends: pciutils but it is not installed
        Depends: procps but it is not installed
        Recommends: dmidecode but it is not installed
        Recommends: file but it is not installed
        Recommends: hddtemp but it is not installed
        Recommends: iproute2 but it is not installed
        Recommends: lm-sensors but it is not installed
        Recommends: mesa-utils but it is not installed
        Recommends: kmod but it is not installed
        Recommends: net-tools but it is not installed
        Recommends: sudo
        Recommends: usbutils but it is not installed
        Recommends: x11-utils but it is not installed
        Recommends: x11-xserver-utils but it is not installed
 iproute : Depends: iproute2 but it is not installed
 java-wrappers : Depends: unzip but it is not installed
 katepart:amd64 : Depends: kate-data:amd64 (>= 4:4.14.3-0ubuntu4) but it is not installable
 kbd:amd64 : Depends: console-setup:amd64 but it is not installable or
                      console-setup-mini:amd64 but it is not installable
 kde-runtime:amd64 : Depends: kde-runtime-data:amd64 (>= 4:15.12.3-0ubuntu1) but it is not installable
                     Depends: oxygen-icon-theme:amd64 (>= 4:4.6) but it is not installable
 kde-runtime-data : Depends: perl but it is not installed
 kdelibs5-data : Depends: perl but it is not installed
 kdelibs5-plugins:amd64 : Depends: kdelibs5-data:amd64 (= 4:4.14.16-0ubuntu3.2) but it is not installable
 keyboard-configuration : Depends: liblocale-gettext-perl but it is not installed
                          Depends: initscripts but it is not installed
 language-pack-en : PreDepends: dpkg (>= 1.16.1) but it is not installed
 language-pack-en-base : PreDepends: dpkg (>= 1.16.1) but it is not installed
 language-pack-gnome-en : PreDepends: dpkg (>= 1.16.1) but it is not installed
 language-pack-gnome-en-base : PreDepends: dpkg (>= 1.16.1) but it is not installed
 language-pack-gnome-it : PreDepends: dpkg (>= 1.16.1) but it is not installed
 language-pack-gnome-it-base : PreDepends: dpkg (>= 1.16.1) but it is not installed
 language-pack-it : PreDepends: dpkg (>= 1.16.1) but it is not installed
 language-pack-it-base : PreDepends: dpkg (>= 1.16.1) but it is not installed
 language-selector-common : PreDepends: dpkg (>= 1.15.7.2) but it is not installed
                            Depends: python3:any (>= 3.3.2-2~)
                            Depends: python3-apt (>= 0.7.12.0) but it is not installed
                            Depends: python3-dbus but it is not installed
                            Depends: dbus but it is not installed
                            Depends: accountsservice (>= 0.6.29-1ubuntu6) but it is not installed
 language-selector-gnome : Depends: python3:any (>= 3.3.2-2~)
                           Depends: python3-gi but it is not installed
                           Depends: gir1.2-gtk-3.0 but it is not installed
                           Depends: python3-apt but it is not installed
                           Recommends: yelp but it is not installed
 liba11y-profile-manager-data : Depends: dconf-gsettings-backend but it is not installed or
                                         gsettings-backend
 libatrildocument3:amd64 : Depends: libjs-mathjax:amd64 but it is not installable
 libaudio2 : PreDepends: multiarch-support but it is not installed
 libbluray-bdj : Depends: libbluray1 (>= 1:0.9.2-2) but it is not installed
                 Depends: libbluray1 (< 1:0.9.2-2.1~) but it is not installed
                 Depends: default-jre-headless but it is not installed or
                          java2-runtime-headless
 libbrasero-media3-1:amd64 : Depends: brasero-common:amd64 (= 3.12.1-1ubuntu3~16.04) but it is not installable
 libcapi20-3 : PreDepends: multiarch-support but it is not installed
 libdpkg-perl : Depends: dpkg (>= 1.16.3) but it is not installed
                Depends: perl but it is not installed
                Recommends: libfile-fcntllock-perl but it is not installed
                Recommends: bzip2 but it is not installed
                Recommends: xz-utils but it is not installed

E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

Do I have to reinstall the OS?

---

### Post by erotavlas on 2017-10-28
Hi,
I investigated further by installing a virtual machine with the same os and by repeating the same steps.
In the first post I forgot to say that the script that I run was this with a comment on architecture variable (first row) and this is the source of the problem:
```

#!/bin/bash

#architecture=$(uname -m)
apt-get install megatools gdebi -y --force-yes --quiet
arch="i386"if [[ $architecture = "x86_64" ]]; then
    arch="amd64"
fi
versionID="$(cat /etc/*-release | grep "DISTRIB_RELEASE=" | cut -d "=" -f2)"
megasync="megasync-xUbuntu_${versionID}_$arch.deb"
wget "https://mega.nz/linux/MEGAsync/xUbuntu_$versionID/$arch/$megasync"
gdebi "$megasync" -n
rm -rf "$megasync"
```
The same script without the comment works well and I used it many times.

The updater started to update a lot of packages as I think it installed i386 version instead of amd64 version. What can I do to restore it?

P.S. I added error messages 
[https://mega.nz/#F!WA0HiRJY!YV5DpQsYm2le8CsUsQ-6Aw](https://mega.nz/#F!WA0HiRJY!YV5DpQsYm2le8CsUsQ-6Aw)

---

### Post by erotavlas on 2017-10-30
Hi,
I have a problem started with a small script that a due to commented line ```
#architecture=$(uname -m)
``` started to install and I think to replace amd64 packages with i386 packages.
```
#!/bin/bash

architecture=$(uname -m)
apt-get install megatools gdebi -y --force-yes --quiet
arch="i386"
if [[ $architecture = "x86_64" ]]; then
    arch="amd64"
fi
versionID="$(cat /etc/*-release | grep "DISTRIB_RELEASE=" | cut -d "=" -f2)"
megasync="megasync-xUbuntu_${versionID}_$arch.deb"
wget "https://mega.nz/linux/MEGAsync/xUbuntu_$versionID/$arch/$megasync"
gdebi "$megasync" -n
rm -rf "$megasync"
```

Now, I have many unmet dependencies that I'm not able to solve via ```
apt-get install -f
``` since I get:
```
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages. 
E: Unable to correct dependencies

```
I'm sorry for [double posting]("https://ubuntuforums.org/showthread.php?t=2375880") in different section of this forum, maybe here you have a better knowledge. I work with my PC and if I could not find a solution in one two more days, I have to reinstall the OS as last unique option.
Thank you in advance.

---

### Post by ajgreeny on 2017-10-30
Threads merged.

**Please do not create duplicate posts;** it is confusing for all including you and dilutes the forum's ability to help. 
If you wish a post or thread to be moved to another forum section please use the **Report Post** button, bottom left of every post and staff will decide if it is appropriate to move it.

---

### Post by slickymaster on 2017-10-30
Thread moved from Programming Talk to **General Help** for a better fit

---

### Post by ian-weisser on 2017-10-30
Here's one way to fix it.

1) Review the logs of what was installed: /var/log/apt/
2) Build a list of every package that megasync installed.
3) Uninstall every last one of those packages.
4) Run an apt update and apt upgrade to confirm that the problem is fixed.

---

### Post by erotavlas on 2017-10-31
> **ian-weisser said:**
> Here's one way to fix it.

1) Review the logs of what was installed: /var/log/apt/
2) Build a list of every package that megasync installed.
3) Uninstall every last one of those packages.
4) Run an apt update and apt upgrade to confirm that the problem is fixed.

Thank you very much, you solved my problem. You are great, can I offer you a beer or a fruit juice? :popcorn:
For the future, I report the steps that I did.
1) I remove all packages via dpkg -i all_package_name
2) I removed all the file from /etc/apt/sources.list.d/ folder
3) apt-get update && apt-get upgrade
4) I added again the repositories

```

Start-Date: 2017-10-28  10:56:37
Commandline: apt-get install megatools
Requested-By: user (1000)
Install: megatools:amd64 (1.9.97-1)
End-Date: 2017-10-28  10:56:39

Start-Date: 2017-10-28  11:11:32
Requested-By: tore (1000)
Install: libc-ares2:i386 (1.10.0-3ubuntu0.2, automatic), libkrb5-3:i386 (1.13.2+dfsg-5ubuntu2, automatic), libgssapi-krb5-2:i386 (1.13.2+dfsg-5ubuntu2, automatic), libqt4-xmlpatterns:i386 (4:4.8.7+dfsg-5ubuntu2, automatic), libcups2:i386 (2.1.3-4ubuntu0.3, automatic), qt-at-spi:i386 (0.4.0-3, automatic), libqt4-declarative:i386 (4:4.8.7+dfsg-5ubuntu2, automatic), apt:i386 (1.2.24, automatic), libbz2-1.0:i386 (1.0.6-8, automatic), libavahi-common-data:i386 (0.6.32~rc+dfsg-1ubuntu2, automatic), libavahi-common3:i386 (0.6.32~rc+dfsg-1ubuntu2, automatic), libqtcore4:i386 (4:4.8.7+dfsg-5ubuntu2, automatic), libk5crypto3:i386 (1.13.2+dfsg-5ubuntu2, automatic), libapt-pkg5.0:i386 (1.2.24, automatic), libqtgui4:i386 (4:4.8.7+dfsg-5ubuntu2, automatic), libqt4-script:i386 (4:4.8.7+dfsg-5ubuntu2, automatic), librtmp1:i386 (2.4+20151223.gitfa8646d-1ubuntu0.1, automatic), libxi6:i386 (2:1.7.6-1, automatic), libkrb5support0:i386 (1.13.2+dfsg-5ubuntu2, automatic), libxt6:i386 (1:1.1.5-0ubuntu1, automatic), libkeyutils1:i386 (1.5.9-8ubuntu1, automatic), libqtdbus4:i386 (4:4.8.7+dfsg-5ubuntu2, automatic), liblz4-1:i386 (0.0~r131-2ubuntu2, automatic), mysql-common:amd64 (5.7.20-0ubuntu0.16.04.1, automatic), libqt4-sql:i386 (4:4.8.7+dfsg-5ubuntu2, automatic), libmysqlclient20:i386 (5.7.20-0ubuntu0.16.04.1, automatic), libqt4-xml:i386 (4:4.8.7+dfsg-5ubuntu2, automatic), libcrypto++9v5:i386 (5.6.1-9, automatic), apt-transport-https:i386 (1.2.24, automatic), libqt4-dbus:i386 (4:4.8.7+dfsg-5ubuntu2, automatic), libavahi-client3:i386 (0.6.32~rc+dfsg-1ubuntu2, automatic), libqt4-sql-mysql:i386 (4:4.8.7+dfsg-5ubuntu2, automatic), libglib2.0-0:i386 (2.48.2-0ubuntu1, automatic), libaudio2:i386 (1.9.4-4, automatic), libcurl3-gnutls:i386 (7.47.0-1ubuntu2.4, automatic), libmng2:i386 (2.0.2-0ubuntu3, automatic), libssl1.0.0:i386 (1.0.2g-1ubuntu4.8, automatic), libqt4-network:i386 (4:4.8.7+dfsg-5ubuntu2, automatic)
Remove: apt:amd64 (1.2.24), megasync:amd64 (3.1.4-1.1), ubuntu-mate-core:amd64 (1.154.1), ubuntu-minimal:amd64 (1.361), apt-utils:amd64 (1.2.24), unattended-upgrades:amd64 (0.90ubuntu0.8), libcrypto++9v5:amd64 (5.6.1-9), apt-transport-https:amd64 (1.2.24)
End-Date: 2017-10-28  11:11:48
```

That's all :)

---


---
title: "Won't boot after 10.04 -&gt; 12.04 upgrade, udev/package problem"
date: 2013-12-05
forum: General Help
---

### Post by viktorw on 2013-12-05
Hi!
I took the leap of faith and upgraded my ubuntu server from 10.04 to 12.04.
After the upgrade there where some "broken/couldn't be upgraded" packages.
Meh, fine, I'll fix them later, I thought. 

But after restart the server would not boot.
Problems with udev it said. Could not mount anything, really.

Well, I went into rescue mode and manage to mount my drive properly, I think, I could access all my files, so far so good. :)

Next, maybe I can restore/upgrade udev in some way ?
So I tried some apt-get commands and soon realized that udev was not the only package broken.

apt-get install -f produced this little list:
> Läser paketlistor...Bygger beroendeträd...
Läser tillståndsinformation...
Korrigerar beroenden.... misslyckades.
Följande paket har beroenden som inte kan tillfredsställas:
  consolekit: Beroende av: libdbus-glib-1-2 (>= 0.88) men 0.84-1 är installerat
              Beroende av: libglib2.0-0 (>= 2.31.2) men 2.24.1-0ubuntu1 är installerat
  dmsetup: Beroende av: libdevmapper1.02.1 (>= 2:1.02.47) men 2:1.02.39-1ubuntu4 är installerat
  fuse-utils: Beroende av: fuse men det är inte installerat
  gnome-power-manager: Beroende av: libglib2.0-0 (>= 2.31.18) men 2.24.1-0ubuntu1 är installerat
                       Beroende av: libgtk-3-0 (>= 3.3.8) men det är inte installerat
                       Beroende av: dconf-gsettings-backend men det är inte installerat eller
                                    gsettings-backend
  gnome-session: Beroende av: gnome-session-common (= 3.2.1-0ubuntu8) men det är inte installerat
                 Rekommenderar: unity men det är inte installerat eller
                                unity-2d men det är inte installerat eller
                                gnome-shell (>= 3.0) men det är inte installerat
  gnome-session-bin: Beroende av: gconf-service men det är inte installerat
                     Beroende av: libdbus-glib-1-2 (>= 0.88) men 0.84-1 är installerat
                     Beroende av: libgconf-2-4 (>= 2.31.1) men det är inte installerat
                     Beroende av: libgdk-pixbuf2.0-0 (>= 2.22.0) men det är inte installerat
                     Beroende av: libglib2.0-0 (>= 2.31.8) men 2.24.1-0ubuntu1 är installerat
                     Beroende av: libgtk-3-0 (>= 3.0.0) men det är inte installerat
                     Beroende av: libjson-glib-1.0-0 (>= 0.12.0) men 0.7.6-0ubuntu2 är installerat
                     Beroende av: dconf-gsettings-backend men det är inte installerat eller
                                  gsettings-backend
                     Beroende av: gsettings-desktop-schemas men det är inte installerat
  gnome-settings-daemon: Beroende av: gconf-service men det är inte installerat
                         Beroende av: libappindicator3-1 (>= 0.4.90) men det är inte installerat
                         Beroende av: libcairo2 (>= 1.10.0) men 1.8.10-2ubuntu1 är installerat
                         Beroende av: libcanberra-gtk3-0 (>= 0.25) men det är inte installerat
                         Beroende av: libcolord1 (>= 0.1.12) men det är inte installerat
                         Beroende av: libdbus-glib-1-2 (>= 0.88) men 0.84-1 är installerat
                         Beroende av: libgconf-2-4 (>= 2.31.1) men det är inte installerat
                         Beroende av: libgdk-pixbuf2.0-0 (>= 2.22.0) men det är inte installerat
                         Beroende av: libglib2.0-0 (>= 2.31.8) men 2.24.1-0ubuntu1 är installerat
                         Beroende av: libgnome-desktop-3-2 (>= 3.3.4) men det är inte installerat
                         Beroende av: libgnomekbd7 (>= 2.91.90) men det är inte installerat
                         Beroende av: libgtk-3-0 (>= 3.3.4) men det är inte installerat
                         Beroende av: liblcms2-2 (>= 2.2+git20110628-2) men det är inte installerat
                         Beroende av: libnotify4 (>= 0.7.3) men det är inte installerat
                         Beroende av: libnspr4 (>= 1.8.0.10) men det är inte installerat
                         Beroende av: libnss3 (>= 3.12.0~1.9b1) men det är inte installerat
                         Beroende av: libpolkit-gobject-1-0 (>= 0.99) men 0.96-2ubuntu0.1 är installerat
                         Beroende av: libpulse-mainloop-glib0 (>= 1:0.99.1) men 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 är installerat
                         Beroende av: libpulse0 (>= 1:0.99.1) men 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 är installerat
                         Beroende av: libupower-glib1 (>= 0.9.9) men 0.9.1-1ubuntu1 är installerat
                         Beroende av: libwacom2 (>= 0.3) men det är inte installerat
                         Beroende av: dconf-gsettings-backend men det är inte installerat eller
                                      gsettings-backend
                         Beroende av: gsettings-desktop-schemas (>= 3.3.90-0ubuntu2) men det är inte installerat
  initramfs-tools: Beroende av: initramfs-tools-bin (>= 0.99ubuntu13.4) men 0.92bubuntu78 är installerat
  initscripts: Beroende av: mountall (>= 2.28) men 2.14 är installerat
  libapparmor-perl: Beroende av: perl (>= 5.14.2-6ubuntu2.3) men 5.10.1-8ubuntu2 är installerat
                    Beroende av: perlapi-5.14.2
  libcairo-perl: Beroende av: perl (>= 5.14.2-3build1) men 5.10.1-8ubuntu2 är installerat
                 Beroende av: perlapi-5.14.2
                 Beroende av: libcairo2 (>= 1.10.0) men 1.8.10-2ubuntu1 är installerat
  libdigest-sha-perl: Beroende av: perl (>= 5.14.2-6ubuntu1) men 5.10.1-8ubuntu2 är installerat
                      Beroende av: perlapi-5.14.2
  libdpkg-perl: Beroende av: dpkg (>= 1.15.8) men 1.15.5.6ubuntu4 är installerat
  libgnome-desktop-2-17: Beroende av: libgconf2-4 (>= 2.31.1) men 2.28.1-0ubuntu1 är installerat
                         Beroende av: libgdk-pixbuf2.0-0 (>= 2.22.0) men det är inte installerat
                         Beroende av: libglib2.0-0 (>= 2.31.2) men 2.24.1-0ubuntu1 är installerat
                         Beroende av: libgtk2.0-0 (>= 2.24.0) men 2.20.1-0ubuntu2.1 är installerat
                         Rekommenderar: hwdata (>= 0.227-1) men det är inte installerat
  libsub-name-perl: Beroende av: perl (>= 5.14.2-3build1) men 5.10.1-8ubuntu2 är installerat
                    Beroende av: perlapi-5.14.2
  nautilus: Beroende av: libcairo-gobject2 (>= 1.10.0) men det är inte installerat
            Beroende av: libcairo2 (>= 1.10.0) men 1.8.10-2ubuntu1 är installerat
            Beroende av: libdbusmenu-glib4 (>= 0.4.2) men det är inte installerat
            Beroende av: libexempi3 (>= 2.2.0) men 2.1.1-1build2 är installerat
            Beroende av: libgail-3-0 (>= 3.0.0) men det är inte installerat
            Beroende av: libgdk-pixbuf2.0-0 (>= 2.22.0) men det är inte installerat
            Beroende av: libglib2.0-0 (>= 2.31.18) men 2.24.1-0ubuntu1 är installerat
            Beroende av: libgnome-desktop-3-2 (>= 3.2.0) men det är inte installerat
            Beroende av: libgtk-3-0 (>= 3.3.18) men det är inte installerat
            Beroende av: liblaunchpad-integration-3.0-1 (>= 0.1.17) men det är inte installerat
            Beroende av: libnautilus-extension1a (>= 1:2.91) men det är inte installerat
            Beroende av: libnotify4 (>= 0.7.0) men det är inte installerat
            Beroende av: libunity9 (>= 3.8.4) men det är inte installerat
            Beroende av: libzeitgeist-1.0-1 (>= 0.3.14) men det är inte installerat
            Beroende av: dconf-gsettings-backend men det är inte installerat eller
                         gsettings-backend
            Beroende av: nautilus-data (>= 1:3.4) men 1:2.30.1-0ubuntu1.2 är installerat
            Beroende av: gsettings-desktop-schemas men det är inte installerat
            Rekommenderar: brasero (>= 2.26) men det är inte installerat
  perl-modules: Beroende av: perl (>= 5.14.2-1) men 5.10.1-8ubuntu2 är installerat
  plymouth: Beroende av: libplymouth2 (= 0.8.2-2ubuntu31.1) men 0.8.2-2ubuntu2 är installerat]

Some of the words are in Swedish but I think you'll understand by the context :)

What do I do ?
Where do I begin ?

Thanks
Linux noob Viktor

---

### Post by ibjsb4 on 2013-12-06
Have you look in /sources.list to see if any 10.04 sources are laying around?  And I would guess your /sources.list.d is empty.

---


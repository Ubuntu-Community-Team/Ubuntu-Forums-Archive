---
title: "ubuntu12.04, installing libc6-i386 removed many other packages"
date: 2014-05-26
forum: General Help
---

### Post by Giulio_Moro on 2014-05-26
Hi 
I am running Ubuntu 12.04 Desktop on virtual box on a Windows 8 host.
today I tried to install teamviewer by downloading the .deb pkg and usin dpkg to install it. During installation it complained about the fact that libc6-i386 was not installed. I was in a bit of a hurry so I tried 
sudo apt-get install libc6-i386 
as I was in a hurry, I didn't care much about the fact that it notified me that 600+MB's of space would have been FREED after this operation, and I decided to continue. At some point I was also suggested to do 
sudo apt-get install -f
which I did. Anyhow after all of this I realized that most of the software didn't work at all anymore, as it had been uninstalled (???). So I rebooted to see what would happen but I couldn't get to the login page. I tried to hit esc during login and I managed to get to the console. After login I ran 
dpkg -l | grep "rc  "
to see which packages had been removed, and the output is

```
rc  audacity                                2.0.0-1ubuntu0.1                    fast, cross-platform audio editorrc  checkbox-qt                             0.13.10                             QT4 interface for checkbox
rc  compiz-gnome                            1:0.9.7.12-0ubuntu3                 OpenGL window and compositing manager - GNOME window decorator
rc  dia                                     0.97.2-5                            Diagram editor
rc  dia-common                              0.97.2-5                            Diagram editor (common files)
rc  firefox                                 28.0+build2-0ubuntu0.12.04.1        Safe and easy web browser from Mozilla
rc  flashplugin-installer                   11.2.202.350ubuntu0.12.04.1         Adobe Flash Player plugin installer
rc  gedit                                   3.4.1-0ubuntu1                      official text editor of the GNOME desktop environment
rc  gksu                                    2.0.2-6ubuntu1                      graphical frontend to su
rc  gnome-keyring                           3.2.2-2ubuntu4.1                    GNOME keyring services (daemon and tools)
rc  gnome-media                             3.4.0-0ubuntu3.1                    GNOME media utilities
rc  gnomine                                 1:3.4.1-0ubuntu2.2                  popular minesweeper puzzle game for GNOME
rc  gwibber                                 3.4.2-0ubuntu2.4                    Open source social networking client for GNOME
rc  ibus                                    1.4.1-3ubuntu1                      Intelligent Input Bus - core
rc  jockey-common                           0.9.7-0ubuntu7.14                   user interface and desktop integration for driver management
rc  jockey-gtk                              0.9.7-0ubuntu7.14                   GNOME user interface and desktop integration for driver management
rc  libappindicator1                        0.4.92-0ubuntu1.1                   Application Indicators
rc  libbonoboui2-0                          2.24.5-0ubuntu1.1                   The Bonobo UI library
rc  libc-ares2                              1.7.5-1                             library for asyncronous name resolves
rc  libcanberra-gtk0                        0.28-3ubuntu3                       GTK+ helper for playing widget event sounds with libcanberra
rc  libcurl3                                7.22.0-3ubuntu4.8                   Multi-protocol file transfer library (OpenSSL)
rc  libdbusmenu-qt2                         0.9.2-0ubuntu1                      Qt implementation of the DBusMenu protocol
rc  libdconf-qt0                            0.0.0.110722-0ubuntu4               dconf Qt bindings (library)
rc  libegl1-mesa-drivers-lts-saucy          9.2.1-1ubuntu3~precise1             free implementation of the EGL API -- hardware drivers
rc  libegl1-mesa-lts-saucy                  9.2.1-1ubuntu3~precise1             free implementation of the EGL API -- runtime
rc  libfarstream-0.1-0                      0.1.2-0ubuntu1                      Audio/Video communications framework: core library
rc  libfolks-eds25                          0.6.8-2                             Evolution-data-server backend for libfolks
rc  libgbm1-lts-saucy                       9.2.1-1ubuntu3~precise1             generic buffer management API -- runtime
rc  libgcr-3-1                              3.2.2-2ubuntu4.1                    Library for Crypto UI related task - runtime
rc  libgksu2-0                              2.0.13~pre1-5ubuntu2                library providing su and sudo functionality
rc  libgl1-mesa-dri-lts-saucy               9.2.1-1ubuntu3~precise1             free implementation of the OpenGL API -- DRI modules
rc  libgl1-mesa-glx-lts-saucy               9.2.1-1ubuntu3~precise1             free implementation of the OpenGL API -- GLX runtime
rc  libglade2-0                             1:2.6.4-1ubuntu1.1                  library to load .glade files at runtime
rc  libglapi-mesa-lts-saucy                 9.2.1-1ubuntu3~precise1             free implementation of the GL API -- shared library
rc  libgnomecanvas2-0                       2.30.3-1ubuntu1.1                   powerful object-oriented display engine - runtime files
rc  libgnomeui-0                            2.24.5-2ubuntu2                     GNOME user interface library - runtime files
rc  libgtksourceview-3.0-0                  3.4.2-0ubuntu1                      shared libraries for the GTK+ syntax highlighting widget
rc  libindicator-messages-status-provider1  0.6.0-0ubuntu2                      indicator status provider - shared library
rc  libindicator7                           0.5.0-0ubuntu1                      panel indicator applet - shared library
rc  libkeybinder0                           0.2.2-3build1                       registers global key bindings for applications
rc  libmetacity-private0                    1:2.34.1-1ubuntu11                  library for the Metacity window manager
rc  liboverlay-scrollbar-0.2-0              0.2.16-0ubuntu1.1                   Scrollbar overlayed widget - shared lib
rc  libpurple0                              1:2.10.3-0ubuntu1.4                 multi-protocol instant messaging library
rc  libqt4-dbus                             4:4.8.1-0ubuntu4.6                  Qt 4 D-Bus module
rc  libqt4-declarative                      4:4.8.1-0ubuntu4.6                  Qt 4 Declarative module
rc  libqt4-network                          4:4.8.1-0ubuntu4.6                  Qt 4 network module
rc  libqt4-opengl                           4:4.8.1-0ubuntu4.6                  Qt 4 OpenGL module
rc  libqt4-script                           4:4.8.1-0ubuntu4.6                  Qt 4 script module
rc  libqt4-sql                              4:4.8.1-0ubuntu4.6                  Qt 4 SQL module
rc  libqt4-svg                              4:4.8.1-0ubuntu4.6                  Qt 4 SVG module
rc  libqt4-xml                              4:4.8.1-0ubuntu4.6                  Qt 4 XML module
rc  libqt4-xmlpatterns                      4:4.8.1-0ubuntu4.6                  Qt 4 XML patterns module
rc  libqtbamf1                              0.2.4-0ubuntu1                      Qt binding and QML plugin for bamf - shared library
rc  libqtcore4                              4:4.8.1-0ubuntu4.6                  Qt 4 core module
rc  libqtdee2                               0.2.4-0ubuntu1                      Qt binding and QML plugin for Dee - shared library
rc  libqtgconf1                             0.1-0ubuntu5                        Qt binding and QML plugin for GConf - shared library
rc  libqtgui4                               4:4.8.1-0ubuntu4.6                  Qt 4 GUI module
rc  libslv2-9                               0.6.6+dfsg1-1                       library for simple use of LV2 plugins
rc  libsyncdaemon-1.0-1                     3.0.2-0ubuntu2                      Ubuntu One synchronization daemon library
rc  libtelepathy-farstream2                 0.4.0-0ubuntu1                      Glue library between telepathy and farstream
rc  libunity-2d-private0                    5.14.0-0ubuntu2                     Unity 2D shared library
rc  libv8-3.7.12.22                         3.7.12.22-3                         v8 JavaScript engine - runtime library
rc  libvncserver0                           0.9.8.2-2ubuntu1                    API to write one's own vnc server
rc  libvte9                                 1:0.28.2-3ubuntu2                   Terminal emulator widget for GTK+ 2.0 - runtime files
rc  libwnck22                               1:2.30.7-0ubuntu1                   Window Navigator Construction Kit - runtime files
rc  libxatracker1-lts-saucy                 9.2.1-1ubuntu3~precise1             X acceleration library -- runtime
rc  libxp6                                  1:1.0.1-2ubuntu0.12.04.1            X Printing Extension (Xprint) client library
rc  mahjongg                                1:3.4.1-0ubuntu2.2                  classic Eastern tile game for GNOME
rc  node                                    0.3.2-7.1                           Amateur Packet Radio Node program
rc  nodejs-dev                              0.8.26-1chl1~precise1               Development files for Node.js
rc  npm                                     1.3.0-1chl1~precise1                package manager for nodejs
rc  ntfs-3g                                 1:2012.1.15AR.1-1ubuntu1.2          read/write NTFS driver for FUSE
rc  onboard                                 0.97.0-0ubuntu4                     Simple On-screen Keyboard
rc  python-cupshelpers                      1.3.8+20120201-0ubuntu8.1           Python modules for printer configuration with CUPS
rc  remmina                                 1.0.0-1ubuntu6.3                    remote desktop client for GNOME desktop environment
rc  scite                                   3.0.2-2                             Lightweight GTK-based Programming Editor
rc  seahorse                                3.2.2-0ubuntu2.1                    GNOME front end for GnuPG
rc  shotwell                                0.12.3-0ubuntu0.1                   digital photo organizer
rc  sni-qt                                  0.2.5-0ubuntu3                      indicator support for Qt
rc  software-center                         5.2.10                              Utility for browsing, installing, and removing software
rc  system-config-printer-common            1.3.8+20120201-0ubuntu8.1           Printer configuration GUI
rc  system-config-printer-gnome             1.3.8+20120201-0ubuntu8.1           Printer configuration GUI
ii  sysv-rc                                 2.88dsf-13.10ubuntu11.1             System-V-like runlevel change mechanism
rc  thunderbird                             1:24.4.0+build1-0ubuntu0.12.04.1    Email, RSS and newsgroup client with integrated spam filter
rc  totem                                   3.0.1-0ubuntu21.1                   Simple media player for the GNOME desktop based on GStreamer
rc  ubuntu-sso-client                       3.0.2-0ubuntu3                      Ubuntu Single Sign-On client
rc  ubuntuone-client                        3.0.2-0ubuntu2                      Ubuntu One client
rc  unity-2d-panel                          5.14.0-0ubuntu2                     Unity 2D Panel
rc  update-notifier                         0.119ubuntu8.6                      Daemon which notifies about package updates
rc  vino                                    3.4.2-0ubuntu1.3.1                  VNC server for GNOME
rc  whoopsie                                0.1.34                              Ubuntu crash database submission daemon
rc  x11-apps                                7.6+5ubuntu1                        X applications
rc  xdiagnose                               2.5.3                               X.org diagnosis tool
rc  xserver-xorg-core-lts-saucy             2:1.14.5-1ubuntu2~saucy1~precise2   Xorg X server - core server
rc  xserver-xorg-lts-saucy                  1:7.7+1ubuntu6~precise1             X.Org X server
rc  xserver-xorg-video-intel-lts-saucy      2:2.99.904-0ubuntu2.1~precise1      X.Org X server -- Intel i8xx, i9xx display driver
rc  xserver-xorg-video-openchrome-lts-saucy 1:0.3.1-0ubuntu2.1~precise1         X.Org X server -- VIA display driver
rc  xserver-xorg-video-vmware-lts-saucy     1:13.0.1-0ubuntu2~precise1          X.Org X server -- VMware display driver

```

As you can see, most of my packages were removed.
When I try to 
sudo apt-get install <all of the packages above>
not all of the packages are installed
So I tried again with the ones that were not installed
```
sudo apt-get install audacity compiz-gnome gwibber libegl1-mesa-drivers-lts-saucy libegl1-mesa-lts-saucy libfolks-eds25 libgbm1-lts-saucy libgl1-mesa-dri-lts-saucy libgl1-mesa-glx-lts-saucy libglapi-mesa-lts-saucy libpurple0 libsyncdaemon-1.0-1 libxatracker1-lts-saucy nodejs-dev npm remmina sysv-rc thunderbird totem ubuntuone-client unity-2d-panel update-notifier xserver-xorg-core-lts-saucy xserver-xorg-lts-saucy xserver-xorg-video-intel-lts-saucy xserver-xorg-video-openchrome-lts-saucy xserver-xorg-video-vmware-lts-saucy 
```
And I get 
```

E: Package 'libegl1-mesa-drivers-lts-saucy' has no installation candidate
E: Package 'libegl1-mesa-lts-saucy' has no installation candidate
E: Package 'libgbm1-lts-saucy' has no installation candidate
E: Package 'libgl1-mesa-dri-lts-saucy' has no installation candidate
E: Package 'libgl1-mesa-glx-lts-saucy' has no installation candidate
E: Package 'libglapi-mesa-lts-saucy' has no installation candidate
E: Package 'libxatracker1-lts-saucy' has no installation candidate
E: Package 'xserver-xorg-core-lts-saucy' has no installation candidate
E: Package 'xserver-xorg-lts-saucy' has no installation candidate
E: Package 'xserver-xorg-video-intel-lts-saucy' has no installation candidate
E: Package 'xserver-xorg-video-openchrome-lts-saucy' has no installation candidate
E: Package 'xserver-xorg-video-vmware-lts-saucy' has no installation candidate

The following packages have unmet dependencies.
 audacity : Depends: audacity-data (= 2.0.0-1) but 2.0.0-1ubuntu0.1 is to be installed
 compiz-gnome : Depends: compiz-plugins-default (= 1:0.9.7.6-0ubuntu1) but it is not going to be installed
 gwibber : Depends: gwibber-service (= 3.4.0-0ubuntu4) but 3.4.2-0ubuntu2.4 is to be installed
 libfolks-eds25 : Depends: evolution-data-server (>= 3.2.0) but it is not going to be installed
 libpurple0 : Depends: libsasl2-modules but it is not going to be installed
 nodejs-dev : Depends: nodejs (= 0.8.26-1chl1~precise1) but it is not going to be installed
 remmina : Depends: remmina-common (= 1.0.0-1ubuntu5) but 1.0.0-1ubuntu6.3 is to be installed
           Recommends: remmina-plugin-rdp but it is not going to be installed
           Recommends: remmina-plugin-vnc but it is not going to be installed
 totem : Depends: totem-common (= 3.0.1-0ubuntu21) but 3.0.1-0ubuntu21.1 is to be installed
         Recommends: totem-plugins but it is not going to be installed
         Recommends: totem-mozilla but it is not going to be installed
 ubuntuone-client : Depends: python-ubuntuone-client (= 3.0.0-0ubuntu1) but 3.0.2-0ubuntu2 is to be installed
                    Recommends: ubuntuone-installer (>= 2.99.5-0ubuntu3) but it is not going to be installed
                    Recommends: ubuntu-sso-client-gui (>= 2.99.91)
 unity-2d-panel : Depends: unity-2d-common (= 5.10.0-0ubuntu1) but 5.14.0-0ubuntu2 is to be installed
                  Recommends: indicator-messages but it is not going to be installed
 update-notifier : Depends: update-notifier-common (= 0.119ubuntu8.1) but 0.119ubuntu8.6 is to be installed
                   Depends: update-manager-gnome but it is not installable or
                            update-manager but it is not going to be installed

```


Still I cannot manage to start a Desktop environment (I was using Gnome-fallback), as during the ordinary startup the machine freezes and I have to reboot and hit esc to get to the shell.

What did happen?
and how do I fix it?

---

### Post by claracc on 2014-05-26
I understand you have ubuntu 12.04 precise pangolin but your are trying to install saucy packages which belongs to 13.10 release. You cannot have mixed packages from different releases.

I would try to install teamviewer from a ppa for ubuntu 12.04, as this link addresses: [http://askubuntu.com/questions/218430/cant-install-teamviewer-on-ubuntu-12-04](http://askubuntu.com/questions/218430/cant-install-teamviewer-on-ubuntu-12-04)

As you have removed a lot of ubuntu 12.04 packages I think that you will have to re install ubuntu 12.04 in virtual box

---

### Post by Giulio_Moro on 2014-05-26
Thanks for the reply
I don't care about having teamviewer installed anymore, it was just for a single use, but both the installation and the executable would require libc6-i386. 
I never installed packages from saucy, so I don't know why they are there, is it possible that libc6-i386 tried to install them?
As I am running virtual box, I can easily recover from a previous backup, but I'd like to find out if there is a way to fix the system.
It would be very disappointing for everybody to have to recover the system because they tried to install libc6-i386 using apt-get . I wouldn't expect such issues using a packet manager

---

### Post by claracc on 2014-05-26
Reading more deeply your post and looking for some of your lost packages as
```
xserver-xorg-core-lts-saucy 2:1.14.5-1ubuntu2~saucy1~precise2 Xorg X server - core server
xserver-xorg-lts-saucy        1:7.7+1ubuntu6~precise1         X.Org X server
xserver-xorg-video-intel-lts-saucy 2:2.99.904-0ubuntu2.1~precise1  X.Org X server -- Intel i8xx, i9xx display driver
xserver-xorg-video-openchrome-lts-saucy 1:0.3.1-0ubuntu2.1~precise1  X.Org X server -- VIA display driver
xserver-xorg-video-vmware-lts-saucy  1:13.0.1-0ubuntu2~precise1   X.Org X server -- VMware display driver
```
I have noted that they are not ubuntu saucy software but ubuntu precise pangolin software, I also have them, as synaptic showed, so you have not mixed packages installed, sorry, it was my mistake.

So the problem seems, you have uninstalled lots of packages, I would start runing ```
sudo apt-get update
``` and then I will try again to install the lost packages.

I don't have libc6-i386 in my 12.04 ubuntu, you could try to remove it also.

If you want to have more control over installation and uninstallation of software, I would use synaptic.

---

### Post by Giulio_Moro on 2014-05-26
No luck, even following your latest instructions. :( : I still get the same error messages as above after doing apt-get update .
by the way, I realized that I have ubuntu 12.04.4 installed

---

### Post by claracc on 2014-05-27
You can try to reinstall ubuntu-desktop:
```
sudo apt-get install --reinstall ubuntu-desktop
```

See link: [http://askubuntu.com/questions/184480/how-to-recover-removed-packages-with-the-purge-flag](http://askubuntu.com/questions/184480/how-to-recover-removed-packages-with-the-purge-flag)
I think, this other link: [http://askubuntu.com/questions/249367/how-to-fix-ubuntu-after-accidentally-uninstalling-many-packages](http://askubuntu.com/questions/249367/how-to-fix-ubuntu-after-accidentally-uninstalling-many-packages) can be useful too in this case.

But I'm afraid, your best bet is to reinstall ubuntu from backup.

---

### Post by Giulio_Moro on 2014-05-27
Ok thanks.
But how did it happen?
And how can I prevent it from happening again?
I mean, it all started with trying to INSTALL a package, and then I just replied "yes" to the apt-get question. I didn't expect that INSTALLING could cause the removal of many packages and basically trash my system

---

### Post by claracc on 2014-05-27
> **Giulio_Moro said:**
> Ok thanks.
But how did it happen?
And how can I prevent it from happening again?
I mean, it all started with trying to INSTALL a package, and then I just replied "yes" to the apt-get question. I didn't expect that INSTALLING could cause the removal of many packages and basically trash my system

Well, I think the answer is in your first post:
> Hi
I am running Ubuntu 12.04 Desktop on virtual box on a Windows 8 host.
today I tried to install teamviewer by downloading the .deb pkg and usin dpkg to install it. During installation it complained about the fact that libc6-i386 was not installed. I was in a bit of a hurry so I tried
sudo apt-get install libc6-i386
as I was in a hurry, I didn't care much about the fact that it notified me that 600+MB's of space would have been FREED after this operation, and I decided to continue.

After running ```
sudo apt-get install libc6-i386
``` you were informed about that it will be required to uninstall a series of packages to met dependencies, these packages ocuppied more than 600 MB, you were asked to continue the operation, yes or not, as you answered yes the packages on your 12.04 ubuntu desktop were removed.

As I suggested previously, you get more control of packages to install and its dependencies using synaptic package manager.

I have searched a little and it seems that libc6-i383 is for AMD architectures, as I said previously, this library is not in my ubuntu 12.04.

---

### Post by ptn107 on 2014-05-27
You can copy/paste the following in your terminal to remove all uninstalled packages that left their configuration files behind.  Seems like you had a bunch.
```
sudo apt-get autoremove; dpkg -l | grep -e ^rc | awk '{print $2}' | xargs sudo apt-get -y purge
```

---

### Post by Giulio_Moro on 2014-05-27
Yeah I know that I should have read it more carefully and not answer "yes" , but the question is:
why should installing a single package require to remove 600MB of other packages?

---


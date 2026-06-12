---
title: "Unable to fix broken packages"
date: 2016-08-08
forum: General Help
---

### Post by waftring on 2016-08-08
I recently upgraded from Ubuntu 14.04 to 16.04 and I tried get things up to date and I got this result.
```
will@will-TECRA-Z40t-A:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-tools-4.4.0-28-generic : Depends: linux-tools-4.4.0-28 but it is not installed
 linux-tools-4.4.0-31-generic : Depends: linux-tools-4.4.0-31 but it is not installed
E: Unmet dependencies. Try using -f.

```
 and when I try to fix them I get this output
```
will@will-TECRA-Z40t-A:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  account-plugin-twitter checkbox-ng friends friends-dispatcher friends-facebook friends-twitter
  g++-4.8 gcc-4.8-base:i386 gcc-4.9-base:i386 gcj-4.8-jre-lib geoclue-2.0 gir1.2-ebook-1.2
  gir1.2-ebookcontacts-1.2 gir1.2-edataserver-1.2 gir1.2-gnomebluetooth-1.0 gir1.2-messagingmenu-1.0
  gir1.2-networkmanager-1.0 gnome-desktop-data gstreamer0.10-nice gstreamer1.0-clutter
  gtk3-engines-unico heirloom-mailx iproute libamd2.3.1 libass4 libatk-wrapper-java
  libatk-wrapper-java-jni libbasicusageenvironment0 libbind9-90 libboost-date-time1.54.0
  libboost-system1.54.0 libcamd2.3.1 libcamel-1.2-45 libccolamd2.8.0 libcdr-0.0-0 libcgmanager0:i386
  libcholmod2.1.2 libcmis-0.4-4 libcolamd2.8.0 libcolord1 libcolorhug1 libcrypt-passwdmd5-perl
  libdirac-encoder0 libdns100 libdvbpsi8 libebackend-1.2-7 libebook-1.2-14 libebook-contacts-1.2-0
  libedata-book-1.2-20 libedataserver-1.2-18 libegl1-mesa-lts-vivid libelfg0 libenca0 libept1.4.12
  libexiv2-12 libfarstream-0.1-0 libfriends0 libgbm1-lts-vivid libgcj14 libgconf2-4 libgcrypt11:i386
  libgdata13 libgee2 libgegl-0.2-0 libgif4 libgif4:i386 libgl1-mesa-dri-lts-vivid
  libgl1-mesa-dri-lts-vivid:i386 libgl1-mesa-glx-lts-vivid libgl1-mesa-glx-lts-vivid:i386
  libglapi-mesa-lts-vivid libglapi-mesa-lts-vivid:i386 libgles1-mesa-lts-vivid libgles2-mesa-lts-vivid
  libglew1.10 libglewmx1.10 libgnome-bluetooth11 libgnome-control-center1 libgnome-desktop-3-7
  libgnome2-0 libgnome2-bin libgnutls26:i386 libgphoto2-port10 libgphoto2-port10:i386 libgrip0
  libgroupsock1 libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386 libgtkmathview0c2a
  libgtksourceview2.0-0 libgtksourceview2.0-common libgtop2-7 libicu52 libidl-common libilmbase6
  libimobiledevice4 libisc95 libisccc90 libisccfg90 libisl10 libjasper1:i386
  libjavascriptcoregtk-1.0-0 libjpeg-progs liblivemedia23 libllvm3.6 libllvm3.6:i386 liblouis2
  liblwres90 libmagickcore5 libmagickcore5-extra libmagickwand5 libmbim-glib0 libminiupnpc8
  libmirclient7 libmirclientplatform-mesa libmirprotobuf-dev libmirprotobuf0 libmspub-0.0-0
  libnih-dbus1:i386 libnih1:i386 libnl-route-3-200 libntdb1 liboil0.3 libopenexr6 liborbit2
  liborc-0.4-0:i386 liborcus-0.6-0 libparted0debian1 libplist1 libpocketsphinx1 libpoppler44
  libpostproc52 libprotobuf-lite8 libprotobuf8 libqmi-glib0 libqpdf13 libqt5qml-graphicaleffects
  libqt5sensors5 libqt5webkit5-qmlwebkitplugin libraw9 librhythmbox-core8 libsctp1 libsexy2
  libsoundtouch0 libsphinxbase1 libstdc++-4.8-dev libswscale2 libsystemd-daemon0 libsystemd-journal0
  libsystemd-login0 libt1-5 libtar0 libthumbnailer0 libts-0.0-0 libumfpack5.6.2 libunityvoice1
  libupower-glib1 libusageenvironment1 libusbmuxd2 libvisio-0.0-0 libvpx1:i386 libwebkitgtk-1.0-0
  libwebkitgtk-1.0-common libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2 libwxbase2.8-0 libwxgtk-media2.8-0
  libwxgtk2.8-0 libxatracker2-lts-vivid libxcb-util0 libxtables10 linux-headers-3.19.0-25
  linux-headers-3.19.0-25-generic linux-headers-3.19.0-64 linux-headers-3.19.0-64-generic
  linux-headers-generic-lts-vivid linux-image-3.19.0-25-generic linux-image-3.19.0-64-generic
  linux-image-extra-3.19.0-25-generic linux-image-extra-3.19.0-64-generic
  linux-image-generic-lts-vivid linux-lts-xenial-tools-4.4.0-28 linux-signed-image-3.19.0-25-generic
  linux-signed-image-3.19.0-64-generic linux-signed-image-generic-lts-vivid linux-tools-4.4.0-28
  linux-tools-4.4.0-28-generic linux-tools-virtual-lts-xenial lksctp-tools obex-data-server
  python-commandnotfound python-dbus-dev python-gconf python-gdbm python-gnomekeyring python-gobject
  python-ibus python-libxml2 python-notify python-ntdb python-pexpect python-ptyprocess
  python-renderpm python-reportlab python-reportlab-accel python-requests python-smbc python-wxgtk2.8
  python3-checkbox-ng qtdeclarative5-dialogs-plugin qtdeclarative5-localstorage-plugin
  qtdeclarative5-privatewidgets-plugin qtdeclarative5-qtfeedback-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets
  qtdeclarative5-window-plugin rhythmbox-mozilla sphinx-voxforge-hmm-en sphinx-voxforge-lm-en
  telepathy-indicator tsconf ubuntu-extras-keyring unity-lens-friends unity-scope-audacious
  unity-scope-clementine unity-scope-gmusicbrowser unity-scope-gourmet unity-scope-guayadeque
  unity-scope-musique unity-voice-service xchat-common xfonts-mathml xscreensaver-data
  xserver-xorg-input-evdev-lts-vivid xserver-xorg-input-mouse-lts-vivid
  xserver-xorg-input-synaptics-lts-vivid xserver-xorg-input-vmmouse-lts-vivid
  xserver-xorg-input-wacom-lts-vivid xserver-xorg-video-ati-lts-vivid
  xserver-xorg-video-cirrus-lts-vivid xserver-xorg-video-fbdev-lts-vivid
  xserver-xorg-video-intel-lts-vivid xserver-xorg-video-mach64-lts-vivid
  xserver-xorg-video-mga-lts-vivid xserver-xorg-video-neomagic-lts-vivid
  xserver-xorg-video-nouveau-lts-vivid xserver-xorg-video-openchrome-lts-vivid
  xserver-xorg-video-r128-lts-vivid xserver-xorg-video-radeon-lts-vivid
  xserver-xorg-video-savage-lts-vivid xserver-xorg-video-siliconmotion-lts-vivid
  xserver-xorg-video-sisusb-lts-vivid xserver-xorg-video-tdfx-lts-vivid
  xserver-xorg-video-trident-lts-vivid xserver-xorg-video-vesa-lts-vivid
  xserver-xorg-video-vmware-lts-vivid
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-tools-4.4.0-28 linux-tools-4.4.0-31
The following NEW packages will be installed:
  linux-tools-4.4.0-28 linux-tools-4.4.0-31
0 upgraded, 2 newly installed, 0 to remove and 3 not upgraded.
4 not fully installed or removed.
Need to get 0 B/1,366 kB of archives.
After this operation, 4,426 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 354786 files and directories currently installed.)
Preparing to unpack .../linux-tools-4.4.0-28_4.4.0-28.47_amd64.deb ...
Unpacking linux-tools-4.4.0-28 (4.4.0-28.47) ...
dpkg: error processing archive /var/cache/apt/archives/linux-tools-4.4.0-28_4.4.0-28.47_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libcpupower.so.4.4.0-28', which is also in package linux-lts-xenial-tools-4.4.0-28 4.4.0-28.47~14.04.1
Preparing to unpack .../linux-tools-4.4.0-31_4.4.0-31.50_amd64.deb ...
Unpacking linux-tools-4.4.0-31 (4.4.0-31.50) ...
dpkg: error processing archive /var/cache/apt/archives/linux-tools-4.4.0-31_4.4.0-31.50_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libcpupower.so.4.4.0-31', which is also in package linux-lts-xenial-tools-4.4.0-31 4.4.0-31.50~14.04.1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-tools-4.4.0-28_4.4.0-28.47_amd64.deb
 /var/cache/apt/archives/linux-tools-4.4.0-31_4.4.0-31.50_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'm fairly new to ubuntu so any sort of guidance would be helpful!

---

### Post by Bashing-om on 2016-08-08
waftring; Yuk !

That is a lot of " automatically installed and are no longer required: " from a wide variety of sources.
When we comply with the system's request, there is a high degree of probability we will break the system. Are you prepared for this eventuality and have made the backup of your important data ??

To the problem at hand, we are looking at kernel install issues in 4.4 so we look at what is :
post back
a) The kernel that you are booting with:
```

uname -a

```
b) The kernels that are installed:
```

dpkg -l | grep linux-

```
c) How much disk space do we have to operate with :
```

df -h
df -i

```

And we get ready to break something.
[INDENT][INDENT]fixing breakage, the first step in the learning process
[/INDENT][/INDENT]

---

### Post by Frogs Hair on 2016-08-08
Hello waftring:

Is this Ubuntu or a Ubuntu based operating system ?

---

### Post by waftring on 2016-08-09
> **Bashing-om said:**
> waftring; Yuk !

That is a lot of " automatically installed and are no longer required: " from a wide variety of sources.
When we comply with the system's request, there is a high degree of probability we will break the system. Are you prepared for this eventuality and have made the backup of your important data ??

To the problem at hand, we are looking at kernel install issues in 4.4 so we look at what is :
post back
a) The kernel that you are booting with:
```

uname -a

```
b) The kernels that are installed:
```

dpkg -l | grep linux-

```
c) How much disk space do we have to operate with :
```

df -h
df -i

```

And we get ready to break something.[INDENT][INDENT]fixing breakage, the first step in the learning process
[/INDENT]
[/INDENT]

Here is what I get back for each
a) uname -a
```
will@will-TECRA-Z40t-A:~$ uname -a
Linux will-TECRA-Z40t-A 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

b) dpkg -l | grep linux-
```
will@will-TECRA-Z40t-A:~$ dpkg -l | grep linux-ii  linux-base                                            4.0ubuntu1                                                  all          Linux image base package
ii  linux-firmware                                        1.157.2                                                     all          Firmware for Linux kernel drivers
ii  linux-generic                                         4.4.0.31.33                                                 amd64        Complete Generic Linux kernel and headers
ii  linux-generic-lts-vivid                               4.4.0.31.33                                                 amd64        Complete Generic Linux kernel and headers (dummy transitional package)
ii  linux-headers-3.19.0-25                               3.19.0-25.26~14.04.1                                        all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-25-generic                       3.19.0-25.26~14.04.1                                        amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-64                               3.19.0-64.72~14.04.1                                        all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-64-generic                       3.19.0-64.72~14.04.1                                        amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-65                               3.19.0-65.73~14.04.1                                        all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-65-generic                       3.19.0-65.73~14.04.1                                        amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-31                                4.4.0-31.50                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-31-generic                        4.4.0-31.50                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 4.4.0.31.33                                                 amd64        Generic Linux kernel headers
ii  linux-headers-generic-lts-vivid                       4.4.0.31.33                                                 amd64        Generic Linux kernel headers (dummy transitional package)
ii  linux-image-3.19.0-25-generic                         3.19.0-25.26~14.04.1                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-64-generic                         3.19.0-64.72~14.04.1                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-65-generic                         3.19.0-65.73~14.04.1                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-31-generic                          4.4.0-31.50                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-25-generic                   3.19.0-25.26~14.04.1                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-64-generic                   3.19.0-64.72~14.04.1                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-65-generic                   3.19.0-65.73~14.04.1                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-31-generic                    4.4.0-31.50                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                                   4.4.0.31.33                                                 amd64        Generic Linux kernel image
ii  linux-image-generic-lts-vivid                         4.4.0.31.33                                                 amd64        Generic Linux kernel image (dummy transitional package)
ii  linux-libc-dev:amd64                                  4.4.0-31.50                                                 amd64        Linux Kernel Headers for development
ii  linux-lts-xenial-tools-4.4.0-28                       4.4.0-28.47~14.04.1                                         amd64        Linux kernel version specific tools for version 4.4.0-28
ii  linux-lts-xenial-tools-4.4.0-31                       4.4.0-31.50~14.04.1                                         amd64        Linux kernel version specific tools for version 4.4.0-31
ii  linux-signed-generic                                  4.4.0.31.33                                                 amd64        Complete Signed Generic Linux kernel and headers
ii  linux-signed-generic-lts-vivid                        4.4.0.31.33                                                 amd64        Complete Signed Generic Linux kernel and headers (dummy transitional package)
ii  linux-signed-image-3.19.0-25-generic                  3.19.0-25.26~14.04.1                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.19.0-64-generic                  3.19.0-64.72~14.04.1                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.19.0-65-generic                  3.19.0-65.73~14.04.1                                        amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-31-generic                   4.4.0-31.50                                                 amd64        Signed kernel image generic
ii  linux-signed-image-generic                            4.4.0.31.33                                                 amd64        Signed Generic Linux kernel image
ii  linux-signed-image-generic-lts-vivid                  4.4.0.31.33                                                 amd64        Signed Generic Linux kernel image (dummy transitional package)
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu5                                        all          base package for ALSA and OSS sound systems
iU  linux-tools-4.4.0-28-generic                          4.4.0-28.47                                                 amd64        Linux kernel version specific tools for version 4.4.0-28
iU  linux-tools-4.4.0-31-generic                          4.4.0-31.50                                                 amd64        Linux kernel version specific tools for version 4.4.0-31
ii  linux-tools-common                                    4.4.0-31.50                                                 all          Linux kernel version specific tools for version 4.4.0
iU  linux-tools-virtual                                   4.4.0.31.33                                                 amd64        This package will always depend on the latest minimal generic kernel tools.
iU  linux-tools-virtual-lts-xenial                        4.4.0.31.33                                                 amd64        This package will always depend on the latest minimal generic kernel tools. (dummy transitional package)
ii  syslinux-common                                       3:6.03+dfsg-11ubuntu1                                       all          collection of bootloaders (common)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu8                                        amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

c) How much disk space there is 
```
will@will-TECRA-Z40t-A:~$ df -hFilesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           790M  9.7M  780M   2% /run
/dev/sda2       451G   44G  384G  11% /
tmpfs           3.9G   99M  3.8G   3% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda1       511M  3.6M  508M   1% /boot/efi
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           790M   64K  790M   1% /run/user/1000
will@will-TECRA-Z40t-A:~$ df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
udev            1005402    563  1004839    1% /dev
tmpfs           1010279    836  1009443    1% /run
/dev/sda2      29974528 504097 29470431    2% /
tmpfs           1010279     55  1010224    1% /dev/shm
tmpfs           1010279      6  1010273    1% /run/lock
tmpfs           1010279     18  1010261    1% /sys/fs/cgroup
/dev/sda1             0      0        0     - /boot/efi
cgmfs           1010279     14  1010265    1% /run/cgmanager/fs
tmpfs           1010279     32  1010247    1% /run/user/1000



```

> **Frogs Hair said:**
> Hello waftring:

Is this Ubuntu or a Ubuntu based operating system ?

And this is ubuntu 16.04 not an ubuntu based operating system.

---

### Post by howefield on 2016-08-09
> **waftring said:**
> And this is ubuntu 16.04 not an ubuntu based operating system.

So.. moved to the "*General Help*" forum.

---

### Post by Bashing-om on 2016-08-09
waftring; Ho Kay !

Looks to me like we are clear to launch .
Let's clean this system up and get the xenial kernel support packages installed.
The clean up:
```

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean
sudo apt update
sudo apt upgrade
sudo apt -f install

```
Note we use the re-written 'apt' for the update/upgrade. It would be nice to post these outputs such that we have a record of the package manager's actions.

Now what is the status of the kernels after the above runs :
```

d[kg -l | grep linux-

```
and next we see what results when we remove vivid and install xenial for the kernel's support .

Of some concern is the state of the graphic's driver . We will see about that !

[INDENT][INDENT]this ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by waftring on 2016-08-09
> **Bashing-om said:**
> waftring; Ho Kay !

Looks to me like we are clear to launch .
Let's clean this system up and get the xenial kernel support packages installed.
The clean up:
```

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean
sudo apt update
sudo apt upgrade
sudo apt -f install

```
Note we use the re-written 'apt' for the update/upgrade. It would be nice to post these outputs such that we have a record of the package manager's actions.

Now what is the status of the kernels after the above runs :
```

d[kg -l | grep linux-

```
and next we see what results when we remove vivid and install xenial for the kernel's support .

Of some concern is the state of the graphic's driver . We will see about that ![INDENT][INDENT]this ain't no step for a stepper
[/INDENT]
[/INDENT]


So here we go here are the outputs one by one
```
will@will-TECRA-Z40t-A:~$ sudo apt-get autoclean
[sudo] password for will: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del base-files 7.2ubuntu5.5 [67.5 kB]
Del grub-efi-amd64-signed 1.34.13+2.02~beta2-9ubuntu1.11 [245 kB]
Del paper-icon-theme 1.3+r567~daily~ubuntu14.04.1 [35.4 MB]
Del curl 7.35.0-1ubuntu2.7 [123 kB]
Del linux-signed-image-generic 4.4.0.31.33 [2,358 B]
Del linux-libc-dev 4.4.0-31.50 [835 kB]
Del libpurple0 1:2.10.9-0ubuntu3.3 [1,284 kB]
Del thunderbird-locale-en-gb 1:45.2.0+build1-0ubuntu0.14.04.3 [10.5 kB]
Del libdrm-intel1 2.4.67-1ubuntu0.14.04.1 [54.7 kB]
Del avahi-daemon 0.6.31-4ubuntu1.1 [58.8 kB]
Del libdrm2 2.4.67-1ubuntu0.14.04.1 [27.8 kB]
Del grub-common 2.02~beta2-9ubuntu1.12 [1,681 kB]
Del libnss3 2:3.23-0ubuntu0.14.04.1 [1,119 kB]
Del linux-image-generic-lts-vivid 3.19.0.65.47 [2,324 B]
Del grub-efi-amd64-bin 2.02~beta2-9ubuntu1.11 [649 kB]
Del libavahi-glib1 0.6.31-4ubuntu1.1 [7,758 B]
Del tor-browser 6.0.2-1~webupd8~0 [69.5 MB]
Del shim-signed 1.18~14.04.1+0.8-0ubuntu2 [315 kB]
Del liboxideqtquick0 1.16.5-0ubuntu0.14.04.1 [267 kB]
Del firefox 48.0+build2-0ubuntu0.14.04.1 [45.7 MB]
Del linux-signed-image-generic-lts-vivid 3.19.0.65.47 [2,354 B]
Del avahi-autoipd 0.6.31-4ubuntu1.1 [35.8 kB]
Del libefivar0 0.21-1~14.04.2 [42.7 kB]
Del linux-signed-generic-lts-vivid 4.4.0.31.33 [1,816 B]
Del libdrm-dev 2.4.67-1ubuntu0.14.04.1 [205 kB]
Del libnspr4 2:4.12-0ubuntu0.14.04.1 [110 kB]
Del libcurl3-gnutls 7.35.0-1ubuntu2.7 [165 kB]
Del linux-generic-lts-vivid 4.4.0.31.33 [1,804 B]
Del gimp-data 2.8.10-0ubuntu1.1 [3,066 kB]
Del linux-headers-3.19.0-65-generic 3.19.0-65.73~14.04.1 [754 kB]
Del libxrandr2 2:1.5.0-1~trusty1 [17.0 kB]
Del paper-cursor-theme 1.3+r567~daily~ubuntu14.04.1 [74.5 kB]
Del linux-signed-image-3.19.0-65-generic 3.19.0-65.73~14.04.1 [4,090 B]
Del thunderbird 1:45.2.0+build1-0ubuntu0.14.04.3 [34.9 MB]
Del thunderbird-locale-en-us 1:45.2.0+build1-0ubuntu0.14.04.3 [10.4 kB]
Del avahi-utils 0.6.31-4ubuntu1.1 [24.2 kB]
Del libdrm-nouveau2 2.4.67-1ubuntu0.14.04.1 [15.9 kB]
Del language-pack-en-base 1:14.04+20160720 [484 kB]
Del oxideqt-codecs 1.16.5-0ubuntu0.14.04.1 [540 kB]
Del libavahi-gobject0 0.6.31-4ubuntu1.1 [16.9 kB]
Del libavahi-common-data 0.6.31-4ubuntu1.1 [21.2 kB]
Del libavahi-common3 0.6.31-4ubuntu1.1 [22.2 kB]
Del linux-libc-dev 3.13.0-92.139 [770 kB]
Del libdrm-radeon1 2.4.67-1ubuntu0.14.04.1 [21.2 kB]
Del initramfs-tools-bin 0.103ubuntu4.4 [9,134 B]
Del libcurl3 7.35.0-1ubuntu2.7 [173 kB]
Del libdrm2 2.4.67-1ubuntu0.14.04.1 [27.1 kB]
Del libsoundtouch0 1.7.1-5 [33.6 kB]
Del linux-image-3.19.0-65-generic 3.19.0-65.73~14.04.1 [16.8 MB]
Del language-pack-en 1:14.04+20160720 [1,820 B]
Del gimp 2.8.10-0ubuntu1.1 [3,401 kB]
Del linux-signed-generic-lts-vivid 3.19.0.65.47 [1,832 B]
Del language-pack-gnome-en 1:14.04+20160720 [1,844 B]
Del libdrm-radeon1 2.4.67-1ubuntu0.14.04.1 [22.3 kB]
Del grub2-common 2.02~beta2-9ubuntu1.12 [501 kB]
Del libgtkglext1 1.2.0-3.1fakesync3 [76.6 kB]
Del libgd3 2.1.0-3ubuntu0.2 [122 kB]
Del isc-dhcp-client 4.2.4-7ubuntu12.5 [639 kB]
Del shim-signed 1.17~14.04.1+0.8-0ubuntu2 [314 kB]
Del linux-headers-generic-lts-vivid 4.4.0.31.33 [1,800 B]
Del libldap-2.4-2 2.4.31-1+nmu2ubuntu8.3 [153 kB]
Del firefox-locale-en 48.0+build2-0ubuntu0.14.04.1 [604 kB]
Del grub-efi-amd64-bin 2.02~beta2-9ubuntu1.12 [649 kB]
Del libavahi-common-data 0.6.31-4ubuntu1.1 [21.3 kB]
Del linux-signed-generic 4.4.0.31.33 [1,816 B]
Del initramfs-tools 0.103ubuntu4.4 [44.5 kB]
Del grub-efi-amd64-signed 1.34.14+2.02~beta2-9ubuntu1.12 [246 kB]
Del pidgin-data 1:2.10.9-0ubuntu3.3 [998 kB]
Del tzdata-java 2016f-0ubuntu0.14.04 [69.6 kB]
Del python-gpgme 0.3-0ubuntu3 [24.0 kB]
Del thunderbird-locale-en 1:45.2.0+build1-0ubuntu0.14.04.3 [384 kB]
Del libgimp2.0 2.8.10-0ubuntu1.1 [484 kB]
Del grub2-common 2.02~beta2-9ubuntu1.11 [501 kB]
Del thunderbird-gnome-support 1:45.2.0+build1-0ubuntu0.14.04.3 [8,538 B]
Del liboxideqtcore0 1.16.5-0ubuntu0.14.04.1 [28.8 MB]
Del pidgin 1:2.10.9-0ubuntu3.3 [490 kB]
Del linux-lts-xenial-tools-4.4.0-31 4.4.0-31.50~14.04.1 [675 kB]
Del libldap-2.4-2 2.4.31-1+nmu2ubuntu8.3 [150 kB]
Del libnss3-nssdb 2:3.23-0ubuntu0.14.04.1 [10.6 kB]
Del linux-headers-generic 4.4.0.31.33 [2,294 B]
Del desmume 0.9.9-1 [2,492 kB]
Del tzdata 2016f-0ubuntu0.14.04 [166 kB]
Del paper-gtk-theme 2.1+r264~daily~ubuntu14.04.1 [469 kB]
Del vim-runtime 2:7.4.052-1ubuntu3 [4,888 kB]
Del libdrm-intel1 2.4.67-1ubuntu0.14.04.1 [55.3 kB]
Del linux-image-generic-lts-vivid 4.4.0.31.33 [1,794 B]
Del linux-headers-generic-lts-vivid 3.19.0.65.47 [2,304 B]
Del linux-headers-3.19.0-65 3.19.0-65.73~14.04.1 [9,311 kB]
Del paper-icon-theme 1.3+r568~daily~ubuntu14.04.1 [35.4 MB]
Del libpurple-bin 1:2.10.9-0ubuntu3.3 [15.3 kB]
Del grub-efi-amd64 2.02~beta2-9ubuntu1.12 [44.9 kB]
Del nautilus-dropbox 1.6.1-1 [86.3 kB]
Del libarchive13 3.1.2-7ubuntu2.3 [261 kB]
Del vim 2:7.4.052-1ubuntu3 [956 kB]
Del linux-signed-image-generic-lts-vivid 4.4.0.31.33 [1,808 B]
Del libdrm-amdgpu1 2.4.67-1ubuntu0.14.04.1 [16.3 kB]
Del grub-efi-amd64 2.02~beta2-9ubuntu1.11 [45.2 kB]
Del libxrandr2 2:1.5.0-1~trusty1 [17.5 kB]
Del grub-common 2.02~beta2-9ubuntu1.11 [1,674 kB]
Del isc-dhcp-common 4.2.4-7ubuntu12.5 [707 kB]
Del libdrm-nouveau2 2.4.67-1ubuntu0.14.04.1 [16.8 kB]
Del paper-gtk-theme 2.1+r263~daily~ubuntu14.04.1 [470 kB]
Del libavahi-client3 0.6.31-4ubuntu1.1 [24.5 kB]
Del language-pack-gnome-en-base 1:14.04+20160720 [957 kB]
Del libavahi-common3 0.6.31-4ubuntu1.1 [21.7 kB]
Del libavahi-client3 0.6.31-4ubuntu1.1 [25.1 kB]
Del liboxideqt-qmlplugin 1.16.5-0ubuntu0.14.04.1 [187 kB]
Del sbsigntool 0.6-0ubuntu7.2 [53.9 kB]
Del linux-image-generic 4.4.0.31.33 [2,316 B]
Del libimobiledevice4 1.1.5+git20140313.bafe6a9e-0ubuntu1.1 [52.7 kB]
Del linux-generic-lts-vivid 3.19.0.65.47 [1,796 B]
Del paper-cursor-theme 1.3+r568~daily~ubuntu14.04.1 [74.7 kB]
Del linux-generic 4.4.0.31.33 [1,790 B]
Del libavahi-core7 0.6.31-4ubuntu1.1 [80.9 kB]
Del linux-image-extra-3.19.0-65-generic 3.19.0-65.73~14.04.1 [38.3 MB]
Del libgd3 2.1.0-3ubuntu0.2 [118 kB]

```

And the second
```
will@will-TECRA-Z40t-A:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-tools-4.4.0-28-generic : Depends: linux-tools-4.4.0-28 but it is not installed
 linux-tools-4.4.0-31-generic : Depends: linux-tools-4.4.0-31 but it is not installed
E: Unmet dependencies. Try using -f.

```
The third
```
ill@will-TECRA-Z40t-A:~$ sudo apt-get clean

```
Fourth
```
will@will-TECRA-Z40t-A:~$ sudo apt-get update
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [95.7 kB]   
Ign:3 http://dl.google.com/linux/chrome/deb stable InRelease                   
Get:4 http://security.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]    
Hit:5 http://archive.canonical.com/ubuntu xenial InRelease                     
Hit:6 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:7 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease           
Get:8 http://us.archive.ubuntu.com/ubuntu xenial-updates/main Sources [175 kB] 
Get:10 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [361 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [357 kB]
Get:12 http://security.ubuntu.com/ubuntu xenial-security/main Sources [33.9 kB]
Get:13 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages [128 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [311 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [308 kB]
Get:16 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages [125 kB]
Get:17 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en [50.5 kB]
Get:18 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [44.1 kB]
Get:19 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [50.8 kB]
Get:20 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [38.6 kB]
Get:21 http://security.ubuntu.com/ubuntu xenial-security/universe i386 Packages [38.6 kB]
Get:22 http://security.ubuntu.com/ubuntu xenial-security/universe Translation-en [23.0 kB]
Get:23 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [2,329 B]
Fetched 2,237 kB in 5s (423 kB/s)              
Reading package lists... Done

```
Fifth
```
will@will-TECRA-Z40t-A:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-tools-4.4.0-28-generic : Depends: linux-tools-4.4.0-28 but it is not installed
 linux-tools-4.4.0-31-generic : Depends: linux-tools-4.4.0-31 but it is not installed
E: Unmet dependencies. Try using -f.

```
Sixth...
```
will@will-TECRA-Z40t-A:~$ sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  account-plugin-twitter checkbox-ng friends friends-dispatcher
  friends-facebook friends-twitter g++-4.8 gcc-4.8-base:i386 gcc-4.9-base:i386
  gcj-4.8-jre-lib geoclue-2.0 gir1.2-ebook-1.2 gir1.2-ebookcontacts-1.2
  gir1.2-edataserver-1.2 gir1.2-gnomebluetooth-1.0 gir1.2-messagingmenu-1.0
  gir1.2-networkmanager-1.0 gnome-desktop-data gstreamer0.10-nice
  gstreamer1.0-clutter gtk3-engines-unico heirloom-mailx iproute libamd2.3.1
  libass4 libatk-wrapper-java libatk-wrapper-java-jni
  libbasicusageenvironment0 libbind9-90 libboost-date-time1.54.0
  libboost-system1.54.0 libcamd2.3.1 libcamel-1.2-45 libccolamd2.8.0
  libcdr-0.0-0 libcgmanager0:i386 libcholmod2.1.2 libcmis-0.4-4 libcolamd2.8.0
  libcolord1 libcolorhug1 libcrypt-passwdmd5-perl libdirac-encoder0 libdns100
  libdvbpsi8 libebackend-1.2-7 libebook-1.2-14 libebook-contacts-1.2-0
  libedata-book-1.2-20 libedataserver-1.2-18 libegl1-mesa-lts-vivid libelfg0
  libenca0 libept1.4.12 libexiv2-12 libfarstream-0.1-0 libfriends0
  libgbm1-lts-vivid libgcj14 libgconf2-4 libgcrypt11:i386 libgdata13 libgee2
  libgegl-0.2-0 libgif4 libgif4:i386 libgl1-mesa-dri-lts-vivid
  libgl1-mesa-dri-lts-vivid:i386 libgl1-mesa-glx-lts-vivid
  libgl1-mesa-glx-lts-vivid:i386 libglapi-mesa-lts-vivid
  libglapi-mesa-lts-vivid:i386 libgles1-mesa-lts-vivid libgles2-mesa-lts-vivid
  libglew1.10 libglewmx1.10 libgnome-bluetooth11 libgnome-control-center1
  libgnome-desktop-3-7 libgnome2-0 libgnome2-bin libgnutls26:i386
  libgphoto2-port10 libgphoto2-port10:i386 libgrip0 libgroupsock1
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386
  libgtkmathview0c2a libgtksourceview2.0-0 libgtksourceview2.0-common
  libgtop2-7 libicu52 libidl-common libilmbase6 libimobiledevice4 libisc95
  libisccc90 libisccfg90 libisl10 libjasper1:i386 libjavascriptcoregtk-1.0-0
  libjpeg-progs liblivemedia23 libllvm3.6 libllvm3.6:i386 liblouis2 liblwres90
  libmagickcore5 libmagickcore5-extra libmagickwand5 libmbim-glib0
  libminiupnpc8 libmirclient7 libmirclientplatform-mesa libmirprotobuf-dev
  libmirprotobuf0 libmspub-0.0-0 libnih-dbus1:i386 libnih1:i386
  libnl-route-3-200 libntdb1 liboil0.3 libopenexr6 liborbit2 liborc-0.4-0:i386
  liborcus-0.6-0 libparted0debian1 libplist1 libpocketsphinx1 libpoppler44
  libpostproc52 libprotobuf-lite8 libprotobuf8 libqmi-glib0 libqpdf13
  libqt5qml-graphicaleffects libqt5sensors5 libqt5webkit5-qmlwebkitplugin
  libraw9 librhythmbox-core8 libsctp1 libsexy2 libsoundtouch0 libsphinxbase1
  libstdc++-4.8-dev libswscale2 libsystemd-daemon0 libsystemd-journal0
  libsystemd-login0 libt1-5 libtar0 libthumbnailer0 libts-0.0-0
  libumfpack5.6.2 libunityvoice1 libupower-glib1 libusageenvironment1
  libusbmuxd2 libvisio-0.0-0 libvpx1:i386 libwebkitgtk-1.0-0
  libwebkitgtk-1.0-common libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2
  libwxbase2.8-0 libwxgtk-media2.8-0 libwxgtk2.8-0 libxatracker2-lts-vivid
  libxcb-util0 libxtables10 linux-headers-3.19.0-25
  linux-headers-3.19.0-25-generic linux-headers-3.19.0-64
  linux-headers-3.19.0-64-generic linux-headers-generic-lts-vivid
  linux-image-3.19.0-25-generic linux-image-3.19.0-64-generic
  linux-image-extra-3.19.0-25-generic linux-image-extra-3.19.0-64-generic
  linux-image-generic-lts-vivid linux-lts-xenial-tools-4.4.0-28
  linux-signed-image-3.19.0-25-generic linux-signed-image-3.19.0-64-generic
  linux-signed-image-generic-lts-vivid linux-tools-4.4.0-28
  linux-tools-4.4.0-28-generic linux-tools-virtual-lts-xenial lksctp-tools
  obex-data-server python-commandnotfound python-dbus-dev python-gconf
  python-gdbm python-gnomekeyring python-gobject python-ibus python-libxml2
  python-notify python-ntdb python-pexpect python-ptyprocess python-renderpm
  python-reportlab python-reportlab-accel python-requests python-smbc
  python-wxgtk2.8 python3-checkbox-ng qtdeclarative5-dialogs-plugin
  qtdeclarative5-localstorage-plugin qtdeclarative5-privatewidgets-plugin
  qtdeclarative5-qtfeedback-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets
  qtdeclarative5-window-plugin rhythmbox-mozilla sphinx-voxforge-hmm-en
  sphinx-voxforge-lm-en telepathy-indicator tsconf ubuntu-extras-keyring
  unity-lens-friends unity-scope-audacious unity-scope-clementine
  unity-scope-gmusicbrowser unity-scope-gourmet unity-scope-guayadeque
  unity-scope-musique unity-voice-service xchat-common xfonts-mathml
  xscreensaver-data xserver-xorg-input-evdev-lts-vivid
  xserver-xorg-input-mouse-lts-vivid xserver-xorg-input-synaptics-lts-vivid
  xserver-xorg-input-vmmouse-lts-vivid xserver-xorg-input-wacom-lts-vivid
  xserver-xorg-video-ati-lts-vivid xserver-xorg-video-cirrus-lts-vivid
  xserver-xorg-video-fbdev-lts-vivid xserver-xorg-video-intel-lts-vivid
  xserver-xorg-video-mach64-lts-vivid xserver-xorg-video-mga-lts-vivid
  xserver-xorg-video-neomagic-lts-vivid xserver-xorg-video-nouveau-lts-vivid
  xserver-xorg-video-openchrome-lts-vivid xserver-xorg-video-r128-lts-vivid
  xserver-xorg-video-radeon-lts-vivid xserver-xorg-video-savage-lts-vivid
  xserver-xorg-video-siliconmotion-lts-vivid
  xserver-xorg-video-sisusb-lts-vivid xserver-xorg-video-tdfx-lts-vivid
  xserver-xorg-video-trident-lts-vivid xserver-xorg-video-vesa-lts-vivid
  xserver-xorg-video-vmware-lts-vivid
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-tools-4.4.0-28 linux-tools-4.4.0-31
The following NEW packages will be installed:
  linux-tools-4.4.0-28 linux-tools-4.4.0-31
0 upgraded, 2 newly installed, 0 to remove and 44 not upgraded.
4 not fully installed or removed.
Need to get 1,366 kB of archives.
After this operation, 4,426 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-tools-4.4.0-28 amd64 4.4.0-28.47 [686 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-tools-4.4.0-31 amd64 4.4.0-31.50 [679 kB]
Fetched 1,366 kB in 1s (928 kB/s)             
(Reading database ... 354786 files and directories currently installed.)
Preparing to unpack .../linux-tools-4.4.0-28_4.4.0-28.47_amd64.deb ...
Unpacking linux-tools-4.4.0-28 (4.4.0-28.47) ...
dpkg: error processing archive /var/cache/apt/archives/linux-tools-4.4.0-28_4.4.0-28.47_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libcpupower.so.4.4.0-28', which is also in package linux-lts-xenial-tools-4.4.0-28 4.4.0-28.47~14.04.1
Preparing to unpack .../linux-tools-4.4.0-31_4.4.0-31.50_amd64.deb ...
Unpacking linux-tools-4.4.0-31 (4.4.0-31.50) ...
dpkg: error processing archive /var/cache/apt/archives/linux-tools-4.4.0-31_4.4.0-31.50_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libcpupower.so.4.4.0-31', which is also in package linux-lts-xenial-tools-4.4.0-31 4.4.0-31.50~14.04.1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-tools-4.4.0-28_4.4.0-28.47_amd64.deb
 /var/cache/apt/archives/linux-tools-4.4.0-31_4.4.0-31.50_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

And the final output
```
will@will-TECRA-Z40t-A:~$ dpkg -l | grep linux-
ii  linux-base                                            4.0ubuntu1                                                  all          Linux image base package
ii  linux-firmware                                        1.157.2                                                     all          Firmware for Linux kernel drivers
ii  linux-generic                                         4.4.0.31.33                                                 amd64        Complete Generic Linux kernel and headers
ii  linux-generic-lts-vivid                               4.4.0.31.33                                                 amd64        Complete Generic Linux kernel and headers (dummy transitional package)
ii  linux-headers-3.19.0-25                               3.19.0-25.26~14.04.1                                        all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-25-generic                       3.19.0-25.26~14.04.1                                        amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-64                               3.19.0-64.72~14.04.1                                        all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-64-generic                       3.19.0-64.72~14.04.1                                        amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-65                               3.19.0-65.73~14.04.1                                        all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-65-generic                       3.19.0-65.73~14.04.1                                        amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-31                                4.4.0-31.50                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-31-generic                        4.4.0-31.50                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 4.4.0.31.33                                                 amd64        Generic Linux kernel headers
ii  linux-headers-generic-lts-vivid                       4.4.0.31.33                                                 amd64        Generic Linux kernel headers (dummy transitional package)
ii  linux-image-3.19.0-25-generic                         3.19.0-25.26~14.04.1                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-64-generic                         3.19.0-64.72~14.04.1                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-65-generic                         3.19.0-65.73~14.04.1                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-31-generic                          4.4.0-31.50                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-25-generic                   3.19.0-25.26~14.04.1                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-64-generic                   3.19.0-64.72~14.04.1                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-65-generic                   3.19.0-65.73~14.04.1                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-31-generic                    4.4.0-31.50                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                                   4.4.0.31.33                                                 amd64        Generic Linux kernel image
ii  linux-image-generic-lts-vivid                         4.4.0.31.33                                                 amd64        Generic Linux kernel image (dummy transitional package)
ii  linux-libc-dev:amd64                                  4.4.0-31.50                                                 amd64        Linux Kernel Headers for development
ii  linux-lts-xenial-tools-4.4.0-28                       4.4.0-28.47~14.04.1                                         amd64        Linux kernel version specific tools for version 4.4.0-28
ii  linux-lts-xenial-tools-4.4.0-31                       4.4.0-31.50~14.04.1                                         amd64        Linux kernel version specific tools for version 4.4.0-31
ii  linux-signed-generic                                  4.4.0.31.33                                                 amd64        Complete Signed Generic Linux kernel and headers
ii  linux-signed-generic-lts-vivid                        4.4.0.31.33                                                 amd64        Complete Signed Generic Linux kernel and headers (dummy transitional package)
ii  linux-signed-image-3.19.0-25-generic                  3.19.0-25.26~14.04.1                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.19.0-64-generic                  3.19.0-64.72~14.04.1                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.19.0-65-generic                  3.19.0-65.73~14.04.1                                        amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-31-generic                   4.4.0-31.50                                                 amd64        Signed kernel image generic
ii  linux-signed-image-generic                            4.4.0.31.33                                                 amd64        Signed Generic Linux kernel image
ii  linux-signed-image-generic-lts-vivid                  4.4.0.31.33                                                 amd64        Signed Generic Linux kernel image (dummy transitional package)
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu5                                        all          base package for ALSA and OSS sound systems
iU  linux-tools-4.4.0-28-generic                          4.4.0-28.47                                                 amd64        Linux kernel version specific tools for version 4.4.0-28
iU  linux-tools-4.4.0-31-generic                          4.4.0-31.50                                                 amd64        Linux kernel version specific tools for version 4.4.0-31
ii  linux-tools-common                                    4.4.0-31.50                                                 all          Linux kernel version specific tools for version 4.4.0
iU  linux-tools-virtual                                   4.4.0.31.33                                                 amd64        This package will always depend on the latest minimal generic kernel tools.
iU  linux-tools-virtual-lts-xenial                        4.4.0.31.33                                                 amd64        This package will always depend on the latest minimal generic kernel tools. (dummy transitional package)
ii  syslinux-common                                       3:6.03+dfsg-11ubuntu1                                       all          collection of bootloaders (common)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu8                                        amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

---

### Post by Bashing-om on 2016-08-09
waftring; Humm .....

Stuck between a rock and a hard place ..

linux-tools-4.4.0-31-generic :
Let's try then:
```

sudo apt install --reinstall linux-tools-generic

```
As per:
[http://packages.ubuntu.com/search?keywords=linux-tools&searchon=names&suite=xenial&section=all](http://packages.ubuntu.com/search?keywords=linux-tools&searchon=names&suite=xenial&section=all)
our target here is provided by linux-tools-generic .

I can accept we may have to get the more aggressive and remove the package before the system will re-install .. Le't attempt the less invasive way 1st . We shall see.

[INDENT][INDENT]If at 1st you do not succeed
[INDENT][INDENT][INDENT]try try again ( sky diving excepted )
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by waftring on 2016-08-10
> **Bashing-om said:**
> waftring; Humm .....

Stuck between a rock and a hard place ..

linux-tools-4.4.0-31-generic :
Let's try then:
```

sudo apt install --reinstall linux-tools-generic

```
As per:
[http://packages.ubuntu.com/search?keywords=linux-tools&searchon=names&suite=xenial&section=all](http://packages.ubuntu.com/search?keywords=linux-tools&searchon=names&suite=xenial&section=all)
our target here is provided by linux-tools-generic .

I can accept we may have to get the more aggressive and remove the package before the system will re-install .. Le't attempt the less invasive way 1st . We shall see.[INDENT][INDENT]If at 1st you do not succeed[INDENT][INDENT][INDENT]try try again ( sky diving excepted )
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


This doesn't seem to be going well...
```
will@will-TECRA-Z40t-A:~$ sudo apt install --reinstall linux-tools-generic
[sudo] password for will: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-tools-4.4.0-28-generic : Depends: linux-tools-4.4.0-28 but it is not going to be installed
 linux-tools-4.4.0-31-generic : Depends: linux-tools-4.4.0-31 but it is not going to be installed
 linux-tools-generic : Depends: linux-tools-4.4.0-34-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by Bashing-om on 2016-08-10
waftring; Indeed, a puzzle.

We need to find out the why, and then determine what we can do to make the package manager happy.

Looking at:
> 
apt-cache depends linux-tools-4.4.0-28

we find a couple of things to check;
What results:
```

apt-cache policy linux-lts-xenial-tools-4.4.0-28
apt-cache policy linux-tools-4.4.0-28-generic:i386

```
Same same advisory from:
> 
sysop@1404mini:~$ apt-cache depends inux-tools-4.4.0-28-generic
linux-tools-4.4.0-28-generic
  Depends: linux-lts-xenial-tools-4.4.0-28
  Conflicts: linux-tools-4.4.0-28-generic:i386
sysop@1404mini:~$


When we find the fix for the -28 kernel support .. we can apply it to the 31 and 34 packages also.
The good thing here is that packages are "optional" so as not required for the system at large, we can play around with them .
> 
apt-cache show linux-tools-4.4.0-28-generic

We can consider removing them, see what breaks and then fix that breakage.

[INDENT][INDENT]formulate a plan
[INDENT][INDENT][INDENT]then go do it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by waftring on 2016-08-10
Here is what I get.
> [COLOR=#000000]*apt-cache depends linux-tools-4.4.0-28*[/COLOR]
```
will@will-TECRA-Z40t-A:~$ apt-cache depends linux-tools-4.4.0-28
linux-tools-4.4.0-28
  Depends: binutils
  Depends: binutils
  Depends: libaudit1
  Depends: libc6
  Depends: libdw1
  Depends: libelf1
  Depends: liblzma5
  Depends: libpci3
  Depends: libslang2
  Depends: libudev1
  Depends: libunwind8
  Depends: zlib1g
  Depends: linux-tools-common

```
> [COLOR=#000000][FONT=&amp]apt-cache policy linux-lts-xenial-tools-4.4.0-28
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]apt-cache policy linux-tools-4.4.0-28-generic:i386[/FONT][/COLOR]
```
will@will-TECRA-Z40t-A:~$ apt-cache policy linux-lts-xenial-tools-4.4.0-28linux-lts-xenial-tools-4.4.0-28:
  Installed: 4.4.0-28.47~14.04.1
  Candidate: 4.4.0-28.47~14.04.1
  Version table:
 *** 4.4.0-28.47~14.04.1 100
        100 /var/lib/dpkg/status
will@will-TECRA-Z40t-A:~$ apt-cache policy linux-tools-4.4.0-28-generic:i386
linux-tools-4.4.0-28-generic:i386:
  Installed: (none)
  Candidate: 4.4.0-28.47
  Version table:
     4.4.0-28.47 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages
will@will-TECRA-Z40t-A:~$ apt-cache policy linux-tools-4.4.0-28-generic:i386linux-tools-4.4.0-28-generic:i386:
  Installed: (none)
  Candidate: 4.4.0-28.47
  Version table:
     4.4.0-28.47 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages
```

> [COLOR=#000000]*apt-cache show linux-tools-4.4.0-28-generic*[/COLOR]
```
will@will-TECRA-Z40t-A:~$ apt-cache show linux-tools-4.4.0-28-generic
Package: linux-tools-4.4.0-28-generic
Priority: optional
Section: devel
Installed-Size: 196
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux
Version: 4.4.0-28.47
Depends: linux-tools-4.4.0-28
Filename: pool/main/l/linux/linux-tools-4.4.0-28-generic_4.4.0-28.47_amd64.deb
Size: 1880
MD5sum: f29076fed115df2511bed108a2668489
SHA1: 9d1b18366ddbb80cc0b71ac6841605a0636143be
SHA256: f49429ac2d101298da95dcc9bf5cce328e917f572fc335978b75490800b472a0
Description-en: Linux kernel version specific tools for version 4.4.0-28
 This package provides the architecture dependant parts for kernel
 version locked tools (such as perf and x86_energy_perf_policy) for
 version 4.4.0-28 on
 64 bit x86.
Description-md5: 755cd56a38e121761506298ead05dc88
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 9m

```

---

### Post by Bashing-om on 2016-08-10
waftring; Well, well ... curious and curiouser .

I do not understand all I do not know about this ! Installed on the 16.04 are the 14.04 packages:
[http://packages.ubuntu.com/search?keywords=linux-lts-xenial-tools-4.4.0-28&searchon=names&suite=trusty-updates&section=all](http://packages.ubuntu.com/search?keywords=linux-lts-xenial-tools-4.4.0-28&searchon=names&suite=trusty-updates&section=all)

Let's see what results when we try and remove this one.
```

sudo apt purge linux-lts-xenial-tools-4.4.0-28

``` At a quick glance .. these packages are not supported in 16.04 .

Depending on what happens here, is what we do next.

[INDENT][INDENT]what does it take to keep
[INDENT][INDENT][INDENT]a package manager like you
[INDENT][INDENT][INDENT][INDENT]satisfied
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by waftring on 2016-08-11
> **Bashing-om said:**
> waftring; Well, well ... curious and curiouser .

I do not understand all I do not know about this ! Installed on the 16.04 are the 14.04 packages:
[http://packages.ubuntu.com/search?keywords=linux-lts-xenial-tools-4.4.0-28&searchon=names&suite=trusty-updates&section=all](http://packages.ubuntu.com/search?keywords=linux-lts-xenial-tools-4.4.0-28&searchon=names&suite=trusty-updates&section=all)

Let's see what results when we try and remove this one.
```

sudo apt purge linux-lts-xenial-tools-4.4.0-28

``` At a quick glance .. these packages are not supported in 16.04 .

Depending on what happens here, is what we do next.[INDENT][INDENT]what does it take to keep[INDENT][INDENT][INDENT]a package manager like you[INDENT][INDENT][INDENT][INDENT]satisfied
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

Still hung up with the unmet dependencies.
```
will@will-TECRA-Z40t-A:~$ sudo apt purge linux-lts-xenial-tools-4.4.0-28
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-tools-4.4.0-28-generic : Depends: linux-tools-4.4.0-28 but it is not going to be installed
 linux-tools-4.4.0-31-generic : Depends: linux-tools-4.4.0-31 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by Bashing-om on 2016-08-11
waftring; Welp;

Not totally surprised at the result. Was just a stab to see what might happen ,
Look, still researching trying to understand what is going on here :
I have:
<Bashing-om> find linux-tools ->>
> 
<ubottu> Found: linux-tools-common, linux-tools-generic, linux-tools-generic-lts-utopic, linux-tools-generic-lts-vivid, linux-tools-generic-lts-wily, linux-tools-generic-lts-xenial, linux-tools-lowlatency, linux-tools-lowlatency-lts-utopic, linux-tools-lowlatency-lts-vivid, linux-tools-lowlatency-lts-wily (and 27 others) [http://packages.ubuntu.com/search?keywords=linux-tools&searchon=names&suite=xenial&section=all](http://packages.ubuntu.com/search?keywords=linux-tools&searchon=names&suite=xenial&section=all)


We need to know what is holding " Depends: linux-tools-4.4.0-28" .
It is valid !
> 
<ubottu> linux-tools-4.4.0-28 (source: linux): Linux kernel version specific tools for version 4.4.0-28. In component main, is optional. Version 4.4.0-28.47 (xenial), package size 661 kB, installed size 2067 kB


Let's see what the package manager advises when we attempt to install linux-tools-4.4.0-28
```

sudo apt install linux-tools-4.4.0-28

```

[INDENT][INDENT]got to be a cause
[INDENT][INDENT][INDENT]got to be a reason
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by NEPO on 2016-08-11
WOW Bashing-om!
What level of support!!  Great work!  I feel really happy to this sort of community participation.

I had a problem of broken package too, reading through your post and saw "sudo apt -f install" that fixed it for me.  not sure why apt-get failed.


Thanks!

EDIT:  hope you guys sort it out.  GOOD LUCK!

---

### Post by waftring on 2016-08-12
> **Bashing-om said:**
> waftring; Welp;

Not totally surprised at the result. Was just a stab to see what might happen ,
Look, still researching trying to understand what is going on here :
I have:
<Bashing-om> find linux-tools ->>


We need to know what is holding " Depends: linux-tools-4.4.0-28" .
It is valid !


Let's see what the package manager advises when we attempt to install linux-tools-4.4.0-28
```

sudo apt install linux-tools-4.4.0-28

```[INDENT][INDENT]got to be a cause[INDENT][INDENT][INDENT]got to be a reason
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


This looks new!

```
will@will-TECRA-Z40t-A:~$ sudo apt install linux-tols-4.4.0-28
[sudo] password for will: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-tols-4.4.0-28
E: Couldn't find any package by glob 'linux-tols-4.4.0-28'
E: Couldn't find any package by regex 'linux-tols-4.4.0-28'

```

Looks like at least we are getting something other than try -f install.

---

### Post by vasa1 on 2016-08-12
> **waftring said:**
> This looks new!

```
will@will-TECRA-Z40t-A:~$ sudo apt install linux-tols-4.4.0-28... 
```

Looks like at least we are getting something other than try -f install.

That's because of the typo: *tols* instead of *tools* :(

---

### Post by oldos2er on 2016-08-12
waftring, one of the reasons we put terminal commands into code blocks is it makes copypasting simpler (and thus avoids typos).

---

### Post by Handssolow on 2016-08-12
I've just had a similar issue with an upgrade from 14.04 to 16.04 on a old pentium-M laptop. About 3/4 the way through it aborted and left essentially an unusable system with 4.4.0-34. I made some progress working my way through different kernels, sometimes with eth0 access, sometimes with no GUI, sometimes with no mouse. It kept reporting that there were 266 broken packages, too many so it aborted the upgrade. I worked several hours on this.

After seeing the package virtuosa-nepomuk cropping up early in the error messages I found this-
[https://ubuntuforums.org/showthread.php?t=2251326](https://ubuntuforums.org/showthread.php?t=2251326) which links to-
[https://askubuntu.com/questions/543857/getting-error-with-dpkg](https://askubuntu.com/questions/543857/getting-error-with-dpkg)

After I removed the virtuoso-nepomuk script out of /etc/init.d I could update and install most of the 226 broken packages. Afterwards I had to completely remove and re-install ufw and tinker with the network settings which had got altered when I needed to gain a working eth0. The laptop is on 3.13.0-93-generic but at least it's working and I'm not left having to re-install Ubuntu. I'll explore kernel upgrades in the future.

Edit: these are what I was using in the terminal

sudo dpkg --configure -a
sudo apt-get update
sudo dpkg --configure -a --abort-after=99999
sudo apt-get dist-upgrade
sudo apt-get -f install

From memory, I think early on I had around 400 broken packages which came down to 226 after I ran

sudo dpkg --configure -a --abort-after=99999

---

### Post by waftring on 2016-08-13
> **oldos2er said:**
> waftring, one of the reasons we put terminal commands into code blocks is it makes copypasting simpler (and thus avoids typos).

That would do it wouldn't it.

Here is the correct output.
```
will@will-TECRA-Z40t-A:~$ sudo apt install linux-tools-4.4.0-28
[sudo] password for will: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-tools-4.4.0-31-generic : Depends: linux-tools-4.4.0-31 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



```

---

### Post by Bashing-om on 2016-08-13
waftring; Hey !

That is progress ! We do the same for -31 .
```

sudo apt install linux-tools-4.4.0-31

```

And now what does the package manager think ?

What now from:
```

sudo apt update
sudo apt upgrade
sudo apt -f install

```

All run clean now ?

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]could be, not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-08-16
waftring; Hello ...

Long time no hear. What is the status now .. all good ?

[INDENT]maybe Yes
[/INDENT]

---

### Post by s9032g@comcast.net on 2016-09-11
How about a clean install? If you have things backed up it's easy.  Occams Razor etc

---


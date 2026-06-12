---
title: "Ubuntu Software Icon"
date: 2016-05-15
forum: General Help
---

### Post by arno48 on 2016-05-15
Hello,
Yesterday I tried to install Synaptic Manager, but after several hours the process was still "pending" and I suspended it.
Today the Software Ubuntu icon doesn't launch Ubuntu software anymore. 
When I click,  the small circle loops a few second then stops and nothing happens.
Thanks for your help.

---

### Post by bapoumba on 2016-05-15
Please post the outputs to :
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
```

---

### Post by arno48 on 2016-05-17
Thanks for your interest,
```
matteo@matteo-desktop:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://it.archive.ubuntu.com/ubuntu/ xenial main restricted
     6    deb-src http://it.archive.ubuntu.com/ubuntu/ xenial main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://it.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
    11    deb-src http://it.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://it.archive.ubuntu.com/ubuntu/ xenial universe
    17    deb-src http://it.archive.ubuntu.com/ubuntu/ xenial universe
    18    deb http://it.archive.ubuntu.com/ubuntu/ xenial-updates universe
    19    deb-src http://it.archive.ubuntu.com/ubuntu/ xenial-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://it.archive.ubuntu.com/ubuntu/ xenial multiverse
    27    deb-src http://it.archive.ubuntu.com/ubuntu/ xenial multiverse
    28    deb http://it.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
    29    deb-src http://it.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://it.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
    37    deb-src http://it.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu xenial-security main restricted
    40    deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
    41    deb http://security.ubuntu.com/ubuntu xenial-security universe
    42    deb-src http://security.ubuntu.com/ubuntu xenial-security universe
    43    deb http://security.ubuntu.com/ubuntu xenial-security multiverse
    44    deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb http://archive.canonical.com/ubuntu oneiric partner
    51    # deb-src http://archive.canonical.com/ubuntu oneiric partner
    52    
matteo@matteo-desktop:~$ ls -la /etc/apt/sources.list.d
total 24
drwxr-xr-x 2 root root 4096 apr 18  2014 .
drwxr-xr-x 6 root root 4096 apr 24  2015 ..
-rw-r--r-- 1 root root   81 apr 25 09:34 oneiric-partner.list
-rw-r--r-- 1 root root   79 apr 25 09:34 oneiric-partner.list.distUpgrade
-rw-r--r-- 1 root root  189 apr 25 09:34 private-ppa.launchpad.net_commercial-ppa-uploaders_aphoto_ubuntu.list
-rw-r--r-- 1 root root  189 apr 25 09:34 private-ppa.launchpad.net_commercial-ppa-uploaders_aphoto_ubuntu.list.distUpgrade
matteo@matteo-desktop:~$ tail -v -n +1 /etc/apt/sources.list.d/*
 
```

---

### Post by bapoumba on 2016-05-17
Hello,

you missed posting the output to the last one :)
You may want to disable that oneiric repository if still active.

And sorry, I just forgot to post two other commands of interest :
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by arno48 on 2016-05-18
[LEFT][COLOR=#000000][FONT=Verdana][SIZE=2]*It’s my first **time **in the Terminal, I’m feeling like a Charle Magne Knight entering a magic forest where he could find either a wonderful pri**n**cess or a deadful dragon.*[/SIZE][/FONT][/COLOR][/LEFT] [LEFT][COLOR=#000000][FONT=Verdana][SIZE=2][I]Merci for a such exciting experience.

Here the third output
[/I][/SIZE][/FONT][/COLOR]
[/LEFT]  
```
matteo@matteo-desktop:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/oneiric-partner.list <==
deb http://archive.canonical.com/ubuntu xenial partner #Added by software-center

==> /etc/apt/sources.list.d/oneiric-partner.list.distUpgrade <==
deb http://archive.canonical.com/ubuntu wily partner #Added by software-center

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_aphoto_ubuntu.list <==
# deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/aphoto/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to trusty

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_aphoto_ubuntu.list.distUpgrade <==
# deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/aphoto/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to trusty
matteo@matteo-desktop:~$ 
 
```

Here below the update
```
 matteo@matteo-desktop:~$ sudo apt-get update
[sudo] password for matteo: 
Hit:1 http://it.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://security.ubuntu.com/ubuntu xenial-security InRelease [93,3 kB]
Get:3 http://it.archive.ubuntu.com/ubuntu xenial-updates InRelease [94,5 kB]   
Hit:4 http://archive.canonical.com/ubuntu xenial InRelease                     
Hit:5 http://it.archive.ubuntu.com/ubuntu xenial-backports InRelease           
Get:6 http://it.archive.ubuntu.com/ubuntu xenial-updates/main Sources [28,9 kB]
Get:7 http://it.archive.ubuntu.com/ubuntu xenial-updates/universe Sources [7.768 B]
Get:8 http://it.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [84,5 kB]
Get:9 http://it.archive.ubuntu.com/ubuntu xenial-updates/main Translation-en [35,3 kB]
Get:10 http://it.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [26,7 kB]
Get:11 http://it.archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en [16,3 kB]
Get:12 http://security.ubuntu.com/ubuntu xenial-security/main Sources [13,9 kB]
Get:13 http://security.ubuntu.com/ubuntu xenial-security/universe Sources [3.176 B]
Get:14 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages [50,0 kB]
Get:15 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en [20,2 kB]
Get:16 http://security.ubuntu.com/ubuntu xenial-security/main i386 DEP-11 Metadata [4.815 B]
Get:17 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [17,1 kB]
Get:18 http://security.ubuntu.com/ubuntu xenial-security/universe i386 Packages [7.656 B]
Get:19 http://security.ubuntu.com/ubuntu xenial-security/universe Translation-en [6.584 B]
Get:20 http://security.ubuntu.com/ubuntu xenial-security/universe i386 DEP-11 Metadata [198 B]
Fetched 511 kB in 1s (330 kB/s)                                  
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done

```

and the upgrade
```
 matteo@matteo-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libcdaudio1 libdirectfb-1.2-9 libslv2-9 linux-image-4.2.0-35-generic
  linux-image-extra-4.2.0-35-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  accountsservice adobe-flash-properties-gtk adobe-flashplugin brltty dpkg
  dpkg-dev file-roller fwupd libaccountsservice0 libarchive13 libbrlapi0.6
  libdfu1 libdpkg-perl libfwupd1 libksba8 libmetacity-private3a libndp0
  libnm-gtk-common libnm-gtk0 libnma-common libnma0 libpam-systemd
  libplymouth4 libsystemd0 libudev1 linux-headers-4.4.0-22
  linux-headers-4.4.0-22-generic linux-image-4.4.0-22-generic
  linux-image-extra-4.4.0-22-generic linux-libc-dev metacity metacity-common
  network-manager-gnome nvidia-common openssh-client plymouth plymouth-label
  plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text python3-brlapi snapd
  ssh-askpass-gnome sudo systemd systemd-sysv thermald ubuntu-drivers-common
  udev xbrlapi
49 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 68,0 MB/92,9 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://it.archive.ubuntu.com/ubuntu xenial-updates/main i386 libksba8 i386 1.3.3-1ubuntu0.16.04.1 [98,7 kB]
Get:2 http://it.archive.ubuntu.com/ubuntu xenial-updates/main i386 accountsservice i386 0.6.40-2ubuntu11.1 [60,9 kB]
Get:3 http://it.archive.ubuntu.com/ubuntu xenial-updates/main i386 libaccountsservice0 i386 0.6.40-2ubuntu11.1 [68,7 kB]
Get:4 http://it.archive.ubuntu.com/ubuntu xenial-updates/main i386 libarchive13 i386 3.1.2-11ubuntu0.16.04.1 [299 kB]
Get:5 http://it.archive.ubuntu.com/ubuntu xenial-updates/main i386 libndp0 i386 1.4-2ubuntu0.16.04.1 [11,0 kB]
Get:6 http://it.archive.ubuntu.com/ubuntu xenial-updates/main i386 linux-headers-4.4.0-22 all 4.4.0-22.40 [9.934 kB]
Get:7 http://it.archive.ubuntu.com/ubuntu xenial-updates/main i386 linux-headers-4.4.0-22-generic i386 4.4.0-22.40 [768 kB]
Get:8 http://it.archive.ubuntu.com/ubuntu xenial-updates/main i386 linux-image-4.4.0-22-generic i386 4.4.0-22.40 [17,4 MB]
Get:9 http://it.archive.ubuntu.com/ubuntu xenial-updates/main i386 linux-image-extra-4.4.0-22-generic i386 4.4.0-22.40 [38,5 MB]
Get:10 http://it.archive.ubuntu.com/ubuntu xenial-updates/main i386 linux-libc-dev i386 4.4.0-22.40 [837 kB]
Fetched 68,0 MB in 32s (2.089 kB/s)                                            
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 327074 files and directories currently installed.)
Preparing to unpack .../dpkg_1.18.4ubuntu1.1_i386.deb ...
Unpacking dpkg (1.18.4ubuntu1.1) over (1.18.4ubuntu1) ...
Setting up dpkg (1.18.4ubuntu1.1) ...
Processing triggers for man-db (2.7.5-1) ...
(Reading database ... 327074 files and directories currently installed.)
Preparing to unpack .../libsystemd0_229-4ubuntu5_i386.deb ...
Unpacking libsystemd0:i386 (229-4ubuntu5) over (229-4ubuntu4) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Setting up libsystemd0:i386 (229-4ubuntu5) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
(Reading database ... 327074 files and directories currently installed.)
Preparing to unpack .../libpam-systemd_229-4ubuntu5_i386.deb ...
Unpacking libpam-systemd:i386 (229-4ubuntu5) over (229-4ubuntu4) ...
Preparing to unpack .../systemd_229-4ubuntu5_i386.deb ...
Unpacking systemd (229-4ubuntu5) over (229-4ubuntu4) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for dbus (1.10.6-1ubuntu3) ...
Setting up systemd (229-4ubuntu5) ...
addgroup: The group `systemd-journal' already exists as a system group. Exiting.
(Reading database ... 327074 files and directories currently installed.)
Preparing to unpack .../brltty_5.3.1-2ubuntu2.1_i386.deb ...
Unpacking brltty (5.3.1-2ubuntu2.1) over (5.3.1-2ubuntu2) ...
Preparing to unpack .../udev_229-4ubuntu5_i386.deb ...
Unpacking udev (229-4ubuntu5) over (229-4ubuntu4) ...
Preparing to unpack .../libudev1_229-4ubuntu5_i386.deb ...
Unpacking libudev1:i386 (229-4ubuntu5) over (229-4ubuntu4) ...
Processing triggers for systemd (229-4ubuntu5) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Setting up libudev1:i386 (229-4ubuntu5) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
(Reading database ... 327076 files and directories currently installed.)
Preparing to unpack .../libbrlapi0.6_5.3.1-2ubuntu2.1_i386.deb ...
Unpacking libbrlapi0.6:i386 (5.3.1-2ubuntu2.1) over (5.3.1-2ubuntu2) ...
Preparing to unpack .../systemd-sysv_229-4ubuntu5_i386.deb ...
Unpacking systemd-sysv (229-4ubuntu5) over (229-4ubuntu4) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up systemd-sysv (229-4ubuntu5) ...
(Reading database ... 327076 files and directories currently installed.)
Preparing to unpack .../ubuntu-drivers-common_1%3a0.4.17.1_i386.deb ...
Unpacking ubuntu-drivers-common (1:0.4.17.1) over (1:0.4.17) ...
Preparing to unpack .../libksba8_1.3.3-1ubuntu0.16.04.1_i386.deb ...
Unpacking libksba8:i386 (1.3.3-1ubuntu0.16.04.1) over (1.3.3-1) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Setting up libksba8:i386 (1.3.3-1ubuntu0.16.04.1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
(Reading database ... 327076 files and directories currently installed.)
Preparing to unpack .../sudo_1.8.16-0ubuntu1.1_i386.deb ...
Unpacking sudo (1.8.16-0ubuntu1.1) over (1.8.16-0ubuntu1) ...
Preparing to unpack .../accountsservice_0.6.40-2ubuntu11.1_i386.deb ...
Unpacking accountsservice (0.6.40-2ubuntu11.1) over (0.6.40-2ubuntu10) ...
Preparing to unpack .../libaccountsservice0_0.6.40-2ubuntu11.1_i386.deb ...
Unpacking libaccountsservice0:i386 (0.6.40-2ubuntu11.1) over (0.6.40-2ubuntu10) ...
Preparing to unpack .../libplymouth4_0.9.2-3ubuntu13.1_i386.deb ...
Unpacking libplymouth4:i386 (0.9.2-3ubuntu13.1) over (0.9.2-3ubuntu13) ...
Preparing to unpack .../openssh-client_1%3a7.2p2-4ubuntu1_i386.deb ...
Unpacking openssh-client (1:7.2p2-4ubuntu1) over (1:7.2p2-4) ...
Preparing to unpack .../plymouth-theme-ubuntu-logo_0.9.2-3ubuntu13.1_i386.deb ...
Unpacking plymouth-theme-ubuntu-logo (0.9.2-3ubuntu13.1) over (0.9.2-3ubuntu13) ...
Preparing to unpack .../plymouth-label_0.9.2-3ubuntu13.1_i386.deb ...
Unpacking plymouth-label (0.9.2-3ubuntu13.1) over (0.9.2-3ubuntu13) ...
Preparing to unpack .../plymouth_0.9.2-3ubuntu13.1_i386.deb ...
Unpacking plymouth (0.9.2-3ubuntu13.1) over (0.9.2-3ubuntu13) ...
Preparing to unpack .../plymouth-theme-ubuntu-text_0.9.2-3ubuntu13.1_i386.deb ...
Unpacking plymouth-theme-ubuntu-text (0.9.2-3ubuntu13.1) over (0.9.2-3ubuntu13) ...
Preparing to unpack .../adobe-flash-properties-gtk_1%3a20160512.1-0ubuntu0.16.04.1_i386.deb ...
Unpacking adobe-flash-properties-gtk (1:20160512.1-0ubuntu0.16.04.1) over (1:20160407.1-0ubuntu1) ...
Preparing to unpack .../adobe-flashplugin_1%3a20160512.1-0ubuntu0.16.04.1_i386.deb ...
Unpacking adobe-flashplugin (1:20160512.1-0ubuntu0.16.04.1) over (1:20160407.1-0ubuntu1) ...
Preparing to unpack .../dpkg-dev_1.18.4ubuntu1.1_all.deb ...
Unpacking dpkg-dev (1.18.4ubuntu1.1) over (1.18.4ubuntu1) ...
Preparing to unpack .../libdpkg-perl_1.18.4ubuntu1.1_all.deb ...
Unpacking libdpkg-perl (1.18.4ubuntu1.1) over (1.18.4ubuntu1) ...
Preparing to unpack .../libarchive13_3.1.2-11ubuntu0.16.04.1_i386.deb ...
Unpacking libarchive13:i386 (3.1.2-11ubuntu0.16.04.1) over (3.1.2-11build1) ...
Preparing to unpack .../file-roller_3.16.5-0ubuntu1_i386.deb ...
Unpacking file-roller (3.16.5-0ubuntu1) over (3.16.4-1ubuntu3) ...
Preparing to unpack .../libdfu1_0.7.0-0ubuntu4.1_i386.deb ...
Unpacking libdfu1:i386 (0.7.0-0ubuntu4.1) over (0.7.0-0ubuntu4) ...
Preparing to unpack .../libfwupd1_0.7.0-0ubuntu4.1_i386.deb ...
Unpacking libfwupd1:i386 (0.7.0-0ubuntu4.1) over (0.7.0-0ubuntu4) ...
Preparing to unpack .../fwupd_0.7.0-0ubuntu4.1_i386.deb ...
Unpacking fwupd (0.7.0-0ubuntu4.1) over (0.7.0-0ubuntu4) ...
Preparing to unpack .../metacity_1%3a3.18.4-0ubuntu0.1_i386.deb ...
Unpacking metacity (1:3.18.4-0ubuntu0.1) over (1:3.18.3-1ubuntu3) ...
Preparing to unpack .../libmetacity-private3a_1%3a3.18.4-0ubuntu0.1_i386.deb ...
Unpacking libmetacity-private3a:i386 (1:3.18.4-0ubuntu0.1) over (1:3.18.3-1ubuntu3) ...
Preparing to unpack .../metacity-common_1%3a3.18.4-0ubuntu0.1_all.deb ...
Unpacking metacity-common (1:3.18.4-0ubuntu0.1) over (1:3.18.3-1ubuntu3) ...
Preparing to unpack .../libndp0_1.4-2ubuntu0.16.04.1_i386.deb ...
Unpacking libndp0:i386 (1.4-2ubuntu0.16.04.1) over (1.4-2) ...
Preparing to unpack .../libnm-gtk0_1.2.0-0ubuntu0.16.04.1_i386.deb ...
Unpacking libnm-gtk0:i386 (1.2.0-0ubuntu0.16.04.1) over (1.1.93-1ubuntu1) ...
Preparing to unpack .../libnm-gtk-common_1.2.0-0ubuntu0.16.04.1_all.deb ...
Unpacking libnm-gtk-common (1.2.0-0ubuntu0.16.04.1) over (1.1.93-1ubuntu1) ...
Preparing to unpack .../network-manager-gnome_1.2.0-0ubuntu0.16.04.1_i386.deb ...
Unpacking network-manager-gnome (1.2.0-0ubuntu0.16.04.1) over (1.1.93-1ubuntu1) ...
Preparing to unpack .../libnma0_1.2.0-0ubuntu0.16.04.1_i386.deb ...
Unpacking libnma0:i386 (1.2.0-0ubuntu0.16.04.1) over (1.1.93-1ubuntu1) ...
Preparing to unpack .../libnma-common_1.2.0-0ubuntu0.16.04.1_all.deb ...
Unpacking libnma-common (1.2.0-0ubuntu0.16.04.1) over (1.1.93-1ubuntu1) ...
Preparing to unpack .../linux-headers-4.4.0-22_4.4.0-22.40_all.deb ...
Unpacking linux-headers-4.4.0-22 (4.4.0-22.40) over (4.4.0-22.39) ...
Preparing to unpack .../linux-headers-4.4.0-22-generic_4.4.0-22.40_i386.deb ...
Unpacking linux-headers-4.4.0-22-generic (4.4.0-22.40) over (4.4.0-22.39) ...
Preparing to unpack .../linux-image-4.4.0-22-generic_4.4.0-22.40_i386.deb ...
Done.
Unpacking linux-image-4.4.0-22-generic (4.4.0-22.40) over (4.4.0-22.39) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
Preparing to unpack .../linux-image-extra-4.4.0-22-generic_4.4.0-22.40_i386.deb ...
Unpacking linux-image-extra-4.4.0-22-generic (4.4.0-22.40) over (4.4.0-22.39) ...
Preparing to unpack .../linux-libc-dev_4.4.0-22.40_i386.deb ...
Unpacking linux-libc-dev:i386 (4.4.0-22.40) over (4.4.0-22.39) ...
Preparing to unpack .../nvidia-common_1%3a0.4.17.1_i386.deb ...
Unpacking nvidia-common (1:0.4.17.1) over (1:0.4.17) ...
Preparing to unpack .../archives/snapd_2.0.3_i386.deb ...
Unpacking snapd (2.0.3) over (2.0.2) ...
Preparing to unpack .../ssh-askpass-gnome_1%3a7.2p2-4ubuntu1_i386.deb ...
Unpacking ssh-askpass-gnome (1:7.2p2-4ubuntu1) over (1:7.2p2-4) ...
Preparing to unpack .../thermald_1.5-2ubuntu1_i386.deb ...
Unpacking thermald (1.5-2ubuntu1) over (1.5-2) ...
Preparing to unpack .../python3-brlapi_5.3.1-2ubuntu2.1_i386.deb ...
Unpacking python3-brlapi (5.3.1-2ubuntu2.1) over (5.3.1-2ubuntu2) ...
Preparing to unpack .../xbrlapi_5.3.1-2ubuntu2.1_i386.deb ...
Unpacking xbrlapi (5.3.1-2ubuntu2.1) over (5.3.1-2ubuntu2) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for dbus (1.10.6-1ubuntu3) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for systemd (229-4ubuntu5) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160415-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for gconf2 (3.2.6-3ubuntu6) ...
Processing triggers for libglib2.0-0:i386 (2.48.0-1ubuntu4) ...
Processing triggers for sgml-base (1.26+nmu4ubuntu1) ...
Setting up libpam-systemd:i386 (229-4ubuntu5) ...
Setting up libbrlapi0.6:i386 (5.3.1-2ubuntu2.1) ...
Setting up brltty (5.3.1-2ubuntu2.1) ...
update-initramfs: deferring update (trigger activated)
Setting up udev (229-4ubuntu5) ...
addgroup: The group `input' already exists as a system group. Exiting.
update-initramfs: deferring update (trigger activated)
Setting up ubuntu-drivers-common (1:0.4.17.1) ...
Setting up sudo (1.8.16-0ubuntu1.1) ...
Setting up libaccountsservice0:i386 (0.6.40-2ubuntu11.1) ...
Setting up accountsservice (0.6.40-2ubuntu11.1) ...
Setting up libplymouth4:i386 (0.9.2-3ubuntu13.1) ...
Setting up openssh-client (1:7.2p2-4ubuntu1) ...
Setting up plymouth (0.9.2-3ubuntu13.1) ...
update-initramfs: deferring update (trigger activated)
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Setting up plymouth-label (0.9.2-3ubuntu13.1) ...
Setting up plymouth-theme-ubuntu-logo (0.9.2-3ubuntu13.1) ...
update-initramfs: deferring update (trigger activated)
Setting up plymouth-theme-ubuntu-text (0.9.2-3ubuntu13.1) ...
update-initramfs: deferring update (trigger activated)
Setting up adobe-flashplugin (1:20160512.1-0ubuntu0.16.04.1) ...
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/mozilla/plugins/flashplugin-alternative.so (mozilla-flashplugin) in auto mode
Setting up adobe-flash-properties-gtk (1:20160512.1-0ubuntu0.16.04.1) ...
Setting up libdpkg-perl (1.18.4ubuntu1.1) ...
Setting up dpkg-dev (1.18.4ubuntu1.1) ...
Setting up libarchive13:i386 (3.1.2-11ubuntu0.16.04.1) ...
Setting up file-roller (3.16.5-0ubuntu1) ...
Setting up libdfu1:i386 (0.7.0-0ubuntu4.1) ...
Setting up libfwupd1:i386 (0.7.0-0ubuntu4.1) ...
Setting up fwupd (0.7.0-0ubuntu4.1) ...
Setting up metacity-common (1:3.18.4-0ubuntu0.1) ...
Setting up libmetacity-private3a:i386 (1:3.18.4-0ubuntu0.1) ...
Setting up metacity (1:3.18.4-0ubuntu0.1) ...
Setting up libndp0:i386 (1.4-2ubuntu0.16.04.1) ...
Setting up libnm-gtk-common (1.2.0-0ubuntu0.16.04.1) ...
Setting up libnm-gtk0:i386 (1.2.0-0ubuntu0.16.04.1) ...
Setting up libnma-common (1.2.0-0ubuntu0.16.04.1) ...
Setting up libnma0:i386 (1.2.0-0ubuntu0.16.04.1) ...
Setting up network-manager-gnome (1.2.0-0ubuntu0.16.04.1) ...
Setting up linux-headers-4.4.0-22 (4.4.0-22.40) ...
Setting up linux-headers-4.4.0-22-generic (4.4.0-22.40) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
Setting up linux-image-4.4.0-22-generic (4.4.0-22.40) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(4.4.0-22.39 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(4.4.0-22.39 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-22-generic
Found initrd image: /boot/initrd.img-4.4.0-22-generic
Found linux image: /boot/vmlinuz-4.4.0-21-generic
Found initrd image: /boot/initrd.img-4.4.0-21-generic
Found linux image: /boot/vmlinuz-4.2.0-35-generic
Found initrd image: /boot/initrd.img-4.2.0-35-generic
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.16.0-34-generic
Found initrd image: /boot/initrd.img-3.16.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.11.0-18-generic
Found initrd image: /boot/initrd.img-3.11.0-18-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.2.0-32-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-32-generic-pae
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-extra-4.4.0-22-generic (4.4.0-22.40) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-22-generic
Found initrd image: /boot/initrd.img-4.4.0-22-generic
Found linux image: /boot/vmlinuz-4.4.0-21-generic
Found initrd image: /boot/initrd.img-4.4.0-21-generic
Found linux image: /boot/vmlinuz-4.2.0-35-generic
Found initrd image: /boot/initrd.img-4.2.0-35-generic
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.16.0-34-generic
Found initrd image: /boot/initrd.img-3.16.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.11.0-18-generic
Found initrd image: /boot/initrd.img-3.11.0-18-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.2.0-32-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-32-generic-pae
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-libc-dev:i386 (4.4.0-22.40) ...
Setting up nvidia-common (1:0.4.17.1) ...
Setting up snapd (2.0.3) ...
Installing new version of config file /etc/profile.d/apps-bin-path.sh ...
Setting up ssh-askpass-gnome (1:7.2p2-4ubuntu1) ...
Setting up thermald (1.5-2ubuntu1) ...
Setting up python3-brlapi (5.3.1-2ubuntu2.1) ...
Setting up xbrlapi (5.3.1-2ubuntu2.1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for initramfs-tools (0.122ubuntu8) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-22-generic
matteo@matteo-desktop:~$ 
 
```

[LEFT] [COLOR=#000000][FONT=Verdana][SIZE=2]*In order to remove o**neiric programs may I use following command?*[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] 
 [/LEFT] [LEFT] [COLOR=#000000][FONT=Verdana][SIZE=2][I]```
sudo apt remove 
[/I][/SIZE][/FONT][/COLOR][/LEFT]-rw-r--r-- 1 root root   81 apr 25 09:34 oneiric-partner.list
-rw-r--r-- 1 root root   79 apr 25 09:34 oneiric-partner.list.distUpgrade[COLOR=#000000][FONT=Verdana][SIZE=2][I] 
```

Do you see other programs to be removed?

Thanks for all. Have a nice day.
[/I][/SIZE][/FONT][/COLOR]

---

### Post by bapoumba on 2016-05-18
No, you have to remove the repositories from the Software Sources. One of them says Oneiric in its title but does point to xenial repos, so that is fine. The second one also has oneiric in the description but points to wily < this last one you have to uncheck. Strange it does not show commented out in your repositories but does not get used in the update.

Looks like you had a few packages to upgrade, that went fine. There is only one thing :
```
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
```
Looks like it should be fixed at some point, may be [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1258597](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1258597)
If your boot process goes through without any issue, I would leave it alone for now unless others have easy steps to guide you through updating the grub config.

Is your Ubuntu Software working better after the update/upgrade cycle ? Some theme files got upgraded. Are you using one of the default themes ? If not, can you try with one of them ?

---

### Post by arno48 on 2016-05-18
Hello,
my GRUB version is the following 
```
 matteo@matteo-desktop:~$ grub-install -V
grub-install (GRUB) 2.02~beta2-36ubuntu3

```
My screen background is the rust default colour. No booting difficulties.

 Following to upgrade to Xenial I noticed two (minor) problems:
1) When I click on icon of the Ubuntu Software Center on Launcher, nothing happens;
2) When in Libre Office Writer and Calc,sometimes the Menu bar (File, Edit, View, etc.) does not appear .
Good Night

---

### Post by bapoumba on 2016-05-19
OK, may be a few things. Please run the following to make sure they are no updates left :
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Once done and everything up to date, please post the output to :
```
software-center
```

---

### Post by arno48 on 2016-05-19
Thanks a lot.
```
matteo@matteo-desktop:~$ sudo apt-get update
[sudo] password for matteo: 
Sorry, try again.
[sudo] password for matteo: 
Ign:1 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric InRelease
Ign:2 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric Release
Ign:3 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main i386 Packages
Ign:4 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main all Packages
Ign:5 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-en_US
Ign:6 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-en
Ign:7 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-it
Ign:8 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main i386 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted i386 Packages
Ign:11 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted all Packages
Ign:12 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-en_US
Ign:13 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-en
Ign:14 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-it
Ign:15 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted i386 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main i386 Packages
Ign:4 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main all Packages
Ign:5 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-en_US
Ign:6 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-en
Ign:7 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-it
Ign:8 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main i386 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted i386 Packages
Ign:11 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted all Packages
Ign:12 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-en_US
Ign:13 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-en
Ign:14 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-it
Ign:15 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted i386 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main i386 Packages
Ign:4 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main all Packages
Ign:5 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-en_US
Ign:6 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-en
Ign:7 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-it
Ign:8 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main i386 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted i386 Packages
Ign:11 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted all Packages
Ign:12 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-en_US
Ign:13 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-en
Ign:14 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-it
Ign:15 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted i386 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main i386 Packages
Ign:4 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main all Packages
Ign:5 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-en_US
Ign:6 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-en
Ign:7 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-it
Ign:8 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main i386 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted i386 Packages
Ign:11 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted all Packages
Ign:12 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-en_US
Ign:13 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-en
Ign:14 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-it
Ign:15 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted i386 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main i386 Packages
Ign:4 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main all Packages
Ign:5 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-en_US
Ign:6 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-en
Ign:7 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-it
Ign:8 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main i386 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted i386 Packages
Ign:11 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted all Packages
Ign:12 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-en_US
Ign:13 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-en
Ign:14 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-it
Ign:15 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted i386 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted DEP-11 64x64 Icons
Err:3 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign:4 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main all Packages
Hit:17 http://it.archive.ubuntu.com/ubuntu xenial InRelease
Get:18 http://it.archive.ubuntu.com/ubuntu xenial-updates InRelease [94,5 kB]  
Hit:19 http://it.archive.ubuntu.com/ubuntu xenial-backports InRelease          
Get:20 http://security.ubuntu.com/ubuntu xenial-security InRelease [93,3 kB]
Get:21 http://it.archive.ubuntu.com/ubuntu xenial-updates/main Sources [29,5 kB]
Get:22 http://it.archive.ubuntu.com/ubuntu xenial-updates/universe Sources [9.536 B]
Get:23 http://it.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [85,4 kB]
Get:24 http://it.archive.ubuntu.com/ubuntu xenial-updates/main Translation-en [35,8 kB]
Get:25 http://it.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [29,3 kB]
Get:26 http://it.archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en [17,7 kB]
Get:27 http://security.ubuntu.com/ubuntu xenial-security/main Sources [14,4 kB]
Get:28 http://security.ubuntu.com/ubuntu xenial-security/universe Sources [3.880 B]
Get:29 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages [50,7 kB]
Get:30 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en [20,6 kB]
Get:31 http://security.ubuntu.com/ubuntu xenial-security/main i386 DEP-11 Metadata [4.819 B]
Get:32 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [17,1 kB]
Get:33 http://security.ubuntu.com/ubuntu xenial-security/universe i386 Packages [9.712 B]
Get:34 http://security.ubuntu.com/ubuntu xenial-security/universe Translation-en [7.468 B]
Get:35 http://security.ubuntu.com/ubuntu xenial-security/universe i386 DEP-11 Metadata [198 B]
Fetched 524 kB in 1s (367 kB/s)                                    
Reading package lists... Done
W: The repository 'cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
E: Some index files failed to download. They have been ignored, or old ones used instead.
matteo@matteo-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libcdaudio1 libdirectfb-1.2-9 libslv2-9 linux-image-4.2.0-35-generic linux-image-extra-4.2.0-35-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  firefox firefox-globalmenu firefox-locale-en firefox-locale-it libexpat1 liboxideqt-qmlplugin
  liboxideqtcore0 liboxideqtquick0 oxideqt-codecs thunderbird thunderbird-gnome-support
11 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 115 MB of archives.
After this operation, 193 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://it.archive.ubuntu.com/ubuntu xenial-updates/main i386 libexpat1 i386 2.1.0-7ubuntu0.16.04.1 [74,7 kB]
Get:2 http://it.archive.ubuntu.com/ubuntu xenial-updates/main i386 firefox i386 46.0.1+build1-0ubuntu0.16.04.2 [46,6 MB]
Get:3 http://it.archive.ubuntu.com/ubuntu xenial-updates/universe i386 firefox-globalmenu i386 46.0.1+build1-0ubuntu0.16.04.2 [8.320 B]
Get:4 http://it.archive.ubuntu.com/ubuntu xenial-updates/main i386 firefox-locale-en i386 46.0.1+build1-0ubuntu0.16.04.2 [595 kB]
Get:5 http://it.archive.ubuntu.com/ubuntu xenial-updates/main i386 firefox-locale-it i386 46.0.1+build1-0ubuntu0.16.04.2 [316 kB]
Get:6 http://it.archive.ubuntu.com/ubuntu xenial-updates/main i386 thunderbird i386 1:38.8.0+build1-0ubuntu0.16.04.1 [35,0 MB]
Get:7 http://it.archive.ubuntu.com/ubuntu xenial-updates/main i386 thunderbird-gnome-support i386 1:38.8.0+build1-0ubuntu0.16.04.1 [8.544 B]
Get:8 http://it.archive.ubuntu.com/ubuntu xenial-updates/main i386 liboxideqt-qmlplugin i386 1.14.9-0ubuntu0.16.04.1 [171 kB]
Get:9 http://it.archive.ubuntu.com/ubuntu xenial-updates/main i386 liboxideqtquick0 i386 1.14.9-0ubuntu0.16.04.1 [272 kB]
Get:10 http://it.archive.ubuntu.com/ubuntu xenial-updates/main i386 liboxideqtcore0 i386 1.14.9-0ubuntu0.16.04.1 [31,3 MB]
Get:11 http://it.archive.ubuntu.com/ubuntu xenial-updates/main i386 oxideqt-codecs i386 1.14.9-0ubuntu0.16.04.1 [573 kB]
Fetched 115 MB in 54s (2.095 kB/s)                                                                             
(Reading database ... 327074 files and directories currently installed.)
Preparing to unpack .../libexpat1_2.1.0-7ubuntu0.16.04.1_i386.deb ...
Unpacking libexpat1:i386 (2.1.0-7ubuntu0.16.04.1) over (2.1.0-7) ...
Preparing to unpack .../firefox_46.0.1+build1-0ubuntu0.16.04.2_i386.deb ...
Unpacking firefox (46.0.1+build1-0ubuntu0.16.04.2) over (46.0+build5-0ubuntu0.16.04.2) ...
Preparing to unpack .../firefox-globalmenu_46.0.1+build1-0ubuntu0.16.04.2_i386.deb ...
Unpacking firefox-globalmenu (46.0.1+build1-0ubuntu0.16.04.2) over (46.0+build5-0ubuntu0.16.04.2) ...
Preparing to unpack .../firefox-locale-en_46.0.1+build1-0ubuntu0.16.04.2_i386.deb ...
Unpacking firefox-locale-en (46.0.1+build1-0ubuntu0.16.04.2) over (46.0+build5-0ubuntu0.16.04.2) ...
Preparing to unpack .../firefox-locale-it_46.0.1+build1-0ubuntu0.16.04.2_i386.deb ...
Unpacking firefox-locale-it (46.0.1+build1-0ubuntu0.16.04.2) over (46.0+build5-0ubuntu0.16.04.2) ...
Preparing to unpack .../thunderbird_1%3a38.8.0+build1-0ubuntu0.16.04.1_i386.deb ...
Unpacking thunderbird (1:38.8.0+build1-0ubuntu0.16.04.1) over (1:38.7.2+build1-0ubuntu0.16.04.1) ...
Preparing to unpack .../thunderbird-gnome-support_1%3a38.8.0+build1-0ubuntu0.16.04.1_i386.deb ...
Unpacking thunderbird-gnome-support (1:38.8.0+build1-0ubuntu0.16.04.1) over (1:38.7.2+build1-0ubuntu0.16.04.1) ...
Preparing to unpack .../liboxideqt-qmlplugin_1.14.9-0ubuntu0.16.04.1_i386.deb ...
Unpacking liboxideqt-qmlplugin:i386 (1.14.9-0ubuntu0.16.04.1) over (1.14.7-0ubuntu1) ...
Preparing to unpack .../liboxideqtquick0_1.14.9-0ubuntu0.16.04.1_i386.deb ...
Unpacking liboxideqtquick0:i386 (1.14.9-0ubuntu0.16.04.1) over (1.14.7-0ubuntu1) ...
Preparing to unpack .../liboxideqtcore0_1.14.9-0ubuntu0.16.04.1_i386.deb ...
Unpacking liboxideqtcore0:i386 (1.14.9-0ubuntu0.16.04.1) over (1.14.7-0ubuntu1) ...
Preparing to unpack .../oxideqt-codecs_1.14.9-0ubuntu0.16.04.1_i386.deb ...
Unpacking oxideqt-codecs:i386 (1.14.9-0ubuntu0.16.04.1) over (1.14.7-0ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160415-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up libexpat1:i386 (2.1.0-7ubuntu0.16.04.1) ...
Setting up firefox (46.0.1+build1-0ubuntu0.16.04.2) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (46.0.1+build1-0ubuntu0.16.04.2) ...
Setting up firefox-locale-en (46.0.1+build1-0ubuntu0.16.04.2) ...
Setting up firefox-locale-it (46.0.1+build1-0ubuntu0.16.04.2) ...
Setting up thunderbird (1:38.8.0+build1-0ubuntu0.16.04.1) ...
Setting up thunderbird-gnome-support (1:38.8.0+build1-0ubuntu0.16.04.1) ...
Setting up oxideqt-codecs:i386 (1.14.9-0ubuntu0.16.04.1) ...
Setting up liboxideqtcore0:i386 (1.14.9-0ubuntu0.16.04.1) ...
Setting up liboxideqtquick0:i386 (1.14.9-0ubuntu0.16.04.1) ...
Setting up liboxideqt-qmlplugin:i386 (1.14.9-0ubuntu0.16.04.1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
matteo@matteo-desktop:~$ sudo apt-get dist-upgrade
[sudo] password for matteo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libcdaudio1 libdirectfb-1.2-9 libslv2-9 linux-image-4.2.0-35-generic linux-image-extra-4.2.0-35-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
matteo@matteo-desktop:~$ 
```
Booting is longer than when 15.10 was running. Today it took 2'09" (From my pressing the start button to the screen theme appearing)

```
matteo@matteo-desktop:~$ software-center
Gtk-Message: Failed to load module "gtk-vector-screenshot"
/usr/bin/software-center:25: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, GObject
/usr/share/software-center/softwarecenter/ui/gtk3/views/purchaseview.py:29: PyGIWarning: WebKit2 was imported without specifying a version first. Use gi.require_version('WebKit2', '4.0') before import to ensure that the right version gets loaded.
  from gi.repository import WebKit2 as webkit
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/symbolic_icons.py:23: PyGIWarning: PangoCairo was imported without specifying a version first. Use gi.require_version('PangoCairo', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, Gdk, GLib, PangoCairo
2016-05-19 16:01:26,259 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2016-05-19 16:01:31,347 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.Geoclue.Error.notAvailable: Geoclue master client has no usable Address providers'
2016-05-19 16:01:32,535 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2016-05-19 16:01:32,557 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2016-05-19 16:01:32,695 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2016-05-19 16:01:33,520 - softwarecenter.db.update - WARNING - failed to load file /var/lib/apt-xapian-index/cataloged_times.p: unsupported pickle protocol: 3
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/videoplayer.py:29: PyGIWarning: Gst was imported without specifying a version first. Use gi.require_version('Gst', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gst
Gtk-Message: Failed to load module "gtk-vector-screenshot"
/usr/bin/software-center:184: Warning: Source ID 78 was not found when attempting to remove it
  Gtk.main()
/usr/bin/software-center:184: Warning: Source ID 150 was not found when attempting to remove it
  Gtk.main()
2016-05-19 16:01:38,284 - softwarecenter.db.update - WARNING - failed to load file /var/lib/apt-xapian-index/cataloged_times.p: unsupported pickle protocol: 3
2016-05-19 16:01:40,616 - softwarecenter.backend.spawn_helper - WARNING - exit code 1 from helper for '['/usr/share/software-center/piston_generic_helper.py', '--datadir', '/usr/share/software-center/', '--needs-auth', '--no-relogin', 'SoftwareCenterAgentAPI', 'subscriptions_for_me', '{"complete_only": true}']'
2016-05-19 16:01:40,617 - softwarecenter.backend.spawn_helper - WARNING - got error from helper: 'ERROR:softwarecenter.backend.ubuntusso:api.whoami failed with APIError: '401: {'status': '401', 'x-request-id': 'Vz3HN38AAQEAAAJIIewAAABA1', 'x-xss-protection': '1; mode=block', 'x-content-type-options': 'nosniff', 'content-language': 'en', 'transfer-encoding': 'chunked', 'strict-transport-security': 'max-age=15768000; includeSubDomains; preload', 'vary': 'Authorization,Accept-Language,Cookie', 'server': 'gunicorn/19.3.0', 'x-bzr-revision-number': '1465', 'date': 'Thu, 19 May 2016 14:01:27 GMT', 'x-frame-options': 'SAMEORIGIN', 'content-type': 'text/html; charset=utf-8', 'www-authenticate': 'OAuth realm="Ubuntu Single Sign On API"'}'
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/backend/ubuntusso.py", line 121, in verify_token_sync
    res = api.whoami()
  File "/usr/lib/python2.7/dist-packages/piston_mini_client/validators.py", line 120, in wrapper
    return func(self, *args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/piston_mini_client/__init__.py", line 131, in wrapper
    body = func(*args, **kwargs)
  File "/usr/share/software-center/softwarecenter/backend/piston/ubuntusso_pristine.py", line 22, in whoami
    scheme=AUTHENTICATED_API_SCHEME)
  File "/usr/lib/python2.7/dist-packages/piston_mini_client/__init__.py", line 787, in _get
    extra_headers=extra_headers)
  File "/usr/lib/python2.7/dist-packages/piston_mini_client/__init__.py", line 491, in get
    return self.request_url(url, method='GET', headers=headers)
  File "/usr/lib/python2.7/dist-packages/piston_mini_client/__init__.py", line 435, in request_url
    body = handler.handle(response, response_body)
  File "/usr/lib/python2.7/dist-packages/piston_mini_client/failhandlers.py", line 116, in handle
    data=self.data)
APIError: 401: {'status': '401', 'x-request-id': 'Vz3HN38AAQEAAAJIIewAAABA1', 'x-xss-protection': '1; mode=block', 'x-content-type-options': 'nosniff', 'content-language': 'en', 'transfer-encoding': 'chunked', 'strict-transport-security': 'max-age=15768000; includeSubDomains; preload', 'vary': 'Authorization,Accept-Language,Cookie', 'server': 'gunicorn/19.3.0', 'x-bzr-revision-number': '1465', 'date': 'Thu, 19 May 2016 14:01:27 GMT', 'x-frame-options': 'SAMEORIGIN', 'content-type': 'text/html; charset=utf-8', 'www-authenticate': 'OAuth realm="Ubuntu Single Sign On API"'}
ERROR: can not obtain a oauth token
'
2016-05-19 16:01:40,617 - softwarecenter.db.update - WARNING - update_from_software_center_agent: error: 'ERROR:softwarecenter.backend.ubuntusso:api.whoami failed with APIError: \'401: {\'status\': \'401\', \'x-request-id\': \'Vz3HN38AAQEAAAJIIewAAABA1\', \'x-xss-protection\': \'1; mode=block\', \'x-content-type-options\': \'nosniff\', \'content-language\': \'en\', \'transfer-encoding\': \'chunked\', \'strict-transport-security\': \'max-age=15768000; includeSubDomains; preload\', \'vary\': \'Authorization,Accept-Language,Cookie\', \'server\': \'gunicorn/19.3.0\', \'x-bzr-revision-number\': \'1465\', \'date\': \'Thu, 19 May 2016 14:01:27 GMT\', \'x-frame-options\': \'SAMEORIGIN\', \'content-type\': \'text/html; charset=utf-8\', \'www-authenticate\': \'OAuth realm="Ubuntu Single Sign On API"\'}\'\nTraceback (most recent call last):\n  File "/usr/share/software-center/softwarecenter/backend/ubuntusso.py", line 121, in verify_token_sync\n    res = api.whoami()\n  File "/usr/lib/python2.7/dist-packages/piston_mini_client/validators.py", line 120, in wrapper\n    return func(self, *args, **kwargs)\n  File "/usr/lib/python2.7/dist-packages/piston_mini_client/__init__.py", line 131, in wrapper\n    body = func(*args, **kwargs)\n  File "/usr/share/software-center/softwarecenter/backend/piston/ubuntusso_pristine.py", line 22, in whoami\n    scheme=AUTHENTICATED_API_SCHEME)\n  File "/usr/lib/python2.7/dist-packages/piston_mini_client/__init__.py", line 787, in _get\n    extra_headers=extra_headers)\n  File "/usr/lib/python2.7/dist-packages/piston_mini_client/__init__.py", line 491, in get\n    return self.request_url(url, method=\'GET\', headers=headers)\n  File "/usr/lib/python2.7/dist-packages/piston_mini_client/__init__.py", line 435, in request_url\n    body = handler.handle(response, response_body)\n  File "/usr/lib/python2.7/dist-packages/piston_mini_client/failhandlers.py", line 116, in handle\n    data=self.data)\nAPIError: 401: {\'status\': \'401\', \'x-request-id\': \'Vz3HN38AAQEAAAJIIewAAABA1\', \'x-xss-protection\': \'1; mode=block\', \'x-content-type-options\': \'nosniff\', \'content-language\': \'en\', \'transfer-encoding\': \'chunked\', \'strict-transport-security\': \'max-age=15768000; includeSubDomains; preload\', \'vary\': \'Authorization,Accept-Language,Cookie\', \'server\': \'gunicorn/19.3.0\', \'x-bzr-revision-number\': \'1465\', \'date\': \'Thu, 19 May 2016 14:01:27 GMT\', \'x-frame-options\': \'SAMEORIGIN\', \'content-type\': \'text/html; charset=utf-8\', \'www-authenticate\': \'OAuth realm="Ubuntu Single Sign On API"\'}\nERROR: can not obtain a oauth token\n'
/usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:573: Warning: Source ID 20 was not found when attempting to remove it
  super(MainLoop, self).run()
2016-05-19 16:01:41,333 - softwarecenter.db.utils - INFO - software-center-agent finished with status 0


``` 

The output of the Command       	 	 	 	   [COLOR=#0000ff]sudo apt-get update[/COLOR]  of my previous post   shows several lines referring to Oneiric Ocelot, i.e. the version 11.10, probabily  the first Ubuntu version I runned.

No, I gave you a wrong information. My first version was 11.04.

---

### Post by bapoumba on 2016-05-20
Thanks. I'm not ignoring you, i'll come back to this later as I do not have time to search around for now. Do you have another user on this machine (always a good idea to have a second user with root privileges in case your main user goes a bit strange) and if so, do you see the same behavior ?

---

### Post by arno48 on 2016-05-20
[LEFT][COLOR=#800000]*[COLOR=#000000][FONT=Verdana][SIZE=2]Please do not excuse. You are a fr[/SIZE][/FONT][/COLOR]**[COLOR=#000000][FONT=Verdana][SIZE=2]i[/SIZE][/FONT][/COLOR]**[COLOR=#000000][FONT=Verdana][SIZE=2]endly and wonderfully helpful person.[/SIZE][/FONT][/COLOR]*[/COLOR][/LEFT] [LEFT][COLOR=#800000]*[COLOR=#000000][FONT=Verdana][SIZE=2]No, I&#8217;m the only user of this desktop.[/SIZE][/FONT][/COLOR]*[/COLOR][/LEFT] [LEFT][COLOR=#800000]*[COLOR=#000000][FONT=Verdana][SIZE=2]A strange thing: Suddendly Menu bar appears aga[/SIZE][/FONT][/COLOR]**[COLOR=#000000][FONT=Verdana][SIZE=2]i[/SIZE][/FONT][/COLOR]**[COLOR=#000000][FONT=Verdana][SIZE=2]n [/SIZE][/FONT][/COLOR]**[COLOR=#000000][FONT=Verdana][SIZE=2]both on[/SIZE][/FONT][/COLOR]**[COLOR=#000000][FONT=Verdana][SIZE=2] Writer and on Calc.[/SIZE][/FONT][/COLOR]*[/COLOR]
[/LEFT] [LEFT][COLOR=#800000]*[COLOR=#000000][FONT=Verdana][SIZE=2]By &#8220;Search Your Computer&#8221; icon I lauched &#8220;Ubuntu Software Center&#8221; and locked the icon to [/SIZE][/FONT][/COLOR]**[COLOR=#000000][FONT=Verdana][SIZE=2]the [/SIZE][/FONT][/COLOR]**[COLOR=#000000][FONT=Verdana][SIZE=2]Laucher. Th[/SIZE][/FONT][/COLOR]**[COLOR=#000000][FONT=Verdana][SIZE=2]e[/SIZE][/FONT][/COLOR]**[COLOR=#000000][FONT=Verdana][SIZE=2] new icon is working perfectely [/SIZE][/FONT][/COLOR]**[COLOR=#000000][FONT=Verdana][SIZE=2]now[/SIZE][/FONT][/COLOR]**[COLOR=#000000][FONT=Verdana][SIZE=2].[/SIZE][/FONT][/COLOR]*[/COLOR][/LEFT] [LEFT][COLOR=#800000]*[COLOR=#000000][FONT=Verdana][SIZE=2]My issues are therefore solved.[/SIZE][/FONT][/COLOR]*[/COLOR][/LEFT] [LEFT][COLOR=#800000]*[COLOR=#000000][FONT=Verdana][SIZE=2]A last suggestion if I can go on asking you.[/SIZE][/FONT][/COLOR]*[/COLOR][/LEFT] [LEFT][COLOR=#800000]*[COLOR=#000000][FONT=Verdana][SIZE=2]A[/SIZE][/FONT][/COLOR]**[COLOR=#000000][FONT=Verdana][SIZE=2]s per my post # [/SIZE][/FONT][/COLOR]**[COLOR=#000000][FONT=Verdana][SIZE=2]9[/SIZE][/FONT][/COLOR]**[COLOR=#000000][FONT=Verdana][SIZE=2]  there are a lot of Oneiric Ocelot [/SIZE][/FONT][/COLOR]**[COLOR=#000000][FONT=Verdana][SIZE=2]lines probably due to a mistake of mine when 11.10 version was update to 12.4 one, [/SIZE][/FONT][/COLOR]*[/COLOR] [/LEFT] [LEFT][COLOR=#800000]*[COLOR=#000000][FONT=Verdana][SIZE=2]is there a sure way to remove them or [/SIZE][/FONT][/COLOR]**[COLOR=#000000][FONT=Verdana][SIZE=2]it [/SIZE][/FONT][/COLOR]**[COLOR=#000000][FONT=Verdana][SIZE=2]is better to leave them?[/SIZE][/FONT][/COLOR]*[/COLOR][/LEFT] [LEFT][COLOR=#800000]*[COLOR=#000000][FONT=Verdana][SIZE=2]Thanks a lot for a[/SIZE][/FONT][/COLOR]**[COLOR=#000000][FONT=Verdana][SIZE=2]ll[/SIZE][/FONT][/COLOR]**[COLOR=#000000][FONT=Verdana][SIZE=2] [/SIZE][/FONT][/COLOR]*[/COLOR] [/LEFT]

---

### Post by bapoumba on 2016-05-20
OK, for the oneiric error lines :
```
Ign:1 cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric InRelease
```
Is a bit strange as your oneiric cdrom (from which I suppose you first installed Ubuntu on this machine) is disabled here, as there is a "#" at the beginning of the line :
```
 1    # deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted
```

Please have a look at Software Sources and make sure the Oneiric CDROM is unchecked. When you are there, have a look at any third party repositories that you would not recognize or are not set up for xenial and uncheck them. Once done, hit the reload button and run the update/upgrade commands again.

Just to make sure, please post the output to 
```
apt-cache policy ubuntu-desktop
```

I did look about a bit and I do not have software-center installed here (fresh 16.04 install), so I looked a bit further and looks like it's been replaced with gnome-software.
So what does 
```
gnome-software
```
return ?
Not using Ubuntu but a flavor, I do not have it installed either :)

---

### Post by arno48 on 2016-05-22
Hello, Thanks for your Post.
Herebelow the screenshot of my Software & Updates [IMG]/home/matteo/Screenshot from 2016-05-22 14-05-46.png[/IMG]
the origin is probably explained in[COLOR=#800000]**  Ubuntu software search ** [/COLOR]where searching for Oneiric Ocelot the answer is
 >    	 	 	 	   [COLOR=#800000]ubuntu-wallpapers-oneiric[/COLOR] 	
 	 	[COLOR=#800000]Version: ubuntu-wallpapers-oneiric 	16.04.1-0ubuntu1[/COLOR] 	[COLOR=#800000]Wallpapers  from the Ubuntu 11.10 community 	contest[/COLOR]  

I'm leaving now and until Thursday I'll have no internet connection.
As soon as back home I'll clean my desktop as per your above commands and send you the results.


P.S. Today Writer and Calc Menu Bar disappeared again. May it be a Ubuntu 16.04 bug?
Enjoy a nice week

---

### Post by bapoumba on 2016-05-22
Take your time and have a nice week too :)

I think it has more to do with a failed complete upgrade to 16.04 than anything else.

---

### Post by arno48 on 2016-05-26
[SIZE=3][COLOR=#800000][FONT=Times New Roman][COLOR=#000000]Back home I am glad to resume our writing.
I hope you enjoyed good days.
[/COLOR][/FONT][/COLOR]

 [COLOR=#800000][FONT=Times New Roman][COLOR=#000000]I unchecked  Cdrom with Ubuntu 11.10   &#8216;Oneiric Ocelot&#8217;  which was the only one checked of  the  &#8220;Other Software&#8221;. (Please see the attachment)
[/COLOR][B][COLOR=#000000]
 [/COLOR][/B][COLOR=#000000]Then [/COLOR][/FONT][/COLOR][COLOR=#800000][FONT=Times New Roman][COLOR=#000000]I hit the CLOSE button (is this the reload button you asked for?), then[/COLOR][B][COLOR=#000000]
[/COLOR][/B][/FONT][/COLOR][/SIZE]```

[SIZE=3][COLOR=#800000][FONT=Times New Roman][COLOR=#000000]sudo apt-get update[/COLOR][/FONT][/COLOR]
sudo apt-get upgrade
[COLOR=#800000][FONT=Times New Roman][COLOR=#000000]sudo apt-get dist-upgrade
[/COLOR][/FONT][/COLOR][COLOR=#800000][FONT=Times New Roman][COLOR=#000000]apt-cache policy ubuntu-desktop[/COLOR][/FONT][/COLOR]
``` 


[COLOR=#800000][FONT=Times New Roman][COLOR=#000000]The return is the following:[/COLOR][/FONT][/COLOR][/SIZE]
```
matteo@matteo-desktop:~$ apt-cache policy ubuntu-desktop
ubuntu-desktop:
  Installed: 1.361
  Candidate: 1.361
  Version table:
 *** 1.361 500
        500 http://it.archive.ubuntu.com/ubuntu xenial/main i386 Packages
        100 /var/lib/dpkg/status
matteo@matteo-desktop:~$ gnome-software
Gtk-Message: Failed to load module "gtk-vector-screenshot"

(gnome-software:19572): Gs-WARNING **: failed to open plugin /usr/lib/gs-plugins-9/libgs_plugin_xdg_app_reviews.so: /usr/lib/gs-plugins-9/libgs_plugin_xdg_app_reviews.so: cannot open shared object file: No such file or directory

```
[B][COLOR=#800000][FONT=Times New Roman][SIZE=4][COLOR=#000000]
[/COLOR][/SIZE][/FONT][/COLOR][/B][SIZE=3][COLOR=#800000][FONT=Times New Roman][COLOR=#000000]as far as the command[/COLOR][/FONT][/COLOR][/SIZE]**[COLOR=#800000][FONT=Times New Roman][SIZE=4][COLOR=#000000][/COLOR][/SIZE][/FONT][/COLOR]**
```
[SIZE=3][COLOR=#800000][FONT=Times New Roman][COLOR=#000000]gnome-software[/COLOR][/FONT][/COLOR][/SIZE]
```

[SIZE=3][COLOR=#800000][FONT=Times New Roman][COLOR=#000000]did I make any error?[/COLOR][/FONT][/COLOR]
[COLOR=#800000][FONT=Times New Roman][COLOR=#000000]Thanks for your kind interest. I hope my questions are not boring you too much.[/COLOR][/FONT][/COLOR][/SIZE]

---


---
title: "[SOLVED] Impossible to reinstall gimp"
date: 2014-06-17
forum: General Help
---

### Post by Raphael_Poli on 2014-06-17
Hello I installed Ubuntu 14.04 recently and many problems occur since then. Now the biggest one is that gimp cannot be reinstalled after trying to fix it by uninstalling/reinstalling. Is that a problem with gimp? or a bug from my system?
thanks!

apt-get install gimp gives that error message: 

Package gimp is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  gimp-data

---

### Post by claracc on 2014-06-17
As far as I know, you have to install gimp from a ppa, please read: [http://howtoubuntu.org/things-to-do-after-installing-ubuntu-14-04-trusty-tahr](http://howtoubuntu.org/things-to-do-after-installing-ubuntu-14-04-trusty-tahr) there is a specific input for gimp software or you can try the otto's ppa for gimp: [https://launchpad.net/~otto-kesselgulasch/+archive/gimp?field.series_filter=trusty](https://launchpad.net/~otto-kesselgulasch/+archive/gimp?field.series_filter=trusty)

---

### Post by slickymaster on 2014-06-17
Can you try the following in a terminal window:```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update
sudo apt-get install gimp
```

---

### Post by Raphael_Poli on 2014-06-17
I executed" ```
sudo add-apt-repository -y ppa:otto-kesselgulasch/gimp"
``` without error message but I don't understand what it did. it did not install gimp anyway. the ubuntu software center finds gimp, but when I click "more info" it says " There isn&#8217;t a software package called &#8220;gimp&#8221; in your current software sources."
PPA is a new software repository?

---

### Post by Raphael_Poli on 2014-06-17
@slickymaster 
I did what you gave me, but "install gimp" gives an error message:
```

The following packages have unmet dependencies:
 gimp : Depends: libbabl-0.1-0 (>= 0.1.10) but it is not installable
        Depends: libgegl-0.2-0 (>= 0.2.0) but it is not installable
        Depends: libmng1 (>= 1.0.10) but it is not installable
        Depends: libwebkitgtk-1.0-0 (>= 1.3.10) but it is not installable
E: Unable to correct problems, you have held broken packages.
```

---

### Post by lisati on 2014-06-17
> **Raphael_Poli said:**
> I executed" sudo add-apt-repository -y ppa:otto-kesselgulasch/gimp" without error message but I don't understand what it did. it did not install gimp anyway. the ubuntu software center finds gimp, but when I click "more info" it says " There isn&#8217;t a software package called &#8220;gimp&#8221; in your current software sources."
PPA is a new software repository?

*sudo add-apt-repository* tells the software centre about another place to look for software, but you need to run *sudo apt-get update* before the change takes full effect.

[s]Did you get any error messages at all when you ran the commands, one at a time, that slickymaster suggested?[/s]

Edit: Ah, I see you got error messages...... :D

---

### Post by slickymaster on 2014-06-17
The acrynom PPA stands for Personal Package Archives.

You have to run, one at a time, all three commands I posted, not just the first.

Basically this is what they do:```
**sudo add-apt-repository ppa:otto-kesselgulasch/gimp** ### You're adding a Launchpad PPA Repository. Your system will fetch the PPA's key. This enables your Ubuntu system to verify that the packages in the PPA have not been interfered with since they were built.
**sudo apt-get update** ### You're telling your system to pull down the latest list of software from each archive it knows about, including the PPA you just added.
**sudo apt-get install gimp** ### You're installing the software from the PPA.
```

---

### Post by slickymaster on 2014-06-17
> **Raphael_Poli said:**
> @slickymaster 
I did what you gave me, but "install gimp" gives an error message:
```

The following packages have unmet dependencies:
 gimp : Depends: libbabl-0.1-0 (>= 0.1.10) but it is not installable
        Depends: libgegl-0.2-0 (>= 0.2.0) but it is not installable
        Depends: libmng1 (>= 1.0.10) but it is not installable
        Depends: libwebkitgtk-1.0-0 (>= 1.3.10) but it is not installable
E: Unable to correct problems, you have held broken packages.
```

Can you please run in a terminal```
sud apt-get autoremove && sudo apt-get autoclean
sudo dpkg --configure -a 
```
Post back here the results you get, please.

---

### Post by Raphael_Poli on 2014-06-17
Yes thanks for explanation slickymaster, I saw your post after I replied to claracc.
now I have another error (see above)

---

### Post by Raphael_Poli on 2014-06-17
This is the return for "autoclean"
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del libwebkitgtk-1.0-0 2.4.2-1ubuntu0.1 [6 471 kB]
Del libgirepository-1.0-1 1.40.0-1ubuntu0.1 [85,5 kB]
Del python3-apport 2.14.1-0ubuntu3.2 [75,0 kB]
Del libxml2 2.9.1+dfsg1-3ubuntu4.2 [555 kB]
Del libjavascriptcoregtk-3.0-0 2.4.2-1ubuntu0.1 [1 820 kB]
Del thunderbird-locale-en-us 1:24.5.0+build1-0ubuntu0.14.04.1 [11,4 kB]
Del libgnutls26 2.12.23-12ubuntu2.1 [393 kB]
Del libglapi-mesa 10.1.0-4ubuntu5 [21,4 kB]
Del libkrosscore4 4:4.13.0-0ubuntu1 [55,8 kB]
Del gstreamer1.0-plugins-base 1.2.4-1~ubuntu1 [485 kB]
Del libdpkg-perl 1.17.5ubuntu5.2 [179 kB]
Del python3-update-manager 1:0.196.12 [31,5 kB]
Del cups-filters 1.0.52-0ubuntu1.1 [436 kB]
Del libnm-gtk-common 0.9.8.8-0ubuntu4.1 [5 474 B]
Del qtdeclarative5-ubuntu-ui-extras-browser-plugin 0.23+14.04.20140428-0ubuntu1 [20,5 kB]
Del libqt5quick5 5.2.1-3ubuntu15.1 [981 kB]
Del linux-headers-3.13.0-27-generic 3.13.0-27.50 [700 kB]
Del patch 2.7.1-4ubuntu1 [84,4 kB]
Del libosmesa6 10.1.3-0ubuntu0.1 [989 kB]
Del libosmesa6 10.1.0-4ubuntu5 [986 kB]
Del libkio5 4:4.13.0-0ubuntu1.1 [826 kB]
Del libknewstuff3-4 4:4.13.0-0ubuntu1 [150 kB]
Del samba 2:4.1.6+dfsg-1ubuntu2.14.04.1 [839 kB]
Del libudev1 204-5ubuntu20.2 [33,3 kB]
Del libwebkitgtk-3.0-0 2.4.2-1ubuntu0.1 [6 483 kB]
Del linux-image-3.13.0-24-generic 3.13.0-24.47 [15,0 MB]
Del libkjsapi4 4:4.13.0-0ubuntu1 [258 kB]
Del libqt5test5 5.2.1+dfsg-1ubuntu14.2 [73,3 kB]
Del libebook-1.2-14 3.10.4-0ubuntu1.1 [46,1 kB]
Del libasprintf0c2 0.18.3.1-1ubuntu3 [6 712 B]
Del kdelibs-bin 4:4.13.0-0ubuntu1.1 [200 kB]
Del libkntlm4 4:4.13.0-0ubuntu1.1 [28,5 kB]
Del linux-headers-generic 3.13.0.24.29 [2 386 B]
Del language-pack-en 1:14.04+20140522 [287 kB]
Del app-install-data 14.04.1 [12,6 MB]
Del simple-scan 3.12.1-0ubuntu1 [134 kB]
Del linux-signed-image-3.13.0-24-generic 3.13.0-24.47 [3 962 B]
Del iputils-ping 3:20121221-4ubuntu1.1 [52,6 kB]
Del liblightdm-gobject-1-0 1.10.1-0ubuntu1 [32,0 kB]
Del linux-libc-dev 3.13.0-24.47 [780 kB]
Del python-samba 2:4.1.6+dfsg-1ubuntu2.14.04.1 [879 kB]
Del libsane 1.0.23-3ubuntu3.1 [1 858 kB]
Del libgtk2.0-0 2.24.23-0ubuntu1.1 [1 733 kB]
Del network-manager-gnome 0.9.8.8-0ubuntu4.1 [313 kB]
Del libktexteditor4 4:4.13.0-0ubuntu1.1 [96,2 kB]
Del libwbclient0 2:4.1.6+dfsg-1ubuntu2.14.04.1 [28,0 kB]
Del gettext 0.18.3.1-1ubuntu3 [829 kB]
Del openssl 1.0.1f-1ubuntu2.2 [488 kB]
Del libpurple-bin 1:2.10.9-0ubuntu3.1 [15,1 kB]
Del libgles2-mesa 10.1.3-0ubuntu0.1 [12,5 kB]
Del software-properties-common 0.92.37.1 [9 382 B]
Del libkdewebkit5 4:4.13.0-0ubuntu1.1 [61,7 kB]
Del libedata-cal-1.2-23 3.10.4-0ubuntu1.1 [66,4 kB]
Del im-config 0.24-1ubuntu4.1 [22,3 kB]
Del xserver-xorg-video-ati 1:7.3.0-1ubuntu3.1 [6 754 B]
Del libkcmutils4 4:4.13.0-0ubuntu1 [92,1 kB]
Del update-manager-core 1:0.196.12 [5 252 B]
Del libkde3support4 4:4.13.0-0ubuntu1 [295 kB]
Del libcupsfilters1 1.0.52-0ubuntu1.1 [74,4 kB]
Del libssl1.0.0 1.0.1f-1ubuntu2.2 [779 kB]
Del qtdeclarative5-qtquick2-plugin 5.2.1-3ubuntu15.1 [34,0 kB]
Del nautilus-data 1:3.10.1-0ubuntu9.1 [50,9 kB]
Del empathy 3.8.6-0ubuntu9.1 [572 kB]
Del evolution-data-server-common 3.10.4-0ubuntu1.1 [109 kB]
Del libpurple0 1:2.10.9-0ubuntu3.1 [1 284 kB]
Del libedataserver-1.2-18 3.10.4-0ubuntu1.1 [171 kB]
Del linux-image-generic 3.13.0.24.29 [2 396 B]
Del libgstreamer1.0-0 1.2.4-0ubuntu1 [596 kB]
Del thunderbird 1:24.5.0+build1-0ubuntu0.14.04.1 [23,8 MB]
Del libselinux1 2.2.2-1ubuntu0.1 [57,5 kB]
Del libpam-systemd 204-5ubuntu20.2 [25,5 kB]
Del libselinux1 2.2.2-1ubuntu0.1 [58,7 kB]
Del ghostscript-x 9.10~dfsg-0ubuntu10.1 [33,3 kB]
Del libgs9 9.10~dfsg-0ubuntu10.1 [1 942 kB]
Del libkdesu5 4:4.13.0-0ubuntu1.1 [50,8 kB]
Del libgettextpo-dev 0.18.3.1-1ubuntu3 [122 kB]
Del apport 2.14.1-0ubuntu3.2 [178 kB]
Del libegl1-mesa 10.1.3-0ubuntu0.1 [59,1 kB]
Del libnepomuk4 4:4.13.0-0ubuntu1.1 [203 kB]
Del dpkg 1.17.5ubuntu5.2 [1 953 kB]
Del libxfont1 1:1.4.7-1ubuntu0.1 [95,2 kB]
Del python-lxml 3.3.3-1ubuntu0.1 [629 kB]
Del libqt5sql5-sqlite 5.2.1+dfsg-1ubuntu14.2 [30,7 kB]
Del libsystemd-login0 204-5ubuntu20.2 [26,8 kB]
Del samba-common-bin 2:4.1.6+dfsg-1ubuntu2.14.04.1 [487 kB]
Del libxatracker2 10.1.3-0ubuntu0.1 [143 kB]
Del libkfile4 4:4.13.0-0ubuntu1 [216 kB]
Del libcgmanager0 0.24-0ubuntu6 [29,1 kB]
Del libsane 1.0.23-3ubuntu3.1 [1 929 kB]
Del libasprintf-dev 0.18.3.1-1ubuntu3 [4 438 B]
Del kdelibs-bin 4:4.13.0-0ubuntu1 [199 kB]
Del linux-headers-3.13.0-24 3.13.0-24.47 [8 865 kB]
Del libkdecore5 4:4.13.0-0ubuntu1.1 [897 kB]
Del openssh-client 1:6.6p1-2ubuntu2 [565 kB]
Del linux-firmware 1.127.2 [19,1 MB]
Del libkrosscore4 4:4.13.0-0ubuntu1.1 [55,7 kB]
Del linux-image-generic 3.13.0.27.33 [2 496 B]
Del kdoctools 4:4.13.0-0ubuntu1 [172 kB]
Del libfreetype6 2.5.2-1ubuntu2.2 [305 kB]
Del python3-lxml 3.3.3-1ubuntu0.1 [625 kB]
Del libkpty4 4:4.13.0-0ubuntu1.1 [32,7 kB]
Del rhythmbox-plugin-zeitgeist 3.0.2-0ubuntu2 [54,1 kB]
Del libgtk2.0-common 2.24.23-0ubuntu1.1 [121 kB]
Del gir1.2-ebook-1.2 3.10.4-0ubuntu1.1 [7 110 B]
Del gir1.2-webkit-3.0 2.4.2-1ubuntu0.1 [60,1 kB]
Del libkhtml5 4:4.13.0-0ubuntu1 [1 914 kB]
Del winbind 2:4.1.6+dfsg-1ubuntu2.14.04.1 [399 kB]
Del gettext-base 0.18.3.1-1ubuntu3 [48,8 kB]
Del linux-generic 3.13.0.24.29 [1 780 B]
Del evolution-data-server-online-accounts 3.10.4-0ubuntu1.1 [30,7 kB]
Del oxideqt-codecs-extra 1.0.0~bzr501-0ubuntu2 [869 kB]
Del libnautilus-extension1a 1:3.10.1-0ubuntu9.1 [52,5 kB]
Del libglapi-mesa 10.1.3-0ubuntu0.1 [21,2 kB]
Del linux-generic 3.13.0.27.33 [1 786 B]
Del libqt5xml5 5.2.1+dfsg-1ubuntu14.2 [90,1 kB]
Del libgnutls-openssl27 2.12.23-12ubuntu2.1 [18,3 kB]
Del libsystemd-journal0 204-5ubuntu20.2 [49,6 kB]
Del libgail18 2.24.23-0ubuntu1.1 [14,2 kB]
Del linux-image-generic 3.13.0.29.35 [2 428 B]
Del libedata-book-1.2-20 3.10.4-0ubuntu1.1 [69,8 kB]
Del gnome-calculator 1:3.10.2-0ubuntu1.1 [206 kB]
Del firefox 29.0+build1-0ubuntu0.14.04.2 [29,1 MB]
Del libtiff5 4.0.3-7ubuntu0.1 [142 kB]
Del cups-filters-core-drivers 1.0.52-0ubuntu1.1 [92,5 kB]
Del libqt5core5a 5.2.1+dfsg-1ubuntu14.2 [1 748 kB]
Del libkdeui5 4:4.13.0-0ubuntu1.1 [1 262 kB]
Del libkjsapi4 4:4.13.0-0ubuntu1.1 [259 kB]
Del libido3-0.1-0 13.10.0+14.04.20140423-0ubuntu1 [48,1 kB]
Del initramfs-tools 0.103ubuntu4.1 [44,3 kB]
Del libkmediaplayer4 4:4.13.0-0ubuntu1 [29,2 kB]
Del libknotifyconfig4 4:4.13.0-0ubuntu1 [39,3 kB]
Del libgbm1 10.1.3-0ubuntu0.1 [19,0 kB]
Del libnepomukutils4 4:4.13.0-0ubuntu1.1 [84,6 kB]
Del libkdeclarative5 4:4.13.0-0ubuntu1 [38,4 kB]
Del gdb 7.7-0ubuntu3.1 [2 197 kB]
Del smbclient 2:4.1.6+dfsg-1ubuntu2.14.04.1 [237 kB]
Del libxml2-utils 2.9.1+dfsg1-3ubuntu4.2 [34,7 kB]
Del libkdnssd4 4:4.13.0-0ubuntu1 [66,0 kB]
Del gir1.2-gstreamer-1.0 1.2.4-0ubuntu1 [65,6 kB]
Del libkfile4 4:4.13.0-0ubuntu1.1 [215 kB]
Del libjbig0 2.0-2ubuntu4.1 [26,1 kB]
Del ssh-askpass-gnome 1:6.6p1-2ubuntu2 [14,4 kB]
Del libwebkitgtk-1.0-common 2.4.2-1ubuntu0.1 [106 kB]
Del libgl1-mesa-dri 10.1.3-0ubuntu0.1 [4 947 kB]
Del libsolid4 4:4.13.0-0ubuntu1 [264 kB]
Del libgnutls26 2.12.23-12ubuntu2.1 [374 kB]
Del libsmbclient 2:4.1.6+dfsg-1ubuntu2.14.04.1 [49,9 kB]
Del xserver-xorg-video-radeon 1:7.3.0-1ubuntu3.1 [121 kB]
Del rhythmbox-plugin-magnatune 3.0.2-0ubuntu2 [22,2 kB]
Del libcgmanager0 0.24-0ubuntu6 [25,3 kB]
Del system-config-printer-common 1.4.3+20140219-0ubuntu2.1 [36,5 kB]
Del libgstreamer-plugins-base1.0-0 1.2.4-1~ubuntu1 [436 kB]
Del libcups2 1.7.2-0ubuntu1 [175 kB]
Del libkpty4 4:4.13.0-0ubuntu1 [32,7 kB]
Del libwebkitgtk-3.0-common 2.4.2-1ubuntu0.1 [106 kB]
Del libgl1-mesa-glx 10.1.3-0ubuntu0.1 [112 kB]
Del qtdeclarative5-dialogs-plugin 5.2.1-3ubuntu15.1 [79,8 kB]
Del linux-headers-generic 3.13.0.29.35 [2 416 B]
Del kdelibs5-data 4:4.13.0-0ubuntu1.1 [2 589 kB]
Del ifupdown 0.7.47.2ubuntu4.1 [52,1 kB]
Del libfreetype6 2.5.2-1ubuntu2.2 [300 kB]
Del qtdeclarative5-window-plugin 5.2.1-3ubuntu15.1 [16,2 kB]
Del libsdl1.2debian 1.2.15-8ubuntu1.1 [162 kB]
Del libgettextpo0 0.18.3.1-1ubuntu3 [108 kB]
Del libnepomukquery4a 4:4.13.0-0ubuntu1.1 [107 kB]
Del libebackend-1.2-7 3.10.4-0ubuntu1.1 [112 kB]
Del libelf1 0.158-0ubuntu5.1 [38,3 kB]
Del libkdnssd4 4:4.13.0-0ubuntu1.1 [66,0 kB]
Del cups-browsed 1.0.52-0ubuntu1.1 [49,4 kB]
Del libfontembed1 1.0.52-0ubuntu1.1 [44,0 kB]
Del qtdeclarative5-localstorage-plugin 5.2.1-3ubuntu15.1 [28,5 kB]
Del openssl 1.0.1f-1ubuntu2.1 [489 kB]
Del systemd-services 204-5ubuntu20.2 [197 kB]
Del libthreadweaver4 4:4.13.0-0ubuntu1 [46,7 kB]
Del gir1.2-gst-plugins-base-1.0 1.2.4-1~ubuntu1 [61,8 kB]
Del libgudev-1.0-0 1:204-5ubuntu20.2 [14,1 kB]
Del libplasma3 4:4.13.0-0ubuntu1.1 [884 kB]
Del rhythmbox-mozilla 3.0.2-0ubuntu2 [5 474 B]
Del libkidletime4 4:4.13.0-0ubuntu1.1 [37,4 kB]
Del libkjsembed4 4:4.13.0-0ubuntu1 [302 kB]
Del gstreamer1.0-alsa 1.2.4-1~ubuntu1 [28,4 kB]
Del liboxideqt-qmlplugin 1.0.0~bzr501-0ubuntu2 [234 kB]
Del libqt5printsupport5 5.2.1+dfsg-1ubuntu14.2 [152 kB]
Del gstreamer1.0-plugins-good 1.2.4-1~ubuntu1 [1 286 kB]
Del libqt5dbus5 5.2.1+dfsg-1ubuntu14.2 [176 kB]
Del linux-libc-dev 3.13.0-29.53 [780 kB]
Del firefox-locale-en 29.0+build1-0ubuntu0.14.04.2 [519 kB]
Del libtiff5 4.0.3-7ubuntu0.1 [142 kB]
Del linux-image-3.13.0-27-generic 3.13.0-27.50 [15,0 MB]
Del gstreamer1.0-x 1.2.4-1~ubuntu1 [64,1 kB]
Del libkio5 4:4.13.0-0ubuntu1 [825 kB]
Del rhythmbox-plugin-cdrecorder 3.0.2-0ubuntu2 [14,0 kB]
Del gnome-control-center-shared-data 1:3.6.3-0ubuntu56.1 [181 kB]
Del libgl1-mesa-dri 10.1.0-4ubuntu5 [4 987 kB]
Del libkparts4 4:4.13.0-0ubuntu1 [117 kB]
Del locales 2.13+git20120306-12.1 [2 695 kB]
Del libgs9-common 9.10~dfsg-0ubuntu10.1 [2 066 kB]
Del mcp-account-manager-uoa 3.8.6-0ubuntu9.1 [25,1 kB]
Del libuuid1 2.20.1-5.1ubuntu20 [11,7 kB]
Del update-manager 1:0.196.12 [544 kB]
Del python3-problem-report 2.14.1-0ubuntu3.2 [8 936 B]
Del initramfs-tools-bin 0.103ubuntu4.1 [8 898 B]
Del account-plugin-salut 3.8.6-0ubuntu9.1 [8 864 B]
Del libkhtml5 4:4.13.0-0ubuntu1.1 [1 917 kB]
Del libsystemd-daemon0 204-5ubuntu20.2 [9 748 B]
Del tzdata 2014c-0ubuntu0.14.04 [181 kB]
Del webbrowser-app 0.23+14.04.20140428-0ubuntu1 [565 kB]
Del libthreadweaver4 4:4.13.0-0ubuntu1.1 [46,6 kB]
Del libkmediaplayer4 4:4.13.0-0ubuntu1.1 [29,2 kB]
Del gstreamer1.0-pulseaudio 1.2.4-1~ubuntu1 [49,4 kB]
Del linux-headers-3.13.0-27 3.13.0-27.50 [8 865 kB]
Del libc6-i386 2.19-0ubuntu6 [2 204 kB]
Del libqt5network5 5.2.1+dfsg-1ubuntu14.2 [503 kB]
Del sane-utils 1.0.23-3ubuntu3.1 [165 kB]
Del libgail-common 2.24.23-0ubuntu1.1 [110 kB]
Del libnepomuk4 4:4.13.0-0ubuntu1 [202 kB]
Del account-plugin-aim 3.8.6-0ubuntu9.1 [8 830 B]
Del rhythmbox-data 3.0.2-0ubuntu2 [383 kB]
Del linux-headers-generic 3.13.0.27.33 [2 486 B]
Del libqt5qml5 5.2.1-3ubuntu15.1 [1 212 kB]
Del libkcmutils4 4:4.13.0-0ubuntu1.1 [91,4 kB]
Del libkdesu5 4:4.13.0-0ubuntu1 [50,8 kB]
Del gir1.2-ebookcontacts-1.2 3.10.4-0ubuntu1.1 [12,6 kB]
Del libkparts4 4:4.13.0-0ubuntu1.1 [118 kB]
Del unity-greeter 14.04.10-0ubuntu1 [140 kB]
Del libktexteditor4 4:4.13.0-0ubuntu1 [96,3 kB]
Del qtdeclarative5-privatewidgets-plugin 5.2.1-3ubuntu15.1 [40,4 kB]
Del libgstreamer-plugins-good1.0-0 1.2.4-1~ubuntu1 [31,8 kB]
Del kdelibs5-data 4:4.13.0-0ubuntu1 [2 591 kB]
Del account-plugin-jabber 3.8.6-0ubuntu9.1 [8 844 B]
Del gir1.2-rb-3.0 3.0.2-0ubuntu2 [37,6 kB]
Del libkidletime4 4:4.13.0-0ubuntu1 [37,4 kB]
Del libgexiv2-2 0.10.0-1ubuntu2 [41,0 kB]
Del lightdm 1.10.1-0ubuntu1 [100 kB]
Del libqt5widgets5 5.2.1+dfsg-1ubuntu14.2 [2 216 kB]
Del libcamel-1.2-45 3.10.4-0ubuntu1.1 [548 kB]
Del libebook-contacts-1.2-0 3.10.4-0ubuntu1.1 [47,5 kB]
Del linux-image-extra-3.13.0-29-generic 3.13.0-29.53 [36,6 MB]
Del linux-image-3.13.0-29-generic 3.13.0-29.53 [15,0 MB]
Del python-cupshelpers 1.4.3+20140219-0ubuntu2.1 [31,9 kB]
Del libosmesa6 10.1.3-0ubuntu0.1 [966 kB]
Del libssl1.0.0 1.0.1f-1ubuntu2.1 [779 kB]
Del evolution-data-server 3.10.4-0ubuntu1.1 [314 kB]
Del flashplugin-installer 11.2.202.359ubuntu0.14.04.1 [6 858 B]
Del libkdecore5 4:4.13.0-0ubuntu1 [896 kB]
Del rhythmbox 3.0.2-0ubuntu2 [120 kB]
Del libjavascriptcoregtk-1.0-0 2.4.2-1ubuntu0.1 [1 821 kB]
Del libgtk2.0-bin 2.24.23-0ubuntu1.1 [9 738 B]
Del libkemoticons4 4:4.13.0-0ubuntu1 [41,4 kB]
Del libxml2-utils 2.9.1+dfsg1-3ubuntu4.1 [34,7 kB]
Del libqt5sql5 5.2.1+dfsg-1ubuntu14.2 [99,1 kB]
Del libudev1 204-5ubuntu20.2 [34,2 kB]
Del thunderbird-gnome-support 1:24.5.0+build1-0ubuntu0.14.04.1 [8 538 B]
Del libkdewebkit5 4:4.13.0-0ubuntu1 [61,7 kB]
Del ltrace 0.7.3-4ubuntu5.1 [120 kB]
Del linux-headers-3.13.0-29-generic 3.13.0-29.53 [706 kB]
Del ubuntu-drivers-common 1:0.2.91.5 [41,7 kB]
Del unity-services 7.2.0+14.04.20140423-0ubuntu1.2 [29,3 kB]
Del gnome-settings-daemon-schemas 3.8.6.1-0ubuntu11.1 [44,3 kB]
Del libkjsembed4 4:4.13.0-0ubuntu1.1 [302 kB]
Del python-pexpect 3.1-1ubuntu0.1 [37,8 kB]
Del libkde3support4 4:4.13.0-0ubuntu1.1 [294 kB]
Del libxml2 2.9.1+dfsg1-3ubuntu4.1 [570 kB]
Del gir1.2-freedesktop 1.40.0-1ubuntu0.1 [5 674 B]
Del rhythmbox-plugins 3.0.2-0ubuntu2 [207 kB]
Del libfreetype6 2.5.2-1ubuntu2.1 [300 kB]
Del libkdeclarative5 4:4.13.0-0ubuntu1.1 [38,3 kB]
Del qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets 0.23+14.04.20140428-0ubuntu1 [6 222 B]
Del gstreamer1.0-plugins-base-apps 1.2.4-1~ubuntu1 [25,2 kB]
Del libglapi-mesa 10.1.3-0ubuntu0.1 [21,3 kB]
Del libplasma3 4:4.13.0-0ubuntu1 [884 kB]
Del gir1.2-edataserver-1.2 3.10.4-0ubuntu1.1 [19,0 kB]
Del duplicity 0.6.23-1ubuntu4.1 [199 kB]
Del libjbig0 2.0-2ubuntu4.1 [25,1 kB]
Del bash 4.3-7ubuntu1 [575 kB]
Del libnepomukquery4a 4:4.13.0-0ubuntu1 [107 kB]
Del language-pack-gnome-en 1:14.04+20140522 [108 kB]
Del gir1.2-gudev-1.0 1:204-5ubuntu20.2 [5 488 B]
Del ghostscript 9.10~dfsg-0ubuntu10.1 [40,9 kB]
Del samba-libs 2:4.1.6+dfsg-1ubuntu2.14.04.1 [4 099 kB]
Del libxml2 2.9.1+dfsg1-3ubuntu4.2 [570 kB]
Del libssl1.0.0 1.0.1f-1ubuntu2.1 [822 kB]
Del software-center 13.10-0ubuntu4.1 [325 kB]
Del linux-image-extra-3.13.0-27-generic 3.13.0-27.50 [36,7 MB]
Del samba-dsdb-modules 2:4.1.6+dfsg-1ubuntu2.14.04.1 [218 kB]
Del libelf1 0.158-0ubuntu5.1 [42,7 kB]
Del libxml2 2.9.1+dfsg1-3ubuntu4.1 [555 kB]
Del libgl1-mesa-dri 10.1.3-0ubuntu0.1 [4 962 kB]
Del nautilus 1:3.10.1-0ubuntu9.1 [480 kB]
Del libkntlm4 4:4.13.0-0ubuntu1 [28,5 kB]
Del empathy-common 3.8.6-0ubuntu9.1 [1 519 kB]
Del samba-common 2:4.1.6+dfsg-1ubuntu2.14.04.1 [157 kB]
Del libgnome-control-center1 1:3.6.3-0ubuntu56.1 [80,4 kB]
Del libsolid4 4:4.13.0-0ubuntu1.1 [263 kB]
Del python3-software-properties 0.92.37.1 [19,2 kB]
Del libkdeui5 4:4.13.0-0ubuntu1 [1 262 kB]
Del liboxideqtcore0 1.0.0~bzr501-0ubuntu2 [20,3 MB]
Del iputils-tracepath 3:20121221-4ubuntu1.1 [32,6 kB]
Del libqt5gui5 5.2.1+dfsg-1ubuntu14.2 [1 854 kB]
Del linux-image-extra-3.13.0-24-generic 3.13.0-24.47 [36,6 MB]
Del libgl1-mesa-glx 10.1.0-4ubuntu5 [112 kB]
Del gir1.2-glib-2.0 1.40.0-1ubuntu0.1 [124 kB]
Del libssl1.0.0 1.0.1f-1ubuntu2.2 [826 kB]
Del software-properties-gtk 0.92.37.1 [46,9 kB]
Del libc6 2.19-0ubuntu6 [4 017 kB]
Del nautilus-sendto-empathy 3.8.6-0ubuntu9.1 [11,8 kB]
Del gstreamer1.0-tools 1.2.4-0ubuntu1 [37,0 kB]
Del librhythmbox-core8 3.0.2-0ubuntu2 [469 kB]
Del libgl1-mesa-glx 10.1.3-0ubuntu0.1 [114 kB]
Del libegl1-mesa-drivers 10.1.3-0ubuntu0.1 [1 995 kB]
Del apport-gtk 2.14.1-0ubuntu3.2 [9 548 B]
Del libqt5opengl5 5.2.1+dfsg-1ubuntu14.2 [134 kB]
Del libwayland-egl1-mesa 10.1.3-0ubuntu0.1 [6 460 B]
Del system-config-printer-udev 1.4.3+20140219-0ubuntu2.1 [18,7 kB]
Del libunity-core-6.0-9 7.2.0+14.04.20140423-0ubuntu1.2 [448 kB]
Del system-config-printer-gnome 1.4.3+20140219-0ubuntu2.1 [136 kB]
Del libnm-gtk0 0.9.8.8-0ubuntu4.1 [61,0 kB]
Del thunderbird-locale-en 1:24.5.0+build1-0ubuntu0.14.04.1 [335 kB]
Del libopenvg1-mesa 10.1.3-0ubuntu0.1 [12,8 kB]
Del account-plugin-yahoo 3.8.6-0ubuntu9.1 [8 846 B]
Del libsane-common 1.0.23-3ubuntu3.1 [451 kB]
Del libosmesa6 10.1.0-4ubuntu5 [965 kB]
Del libkemoticons4 4:4.13.0-0ubuntu1.1 [41,4 kB]
Del linux-libc-dev 3.13.0-27.50 [780 kB]
Del iputils-arping 3:20121221-4ubuntu1.1 [26,6 kB]
Del rsync 3.1.0-2ubuntu0.1 [283 kB]
Del libfreetype6 2.5.2-1ubuntu2.1 [305 kB]
Del samba-vfs-modules 2:4.1.6+dfsg-1ubuntu2.14.04.1 [208 kB]
Del udev 204-5ubuntu20.2 [734 kB]
Del libknotifyconfig4 4:4.13.0-0ubuntu1.1 [39,4 kB]
Del unity 7.2.0+14.04.20140423-0ubuntu1.2 [1 437 kB]
Del libnepomukutils4 4:4.13.0-0ubuntu1 [84,8 kB]
Del libknewstuff3-4 4:4.13.0-0ubuntu1.1 [152 kB]
Del python-libxml2 2.9.1+dfsg1-3ubuntu4.1 [139 kB]
Del python-libxml2 2.9.1+dfsg1-3ubuntu4.2 [138 kB]
Del libecal-1.2-16 3.10.4-0ubuntu1.1 [97,7 kB]
Del gir1.2-javascriptcoregtk-3.0 2.4.2-1ubuntu0.1 [11,8 kB]
Del webapp-container 0.23+14.04.20140428-0ubuntu1 [33,0 kB]
Del kdoctools 4:4.13.0-0ubuntu1.1 [172 kB]
Del linux-headers-3.13.0-29 3.13.0-29.53 [8 877 kB]
Del linux-headers-3.13.0-24-generic 3.13.0-24.47 [708 kB]
raphael@Navagraha:~$ sudo dpkg --configure -a


```

No return for dpkg configure

I tried to re run the installation, and the same error occurs (see above)

---

### Post by mc4man on 2014-06-17
You should note that the 14.04 gimp packages in that ppa are versioned lower than trusty so they won't be used.
What does this report 
```
sudo apt-get update
```
```
apt-cache policy libbabl-0.1.0 libgegl-0.2-0 libmng1 libwebkitgtk-1.0-0 gimp
```

---

### Post by Raphael_Poli on 2014-06-17
I tried 
```

sudo apt-get remove libbabl


```
but it says

" Unable to locate package libbabl"

---

### Post by Raphael_Poli on 2014-06-17
I did 
```

sudo apt-get update
apt-cache policy libbabl-0.1.0 libgegl-0.2-0 libmng1 libwebkitgtk-1.0-0 gimp
```here is the return of the latest:
```

raphael@Navagraha:~$ apt-cache policy libbabl-0.1.0 libgegl-0.2-0 libmng1 libwebkitgtk-1.0-0 gimp
libbabl-0.1-0:
  Installed: (none)
  Candidate: (none)
  Version table:
     0.1.10-1ubuntu2 0
        100 /var/lib/dpkg/status
libgegl-0.2-0:
  Installed: (none)
  Candidate: (none)
  Version table:
     0.2.0-4ubuntu1 0
        100 /var/lib/dpkg/status
libmng1:
  Installed: (none)
  Candidate: (none)
  Version table:
libwebkitgtk-1.0-0:
  Installed: (none)
  Candidate: (none)
  Version table:
     2.4.2-1ubuntu0.1 0
        100 /var/lib/dpkg/status
gimp:
  Installed: (none)
  Candidate: 2.8.10-0trusty4~ppa
  Version table:
     2.8.10-0ubuntu1 0
        100 /var/lib/dpkg/status
     2.8.10-0trusty4~ppa 0
        500 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu/ trusty/main amd64 Packages


```

What I don't understand is that the "update" command does not update those libraries?

---

### Post by Raphael_Poli on 2014-06-17
I tried ```
raphael@Navagraha:~$ sudo apt-get remove libbabl-0.1.0
[sudo] password for raphael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libbabl-0.1-0' for regex 'libbabl-0.1.0'
Package 'libbabl-0.1-0' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.

 
```

and then

```

raphael@Navagraha:~$ sudo apt-get install libbabl-0.1.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libbabl-0.1-0' for regex 'libbabl-0.1.0'
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.


```

so then of course 
```

 sudo apt-get install  libbabl-0.1-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libbabl-0.1-0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


```

I tend to understand that the demanded library is not available in the repository?

---

### Post by mc4man on 2014-06-17
It would have been useful to post what sudo apt-get update showed (unless it returned nothing??

---

### Post by Raphael_Poli on 2014-06-17
oh sorry yes it returned something but unfortunately I closed the window! oops!
Do you think I should run it again?

...I ran it again

```

raphael@Navagraha:~$ sudo apt-get update
[sudo] password for raphael: 
Ign http://extras.ubuntu.com trusty InRelease
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty Release                          
Hit http://ppa.launchpad.net trusty Release                          
Ign http://archive.ubuntu.com trusty InRelease                        
Ign http://security.ubuntu.com trusty-security InRelease             
Hit http://extras.ubuntu.com trusty/main Sources                     
Hit http://ppa.launchpad.net trusty/main amd64 Packages              
Hit http://extras.ubuntu.com trusty/main amd64 Packages              
Hit http://ppa.launchpad.net trusty/main i386 Packages               
Hit http://extras.ubuntu.com trusty/main i386 Packages               
Ign http://archive.ubuntu.com trusty-updates InRelease               
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B] 
Hit http://archive.ubuntu.com trusty Release.gpg                               
Get:2 http://security.ubuntu.com trusty-security Release [58,5 kB]   
Get:3 http://archive.ubuntu.com trusty-updates Release.gpg [933 B]             
Hit http://archive.ubuntu.com trusty Release                                   
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:4 http://archive.ubuntu.com trusty-updates Release [58,5 kB]
Get:5 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [1 157 B]
Get:6 http://security.ubuntu.com trusty-security/universe amd64 Packages [19,3 kB]
Hit http://archive.ubuntu.com trusty/universe amd64 Packages                   
Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages                 
Get:7 http://security.ubuntu.com trusty-security/multiverse i386 Packages [1 392 B]
Hit http://archive.ubuntu.com trusty/universe i386 Packages            
Get:8 http://security.ubuntu.com trusty-security/universe i386 Packages [19,3 kB]
Hit http://archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://archive.ubuntu.com trusty/multiverse Translation-en
Hit http://archive.ubuntu.com trusty/universe Translation-en           
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Get:9 http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages [7 090 B]
Get:10 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [122 kB]
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Get:11 http://archive.ubuntu.com trusty-updates/multiverse i386 Packages [7 282 B]
Get:12 http://archive.ubuntu.com trusty-updates/universe i386 Packages [123 kB]
Ign http://security.ubuntu.com trusty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com trusty-security/universe Translation-en_US
Hit http://archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://archive.ubuntu.com trusty-updates/universe Translation-en
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://archive.ubuntu.com trusty/universe Translation-en_US
Ign http://archive.ubuntu.com trusty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com trusty-updates/universe Translation-en_US        
Fetched 419 kB in 6s (68,1 kB/s)                                               
Reading package lists... Done


```

---

### Post by SeijiSensei on 2014-06-17
Why is everyone suggesting the OP use a PPA?  I've always installed gimp from the standard repositories with "sudo apt-get install gimp".  Here's the result for "dpkg -s gimp" on my Kubuntu 14.04 machine:
> 
Seiji@GhostWorld:~$ dpkg -s gimp
Package: gimp
Status: install ok installed
Priority: optional
Section: graphics
Installed-Size: 15370
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 2.8.10-0ubuntu1
Replaces: gimp-plugin-registry (<< 4.20120506)
Provides: gimp-helpbrowser, gimp-python
Depends: libgimp2.0 (>= 2.8.10), libgimp2.0 (<= 2.8.10-z), gimp-data (>= 2.8.10), gimp-data (<= 2.8.10-z), python-gtk2 (>= 2.8.0), libgdk-pixbuf2.0-0 (>= 2.24.1), libaa1 (>= 1.4p5), libbabl-0.1-0 (>= 0.1.10), libbz2-1.0, libc6 (>= 2.15), libcairo2 (>= 1.10.2), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.88), libexif12, libfontconfig1 (>= 2.9.0), libfreetype6 (>= 2.2.1), libgegl-0.2-0 (>= 0.2.0), libglib2.0-0 (>= 2.37.3), libgs9 (>= 8.61.dfsg.1), libgtk2.0-0 (>= 2.24.10), libgudev-1.0-0 (>= 146), libjasper1, libjpeg8 (>= 8c), liblcms2-2 (>= 2.2+git20110628), libmng2 (>= 1.0.10), libpango-1.0-0 (>= 1.29.4), libpangocairo-1.0-0 (>= 1.29.4), libpangoft2-1.0-0 (>= 1.29.4), libpng12-0 (>= 1.2.13-4), libpoppler-glib8 (>= 0.18.0), librsvg2-2 (>= 2.14.4), libtiff5 (>= 4.0.3), libwebkitgtk-1.0-0 (>= 1.3.10), libwmf0.2-7 (>= 0.2.8.4), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3, libxmu6, libxpm4, zlib1g (>= 1:1.1.4), python:any (>= 2.7.1-0ubuntu2), python2.7
Recommends: ghostscript
Suggests: gimp-help-en | gimp-help, gimp-data-extras, gvfs-backends, libasound2
Breaks: gimp-plugin-registry (<< 4.20120506)
Description: The GNU Image Manipulation Program
 GIMP is an advanced picture editor. You can use it to edit, enhance, and
 retouch photos and scans, create drawings, and make your own images.
 It has a large collection of professional-level editing tools and
 filters, similar to the ones you might find in Photoshop. Numerous
 fine-control settings and features like layers, paths, masks, and
 scripting give you total control over your images.
 .
 Many image file formats are supported, including JPEG, Photoshop (.psd),
 and Paint Shop Pro (.psp) files. It can also be used to scan and print
 photos.
 .
 To open files remotely (like over HTTP), install the gvfs-backends
 package.
 .
 To use a MIDI device (like a musical keyboard) as an input controller in GIMP,
 install libasound2 and read the how-to at /usr/share/doc/gimp/README.MIDI
Homepage: [http://www.gimp.org/](http://www.gimp.org/)
Original-Maintainer: Ari Pollak <ari@debian.org>


Did you try running "sudo apt-get purge gimp" before reinstalling?

---

### Post by mc4man on 2014-06-17
It appears you.may have disabled the trusty main repo, that's why you have no candidates as shown in post 13.
Open up Software & Updates, make sure the first 4 sources are enabled. Also under the Updates tab make sure the first 2 are enabled.
Then reload ( update) your sources  & then install gimp

---

### Post by oldos2er on 2014-06-17
> **Raphael_Poli said:**
> Hello I installed Ubuntu 14.04 recently and many problems occur since then. Now the biggest one is that gimp cannot be reinstalled after trying to fix it by uninstalling/reinstalling. 

What is the original problem you're trying to fix with a reinstall?

---

### Post by LastDino on 2014-06-17
> **oldos2er said:**
> What is the original problem you're trying to fix with a reinstall?

+1

IMO, GIMP in default package manager installs and works fine. Using one on both Xubuntu 14.04 and Gnome 14.04. This doesn't seems to be problem specifically related to GIMP.

---

### Post by Raphael_Poli on 2014-06-18
Oldos2er the original problem was that when clicking the gimp icon, the program started, but the window would not appear. Impossible to use the software at all then...
I saw that there was a problem in my update preferences: the open source repository was disabled. (I know that's stupid!! (I don't remember doing this!)
I could reinstall gimp! (but the window still does not appear!... so still impossible to use the software!)

---

### Post by Raphael_Poli on 2014-06-18
Hello I don't know what happened, but now when I run gimp, the window does not appear at all, impossible to use the software.
I tried reinstalling, but it doesn't solve the problem.
I searched for the multiscreen button (multitask with different hidden screen zones) but did not find it.

Finally I found the F8 key, and switched between multitask screens.

---

### Post by LastDino on 2014-06-18
Try pressing F8?

---

### Post by bapoumba on 2014-06-18
Threads merged.

---

### Post by Impavidus on 2014-06-18
There may be something wrong with your user config files. Try renaming (or deleting) the directory **.gimp-2.8**. It should be recreated when you start gimp.

---

### Post by Raphael_Poli on 2014-06-18
hello impavidus, where is that directory?

---

### Post by Raphael_Poli on 2014-06-18
I found it in the home directory

---

### Post by Impavidus on 2014-06-18
It's a hidden directory, sitting in your home directory (/home/username/.gimp-2.8/). Ctrl-h should show hidden files in your file manager.

---

### Post by Raphael_Poli on 2014-06-18
thanks impavidus that's two great tips (solving config problems in gimp and ctrl H)

---


---
title: "OpenBox Mistake"
date: 2014-09-03
forum: General Help
---

### Post by SUPERFITTER on 2014-09-03
I'm running 12.04 LTS and I logged out and logged back into OpenBox and now I have a blank screen.  I tried running off of the disk but I cannot log back into ubuntu. How do I fix this problem?

Thank You

---

### Post by vasa1 on 2014-09-03
Can you open a user account terminal? In it, what happens when you type **openbox --exit**?

AFAIK, Ubuntu 12.04 doesn't come with Openbox.

---

### Post by SUPERFITTER on 2014-09-03
ubuntu@ubuntu:~$ openbox --exit
The program 'openbox' is currently not installed.  You can install it by typing:
sudo apt-get install openbox
You will have to enable the component called 'universe'
ubuntu@ubuntu:~$

---

### Post by SUPERFITTER on 2014-09-03
If I install openbox does anyone know how to enable universe?

---

### Post by vasa1 on 2014-09-03
> **SUPERFITTER said:**
> If I install openbox does anyone know how to enable universe?
But your original post implies you have Openbox installed. I'm confused!

---

### Post by SUPERFITTER on 2014-09-03
> **vasa1 said:**
> But your original post implies you have Openbox installed. I'm confused!

I did not have Openbox installed. When I logged back in I made a mistake and clicked Openbox instead of Ubuntu. I am now looking at a white empty screen, with no panels, icons etc. I was now wondering if I can install Openbox  and try that Desktop because I am running an older machine to try different desktops and other things. The problem now is what is:

ubuntu@ubuntu:~$ openbox --exit
 The program 'openbox' is currently not installed.  You can install it by typing:
 sudo apt-get install openbox

 [COLOR=#FF0000]******[/COLOR][COLOR=#0000ff]**You will have to enable the component called 'universe'**[COLOR=#FF0000][B]**
[/B][/COLOR][/COLOR]
 ubuntu@ubuntu:~$ 

**[COLOR=#0000ff]'universe'[/COLOR]**  Is this found in the Ubuntu Menu or something else that I have to enable in Openbox once I have it installed?  I don't want to make a mistake and compound the problem , that's why I'm asking the question.

Thank you for the help.

---

### Post by ibjsb4 on 2014-09-03
I also do not understand how you have and not have OB, but no matter.

To enable universe:
At the login screen press Ctrl + Alt + F1

Then:
```
sudo nano /etc/apt/sources.list
```
Find the lines:
> #deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
Remove the hash marks (#); save and close.
[https://help.ubuntu.com/community/Nano#Opening.2C_Saving.2C_and_Closing_Files](https://help.ubuntu.com/community/Nano#Opening.2C_Saving.2C_and_Closing_Files)
Have a care, a mistake can bork your system.

Then update:
```
sudo apt-get update
```
To install OB.
```
sudo apt-get install openbox
```
Then reboot
```
sudo reboot
```
And choose your desktop at the login window.

---

### Post by SUPERFITTER on 2014-09-04
Thank you_ [**[COLOR=#000000]ibjsb4[/COLOR]**]("http://ubuntuforums.org/member.php?u=1729120")_
I tried:
1. At the login screen press Ctrl + Alt + F1     **OK**

2. sudo nano /etc/apt/sources.list                   **OK**

3. #deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe                   
    #deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe   ** No # in front of either one**

4. sudo apt-get update   ** OK Got update**

5. sudo apt-get install openbox   **  E: Unable to locate package openbox**

6. sudo reboot   **  Boots to blank screen, no Panels, Icons, etc., just a fuzzy off white screen**


I did the procedure twice, same results. 

On this computer when I logged  off it gave me a few choices to log back into the desktop and Openbox  was one of the choices. 

But there is no Openbox installed as you can see from my reply.

---

### Post by ibjsb4 on 2014-09-04
Please post the output of:
```
uname -r
```
and
```
find /usr/share/xsessions -name "*.desktop" -exec basename "{}" .desktop ";"
```

---

### Post by SUPERFITTER on 2014-09-04
ubuntu@ubuntu:~$ uname -r
3.2.0-23-generic-pae
ubuntu@ubuntu:~$ find /usr/share/xsessions -name "*.desktop" -exec basename "{}" .desktop ";"
gnome-shell
gnome
ubuntu-2d
ubuntu
ubuntu@ubuntu:~$

---

### Post by Bashing-om on 2014-09-04
SUPERFITTER; Wow;
@ ibjsb4 pardon me if I am intruding, but I think ->
> 
ubuntu@ubuntu:~$ uname -r
3.2.0-23-generic-pae

Now that is a real old kernel ! .. What is going on here that the system is not updated to what is current ?
Maybe best at this time to investigate these circumstances prior to attempting to add any additional software to the system ?

To that end, let's look at the condition of the package management system;
Post back - between code tags - the outputs of terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install

```
Then return to ibjsb4's line of thought and investigate the software sources, as surely OB is available in the 'precise' repository .

[INDENT][INDENT][INDENT]just my thought
[/INDENT][/INDENT][/INDENT]

---

### Post by SUPERFITTER on 2014-09-04
```

ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates InRelease                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg [198 B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg [198 B]            
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/main TranslationIndex
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/restricted TranslationIndex
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/main Translation-en_US
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/main Translation-en
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/restricted Translation-en_US
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/restricted Translation-en
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release [49.6 kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [50.7 kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release [98.7 kB] 
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages [1,274 kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [450 kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [72 B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages [8,431 B]    
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex [3,706 B]       
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex [2,596 B] 
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en [192 kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages [862 kB]   
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en [1,253 B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages [13.7 kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en [726 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en                
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en [364 kB]  
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en [3,027 B]
Fetched 4,111 kB in 11s (350 kB/s)                                             
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  duplicity ginn hplip hplip-data libgrip0 libhpmud0 libsane-hpaio
  libunity-2d-private0 libunity-core-5.0-5 linux-generic-pae
  linux-headers-generic-pae linux-image-generic-pae printer-driver-hpcups
  printer-driver-hpijs unity unity-2d-common unity-2d-panel unity-2d-shell
  unity-2d-spread unity-common unity-services update-notifier
  update-notifier-common
The following packages will be upgraded:
  accountsservice acpi-support activity-log-manager-common
  activity-log-manager-control-center alsa-base alsa-utils apparmor
  appmenu-gtk appmenu-gtk3 apport apport-gtk apport-symptoms apt apt-clone
  apt-transport-https apt-utils apt-xapian-index aptdaemon aptdaemon-data
  at-spi2-core avahi-autoipd avahi-daemon avahi-utils bamfdaemon base-files
  bash bash-completion bc bind9-host binutils bluez bluez-alsa bluez-cups
  bluez-gstreamer brasero brasero-cdrkit brasero-common bsdutils
  busybox-initramfs busybox-static ca-certificates casper checkbox checkbox-qt
  cifs-utils colord compiz compiz-core compiz-gnome compiz-plugins-default
  compiz-plugins-main-default consolekit coreutils cron cups cups-bsd
  cups-client cups-common cups-filters cups-ppdc dbus dbus-x11 dc
  dconf-gsettings-backend dconf-service deja-dup desktop-file-utils dmidecode
  dmsetup dnsmasq-base dnsutils dosfstools dpkg ecryptfs-utils empathy
  empathy-common eog evince evince-common evolution-data-server
  evolution-data-server-common file firefox firefox-globalmenu
  firefox-gnome-support firefox-locale-de firefox-locale-en firefox-locale-es
  firefox-locale-pt firefox-locale-zh-hans fontconfig fontconfig-config
  fonts-liberation fonts-opensymbol foomatic-filters gcalctool gdb
  geoclue-ubuntu-geoip ghostscript ghostscript-cups ghostscript-x
  gir1.2-appindicator3-0.1 gir1.2-atspi-2.0 gir1.2-dbusmenu-glib-0.4
  gir1.2-dbusmenu-gtk-0.4 gir1.2-dee-1.0 gir1.2-gdkpixbuf-2.0
  gir1.2-gnomebluetooth-1.0 gir1.2-gst-plugins-base-0.10 gir1.2-gtk-2.0
  gir1.2-gtk-3.0 gir1.2-gtksource-3.0 gir1.2-gudev-1.0
  gir1.2-javascriptcoregtk-3.0 gir1.2-launchpad-integration-3.0
  gir1.2-pango-1.0 gir1.2-rb-3.0 gir1.2-totem-1.0 gir1.2-ubuntuoneui-3.0
  gir1.2-unity-5.0 gir1.2-webkit-3.0 glib-networking glib-networking-common
  glib-networking-services gnome-accessibility-themes gnome-bluetooth
  gnome-control-center gnome-control-center-data gnome-desktop3-data
  gnome-games-data gnome-icon-theme gnome-keyring gnome-media
  gnome-online-accounts gnome-orca gnome-power-manager gnome-screenshot
  gnome-settings-daemon gnome-sudoku gnomine gnupg gpgv grub-common grub-pc
  grub-pc-bin grub2-common gstreamer0.10-alsa gstreamer0.10-gconf
  gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-x gvfs
  gvfs-backends gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs gwibber
  gwibber-service gwibber-service-facebook gwibber-service-identica
  gwibber-service-twitter hdparm ifupdown im-switch indicator-messages
  indicator-sound indicator-status-provider-mc5 initramfs-tools
  initramfs-tools-bin initscripts iproute iptables isc-dhcp-client
  isc-dhcp-common jockey-common jockey-gtk kpartx kpartx-boot krb5-locales
  landscape-client-ui-install language-pack-de language-pack-de-base
  language-pack-en language-pack-en-base language-pack-es
  language-pack-es-base language-pack-gnome-de language-pack-gnome-de-base
  language-pack-gnome-en language-pack-gnome-en-base language-pack-gnome-es
  language-pack-gnome-es-base language-pack-gnome-pt
  language-pack-gnome-pt-base language-pack-gnome-zh-hans
  language-pack-gnome-zh-hans-base language-pack-pt language-pack-pt-base
  language-pack-zh-hans language-pack-zh-hans-base language-selector-common
  language-selector-gnome launchpad-integration libaccountsservice0
  libappindicator1 libappindicator3-1 libapt-inst1.4 libapt-pkg4.12
  libart-2.0-2 libasn1-8-heimdal libasound2 libatspi2.0-0 libaudio2
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-core7
  libavahi-glib1 libavahi-gobject0 libavahi-ui-gtk3-0 libbamf0 libbamf3-0
  libbind9-80 libblkid1 libbluetooth3 libbrasero-media3-1 libc-bin
  libc-dev-bin libc6 libc6-dev libcairo-gobject2 libcairo2 libcamel-1.2-29
  libck-connector0 libcolord1 libcroco3 libcups2 libcupscgi1 libcupsdriver1
  libcupsfilters1 libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3
  libcurl3-gnutls libcurl3-nss libdbus-1-3 libdbus-glib-1-2 libdbusmenu-glib4
  libdbusmenu-gtk3-4 libdbusmenu-gtk4 libdconf-dbus-1-0 libdconf0
  libdebian-installer4 libdecoration0 libdee-1.0-4 libdevmapper-event1.02.1
  libdevmapper1.02.1 libdjvulibre-text libdjvulibre21 libdns81 libdrm-intel1
  libdrm-nouveau1a libdrm-radeon1 libdrm2 libebackend-1.2-1 libebook-1.2-12
  libecal-1.2-10 libecryptfs0 libedata-book-1.2-11 libedata-cal-1.2-13
  libedataserver-1.2-15 libedataserverui-3.0-1 libevince3-3 libexif12
  libexpat1 libfontconfig1 libfreerdp-plugins-standard libfreerdp1
  libfreetype6 libfs6 libgail-3-0 libgail-common libgail18 libgck-1-0
  libgcr-3-1 libgcr-3-common libgcrypt11 libgdk-pixbuf2.0-0
  libgdk-pixbuf2.0-common libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa
  libglib2.0-0 libglib2.0-bin libglib2.0-data libglu1-mesa libgnome-bluetooth8
  libgnome-control-center1 libgnome-desktop-3-2 libgnome2-common
  libgnomekbd-common libgnomekbd7 libgnutls26 libgoa-1.0-0 libgoa-1.0-common
  libgpgme11 libgphoto2-2 libgphoto2-l10n libgphoto2-port0 libgs9
  libgs9-common libgssapi-krb5-2 libgssapi3-heimdal
  libgstreamer-plugins-base0.10-0 libgtk-3-0 libgtk-3-bin libgtk-3-common
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtksourceview-3.0-0
  libgtksourceview-3.0-common libgudev-1.0-0 libgutenprint2 libgwibber-gtk2
  libgwibber2 libhcrypto4-heimdal libheimbase1-heimdal libheimntlm0-heimdal
  libhx509-5-heimdal libicu48 libindicator-messages-status-provider1 libisc83
  libisccc80 libisccfg82 libjack-jackd2-0 libjavascriptcoregtk-3.0-0
  libjpeg-turbo8 libjson0 libk5crypto3 libkrb5-26-heimdal libkrb5-3
  libkrb5support0 liblaunchpad-integration-3.0-1
  liblaunchpad-integration-common liblcms2-2 libldap-2.4-2
  liblightdm-gobject-1-0 liblockfile-bin liblockfile1 liblua5.1-0
  liblvm2app2.2 liblwres80 libmagic1 libminiupnpc8 libmission-control-plugins0
  libmount1 libmtp-common libmtp-runtime libmtp9 libnautilus-extension1a
  libneon27-gnutls libnih-dbus1 libnih1 libnm-glib-vpn1 libnm-glib4
  libnm-gtk-common libnm-gtk0 libnm-util2 libnspr4 libnss3 libnss3-1d
  libnux-2.0-0 libnux-2.0-common liborbit2 liboverlay-scrollbar-0.2-0
  liboverlay-scrollbar3-0.2-0 libpam-ck-connector libpam-gnome-keyring
  libpango1.0-0 libparted0debian1 libpci3 libpciaccess0 libperl5.14
  libpixman-1-0 libplymouth2 libpolkit-agent-1-0 libpolkit-backend-1-0
  libpolkit-gobject-1-0 libpoppler-glib8 libpoppler19 libproxy1
  libproxy1-plugin-gsettings libproxy1-plugin-networkmanager
  libpulse-mainloop-glib0 libpulse0 libpulsedsp libpurple-bin libpurple0
  libpython2.7 libqt4-dbus libqt4-declarative libqt4-network libqt4-opengl
  libqt4-script libqt4-sql libqt4-sql-sqlite libqt4-svg libqt4-xml
  libqt4-xmlpatterns libqtbamf1 libqtcore4 libqtgui4 libraptor2-0 libraw5
  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core
  libreoffice-draw libreoffice-emailmerge libreoffice-gnome libreoffice-gtk
  libreoffice-help-en-us libreoffice-impress libreoffice-math
  libreoffice-style-human libreoffice-style-tango libreoffice-writer
  librhythmbox-core5 libroken18-heimdal librsvg2-2 librsvg2-common libsasl2-2
  libsasl2-modules libsmbclient libsnmp-base libsnmp15 libsqlite3-0 libssh-4
  libssl1.0.0 libsyncdaemon-1.0-1 libtasn1-3 libtelepathy-glib0 libtiff4
  libtotem0 libubuntuoneui-3.0-1 libudev0 libunity9 libupower-glib1
  libusbmuxd1 libutouch-geis1 libuuid1 libv4l-0 libv4lconvert0 libwbclient0
  libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libwind0-heimdal libx11-6
  libx11-data libx11-xcb1 libxatracker1 libxcb-dri2-0 libxcb-glx0
  libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb1 libxcursor1 libxext6
  libxfixes3 libxfont1 libxi6 libxinerama1 libxkbfile1 libxml2 libxp6
  libxrandr2 libxrender1 libxres1 libxslt1.1 libxt6 libxtst6 libxv1 libxvmc1
  libxxf86dga1 libxxf86vm1 libzeitgeist-1.0-1 light-themes lightdm
  linux-firmware linux-libc-dev linux-sound-base login lsb-base lsb-release
  lupin-casper mahjongg make man-db mount mountall mtools multiarch-support
  nautilus nautilus-data nautilus-sendto-empathy network-manager
  network-manager-gnome notify-osd notify-osd-icons ntfs-3g ntpdate nux-tools
  nvidia-common onboard oneconf openssh-client openssl overlay-scrollbar
  parted passwd pciutils perl perl-base perl-modules plymouth plymouth-label
  plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text pm-utils policykit-1
  policykit-1-gnome poppler-utils printer-driver-gutenprint
  printer-driver-ptouch procps psmisc pulseaudio pulseaudio-module-bluetooth
  pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils python
  python-appindicator python-apport python-apt python-apt-common
  python-aptdaemon python-aptdaemon.gtk3widgets python-aptdaemon.pkcompat
  python-crypto python-cupshelpers python-debtagshw python-gi python-gi-cairo
  python-gobject python-gst0.10 python-httplib2 python-imaging python-keyring
  python-lazr.restfulclient python-libproxy python-libxml2 python-minimal
  python-openssl python-piston-mini-client python-problem-report
  python-software-properties python-ubuntu-sso-client python-ubuntuone-client
  python-ubuntuone-control-panel python-ubuntuone-storageprotocol python-uno
  python-zeitgeist python2.7 python2.7-minimal qdbus remmina remmina-common
  remmina-plugin-rdp remmina-plugin-vnc resolvconf rhythmbox rhythmbox-data
  rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune
  rhythmbox-plugin-zeitgeist rhythmbox-plugins rhythmbox-ubuntuone rsyslog
  rtkit samba-common samba-common-bin seahorse sessioninstaller
  shared-mime-info shotwell simple-scan smbclient software-center
  software-properties-common software-properties-gtk ssh-askpass-gnome
  ssl-cert sudo system-config-printer-common system-config-printer-gnome
  system-config-printer-udev sysv-rc sysvinit-utils telepathy-gabble
  telepathy-idle telepathy-mission-control-5 thunderbird
  thunderbird-globalmenu thunderbird-gnome-support totem totem-common
  totem-mozilla totem-plugins transmission-common transmission-gtk tzdata
  ubiquity ubiquity-casper ubiquity-frontend-gtk ubiquity-slideshow-ubuntu
  ubiquity-ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-keyring
  ubuntu-minimal ubuntu-sso-client ubuntu-sso-client-gtk ubuntu-standard
  ubuntu-system-service ubuntuone-client ubuntuone-client-gnome
  ubuntuone-control-panel ubuntuone-installer udev udisks unattended-upgrades
  unity-2d unity-greeter unity-lens-applications unity-lens-files
  unity-lens-music unity-lens-video unity-scope-musicstores
  unity-scope-video-remote uno-libs3 unzip update-manager update-manager-core
  upower upstart ure usb-creator-common usb-creator-gtk usbmuxd util-linux
  uuid-runtime vim-common vim-tiny vino wget whoopsie wpasupplicant x11-common
  x11-utils xdiagnose xkb-data xorg xserver-common xserver-xorg
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-intel
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-vmware xterm xul-ext-ubufox
  zeitgeist zeitgeist-core zenity zenity-common
702 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
Need to get 459 MB of archives.
After this operation, 88.9 MB of additional disk space will be used.
E: You don't have enough free space in /var/cache/apt/archives/.
ubuntu@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 725 not upgraded.
ubuntu@ubuntu:~$

```

---

### Post by ibjsb4 on 2014-09-04
Is this a wubi install (Ubuntu inside windows)?

Please post the output of:
```
df -h
```
and
```
sudo fdisk -l
```
And you should edit your last post and use code tags.
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

### Post by Bashing-om on 2014-09-04
SUPERFITTER; Hey !

Making progress ! 3 steps forward and 2 back.
725 not upgraded ! Yikes ! Someone not doing their maintenance!

ibjsb4 has ninja'd me, -> on the ball and right on !

> 
E: You don't have enough free space in /var/cache/apt/archives/.
ubuntu@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree 
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 725 not upgraded.

Let's take a gander and see where the space constraints are:
```

ls -la /var/cache/apt/
sudo du -h --max-depth=1 /var

```
@ SUPERFITTER -> please use code tags when submitting requested outputs. We read a lot of 'code' in a days time, and using code tags the formatting is retained and makes reading much much easier !
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Then guys, I suggest we try and clear the cache out, IF all looks good - and try the upgrade again.

Maybe we can move on this - 725 -- wow this might prove interesting !

[INDENT][INDENT][INDENT]elbow room, head room, we need space !
[/INDENT][/INDENT][/INDENT]

---

### Post by SUPERFITTER on 2014-09-05
```

> **ibjsb4 said:**
> Is this a wubi install (Ubuntu inside windows)?

Please post the output of:
[CODE]df -h
```
and
```
sudo fdisk -l
```
And you should edit your last post and use code tags.
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

ubuntu@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/cow            438M   60M  378M  14% /
udev            430M  4.0K  430M   1% /dev
tmpfs           175M  788K  175M   1% /run
/dev/sr0        702M  702M     0 100% /cdrom
/dev/loop0      673M  673M     0 100% /rofs
tmpfs           438M  8.0K  438M   1% /tmp
none            5.0M  4.0K  5.0M   1% /run/lock
none            438M   80K  438M   1% /run/shm
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00022301

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   193540095    96769024   83  Linux
/dev/sda2       193542142   195371007      914433    5  Extended
/dev/sda5       193542144   195371007      914432   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 
[/code]

This was a new clean install

---

### Post by SUPERFITTER on 2014-09-05
> **Bashing-om said:**
> SUPERFITTER; Hey !



Making progress ! 3 steps forward and 2 back.
725 not upgraded ! Yikes ! Someone not doing their maintenance!

ibjsb4 has ninja'd me, -> on the ball and right on !


Let's take a gander and see where the space constraints are:
```

ls -la /var/cache/apt/
sudo du -h --max-depth=1 /var

```
@ SUPERFITTER -> please use code tags when submitting requested outputs. We read a lot of 'code' in a days time, and using code tags the formatting is retained and makes reading much much easier !
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Then guys, I suggest we try and clear the cache out, IF all looks good - and try the upgrade again.

Maybe we can move on this - 725 -- wow this might prove interesting ![INDENT][INDENT][INDENT]elbow room, head room, we need space !
[/INDENT]
[/INDENT]
[/INDENT]


[code]
ubuntu@ubuntu:~$ ls -la /var/cache/apt/
total 9816
drwxr-xr-x 1 root root     100 Sep  5 12:10 .
drwxr-xr-x 1 root root     160 Apr 23  2012 ..
drwxr-xr-x 1 root root      60 Sep  5 12:10 archives
-rw-r--r-- 1 root root 5054528 Sep  5 12:10 pkgcache.bin
-rw-r--r-- 1 root root 5013495 Sep  5 12:10 srcpkgcache.bin
ubuntu@ubuntu:~$ sudo du -h --max-depth=1 /var
0    /var/backups
53M    /var/cache
0    /var/crash
0    /var/games
63M    /var/lib
0    /var/local
1.7M    /var/log
0    /var/mail
0    /var/opt
512    /var/spool
0    /var/tmp
117M    /var
ubuntu@ubuntu:~$ 
[code/]

---

### Post by Bashing-om on 2014-09-05
SUPERFITTER; ibjsb4; Yuk !

I do not know what could have led to be in this circumstance:
> 
This was a new clean install

A clean install of what ????
For reference on my system - very very minimalistic :
```

sysop@1404mini:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
[color=green]/dev/sda1[/color]       4.7G  1.8G  2.8G  39% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           2.0G   12K  2.0G   1% /tmp
tmpfs           396M  736K  395M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   22M  2.0G   2% /run/shm
none            100M  8.0K  100M   1% /run/user
/dev/sda2       9.5G  1.3G  7.8G  14% /home
/dev/sda8       4.7G  1.7G  2.8G  37% /var
sysop@1404mini:~$ 

```
Your first line: " /cow            438M   60M  378M  14% [color=red]/[/color] "
where you are mounting the root (/) on " cow " and NOT to a hard disk partiton, suggest that you are mounting from a external device, a DVD or USB ????
And reference my "  ls -la /var/cache/apt/ " :
```

sysop@1404mini:~$  ls -la /var/cache/apt/
total 80128
drwxr-xr-x  3 root root     4096 Sep  5 12:30 .
drwxr-xr-x 12 root root     4096 Dec 22  2013 ..
drwxr-xr-x  3 root root    [color=red]65536[/color] Sep  4 13:00 archives
-rw-r--r--  1 root root 41012863 Sep  5 12:30 pkgcache.bin
-rw-r--r--  1 root root 40991895 Sep  5 12:30 srcpkgcache.bin
sysop@1404mini:~$

```
And your file size for the directory is a mere "60" .. That stinks real bad .. no way Hose !
My "  sudo du -h --max-depth=1 /var ":
```

sysop@1404mini:~$  sudo du -h --max-depth=1 /var
[sudo] password for sysop: 
4.0K    /var/crash
8.7M    /var/backups
4.0K    /var/opt
4.0K    /var/local
173M    /var/lib
4.0K    /var/tmp
1.5G    /var/cache
36K     /var/spool
4.0K    /var/mail
20M     /var/log
16K     /var/lost+found
1.7G    /var
sysop@1404mini:~$

```

Your subdirectories are not populated ... WHY ! ????

Bottom line; We are not going forward on this ! Let's (RE-)install !!
Check your procedure, verify each step of the way.

Are you, SUPERFITTER, installing from DVD or USB ?
Check the validity of the .iso file:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Burn as an image, slowest setting:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Check the integrity of the liveMedium:
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
-----------------------------
Now we are ready to try again:
In the installer choose " erase disk and install ubuntu "; as I presently see no great benefit not to do the standard install letting the install wizard take care of all the configurations.

That is my thoughts on this, I am open to other suggestions, and/or additional questions/responses.

It's a bad condition;
[INDENT][INDENT][INDENT]start all over
[INDENT][INDENT][INDENT]and do this right
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by SUPERFITTER on 2014-09-05
I just reinstalled the operating system. I rebooted and started updates.

---

### Post by SUPERFITTER on 2014-09-05
[code]xxxxxx@xxxxxx1:~$ **sudo apt-get update**
[sudo] password for xxxxxx: 
Hit http://us.archive.ubuntu.com precise Release.gpg
Hit http://us.archive.ubuntu.com precise-updates Release.gpg                   
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://us.archive.ubuntu.com precise Release                               
Hit http://us.archive.ubuntu.com precise-updates Release                       
Hit http://us.archive.ubuntu.com precise-backports Release                     
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources          
Hit http://us.archive.ubuntu.com precise/universe Sources
Hit http://us.archive.ubuntu.com precise/multiverse Sources
Hit http://us.archive.ubuntu.com precise/main i386 Packages          
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages    
Hit http://us.archive.ubuntu.com precise/universe i386 Packages      
Hit http://extras.ubuntu.com precise Release.gpg
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise/main TranslationIndex
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security Release.gpg
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/main Sources        
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources  
Hit http://us.archive.ubuntu.com precise-updates/universe Sources    
Hit http://us.archive.ubuntu.com precise-updates/multiverse Sources  
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages  
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://extras.ubuntu.com precise Release                         
Hit http://security.ubuntu.com precise-security Release              
Hit http://us.archive.ubuntu.com precise-backports/main Sources
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources
Hit http://us.archive.ubuntu.com precise-backports/universe Sources
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise/main Translation-en
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise/universe Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Hit http://extras.ubuntu.com precise/main Sources                    
Hit http://security.ubuntu.com precise-security/main Sources
Hit http://extras.ubuntu.com precise/main i386 Packages
Ign http://extras.ubuntu.com precise/main TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted Sources
Hit http://security.ubuntu.com precise-security/universe Sources
Hit http://security.ubuntu.com precise-security/multiverse Sources
Hit http://security.ubuntu.com precise-security/main i386 Packages
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Ign http://extras.ubuntu.com precise/main Translation-en_US
Ign http://extras.ubuntu.com precise/main Translation-en
Reading package lists... Done

xxxxxx@xxxxxx1:~$** sudo apt-get upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
xxxxxx@xxxxxx1:~$ 
[code/]

**Is there anything else that I should run to keep this computer running properly?**

---

### Post by Bashing-om on 2014-09-05
SUPERFITTER; Looks good.

Thus far .

Any problems with the operating system at large ?
What now returns:
```

df -h
sudo apt-get -f install
sudo dpkg -C
sudo du -h --max-depth=1 /
sudo du -h --max-depth=1 /var

```

all is =>
[INDENT][INDENT][INDENT]finer than a frog's hair ?
[/INDENT][/INDENT][/INDENT]

---

### Post by SUPERFITTER on 2014-09-05
> **Bashing-om said:**
> SUPERFITTER; Looks good.

Thus far .

Any problems with the operating system at large ?
What now returns:
```

df -h
sudo apt-get -f install
sudo dpkg -C
sudo du -h --max-depth=1 /
sudo du -h --max-depth=1 /var

```

all is =>[INDENT][INDENT][INDENT]finer than a frog's hair ?    **And that's Mighty fine!**
[/INDENT]
[/INDENT]
[/INDENT]




[code]
xxxxxx@xxxxxx1:~$ **df -h**
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        91G  3.3G   83G   4% /
udev            430M  4.0K  430M   1% /dev
tmpfs            88M  784K   87M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            438M  148K  437M   1% /run/shm
xxxxxx@xxxxxx1:~$ **sudo apt-get -f install**
[sudo] password for xxxxxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
xxxxxx@xxxxxx1:~$** sudo dpkg -C**
xxxxxx@xxxxxx1:~$ **sudo du -h --max-depth=1 /**
40K    /tmp
4.0K    /dev
8.5M    /bin
4.0K    /opt
52K    /root
du: cannot access `/proc/5370/task/5370/ns/net': No such file or directory
du: cannot access `/proc/5370/task/5370/ns/uts': No such file or directory
du: cannot access `/proc/5370/task/5370/ns/ipc': No such file or directory
du: cannot access `/proc/5370/ns/net': No such file or directory
du: cannot access `/proc/5370/ns/uts': No such file or directory
du: cannot access `/proc/5370/ns/ipc': No such file or directory
du: cannot access `/proc/5438/task/5438/fd/4': No such file or directory
du: cannot access `/proc/5438/task/5438/fdinfo/4': No such file or directory
du: cannot access `/proc/5438/fd/4': No such file or directory
du: cannot access `/proc/5438/fdinfo/4': No such file or directory
0    /proc
14M    /etc
du: cannot access `/home/xxxxxx/.gvfs': Permission denied
31M    /home
4.0K    /srv
48M    /boot
4.0K    /cdrom
8.6M    /sbin
843M    /var
sudo du -h --max-depth=1 /var
1.9G    /usr
16K    /lost+found
0    /sys
932K    /run
4.0K    /selinux
4.0K    /mnt
4.0K    /media
290M    /lib
3.2G    /
xxxxxx@xxxxxx1:~$** sudo du -h --max-depth=1 /var**
4.0K    /var/tmp
4.0K    /var/crash
4.0K    /var/opt
4.4M    /var/log
4.0K    /var/games
68K    /var/spool
1.4M    /var/backups
4.0K    /var/local
669M    /var/cache
169M    /var/lib
4.0K    /var/mail
843M    /var
xxxxxx@xxxxxx1:~$ 
[code/]
[B]
Thank You for your help[/B]

---

### Post by Bashing-om on 2014-09-05
SUPERFITTER; Hey hey ....

Looks great !
With ibjsb4's agreement, I think this situation is now at an end, and may be marked solved ->
Solved by a proper (RE-)installation.
Top of the post -> thread tools

[INDENT][INDENT]all's well 
[INDENT][INDENT][INDENT]that ends well
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---


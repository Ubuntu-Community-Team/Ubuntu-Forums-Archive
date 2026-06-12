---
title: "Problems with unmet dependencies: libqtgui4:i386; libtiff4:i386"
date: 2013-08-29
forum: General Help
---

### Post by Jura on 2013-08-29
# I started to search for a solution at : [http://askubuntu.com/questions/337282/errors-in-configuration-after-skype-installation-libqtgui4i386-libtiff4i386-l](http://askubuntu.com/questions/337282/errors-in-configuration-after-skype-installation-libqtgui4i386-libtiff4i386-l)

# Then I tried at: [https://answers.launchpad.net/ubuntu/+source/skype/+question/234771](https://answers.launchpad.net/ubuntu/+source/skype/+question/234771)

# ...

# My system:

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 12.04.3 LTS
Release: 12.04
Codename: precise

# Some trials:

$ sudo apt-get update
$ sudo apt-get -f install
$ sudo dpkg --configure -a
$ sudo dpkg --purge libtiff4
$ sudo apt-get --reinstall install libtiff4
$ sudo apt-get  install libtiff4:i386
$ sudo apt-get autoclean
$ sudo apt-get autoremove
$ sudo apt-get -f install

# An overview:

$ sudo apt-get -u dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libqtgui4:i386 : Depends: libtiff4:i386 but it is not installed
E: Unmet dependencies. Try using -f.

$ sudo apt-get -o Debug::pkgProblemResolver=yes dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libqtgui4:i386 : Depends: libtiff4:i386 but it is not installed
E: Unmet dependencies. Try using -f.

$ sudo apt-get remove libqtgui4:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libqt4-declarative:i386 : Depends: libqtgui4:i386 (= 4:4.8.1-0ubuntu4.4) but it is not going to be installed
 libqtwebkit4:i386 : Depends: libqtgui4:i386 (>= 4:4.8.0) but it is not going to be installed
 skype:i386 : Depends: libqtgui4:i386 (>= 4:4.8.0) but it is not going to be installed
              Recommends: sni-qt:i386 but it is not going to be installed
              Recommends: libasound2-plugins:i386 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by squakie on 2013-08-30
If the install of  libqtgui4:i386 is giving the error, you can try the following (don't know if it will work with what you are doing or not):

sudo apt-get build-dep  libqtgui4:i386

That *should* find the dependencies for  libqtgui4:i386 *if* they are available for the state of your install and install them.  Then you can:

sudo apt-get install  libqtgui4:i386

---

### Post by Jura on 2013-08-30
$ sudo apt-get build-dep libqtgui4:i386
# Resulted in :
   Removing skype:i386 ...
   Removing libqtwebkit4:i386 ...
   Removing libqt4-declarative:i386 ...
   Removing libqtgui4:i386 ...
$ sudo apt-get install libqtgui4:i386 
# Resulted in:
    (Reading database ... 422065 files and directories currently installed.)
    Unpacking libtiff4:i386 (from .../libtiff4_3.9.5-2ubuntu1.5_i386.deb) ...
    dpkg: error processing /var/cache/apt/archives/libtiff4_3.9.5-2ubuntu1.5_i386.deb (--unpack):
    './usr/share/lintian/overrides/libtiff4' is different from the same file on the system
    Selecting previously unselected package libqtgui4:i386.
    Unpacking libqtgui4:i386 (from .../libqtgui4_4%3a4.8.1-0ubuntu4.4_i386.deb) ...
    Selecting previously unselected package libqt4-declarative:i386.
    Unpacking libqt4-declarative:i386 (from .../libqt4-declarative_4%3a4.8.1-0ubuntu4.4_i386.deb) ...
    Errors were encountered while processing:
    /var/cache/apt/archives/libtiff4_3.9.5-2ubuntu1.5_i386.deb
    E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by squakie on 2013-08-30
I don't understand the build-dep option REMOVING packages - it should try to find the dependencies for the package specified and INSTALL them.  I've never seen this before.

---

### Post by Jura on 2013-08-30
I saved some part of the process yesterday. Specifically for sudo apt-get build-dep libqtgui4:i386 follows below what happens:

$ sudo apt-get build-dep libqtgui4:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'qt4-x11' as source package instead of 'libqtgui4:i386'
The following packages will be REMOVED:
  libqt4-declarative:i386 libqtgui4:i386 libqtwebkit4:i386 skype:i386
The following NEW packages will be installed:
  build-essential debhelper dh-apparmor dpkg-dev flex freetds-common
  freetds-dev html2text libasound2-dev libatk1.0-dev libaudio-dev
  libcairo-script-interpreter2 libcairo2-dev libct4 libcups2-dev libdbus-1-dev
  libdpkg-perl libdrm-dev libexpat1-dev libfl-dev libfontconfig1-dev
  libgdk-pixbuf2.0-dev libgl1-mesa-dev libglib2.0-dev libglu1-mesa-dev
  libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgtk2.0-dev
  libicu-dev libkms1 libmysqlclient-dev libmysqlclient18 libodbc1 libpam0g-dev
  libpango1.0-dev libpixman-1-dev libpq-dev libsqlite3-dev libsybdb5
  libtimedate-perl libxcb-render0-dev libxcb-shm0-dev libxcomposite-dev
  libxcursor-dev libxdamage-dev libxfixes-dev libxft-dev libxi-dev
  libxinerama-dev libxml2-dev libxml2-utils libxrandr-dev libxrender-dev
  libxslt1-dev libxtst-dev libxv-dev m4 mesa-common-dev odbcinst
  odbcinst1debian2 pkg-kde-tools unixodbc unixodbc-dev x11proto-composite-dev
  x11proto-damage-dev x11proto-fixes-dev x11proto-randr-dev
  x11proto-record-dev x11proto-render-dev x11proto-video-dev
  x11proto-xinerama-dev
0 upgraded, 71 newly installed, 4 to remove and 28 not upgraded.
4 not fully installed or removed.
Need to get 29.7 MB of archives.
After this operation, 32.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? y

---

### Post by Jura on 2013-08-30
At this moment my situation is:

$ sudo apt-get install libqtgui4:i386 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqtgui4:i386 is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libqtgui4:i386 : Depends: libtiff4:i386 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

$ sudo apt-get -f install

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-44-generic libwxsqlite3-2.8-0 linux-headers-3.2.0-44
  nvidia-settings-updates qt4-qmake latex-cjk-xcjk libxml2:i386
  linux-headers-3.5.0-23-generic libasound2:i386 linux-headers-3.5.0-23
  liborc-0.4-0:i386 libxss1:i386 libgstreamer-plugins-base0.10-0:i386
  wx-common texlive-lang-ukenglish libgstreamer0.10-0:i386 libxv1:i386
  libsqlite3-0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libtiff4:i386
The following NEW packages will be installed:
  libtiff4:i386
0 upgraded, 1 newly installed, 0 to remove and 28 not upgraded.
2 not fully installed or removed.
Need to get 0 B/143 kB of archives.
After this operation, 501 kB of additional disk space will be used.
Do you want to continue [Y/n]? y

(Reading database ... 422089 files and directories currently installed.)
Unpacking libtiff4:i386 (from .../libtiff4_3.9.5-2ubuntu1.5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libtiff4_3.9.5-2ubuntu1.5_i386.deb (--unpack):
 './usr/share/lintian/overrides/libtiff4' is different from the same file on the system
Errors were encountered while processing:
 /var/cache/apt/archives/libtiff4_3.9.5-2ubuntu1.5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Jura on 2013-08-30
Trying the solution described in: [http://askubuntu.com/questions/171205/e-sub-process-usr-bin-dpkg-returned-an-error-code-1](http://askubuntu.com/questions/171205/e-sub-process-usr-bin-dpkg-returned-an-error-code-1)

$ sudo dpkg -r libtiff4

dpkg: dependency problems prevent removal of libtiff4:
 libcupsimage2 depends on libtiff4.
 libpoppler19 depends on libtiff4.
 libtiff4-dev depends on libtiff4 (= 3.9.5-2ubuntu1.5).
 libevince3-3 depends on libtiff4.
 libdevil1c2 depends on libtiff4; however:
  Package libtiff4 is to be removed.
 libgs9 depends on libtiff4.
 libopencv-highgui2.3 depends on libtiff4.
 libtiff-tools depends on libtiff4.
 gimp-plugin-registry depends on libtiff4; however:
  Package libtiff4 is to be removed.
 libcupsfilters1 depends on libtiff4.
 libtiffxx0c2 depends on libtiff4.
 libgdk-pixbuf2.0-0 depends on libtiff4.
 libqtgui4 depends on libtiff4.
 libspandsp2 depends on libtiff4.
 libwxgtk2.8-0 depends on libtiff4; however:
  Package libtiff4 is to be removed.
 libsane depends on libtiff4.
 libmagickcore4 depends on libtiff4.
 gimp depends on libtiff4.
dpkg: error processing libtiff4 (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 libtiff4

---

### Post by Jura on 2013-08-30
$ sudo dpkg --purge libtiff4

dpkg: dependency problems prevent removal of libtiff4:
 libcupsimage2 depends on libtiff4.
 libpoppler19 depends on libtiff4.
 libtiff4-dev depends on libtiff4 (= 3.9.5-2ubuntu1.5).
 libevince3-3 depends on libtiff4.
 libdevil1c2 depends on libtiff4; however:
  Package libtiff4 is to be removed.
 libgs9 depends on libtiff4.
 libopencv-highgui2.3 depends on libtiff4.
 libtiff-tools depends on libtiff4.
 gimp-plugin-registry depends on libtiff4; however:
  Package libtiff4 is to be removed.
 libcupsfilters1 depends on libtiff4.
 libtiffxx0c2 depends on libtiff4.
 libgdk-pixbuf2.0-0 depends on libtiff4.
 libqtgui4 depends on libtiff4.
 libspandsp2 depends on libtiff4.
 libwxgtk2.8-0 depends on libtiff4; however:
  Package libtiff4 is to be removed.
 libsane depends on libtiff4.
 libmagickcore4 depends on libtiff4.
 gimp depends on libtiff4.
dpkg: error processing libtiff4 (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 libtiff4

---

### Post by Jura on 2013-08-30
$ sudo apt-get --reinstall install libtiff4

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libqtgui4:i386 : Depends: libtiff4:i386 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by Jura on 2013-08-30
$ sudo apt-get install libtiff4

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libtiff4 is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libqtgui4:i386 : Depends: libtiff4:i386 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by Jura on 2013-08-30
Reading:

ia32-libs-multiarch but it is not installable
[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/1016294](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/1016294)

Unmet Dependencies- I am Totally Lost
[http://ubuntuforums.org/archive/index.php/t-2078792.html](http://ubuntuforums.org/archive/index.php/t-2078792.html)

---

### Post by Jura on 2013-08-30
Reading:

ia32-libs-multiarch but it is not installable
[https://bugs.launchpad.net/ubuntu/+s...s/+bug/1016294](https://bugs.launchpad.net/ubuntu/+s...s/+bug/1016294)

Unmet Dependencies- I am Totally Lost
[http://ubuntuforums.org/archive/inde...t-2078792.html](http://ubuntuforums.org/archive/inde...t-2078792.html)

#####################################

Excuse-me the replication. Was a mistake.

---

### Post by Jura on 2013-08-30
$ sudo dpkg -i /var/cache/apt/archives/libtiff4_3.9.5-2ubuntu1.5_i386.deb

(Reading database ... 422089 files and directories currently installed.)
Unpacking libtiff4:i386 (from .../libtiff4_3.9.5-2ubuntu1.5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libtiff4_3.9.5-2ubuntu1.5_i386.deb (--install):
 './usr/share/lintian/overrides/libtiff4' is different from the same file on the system
Errors were encountered while processing:
 /var/cache/apt/archives/libtiff4_3.9.5-2ubuntu1.5_i386.deb

---

### Post by Jura on 2013-08-30
Problem installing libtiff4_3.9.5-1ubuntu1_i386.deb on a 64bits system
[http://ubuntuforums.org/archive/index.php/t-1857025.html](http://ubuntuforums.org/archive/index.php/t-1857025.html)

---

### Post by Jura on 2013-08-30
:/usr/share/lintian/overrides$ more libtiff4
#
# The synopsis line starts with a capital letter because of the TIFF
# acronym, not because it contains a sentence.
#
libtiff4: description-synopsis-starts-with-a-capital-letter

# This *is* tiff.  Lintian doesn't know we renamed the source package
libtiff4: embedded-library usr/lib/x86_64-linux-gnu/libtiff.so.4.3.6: tiff

---

### Post by Jura on 2013-08-30
$ cd  /var/cache/apt/archives/
:/var/cache/apt/archives$ ls

libtiff4_3.9.5-2ubuntu1.5_i386.deb
libtiff4-dev_3.9.5-2ubuntu1.5_amd64.deb
libtiff-tools_3.9.5-2ubuntu1.5_amd64.deb
libtiffxx0c2_3.9.5-2ubuntu1.5_amd64.deb

---

### Post by Jura on 2013-08-30
&#8220;tiff&#8221; 3.9.5-2ubuntu1.5 source package in Ubuntu
[https://launchpad.net/ubuntu/+source/tiff/3.9.5-2ubuntu1.5](https://launchpad.net/ubuntu/+source/tiff/3.9.5-2ubuntu1.5)

libtiff-doc: TIFF manipulation and conversion documentation 
libtiff-tools: TIFF manipulation and conversion tools 
libtiffxx0c2: Tag Image File Format (TIFF) library -- C++ interface 
libtiff-opengl: TIFF manipulation and conversion tools 
libtiff4: Tag Image File Format (TIFF) library 
libtiff4-dev: Tag Image File Format library (TIFF), development files

---

### Post by Jura on 2013-08-30
$ sudo apt-get build-dep libtiff4:i386

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'tiff' as source package instead of 'libtiff4:i386'
The following packages will be REMOVED:
  libqt4-declarative:i386 libqtgui4:i386
The following NEW packages will be installed:
  autoconf automake cdbs dh-translations freeglut3-dev hardening-wrapper
  intltool libencode-locale-perl libfile-listing-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-date-perl
  libhttp-message-perl libhttp-negotiate-perl libio-socket-ssl-perl
  liblwp-mediatypes-perl liblwp-protocol-https-perl libnet-http-perl
  libnet-ssleay-perl liburi-perl libwww-perl libwww-robotrules-perl
  libxml-parser-perl python-scour
0 upgraded, 26 newly installed, 2 to remove and 28 not upgraded.
2 not fully installed or removed.
Need to get 2745 kB of archives.
After this operation, 7993 kB disk space will be freed.
Do you want to continue [Y/n]? y
...
(Reading database ... 422088 files and directories currently installed.)
Removing libqt4-declarative:i386 ...
Removing libqtgui4:i386 ...
...

---

### Post by Jura on 2013-08-30
sudo apt-get install libtiff4:i386

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libkrb5-3:i386 libk5crypto3:i386 libstdc++6:i386
  linux-headers-3.2.0-44-generic liblcms1:i386 libwxsqlite3-2.8-0
  linux-headers-3.2.0-44 libqt4-script:i386 libqt4-network:i386
  libqt4-dbus:i386 libgnutls26:i386 libtasn1-3:i386 libfreetype6:i386
  libmysqlclient18:i386 libexpat1:i386 libqt4-xmlpatterns:i386
  libavahi-common-data:i386 libxcb1:i386 libp11-kit0:i386 libxau6:i386
  libcups2:i386 nvidia-settings-updates libqtcore4:i386 libkrb5support0:i386
  qt4-qmake libice6:i386 latex-cjk-xcjk libxdmcp6:i386 libgcrypt11:i386
  libxml2:i386 linux-headers-3.5.0-23-generic libkeyutils1:i386
  libqt4-sql:i386 libasound2:i386 linux-headers-3.5.0-23 libxrender1:i386
  liborc-0.4-0:i386 libqt4-xml:i386 libxss1:i386
  libgstreamer-plugins-base0.10-0:i386 wx-common texlive-lang-ukenglish
  libavahi-client3:i386 libx11-6:i386 libfontconfig1:i386 libsm6:i386
  libqt4-sql-mysql:i386 libgssapi-krb5-2:i386 libxi6:i386
  libgstreamer0.10-0:i386 libaudio2:i386 libxt6:i386 libxv1:i386 libxext6:i386
  libavahi-common3:i386 libsqlite3-0:i386 libmng1:i386 libgpg-error0:i386
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libtiff4:i386
0 upgraded, 1 newly installed, 0 to remove and 28 not upgraded.
Need to get 0 B/143 kB of archives.
After this operation, 501 kB of additional disk space will be used.
(Reading database ... 422914 files and directories currently installed.)
Unpacking libtiff4:i386 (from .../libtiff4_3.9.5-2ubuntu1.5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libtiff4_3.9.5-2ubuntu1.5_i386.deb (--unpack):
 './usr/share/lintian/overrides/libtiff4' is different from the same file on the system
Errors were encountered while processing:
 /var/cache/apt/archives/libtiff4_3.9.5-2ubuntu1.5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Jura on 2013-08-30
$ sudo apt-get update

$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done

$  sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  latex-cjk-xcjk libasound2:i386 libaudio2:i386 libavahi-client3:i386
  libavahi-common-data:i386 libavahi-common3:i386 libcups2:i386 libexpat1:i386
  libfontconfig1:i386 libfreetype6:i386 libgcrypt11:i386 libgnutls26:i386
  libgpg-error0:i386 libgssapi-krb5-2:i386
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386 libice6:i386
  libjpeg-turbo8:i386 libjpeg8:i386 libk5crypto3:i386 libkeyutils1:i386
  libkrb5-3:i386 libkrb5support0:i386 liblcms1:i386 libmng1:i386
  libmysqlclient18:i386 liborc-0.4-0:i386 libp11-kit0:i386 libqt4-dbus:i386
  libqt4-network:i386 libqt4-script:i386 libqt4-sql:i386 libqt4-sql-mysql:i386
  libqt4-xml:i386 libqt4-xmlpatterns:i386 libqtcore4:i386 libsm6:i386
  libsqlite3-0:i386 libstdc++6:i386 libtasn1-3:i386 libwxsqlite3-2.8-0
  libx11-6:i386 libxau6:i386 libxcb1:i386 libxdmcp6:i386 libxext6:i386
  libxi6:i386 libxml2:i386 libxrender1:i386 libxss1:i386 libxt6:i386
  libxv1:i386 linux-headers-3.2.0-44 linux-headers-3.2.0-44-generic
  linux-headers-3.5.0-23 linux-headers-3.5.0-23-generic
  nvidia-settings-updates qt4-qmake texlive-lang-ukenglish wx-common
0 upgraded, 0 newly installed, 60 to remove and 27 not upgraded.
After this operation, 189 MB disk space will be freed.
Do you want to continue [Y/n]? y

---

### Post by Jura on 2013-08-30
$ sudo dpkg --configure -a

$ sudo apt-get -f install

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 27 not upgraded.
$

---

### Post by Jura on 2013-08-30
$ sudo apt-get upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apparmor context-modules fonts-thai-tlwg fonts-tlwg-garuda
  fonts-tlwg-kinnari fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi
  fonts-tlwg-purisa fonts-tlwg-sawasdee fonts-tlwg-typewriter
  fonts-tlwg-typist fonts-tlwg-typo fonts-tlwg-umpush fonts-tlwg-waree gazebo
  gnome-control-center gnome-control-center-data info install-info
  libgnome-control-center1 libpci3 lmodern pciutils tex-gyre texinfo thailatex
27 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 90.6 MB of archives.
After this operation, 1381 kB of additional disk space will be used.
Do you want to continue [Y/n]? y

---

### Post by squakie on 2013-08-31
Have you tried [this]("http://askubuntu.com/questions/312556/i-cant-install-libtiff-on-my-64-bit-ubuntu") - leave off the :i386 portion you have been specifying if you are running Ubuntu 64-bit.

---

### Post by Jura on 2013-08-31
Hi squakie,

My interpretation of this trouble is that there is a Bug that makes inviable to run software like Skype:i386 (32-bit programs, because in some moment will appear the unmet dependencies) on the Ubuntu 64-bit. I am sorry about that, because I have a Ubuntu 64-bit and I need to use the Skype.

The indirect solution that solved, for me, the trouble with unmet dependencies was in the way of your suggestion:

Using: sudo apt-get build-dep libqtgui4:i386
Resulted in :
Removing skype:i386 ...
Removing libqtwebkit4:i386 ...
Removing libqt4-declarative:i386 ...
Removing libqtgui4:i386 ..

And the using: sudo apt-get build-dep libtiff4:i386
Removed: libqt4-declarative:i386 libqtgui4:i386

So the trouble of unmet dependencies related with :i386 libraries was solved.

Thank you,

Juracy

---

### Post by squakie on 2013-09-01
Sorry I couldn't be of better help.

---


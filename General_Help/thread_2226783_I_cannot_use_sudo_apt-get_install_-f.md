---
title: "I cannot use sudo apt-get install -f"
date: 2014-05-29
forum: General Help
---

### Post by cipher-decrypter on 2014-05-29
I was using sudo apt-get upgrade
then the terminal ask me to do sudo apt-get install -f
when I run the command it give this error

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  etoys-doc kde-l10n-ar kde-l10n-engb libappindicator1 libbit-vector-perl
  libbonoboui2-0 libbonoboui2-common libcarp-clan-perl
  libclass-data-inheritable-perl libclass-method-modifiers-perl
  libcrypt-openssl-bignum-perl libcrypt-openssl-rsa-perl libdata-random-perl
  libdate-calc-perl libdate-calc-xs-perl libextutils-depends-perl
  libextutils-pkgconfig-perl libfile-which-perl libgd-perl libglade2-0
  libgnome2-canvas-perl libgnome2-gconf-perl libgnome2-perl libgnome2-vfs-perl
  libgnome2-wnck-perl libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0
  libgnomeui-common libgoo-canvas-perl libgoocanvas-common libgoocanvas3
  libgtk2-appindicator-perl libgtk2-imageview-perl libgtk2-unique-perl
  libgtkimageview0 libhttp-server-simple-perl libindicator7 libjson-perl
  libjson-xs-perl libmouse-perl libnet-dropbox-api-perl libnet-oauth-perl
  libpath-class-perl libproc-processtable-perl libproc-simple-perl
  libsort-naturally-perl libunique-1.0-0 libwww-mechanize-perl
  libx11-protocol-perl perlmagick squeak-plugins-scratch
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc-bin
The following NEW packages will be installed:
  libc-bin
0 upgraded, 1 newly installed, 0 to remove and 23 not upgraded.
Need to get 1,168 kB of archives.
After this operation, 3,532 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) trusty/main libc-bin amd64 2.19-0ubuntu6 [1,168 kB]
Fetched 1,168 kB in 11s (103 kB/s)                                             
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
dpkg: warning: 'ldconfig' not found in PATH or not executable
dpkg: error: 1 expected program not found in PATH or not executable
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by ian-weisser on 2014-05-29
> **cipher-decrypter said:**
> I was using sudo apt-get upgrade
then the terminal ask me to do sudo apt-get install -f
when I run the command it give this error

Wait...why are you installing libc-bin as a standalone package?
It's already included with the default install of Ubuntu.
Is there some kind of damage you are trying to repair?

---


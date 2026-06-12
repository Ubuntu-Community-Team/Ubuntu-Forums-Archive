---
title: "Terminating installation abnormally by showing --fix-missing? error."
date: 2014-01-16
forum: General Help
---

### Post by thekeshav on 2014-01-16
Hai,

I am using Ubuntu 12.04 LTS Precise. I thought to run windows applications in Ubuntu for this I intended to download Wine software. I did this through terminal by typing ```
 sudo apt-get install wine 
```

I was fetched from Ubuntu archieves upto 80% + approximately and returns to prompt. I thought installation was completed and able to use Wine, but when I searched for it, was not there and I tried again to install by typing the same in the terminal and process is terminating. I hope below terminal colde and included screen shot of the same, would help to understand what's the problem.............

I tried with ```
 apt-get install --fix-missing 
``` . . . . . . . . . Is it right ? ? 

Thanks . . . . . . . . . :)

```
root@Shiva:~# apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  binfmt-support cabextract fonts-droid fonts-horai-umefont fonts-unfonts-core gcc-4.6-base:i386 gnome-exe-thumbnailer grub-common grub-pc
  grub-pc-bin grub2-common icoutils imagemagick imagemagick-common libasn1-8-heimdal libasn1-8-heimdal:i386 libasound2:i386 libavahi-client3
  libavahi-client3:i386 libavahi-common-data libavahi-common-data:i386 libavahi-common3 libavahi-common3:i386 libc-bin libc-dev-bin libc6 libc6:i386
  libc6-dev libcapi20-3 libcapi20-3:i386 libcdt4 libcomerr2:i386 libcups2:i386 libdb5.1:i386 libdbus-1-3:i386 libdrm-intel1 libdrm-intel1:i386
  libdrm-nouveau2 libdrm-nouveau2:i386 libdrm-radeon1 libdrm-radeon1:i386 libdrm2 libdrm2:i386 libencode-locale-perl libexif12:i386 libexpat1:i386
  libffi6:i386 libfile-listing-perl libfont-afm-perl libfontconfig1:i386 libfreetype6:i386 libgcc1:i386 libgcrypt11:i386 libgd2-xpm:i386
  libgettextpo0 libgif4 libgif4:i386 libgl1-mesa-dri-lts-raring libgl1-mesa-dri-lts-raring:i386 libgl1-mesa-glx-lts-raring
  libgl1-mesa-glx-lts-raring:i386 libglapi-mesa-lts-raring libglapi-mesa-lts-raring:i386 libglib2.0-0 libglib2.0-0:i386 libglib2.0-bin libglu1-mesa
  libglu1-mesa:i386 libgnutls26 libgnutls26:i386 libgpg-error0:i386 libgphoto2-2:i386 libgphoto2-port0:i386 libgpm2:i386 libgraph4
  libgssapi-krb5-2:i386 libgssapi3-heimdal libgssapi3-heimdal:i386 libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386 libgvc5
  libhcrypto4-heimdal libhcrypto4-heimdal:i386 libheimbase1-heimdal libheimbase1-heimdal:i386 libheimntlm0-heimdal libheimntlm0-heimdal:i386
  libhtml-form-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl
  libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libhx509-5-heimdal libhx509-5-heimdal:i386 libice6:i386 libieee1284-3:i386
  libilmbase6 libio-socket-inet6-perl libio-socket-ssl-perl libjpeg-turbo8 libjpeg-turbo8:i386 libjpeg8:i386 libk5crypto3:i386 libkeyutils1:i386
  libkrb5-26-heimdal libkrb5-26-heimdal:i386 libkrb5-3:i386 libkrb5support0:i386 liblcms1:i386 libldap-2.4-2 libldap-2.4-2:i386 libllvm3.2:i386
  liblqr-1-0 libltdl7:i386 liblwp-mediatypes-perl liblwp-protocol-https-perl libmagickcore4 libmagickcore4-extra libmagickwand4 libmailtools-perl
  libmpg123-0 libmpg123-0:i386 libncurses5:i386 libnet-http-perl libnet-ssleay-perl libnetpbm10 libodbc1 libopenal-data libopenal1 libopenal1:i386
  libopenexr6 liborc-0.4-0:i386 libp11-kit0:i386 libpam-winbind libpathplan4 libpciaccess0:i386 libpcre3:i386 libpng12-0:i386 libroken18-heimdal
  libroken18-heimdal:i386 libsane:i386 libsasl2-2:i386 libsasl2-modules:i386 libselinux1:i386 libsm6:i386 libsocket6-perl libsqlite3-0:i386
  libssl1.0.0 libssl1.0.0:i386 libstdc++6:i386 libtasn1-3:i386 libtiff4:i386 libtimedate-perl libtinfo5:i386 libtxc-dxtn-s2tc0:i386 libunistring0
  liburi-perl libusb-0.1-4:i386 libuuid1:i386 libv4l-0:i386 libv4lconvert0:i386 libwbclient0 libwind0-heimdal libwind0-heimdal:i386 libwww-perl
  libwww-robotrules-perl libx11-6 libx11-6:i386 libx11-xcb1 libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb1:i386
  libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3 libxfixes3:i386 libxi6 libxi6:i386 libxinerama1:i386
  libxml2:i386 libxpm4:i386 libxrandr2:i386 libxrender1:i386 libxslt1.1:i386 libxt6:i386 libxxf86vm1:i386 netpbm odbcinst odbcinst1debian2
  samba-common smbclient ttf-droid ttf-mscorefonts-installer ttf-umefont ttf-unfonts-core unixodbc unrar winbind wine-gecko1.4 wine-gecko1.4:i386
  wine1.4 wine1.4-amd64 wine1.4-common wine1.4-i386:i386 winetricks zlib1g:i386
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base libterm-readline-gnu-perl libterm-readline-perl-perl imagemagick-doc autotrace curl enscript ffmpeg
  gimp gnuplot grads hp2xx html2ps libwmf-bin mplayer povray radiance texlive-base-bin transfig ufraw-batch libasound2-plugins:i386
  libasound2-python:i386 glibc-doc glibc-doc:i386 locales:i386 cups-common:i386 rng-tools:i386 libgd-tools:i386 libglide3 libglide3:i386 gnutls-bin
  gnutls-bin:i386 gphoto2:i386 gtkam:i386 gpm:i386 krb5-doc:i386 krb5-user:i386 libvisual-0.4-plugins:i386 gstreamer-codec-install:i386
  gnome-codec-install:i386 gstreamer0.10-tools:i386 gstreamer0.10-plugins-base:i386 libdata-dump-perl liblcms-utils:i386 libcrypt-ssleay-perl
  libmyodbc odbc-postgresql tdsodbc unixodbc-bin hpoj:i386 hplip:i386 libsane-extras:i386 sane-utils:i386 libsasl2-modules-otp:i386
  libsasl2-modules-ldap:i386 libsasl2-modules-sql:i386 libsasl2-modules-gssapi-mit:i386 libsasl2-modules-gssapi-heimdal:i386 libauthen-ntlm-perl
  cifs-utils dosbox
Recommended packages:
  libtxc-dxtn0 libtxc-dxtn0:i386 xml-core:i386 gettext gettext:i386 unixodbc:i386
The following NEW packages will be installed:
  binfmt-support cabextract fonts-droid fonts-horai-umefont fonts-unfonts-core gcc-4.6-base:i386 gnome-exe-thumbnailer icoutils imagemagick
  imagemagick-common libasn1-8-heimdal:i386 libasound2:i386 libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386 libc6:i386
  libcapi20-3 libcapi20-3:i386 libcdt4 libcomerr2:i386 libcups2:i386 libdb5.1:i386 libdbus-1-3:i386 libdrm-intel1:i386 libdrm-nouveau2:i386
  libdrm-radeon1:i386 libdrm2:i386 libencode-locale-perl libexif12:i386 libexpat1:i386 libffi6:i386 libfile-listing-perl libfont-afm-perl
  libfontconfig1:i386 libfreetype6:i386 libgcc1:i386 libgcrypt11:i386 libgd2-xpm:i386 libgettextpo0 libgif4 libgif4:i386
  libgl1-mesa-dri-lts-raring:i386 libgl1-mesa-glx-lts-raring:i386 libglapi-mesa-lts-raring:i386 libglib2.0-0:i386 libglu1-mesa:i386 libgnutls26:i386
  libgpg-error0:i386 libgphoto2-2:i386 libgphoto2-port0:i386 libgpm2:i386 libgraph4 libgssapi-krb5-2:i386 libgssapi3-heimdal:i386
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386 libgvc5 libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386
  libhtml-form-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl
  libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libhx509-5-heimdal:i386 libice6:i386 libieee1284-3:i386 libilmbase6
  libio-socket-inet6-perl libio-socket-ssl-perl libjpeg-turbo8:i386 libjpeg8:i386 libk5crypto3:i386 libkeyutils1:i386 libkrb5-26-heimdal:i386
  libkrb5-3:i386 libkrb5support0:i386 liblcms1:i386 libldap-2.4-2:i386 libllvm3.2:i386 liblqr-1-0 libltdl7:i386 liblwp-mediatypes-perl
  liblwp-protocol-https-perl libmagickcore4 libmagickcore4-extra libmagickwand4 libmailtools-perl libmpg123-0 libmpg123-0:i386 libncurses5:i386
  libnet-http-perl libnet-ssleay-perl libnetpbm10 libodbc1 libopenal-data libopenal1 libopenal1:i386 libopenexr6 liborc-0.4-0:i386 libp11-kit0:i386
  libpam-winbind libpathplan4 libpciaccess0:i386 libpcre3:i386 libpng12-0:i386 libroken18-heimdal:i386 libsane:i386 libsasl2-2:i386
  libsasl2-modules:i386 libselinux1:i386 libsm6:i386 libsocket6-perl libsqlite3-0:i386 libssl1.0.0:i386 libstdc++6:i386 libtasn1-3:i386 libtiff4:i386
  libtimedate-perl libtinfo5:i386 libtxc-dxtn-s2tc0:i386 libunistring0 liburi-perl libusb-0.1-4:i386 libuuid1:i386 libv4l-0:i386 libv4lconvert0:i386
  libwind0-heimdal:i386 libwww-perl libwww-robotrules-perl libx11-6:i386 libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-glx0:i386
  libxcb1:i386 libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxi6:i386 libxinerama1:i386
  libxml2:i386 libxpm4:i386 libxrandr2:i386 libxrender1:i386 libxslt1.1:i386 libxt6:i386 libxxf86vm1:i386 netpbm odbcinst odbcinst1debian2 ttf-droid
  ttf-mscorefonts-installer ttf-umefont ttf-unfonts-core unixodbc unrar winbind wine wine-gecko1.4 wine-gecko1.4:i386 wine1.4 wine1.4-amd64
  wine1.4-common wine1.4-i386:i386 winetricks zlib1g:i386
The following packages will be upgraded:
  grub-common grub-pc grub-pc-bin grub2-common libasn1-8-heimdal libavahi-client3 libavahi-common-data libavahi-common3 libc-bin libc-dev-bin libc6
  libc6-dev libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdrm2 libgl1-mesa-dri-lts-raring libgl1-mesa-glx-lts-raring libglapi-mesa-lts-raring
  libglib2.0-0 libglib2.0-bin libglu1-mesa libgnutls26 libgssapi3-heimdal libhcrypto4-heimdal libheimbase1-heimdal libheimntlm0-heimdal
  libhx509-5-heimdal libjpeg-turbo8 libkrb5-26-heimdal libldap-2.4-2 libroken18-heimdal libssl1.0.0 libwbclient0 libwind0-heimdal libx11-6
  libx11-xcb1 libxfixes3 libxi6 samba-common smbclient
41 upgraded, 176 newly installed, 0 to remove and 195 not upgraded.
Need to get 60.9 kB/223 MB of archives.
After this operation, 515 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libc6-dev libc-dev-bin libc-bin libc6 libssl1.0.0 gcc-4.6-base libgcc1 libc6 libsqlite3-0 libstdc++6 libusb-0.1-4 libcomerr2 libdb5.1 libdbus-1-3
  libdrm2 libdrm-intel1 libdrm2 zlib1g libpciaccess0 libdrm-intel1 libdrm-radeon1 libdrm-radeon1 libffi6 libglib2.0-bin libglib2.0-0 libpcre3
  libselinux1 libglib2.0-0 libtinfo5 libncurses5 libpng12-0 libssl1.0.0 libuuid1 libroken18-heimdal libasn1-8-heimdal libroken18-heimdal
  libasn1-8-heimdal libgpg-error0 libgcrypt11 libgnutls26 libp11-kit0 libtasn1-3 libgnutls26 libkrb5support0 libk5crypto3 libkeyutils1 libkrb5-3
  libgssapi-krb5-2 libhcrypto4-heimdal libheimbase1-heimdal libwind0-heimdal libhx509-5-heimdal libkrb5-26-heimdal libheimntlm0-heimdal
  libgssapi3-heimdal libhcrypto4-heimdal libheimbase1-heimdal libwind0-heimdal libhx509-5-heimdal libkrb5-26-heimdal libheimntlm0-heimdal
  libgssapi3-heimdal libldap-2.4-2 libsasl2-2 libldap-2.4-2 libx11-6 libxau6 libxdmcp6 libxcb1 libx11-6 libxext6 libxml2 libasound2
  libavahi-common-data libavahi-common3 libavahi-client3 libavahi-common-data libavahi-common3 libavahi-client3 libcups2 libdrm-nouveau2
  libdrm-nouveau2 libexif12 libexpat1 libfreetype6 libfontconfig1 libjpeg-turbo8 libjpeg-turbo8 libjpeg8 libxpm4 libgd2-xpm libunistring0
  libgettextpo0 libgif4 libgif4 libx11-xcb1 libxfixes3 libgl1-mesa-dri-lts-raring libgl1-mesa-glx-lts-raring libglapi-mesa-lts-raring
  libglapi-mesa-lts-raring libllvm3.2 libgl1-mesa-dri-lts-raring libx11-xcb1 libxcb-dri2-0 libxcb-glx0 libxdamage1 libxfixes3 libxxf86vm1
  libgl1-mesa-glx-lts-raring libltdl7 libgphoto2-port0 libgphoto2-2 libgpm2 libgstreamer0.10-0 liborc-0.4-0 libgstreamer-plugins-base0.10-0 libice6
  libieee1284-3 liblcms1 libmpg123-0 libmpg123-0 libodbc1 libtiff4 libv4lconvert0 libv4l-0 libsane libsm6 libwbclient0 libxcomposite1 libxrender1
  libxcursor1 libxi6 libxi6 libxinerama1 libxrandr2 libxslt1.1 libxt6 odbcinst odbcinst1debian2 cabextract ttf-mscorefonts-installer wine-gecko1.4
  wine-gecko1.4 libglu1-mesa libopenal-data libopenal1 wine1.4-common wine1.4-amd64 binfmt-support libglu1-mesa libopenal1 wine1.4-i386 wine1.4
  winetricks libcapi20-3 libcapi20-3 libtxc-dxtn-s2tc0 libsasl2-modules fonts-droid fonts-horai-umefont fonts-unfonts-core grub-pc grub-pc-bin
  grub2-common grub-common libencode-locale-perl libtimedate-perl libhttp-date-perl libfile-listing-perl liburi-perl libhtml-tagset-perl
  libhtml-parser-perl libhtml-tree-perl liblwp-mediatypes-perl libhttp-message-perl libhttp-cookies-perl libhttp-negotiate-perl libnet-http-perl
  libnet-ssleay-perl libio-socket-ssl-perl liblwp-protocol-https-perl libwww-robotrules-perl libwww-perl icoutils liblqr-1-0 imagemagick-common
  libmagickcore4 libmagickwand4 imagemagick libcdt4 libfont-afm-perl libgraph4 libpathplan4 libgvc5 libhtml-form-perl libhtml-format-perl
  libhttp-daemon-perl libilmbase6 libsocket6-perl libio-socket-inet6-perl libopenexr6 libmagickcore4-extra libmailtools-perl libnetpbm10 smbclient
  samba-common winbind libpam-winbind netpbm ttf-droid ttf-umefont ttf-unfonts-core unixodbc unrar gnome-exe-thumbnailer wine
Install these packages without verification [y/N]? y
Err http://in.archive.ubuntu.com/ubuntu/ precise-updates/universe libtxc-dxtn-s2tc0 i386 0~git20110809-2.1
  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/universe/s/s2tc/libtxc-dxtn-s2tc0_0~git20110809-2.1_i386.deb  404  Not Found [IP: 91.189.92.156 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@Shiva:~# 
root@Shiva:~# 

```

---

### Post by Bashing-om on 2014-01-16
thekeshav; Hi !

1st, why are you running the system from root ? .. Highly not advised !
OK, let's see what the state of the system is:
Post back to us the out put of terminal commands - as the normal user -:
```

sudo apt-get update
sudo apt-get upgrade
apt-cache policy wine
sudo dpkg -C

```

From a firm foundation
[INDENT][INDENT][INDENT]we can look at any remaining issues
[/INDENT][/INDENT][/INDENT]

---

### Post by wildmanne39 on 2014-01-16
*Thread moved to **General Help**.*

---

### Post by wildmanne39 on 2014-01-16
Please use normal fonts.
Thanks

---


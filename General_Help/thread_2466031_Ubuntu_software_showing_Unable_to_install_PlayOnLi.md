---
title: "Ubuntu software showing: Unable to install PlayOnLinux as not supported"
date: 2021-08-18
forum: General Help
---

### Post by biite on 2021-08-18
Hi all,

On my 21.04 install I get the following message when opening Ubuntu Software: Unable to install PlayOnLinux as not supported

I've had it installed in the past and removed it via Ubuntu software, but it keeps showing this message.
Suspected some remnants might be left so tried 'apt purge playonlinux', but it had nothing to remove.

Any ideas? I've not been able to find the cause yet?

Regards,
Biite

---

### Post by Holger_Gehrke on 2021-08-18
Try installing from the command line using apt (sudo apt install playonlinux). It might not work, but if it doesn't it will give you a more detailed error message.

Holger

---

### Post by monkeybrain20122 on 2021-08-18
Works here
```

$ apt -s install playonlinux
NOTE: This is only a simulation!
      apt needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  fonts-wine gcc-11-base:i386 glib-networking:i386
  gstreamer1.0-plugins-base:i386 gstreamer1.0-plugins-good:i386
  gstreamer1.0-x:i386 icoutils imagemagick imagemagick-6.q16 jq libaa1:i386
  libapparmor1:i386 libasn1-8-heimdal:i386 libasound2:i386
  libasound2-plugins:i386 libasyncns0:i386 libatomic1:i386
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
  libavc1394-0:i386 libblkid1:i386 libbrotli1:i386 libbsd0:i386
  libbz2-1.0:i386 libc6:i386 libcaca0:i386 libcairo-gobject2:i386
  libcairo2:i386 libcap2:i386 libcapi20-3:i386 libcdparanoia0:i386
  libcom-err2:i386 libcrypt1:i386 libcups2:i386 libcurl3-gnutls:i386
  libcurl4:i386 libdatrie1:i386 libdb5.3:i386 libdbus-1-3:i386
  libdeflate0:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386
  libdrm-radeon1:i386 libdrm2:i386 libdv4:i386 libdw1:i386 libedit2:i386
  libelf1:i386 libexif12:i386 libexpat1:i386 libfaudio0:i386
  libffi8ubuntu1:i386 libflac8:i386 libfontconfig1:i386 libfreetype6:i386
  libfribidi0:i386 libgbm1:i386 libgcc-s1:i386 libgcrypt20:i386 libgd3:i386
  libgdbm-compat4:i386 libgdbm6:i386 libgdk-pixbuf-2.0-0:i386 libgl1:i386
  libgl1-mesa-dri:i386 libglapi-mesa:i386 libglib2.0-0:i386 libglu1-mesa:i386
  libglvnd0:i386 libglx-mesa0:i386 libglx0:i386 libgmp10:i386 libgnutls30:i386
  libgpg-error-l10n libgpg-error0:i386 libgphoto2-6:i386
  libgphoto2-port12:i386 libgpm2:i386 libgraphite2-3:i386 libgsm1:i386
  libgssapi-krb5-2:i386 libgssapi3-heimdal:i386
  libgstreamer-plugins-base1.0-0:i386 libgstreamer-plugins-good1.0-0:i386
  libgstreamer1.0-0:i386 libgudev-1.0-0:i386 libharfbuzz0b:i386
  libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386
  libhogweed6:i386 libhx509-5-heimdal:i386 libicu67:i386 libidn2-0:i386
  libiec61883-0:i386 libieee1284-3:i386 libjack-jackd2-0:i386 libjbig0:i386
  libjpeg-turbo8:i386 libjpeg8:i386 libjq1 libjxr-tools libjxr0
  libk5crypto3:i386 libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386
  libkrb5support0:i386 liblcms2-2:i386 libldap-2.4-2:i386 libllvm12:i386
  libltdl7:i386 liblz4-1:i386 liblzma5:i386 libmagickcore-6.q16-6-extra
  libmd0:i386 libmount1:i386 libmp3lame0:i386 libmpg123-0:i386
  libncurses6:i386 libncursesw6:i386 libnetpbm10 libnettle8:i386
  libnghttp2-14:i386 libnsl2:i386 libnspr4:i386 libnss-nis:i386
  libnss-nisplus:i386 libnss3:i386 libodbc1:i386 libogg0:i386 libonig5
  libopenal1:i386 libopenjp2-7:i386 libopus0:i386 liborc-0.4-0:i386
  libosmesa6:i386 libp11-kit0:i386 libpango-1.0-0:i386
  libpangocairo-1.0-0:i386 libpangoft2-1.0-0:i386 libpcap0.8:i386 libpci3:i386
  libpciaccess0:i386 libpcre2-8-0:i386 libpcre3:i386 libperl5.32:i386
  libpixman-1-0:i386 libpng16-16:i386 libpoppler-glib8:i386 libpoppler107:i386
  libproxy1v5:i386 libpsl5:i386 libpulse0:i386 libraw1394-11:i386
  libroken18-heimdal:i386 librtmp1:i386 libsamplerate0:i386 libsane1:i386
  libsasl2-2:i386 libsasl2-modules:i386 libsasl2-modules-db:i386
  libsdl2-2.0-0:i386 libselinux1:i386 libsensors5:i386 libshout3:i386
  libslang2:i386 libsndfile1:i386 libsndio7.0:i386 libsnmp40:i386
  libsoup2.4-1:i386 libspeex1:i386 libsqlite3-0:i386 libssh-4:i386
  libssl1.1:i386 libstb0:i386 libstdc++6:i386 libsystemd0:i386 libtag1v5:i386
  libtag1v5-vanilla:i386 libtasn1-6:i386 libthai0:i386 libtheora0:i386
  libtiff5:i386 libtinfo6:i386 libtirpc3:i386 libtwolame0:i386 libudev1:i386
  libunistring2:i386 libunwind8:i386 libusb-1.0-0:i386 libuuid1:i386
  libv4l-0:i386 libv4lconvert0:i386 libvisual-0.4-0:i386 libvkd3d1:i386
  libvorbis0a:i386 libvorbisenc2:i386 libvpx6:i386 libvulkan1:i386
  libwavpack1:i386 libwayland-client0:i386 libwayland-cursor0:i386
  libwayland-egl1:i386 libwayland-server0:i386 libwebp6:i386
  libwind0-heimdal:i386 libwine:i386 libwrap0:i386 libx11-6:i386
  libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386
  libxcb-glx0:i386 libxcb-present0:i386 libxcb-randr0:i386 libxcb-render0:i386
  libxcb-shm0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 libxcb1:i386
  libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386
  libxext6:i386 libxfixes3:i386 libxi6:i386 libxinerama1:i386
  libxkbcommon0:i386 libxml2:i386 libxpm4:i386 libxrandr2:i386
  libxrender1:i386 libxshmfence1:i386 libxslt1.1:i386 libxss1:i386 libxv1:i386
  libxxf86vm1:i386 libzstd1:i386 mesa-vulkan-drivers:i386 netpbm
  ocl-icd-libopencl1:i386 p7zip p7zip-full python3-natsort python3-wxgtk4.0
  wine wine32:i386 zlib1g:i386
Suggested packages:
  gvfs:i386 libterm-readline-gnu-perl | libterm-readline-perl-perl
  imagemagick-doc autotrace enscript ffmpeg gimp grads graphviz hp2xx html2ps
  libwmf-bin mplayer povray radiance texlive-base-bin transfig ufraw-batch
  glibc-doc:i386 locales:i386 libdv-bin:i386 oss-compat:i386 rng-tools:i386
  libgd-tools:i386 gdbm-l10n:i386 gnutls-bin:i386 gphoto2:i386 gpm:i386
  krb5-doc:i386 krb5-user:i386 libvisual-0.4-plugins:i386
  gstreamer1.0-tools:i386 jackd2:i386 inkscape libmyodbc:i386
  odbc-postgresql:i386 tdsodbc:i386 unixodbc-bin:i386 libportaudio2:i386
  opus-tools:i386 libraw1394-doc:i386 hplip:i386
  libsasl2-modules-gssapi-mit:i386 | libsasl2-modules-gssapi-heimdal:i386
  libsasl2-modules-ldap:i386 libsasl2-modules-otp:i386
  libsasl2-modules-sql:i386 lm-sensors:i386 sndiod:i386 speex:i386
  gstreamer1.0-libav:i386 gstreamer1.0-plugins-bad:i386
  gstreamer1.0-plugins-ugly:i386 opencl-icd:i386 p7zip-rar scrot winbind
  python-natsort-doc wx3.0-doc q4wine winetricks wine-binfmt dosbox
  exe-thumbnailer | kio-extras wine32-preloader:i386
Recommended packages:
  sane-airscan:i386
The following NEW packages will be installed:
  fonts-wine gcc-11-base:i386 glib-networking:i386
  gstreamer1.0-plugins-base:i386 gstreamer1.0-plugins-good:i386
  gstreamer1.0-x:i386 icoutils imagemagick imagemagick-6.q16 jq libaa1:i386
  libapparmor1:i386 libasn1-8-heimdal:i386 libasound2:i386
  libasound2-plugins:i386 libasyncns0:i386 libatomic1:i386
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
  libavc1394-0:i386 libblkid1:i386 libbrotli1:i386 libbsd0:i386
  libbz2-1.0:i386 libc6:i386 libcaca0:i386 libcairo-gobject2:i386
  libcairo2:i386 libcap2:i386 libcapi20-3:i386 libcdparanoia0:i386
  libcom-err2:i386 libcrypt1:i386 libcups2:i386 libcurl3-gnutls:i386
  libcurl4:i386 libdatrie1:i386 libdb5.3:i386 libdbus-1-3:i386
  libdeflate0:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386
  libdrm-radeon1:i386 libdrm2:i386 libdv4:i386 libdw1:i386 libedit2:i386
  libelf1:i386 libexif12:i386 libexpat1:i386 libfaudio0:i386
  libffi8ubuntu1:i386 libflac8:i386 libfontconfig1:i386 libfreetype6:i386
  libfribidi0:i386 libgbm1:i386 libgcc-s1:i386 libgcrypt20:i386 libgd3:i386
  libgdbm-compat4:i386 libgdbm6:i386 libgdk-pixbuf-2.0-0:i386 libgl1:i386
  libgl1-mesa-dri:i386 libglapi-mesa:i386 libglib2.0-0:i386 libglu1-mesa:i386
  libglvnd0:i386 libglx-mesa0:i386 libglx0:i386 libgmp10:i386 libgnutls30:i386
  libgpg-error-l10n libgpg-error0:i386 libgphoto2-6:i386
  libgphoto2-port12:i386 libgpm2:i386 libgraphite2-3:i386 libgsm1:i386
  libgssapi-krb5-2:i386 libgssapi3-heimdal:i386
  libgstreamer-plugins-base1.0-0:i386 libgstreamer-plugins-good1.0-0:i386
  libgstreamer1.0-0:i386 libgudev-1.0-0:i386 libharfbuzz0b:i386
  libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386
  libhogweed6:i386 libhx509-5-heimdal:i386 libicu67:i386 libidn2-0:i386
  libiec61883-0:i386 libieee1284-3:i386 libjack-jackd2-0:i386 libjbig0:i386
  libjpeg-turbo8:i386 libjpeg8:i386 libjq1 libjxr-tools libjxr0
  libk5crypto3:i386 libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386
  libkrb5support0:i386 liblcms2-2:i386 libldap-2.4-2:i386 libllvm12:i386
  libltdl7:i386 liblz4-1:i386 liblzma5:i386 libmagickcore-6.q16-6-extra
  libmd0:i386 libmount1:i386 libmp3lame0:i386 libmpg123-0:i386
  libncurses6:i386 libncursesw6:i386 libnetpbm10 libnettle8:i386
  libnghttp2-14:i386 libnsl2:i386 libnspr4:i386 libnss-nis:i386
  libnss-nisplus:i386 libnss3:i386 libodbc1:i386 libogg0:i386 libonig5
  libopenal1:i386 libopenjp2-7:i386 libopus0:i386 liborc-0.4-0:i386
  libosmesa6:i386 libp11-kit0:i386 libpango-1.0-0:i386
  libpangocairo-1.0-0:i386 libpangoft2-1.0-0:i386 libpcap0.8:i386 libpci3:i386
  libpciaccess0:i386 libpcre2-8-0:i386 libpcre3:i386 libperl5.32:i386
  libpixman-1-0:i386 libpng16-16:i386 libpoppler-glib8:i386 libpoppler107:i386
  libproxy1v5:i386 libpsl5:i386 libpulse0:i386 libraw1394-11:i386
  libroken18-heimdal:i386 librtmp1:i386 libsamplerate0:i386 libsane1:i386
  libsasl2-2:i386 libsasl2-modules:i386 libsasl2-modules-db:i386
  libsdl2-2.0-0:i386 libselinux1:i386 libsensors5:i386 libshout3:i386
  libslang2:i386 libsndfile1:i386 libsndio7.0:i386 libsnmp40:i386
  libsoup2.4-1:i386 libspeex1:i386 libsqlite3-0:i386 libssh-4:i386
  libssl1.1:i386 libstb0:i386 libstdc++6:i386 libsystemd0:i386 libtag1v5:i386
  libtag1v5-vanilla:i386 libtasn1-6:i386 libthai0:i386 libtheora0:i386
  libtiff5:i386 libtinfo6:i386 libtirpc3:i386 libtwolame0:i386 libudev1:i386
  libunistring2:i386 libunwind8:i386 libusb-1.0-0:i386 libuuid1:i386
  libv4l-0:i386 libv4lconvert0:i386 libvisual-0.4-0:i386 libvkd3d1:i386
  libvorbis0a:i386 libvorbisenc2:i386 libvpx6:i386 libvulkan1:i386
  libwavpack1:i386 libwayland-client0:i386 libwayland-cursor0:i386
  libwayland-egl1:i386 libwayland-server0:i386 libwebp6:i386
  libwind0-heimdal:i386 libwine:i386 libwrap0:i386 libx11-6:i386
  libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386
  libxcb-glx0:i386 libxcb-present0:i386 libxcb-randr0:i386 libxcb-render0:i386
  libxcb-shm0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 libxcb1:i386
  libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386
  libxext6:i386 libxfixes3:i386 libxi6:i386 libxinerama1:i386
  libxkbcommon0:i386 libxml2:i386 libxpm4:i386 libxrandr2:i386
  libxrender1:i386 libxshmfence1:i386 libxslt1.1:i386 libxss1:i386 libxv1:i386
  libxxf86vm1:i386 libzstd1:i386 mesa-vulkan-drivers:i386 netpbm
  ocl-icd-libopencl1:i386 p7zip p7zip-full playonlinux python3-natsort
  python3-wxgtk4.0 wine wine32:i386 zlib1g:i386
0 upgraded, 254 newly installed, 0 to remove and 0 not upgraded.
Inst gcc-11-base:i386 (11.1.0-1ubuntu1~21.04 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Inst libgcc-s1:i386 (11.1.0-1ubuntu1~21.04 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386]) []
Inst libcrypt1:i386 (1:4.4.17-1ubuntu3 Ubuntu:21.04/hirsute [i386]) []
Inst libc6:i386 (2.33-0ubuntu5 Ubuntu:21.04/hirsute [i386])
Inst libcap2:i386 (1:2.44-1build1 Ubuntu:21.04/hirsute [i386])
Inst libgpg-error0:i386 (1.38-2build1 Ubuntu:21.04/hirsute [i386])
Inst libgcrypt20:i386 (1.8.7-2ubuntu2 Ubuntu:21.04/hirsute [i386])
Inst liblz4-1:i386 (1.9.3-1ubuntu0.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Inst liblzma5:i386 (5.2.5-1.0build2 Ubuntu:21.04/hirsute [i386])
Inst libzstd1:i386 (1.4.8+dfsg-2build2 Ubuntu:21.04/hirsute [i386])
Conf gcc-11-base:i386 (11.1.0-1ubuntu1~21.04 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Conf libcrypt1:i386 (1:4.4.17-1ubuntu3 Ubuntu:21.04/hirsute [i386])
Conf libgcc-s1:i386 (11.1.0-1ubuntu1~21.04 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Conf libc6:i386 (2.33-0ubuntu5 Ubuntu:21.04/hirsute [i386])
Conf libcap2:i386 (1:2.44-1build1 Ubuntu:21.04/hirsute [i386])
Conf libgpg-error0:i386 (1.38-2build1 Ubuntu:21.04/hirsute [i386])
Conf libgcrypt20:i386 (1.8.7-2ubuntu2 Ubuntu:21.04/hirsute [i386])
Conf liblz4-1:i386 (1.9.3-1ubuntu0.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Conf liblzma5:i386 (5.2.5-1.0build2 Ubuntu:21.04/hirsute [i386])
Conf libzstd1:i386 (1.4.8+dfsg-2build2 Ubuntu:21.04/hirsute [i386])
Inst libsystemd0:i386 (247.3-3ubuntu3.4 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Inst libblkid1:i386 (2.36.1-7ubuntu2 Ubuntu:21.04/hirsute [i386])
Inst libbz2-1.0:i386 (1.0.8-4ubuntu3 Ubuntu:21.04/hirsute [i386])
Inst libcom-err2:i386 (1.45.7-1ubuntu2 Ubuntu:21.04/hirsute [i386])
Inst libdb5.3:i386 (5.3.28+dfsg1-0.6ubuntu4 Ubuntu:21.04/hirsute [i386])
Inst libgmp10:i386 (2:6.2.1+dfsg-1ubuntu2 Ubuntu:21.04/hirsute [i386])
Inst libpcre2-8-0:i386 (10.36-2ubuntu5 Ubuntu:21.04/hirsute [i386])
Inst libselinux1:i386 (3.1-3build1 Ubuntu:21.04/hirsute [i386])
Inst libmount1:i386 (2.36.1-7ubuntu2 Ubuntu:21.04/hirsute [i386])
Inst libtinfo6:i386 (6.2+20201114-2build1 Ubuntu:21.04/hirsute [i386])
Inst libncurses6:i386 (6.2+20201114-2build1 Ubuntu:21.04/hirsute [i386])
Inst libncursesw6:i386 (6.2+20201114-2build1 Ubuntu:21.04/hirsute [i386])
Inst libpcre3:i386 (2:8.39-13build3 Ubuntu:21.04/hirsute [i386])
Inst libudev1:i386 (247.3-3ubuntu3.4 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Inst libuuid1:i386 (2.36.1-7ubuntu2 Ubuntu:21.04/hirsute [i386])
Inst zlib1g:i386 (1:1.2.11.dfsg-2ubuntu6 Ubuntu:21.04/hirsute [i386])
Inst libapparmor1:i386 (3.0.0-0ubuntu7.1 Ubuntu:21.04/hirsute-updates [i386])
Inst libmd0:i386 (1.0.3-3build1 Ubuntu:21.04/hirsute [i386])
Inst libbsd0:i386 (0.11.3-1ubuntu2 Ubuntu:21.04/hirsute [i386])
Inst libdbus-1-3:i386 (1.12.20-1ubuntu3 Ubuntu:21.04/hirsute [i386])
Inst libelf1:i386 (0.183-8 Ubuntu:21.04/hirsute [i386])
Inst libexpat1:i386 (2.2.10-2 Ubuntu:21.04/hirsute [i386])
Inst libffi8ubuntu1:i386 (3.4~20200819gead65ca871-0ubuntu5 Ubuntu:21.04/hirsute [i386])
Inst libfribidi0:i386 (1.0.8-2ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libglib2.0-0:i386 (2.68.1-1~ubuntu21.04.1 Ubuntu:21.04/hirsute-updates [i386])
Inst libnettle8:i386 (3.7-2.1ubuntu1.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Inst libhogweed6:i386 (3.7-2.1ubuntu1.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Inst libunistring2:i386 (0.9.10-4 Ubuntu:21.04/hirsute [i386])
Inst libidn2-0:i386 (2.3.0-5 Ubuntu:21.04/hirsute [i386])
Inst libp11-kit0:i386 (0.23.22-1 Ubuntu:21.04/hirsute [i386])
Inst libtasn1-6:i386 (4.16.0-2 Ubuntu:21.04/hirsute [i386])
Inst libgnutls30:i386 (3.7.1-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libkrb5support0:i386 (1.18.3-4 Ubuntu:21.04/hirsute [i386])
Inst libk5crypto3:i386 (1.18.3-4 Ubuntu:21.04/hirsute [i386])
Inst libkeyutils1:i386 (1.6.1-2ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libssl1.1:i386 (1.1.1j-1ubuntu3.2 Ubuntu:21.04/hirsute-updates [i386])
Inst libkrb5-3:i386 (1.18.3-4 Ubuntu:21.04/hirsute [i386])
Inst libgssapi-krb5-2:i386 (1.18.3-4 Ubuntu:21.04/hirsute [i386])
Inst libstdc++6:i386 (11.1.0-1ubuntu1~21.04 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Inst libicu67:i386 (67.1-6ubuntu2 Ubuntu:21.04/hirsute [i386])
Inst libtirpc3:i386 (1.3.1-1build1 Ubuntu:21.04/hirsute [i386])
Inst libnsl2:i386 (1.3.0-0ubuntu3 Ubuntu:21.04/hirsute [i386])
Inst libslang2:i386 (2.3.2-5build2 Ubuntu:21.04/hirsute [i386])
Inst libsqlite3-0:i386 (3.34.1-3 Ubuntu:21.04/hirsute [i386])
Inst libxml2:i386 (2.9.10+dfsg-6.3ubuntu0.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Inst libedit2:i386 (3.1-20191231-2 Ubuntu:21.04/hirsute [i386])
Inst libgdbm6:i386 (1.19-2 Ubuntu:21.04/hirsute [i386])
Inst libpcap0.8:i386 (1.10.0-2 Ubuntu:21.04/hirsute [i386])
Inst libpci3:i386 (1:3.7.0-5ubuntu2 Ubuntu:21.04/hirsute [i386])
Inst libpng16-16:i386 (1.6.37-3build3 Ubuntu:21.04/hirsute [i386])
Inst libpsl5:i386 (0.21.0-1.2 Ubuntu:21.04/hirsute [i386])
Inst libusb-1.0-0:i386 (2:1.0.24-3 Ubuntu:21.04/hirsute [i386])
Inst libxau6:i386 (1:1.0.9-1build3 Ubuntu:21.04/hirsute [i386])
Inst libxdmcp6:i386 (1:1.1.3-0ubuntu3 Ubuntu:21.04/hirsute [i386])
Inst libxcb1:i386 (1.14-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libx11-6:i386 (2:1.7.0-2ubuntu0.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Inst libxext6:i386 (2:1.3.4-0ubuntu3 Ubuntu:21.04/hirsute [i386])
Inst fonts-wine (5.0.3-3 Ubuntu:21.04/hirsute [all])
Inst libproxy1v5:i386 (0.4.17-1 Ubuntu:21.04/hirsute [i386])
Inst glib-networking:i386 (2.66.0-2 Ubuntu:21.04/hirsute [i386])
Inst libcdparanoia0:i386 (3.10.2+debian-13.1 Ubuntu:21.04/hirsute [i386])
Inst libdw1:i386 (0.183-8 Ubuntu:21.04/hirsute [i386])
Inst libunwind8:i386 (1.3.2-2 Ubuntu:21.04/hirsute [i386])
Inst libgstreamer1.0-0:i386 (1.18.4-1 Ubuntu:21.04/hirsute [i386])
Inst liborc-0.4-0:i386 (1:0.4.32-1 Ubuntu:21.04/hirsute [i386])
Inst libgstreamer-plugins-base1.0-0:i386 (1.18.4-1 Ubuntu:21.04/hirsute [i386])
Inst libogg0:i386 (1.3.4-0.1 Ubuntu:21.04/hirsute [i386])
Inst libopus0:i386 (1.3.1-0.1 Ubuntu:21.04/hirsute [i386])
Inst libbrotli1:i386 (1.0.9-2build2 Ubuntu:21.04/hirsute [i386])
Inst libfreetype6:i386 (2.10.4+dfsg-1build1 Ubuntu:21.04/hirsute [i386])
Inst libfontconfig1:i386 (2.13.1-4.2ubuntu3 Ubuntu:21.04/hirsute [i386])
Inst libpixman-1-0:i386 (0.40.0-1build2 Ubuntu:21.04/hirsute [i386])
Inst libxcb-render0:i386 (1.14-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libxcb-shm0:i386 (1.14-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libxrender1:i386 (1:0.9.10-1build2 Ubuntu:21.04/hirsute [i386])
Inst libcairo2:i386 (1.16.0-5ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libtheora0:i386 (1.1.1+dfsg.1-15ubuntu2 Ubuntu:21.04/hirsute [i386])
Inst libvisual-0.4-0:i386 (0.4.0-17 Ubuntu:21.04/hirsute [i386])
Inst libvorbis0a:i386 (1.3.7-1 Ubuntu:21.04/hirsute [i386])
Inst libvorbisenc2:i386 (1.3.7-1 Ubuntu:21.04/hirsute [i386])
Inst gstreamer1.0-plugins-base:i386 (1.18.4-1 Ubuntu:21.04/hirsute [i386])
Inst libgpm2:i386 (1.20.7-8 Ubuntu:21.04/hirsute [i386])
Inst libaa1:i386 (1.4p5-48 Ubuntu:21.04/hirsute [i386])
Inst libraw1394-11:i386 (2.1.2-2 Ubuntu:21.04/hirsute [i386])
Inst libavc1394-0:i386 (0.5.4-5 Ubuntu:21.04/hirsute [i386])
Inst libcaca0:i386 (0.99.beta19-2.2ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libcairo-gobject2:i386 (1.16.0-5ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libdv4:i386 (1.0.0-13 Ubuntu:21.04/hirsute [i386])
Inst libflac8:i386 (1.3.3-2 Ubuntu:21.04/hirsute [i386])
Inst libjpeg-turbo8:i386 (2.0.6-0ubuntu2 Ubuntu:21.04/hirsute [i386])
Inst libjpeg8:i386 (8c-2ubuntu8 Ubuntu:21.04/hirsute [i386])
Inst libdeflate0:i386 (1.7-1ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libjbig0:i386 (2.1-3.1build1 Ubuntu:21.04/hirsute [i386])
Inst libwebp6:i386 (0.6.1-2ubuntu0.21.04.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Inst libtiff5:i386 (4.2.0-1build1 Ubuntu:21.04/hirsute [i386])
Inst libgdk-pixbuf-2.0-0:i386 (2.42.2+dfsg-1build1 Ubuntu:21.04/hirsute [i386])
Inst libgstreamer-plugins-good1.0-0:i386 (1.18.4-1ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libgudev-1.0-0:i386 (1:234-1 Ubuntu:21.04/hirsute [i386])
Inst libiec61883-0:i386 (1.2.0-4build1 Ubuntu:21.04/hirsute [i386])
Inst libsamplerate0:i386 (0.2.1+ds0-1 Ubuntu:21.04/hirsute [i386])
Inst libjack-jackd2-0:i386 (1.9.17~dfsg-1 Ubuntu:21.04/hirsute [i386])
Inst libmp3lame0:i386 (3.100-3 Ubuntu:21.04/hirsute [i386])
Inst libmpg123-0:i386 (1.26.4-1 Ubuntu:21.04/hirsute [i386])
Inst libasyncns0:i386 (0.8-6 Ubuntu:21.04/hirsute [i386])
Inst libsndfile1:i386 (1.0.31-1ubuntu1.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Inst libwrap0:i386 (7.6.q-31 Ubuntu:21.04/hirsute [i386])
Inst libpulse0:i386 (1:14.2-1ubuntu1.1 Ubuntu:21.04/hirsute-updates [i386])
Inst libspeex1:i386 (1.2~rc1.2-1.1ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libshout3:i386 (2.4.5-1 Ubuntu:21.04/hirsute [i386])
Inst libsoup2.4-1:i386 (2.72.0-3 Ubuntu:21.04/hirsute [i386])
Inst libtag1v5-vanilla:i386 (1.11.1+dfsg.1-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libtag1v5:i386 (1.11.1+dfsg.1-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libtwolame0:i386 (0.4.0-2 Ubuntu:21.04/hirsute [i386])
Inst libv4lconvert0:i386 (1.20.0-3 Ubuntu:21.04/hirsute [i386])
Inst libv4l-0:i386 (1.20.0-3 Ubuntu:21.04/hirsute [i386])
Inst libvpx6:i386 (1.9.0-1 Ubuntu:21.04/hirsute [i386])
Inst libwavpack1:i386 (5.4.0-1 Ubuntu:21.04/hirsute [i386])
Inst libxdamage1:i386 (1:1.1.5-2 Ubuntu:21.04/hirsute [i386])
Inst libxfixes3:i386 (1:5.0.3-2build1 Ubuntu:21.04/hirsute [i386])
Inst gstreamer1.0-plugins-good:i386 (1.18.4-1ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libgraphite2-3:i386 (1.3.14-1 Ubuntu:21.04/hirsute [i386])
Inst libharfbuzz0b:i386 (2.7.4-1ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libdatrie1:i386 (0.2.13-1ubuntu2 Ubuntu:21.04/hirsute [i386])
Inst libthai0:i386 (0.1.28-4 Ubuntu:21.04/hirsute [i386])
Inst libpango-1.0-0:i386 (1.48.2-1build2 Ubuntu:21.04/hirsute [i386])
Inst libpangoft2-1.0-0:i386 (1.48.2-1build2 Ubuntu:21.04/hirsute [i386])
Inst libpangocairo-1.0-0:i386 (1.48.2-1build2 Ubuntu:21.04/hirsute [i386])
Inst libxv1:i386 (2:1.0.11-1 Ubuntu:21.04/hirsute [i386])
Inst gstreamer1.0-x:i386 (1.18.4-1 Ubuntu:21.04/hirsute [i386])
Inst icoutils (0.32.3-3 Ubuntu:21.04/hirsute [amd64])
Inst imagemagick-6.q16 (8:6.9.11.60+dfsg-1ubuntu1 Ubuntu:21.04/hirsute [amd64])
Inst imagemagick (8:6.9.11.60+dfsg-1ubuntu1 Ubuntu:21.04/hirsute [amd64])
Inst libonig5 (6.9.6-1 Ubuntu:21.04/hirsute [amd64])
Inst libjq1 (1.6-2.1ubuntu1 Ubuntu:21.04/hirsute [amd64])
Inst jq (1.6-2.1ubuntu1 Ubuntu:21.04/hirsute [amd64])
Inst libroken18-heimdal:i386 (7.7.0+dfsg-2 Ubuntu:21.04/hirsute [i386])
Inst libasn1-8-heimdal:i386 (7.7.0+dfsg-2 Ubuntu:21.04/hirsute [i386])
Inst libasound2:i386 (1.2.4-1.1ubuntu2 Ubuntu:21.04/hirsute [i386])
Inst libasound2-plugins:i386 (1.2.2-2 Ubuntu:21.04/hirsute [i386])
Inst libatomic1:i386 (11.1.0-1ubuntu1~21.04 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Inst libavahi-common-data:i386 (0.8-5ubuntu3.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Inst libavahi-common3:i386 (0.8-5ubuntu3.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Inst libavahi-client3:i386 (0.8-5ubuntu3.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Inst libcups2:i386 (2.3.3op2-3ubuntu3 Ubuntu:21.04/hirsute [i386])
Inst libheimbase1-heimdal:i386 (7.7.0+dfsg-2 Ubuntu:21.04/hirsute [i386])
Inst libhcrypto4-heimdal:i386 (7.7.0+dfsg-2 Ubuntu:21.04/hirsute [i386])
Inst libwind0-heimdal:i386 (7.7.0+dfsg-2 Ubuntu:21.04/hirsute [i386])
Inst libhx509-5-heimdal:i386 (7.7.0+dfsg-2 Ubuntu:21.04/hirsute [i386])
Inst libkrb5-26-heimdal:i386 (7.7.0+dfsg-2 Ubuntu:21.04/hirsute [i386])
Inst libheimntlm0-heimdal:i386 (7.7.0+dfsg-2 Ubuntu:21.04/hirsute [i386])
Inst libgssapi3-heimdal:i386 (7.7.0+dfsg-2 Ubuntu:21.04/hirsute [i386])
Inst libsasl2-modules-db:i386 (2.1.27+dfsg-2ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libsasl2-2:i386 (2.1.27+dfsg-2ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libldap-2.4-2:i386 (2.4.57+dfsg-2ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libnghttp2-14:i386 (1.43.0-1 Ubuntu:21.04/hirsute [i386])
Inst librtmp1:i386 (2.4+20151223.gitfa8646d.1-2build2 Ubuntu:21.04/hirsute [i386])
Inst libssh-4:i386 (0.9.5-1 Ubuntu:21.04/hirsute [i386])
Inst libcurl3-gnutls:i386 (7.74.0-1ubuntu2.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Inst libcurl4:i386 (7.74.0-1ubuntu2.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Inst libdrm2:i386 (2.4.107-1~kisak~h kisak-mesa fresh:21.04/hirsute [i386])
Inst libdrm-amdgpu1:i386 (2.4.107-1~kisak~h kisak-mesa fresh:21.04/hirsute [i386])
Inst libpciaccess0:i386 (0.16-1build2 Ubuntu:21.04/hirsute [i386])
Inst libdrm-intel1:i386 (2.4.107-1~kisak~h kisak-mesa fresh:21.04/hirsute [i386])
Inst libdrm-nouveau2:i386 (2.4.107-1~kisak~h kisak-mesa fresh:21.04/hirsute [i386])
Inst libdrm-radeon1:i386 (2.4.107-1~kisak~h kisak-mesa fresh:21.04/hirsute [i386])
Inst libexif12:i386 (0.6.22-3 Ubuntu:21.04/hirsute [i386])
Inst libwayland-server0:i386 (1.18.0-2~exp1.1 Ubuntu:21.04/hirsute [i386])
Inst libgbm1:i386 (21.2.0~kisak1~h kisak-mesa fresh:21.04/hirsute [i386])
Inst libwayland-client0:i386 (1.18.0-2~exp1.1 Ubuntu:21.04/hirsute [i386])
Inst libwayland-cursor0:i386 (1.18.0-2~exp1.1 Ubuntu:21.04/hirsute [i386])
Inst libwayland-egl1:i386 (1.18.0-2~exp1.1 Ubuntu:21.04/hirsute [i386])
Inst libxcursor1:i386 (1:1.2.0-2build2 Ubuntu:21.04/hirsute [i386])
Inst libxi6:i386 (2:1.7.10-1build2 Ubuntu:21.04/hirsute [i386])
Inst libxinerama1:i386 (2:1.1.4-2build2 Ubuntu:21.04/hirsute [i386])
Inst libxkbcommon0:i386 (1.0.3-2 Ubuntu:21.04/hirsute [i386])
Inst libxrandr2:i386 (2:1.5.2-0ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libxss1:i386 (1:1.2.3-1 Ubuntu:21.04/hirsute [i386])
Inst libxxf86vm1:i386 (1:1.1.4-1build1 Ubuntu:21.04/hirsute [i386])
Inst libsdl2-2.0-0:i386 (2.0.14+dfsg2-3 Ubuntu:21.04/hirsute [i386])
Inst libstb0:i386 (0.0~git20200713.b42009b-1 Ubuntu:21.04/hirsute [i386])
Inst libfaudio0:i386 (21.02-1 Ubuntu:21.04/hirsute [i386])
Inst libxpm4:i386 (1:3.5.12-1 Ubuntu:21.04/hirsute [i386])
Inst libgd3:i386 (2.3.0-2 Ubuntu:21.04/hirsute [i386])
Inst libgdbm-compat4:i386 (1.19-2 Ubuntu:21.04/hirsute [i386])
Inst libglapi-mesa:i386 (21.2.0~kisak1~h kisak-mesa fresh:21.04/hirsute [i386])
Inst libllvm12:i386 (1:12.0.1-1~kisak~h kisak-mesa fresh:21.04/hirsute [i386])
Inst libsensors5:i386 (1:3.6.0-7 Ubuntu:21.04/hirsute [i386])
Inst libvulkan1:i386 (1.2.162.0-1 Ubuntu:21.04/hirsute [i386])
Inst libgl1-mesa-dri:i386 (21.2.0~kisak1~h kisak-mesa fresh:21.04/hirsute [i386])
Inst libx11-xcb1:i386 (2:1.7.0-2ubuntu0.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Inst libxcb-dri2-0:i386 (1.14-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libxcb-dri3-0:i386 (1.14-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libxcb-glx0:i386 (1.14-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libxcb-present0:i386 (1.14-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libxcb-sync1:i386 (1.14-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libxcb-xfixes0:i386 (1.14-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libxshmfence1:i386 (1.3-1build2 Ubuntu:21.04/hirsute [i386])
Inst libglx-mesa0:i386 (21.2.0~kisak1~h kisak-mesa fresh:21.04/hirsute [i386])
Inst libgpg-error-l10n (1.38-2build1 Ubuntu:21.04/hirsute [all])
Inst libltdl7:i386 (2.4.6-15 Ubuntu:21.04/hirsute [i386])
Inst libgphoto2-port12:i386 (2.5.26-2 Ubuntu:21.04/hirsute [i386])
Inst libgphoto2-6:i386 (2.5.26-2 Ubuntu:21.04/hirsute [i386])
Inst libgsm1:i386 (1.0.18-2 Ubuntu:21.04/hirsute [i386])
Inst libieee1284-3:i386 (0.2.11-14 Ubuntu:21.04/hirsute [i386])
Inst libjxr0 (1.1-6build1 Ubuntu:21.04/hirsute [amd64])
Inst libjxr-tools (1.1-6build1 Ubuntu:21.04/hirsute [amd64])
Inst liblcms2-2:i386 (2.12~rc1-2 Ubuntu:21.04/hirsute [i386])
Inst libmagickcore-6.q16-6-extra (8:6.9.11.60+dfsg-1ubuntu1 Ubuntu:21.04/hirsute [amd64])
Inst libnetpbm10 (2:10.0-15.4 Ubuntu:21.04/hirsute [amd64])
Inst libnspr4:i386 (2:4.29-1 Ubuntu:21.04/hirsute [i386])
Inst libnss-nis:i386 (3.1-0ubuntu4 Ubuntu:21.04/hirsute [i386])
Inst libnss-nisplus:i386 (1.3-0ubuntu4 Ubuntu:21.04/hirsute [i386])
Inst libnss3:i386 (2:3.61-1ubuntu2 Ubuntu:21.04/hirsute [i386])
Inst libodbc1:i386 (2.3.6-0.1build1 Ubuntu:21.04/hirsute [i386])
Inst libosmesa6:i386 (21.2.0~kisak1~h kisak-mesa fresh:21.04/hirsute [i386])
Inst libperl5.32:i386 (5.32.1-3ubuntu2.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Inst libopenjp2-7:i386 (2.3.1-1ubuntu5 Ubuntu:21.04/hirsute [i386])
Inst libpoppler107:i386 (21.02.0-1 Ubuntu:21.04/hirsute [i386])
Inst libpoppler-glib8:i386 (21.02.0-1 Ubuntu:21.04/hirsute [i386])
Inst libsnmp40:i386 (5.9+dfsg-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libsane1:i386 (1.0.32-0ubuntu2 Ubuntu:21.04/hirsute [i386])
Inst libsasl2-modules:i386 (2.1.27+dfsg-2ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libsndio7.0:i386 (1.5.0-3 Ubuntu:21.04/hirsute [i386])
Inst libvkd3d1:i386 (1.1-5 Ubuntu:21.04/hirsute [i386])
Inst libopenal1:i386 (1:1.19.1-2 Ubuntu:21.04/hirsute [i386])
Inst ocl-icd-libopencl1:i386 (2.2.14-2 Ubuntu:21.04/hirsute [i386])
Inst libwine:i386 (5.0.3-3 Ubuntu:21.04/hirsute [i386])
Inst libxcb-randr0:i386 (1.14-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Inst libxcomposite1:i386 (1:0.4.5-1 Ubuntu:21.04/hirsute [i386])
Inst libxslt1.1:i386 (1.1.34-4 Ubuntu:21.04/hirsute [i386])
Inst mesa-vulkan-drivers:i386 (21.2.0~kisak1~h kisak-mesa fresh:21.04/hirsute [i386])
Inst netpbm (2:10.0-15.4 Ubuntu:21.04/hirsute [amd64])
Inst p7zip (16.02+dfsg-8 Ubuntu:21.04/hirsute [amd64])
Inst p7zip-full (16.02+dfsg-8 Ubuntu:21.04/hirsute [amd64])
Inst python3-natsort (7.1.0-1 Ubuntu:21.04/hirsute [all])
Inst python3-wxgtk4.0 (4.0.7+dfsg-10 Ubuntu:21.04/hirsute [amd64])
Inst wine32:i386 (5.0.3-3 Ubuntu:21.04/hirsute [i386])
Inst wine (5.0.3-3 Ubuntu:21.04/hirsute [all])
Inst playonlinux (4.3.4-2 Ubuntu:21.04/hirsute [all])
Inst libcapi20-3:i386 (1:3.27-3 Ubuntu:21.04/hirsute [i386])
Inst libglvnd0:i386 (1.3.2-1 Ubuntu:21.04/hirsute [i386])
Inst libglx0:i386 (1.3.2-1 Ubuntu:21.04/hirsute [i386])
Inst libgl1:i386 (1.3.2-1 Ubuntu:21.04/hirsute [i386])
Inst libglu1-mesa:i386 (9.0.1-1build1 Ubuntu:21.04/hirsute [i386])
Conf libsystemd0:i386 (247.3-3ubuntu3.4 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Conf libblkid1:i386 (2.36.1-7ubuntu2 Ubuntu:21.04/hirsute [i386])
Conf libbz2-1.0:i386 (1.0.8-4ubuntu3 Ubuntu:21.04/hirsute [i386])
Conf libcom-err2:i386 (1.45.7-1ubuntu2 Ubuntu:21.04/hirsute [i386])
Conf libdb5.3:i386 (5.3.28+dfsg1-0.6ubuntu4 Ubuntu:21.04/hirsute [i386])
Conf libgmp10:i386 (2:6.2.1+dfsg-1ubuntu2 Ubuntu:21.04/hirsute [i386])
Conf libpcre2-8-0:i386 (10.36-2ubuntu5 Ubuntu:21.04/hirsute [i386])
Conf libselinux1:i386 (3.1-3build1 Ubuntu:21.04/hirsute [i386])
Conf libmount1:i386 (2.36.1-7ubuntu2 Ubuntu:21.04/hirsute [i386])
Conf libtinfo6:i386 (6.2+20201114-2build1 Ubuntu:21.04/hirsute [i386])
Conf libncurses6:i386 (6.2+20201114-2build1 Ubuntu:21.04/hirsute [i386])
Conf libncursesw6:i386 (6.2+20201114-2build1 Ubuntu:21.04/hirsute [i386])
Conf libpcre3:i386 (2:8.39-13build3 Ubuntu:21.04/hirsute [i386])
Conf libudev1:i386 (247.3-3ubuntu3.4 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Conf libuuid1:i386 (2.36.1-7ubuntu2 Ubuntu:21.04/hirsute [i386])
Conf zlib1g:i386 (1:1.2.11.dfsg-2ubuntu6 Ubuntu:21.04/hirsute [i386])
Conf libapparmor1:i386 (3.0.0-0ubuntu7.1 Ubuntu:21.04/hirsute-updates [i386])
Conf libmd0:i386 (1.0.3-3build1 Ubuntu:21.04/hirsute [i386])
Conf libbsd0:i386 (0.11.3-1ubuntu2 Ubuntu:21.04/hirsute [i386])
Conf libdbus-1-3:i386 (1.12.20-1ubuntu3 Ubuntu:21.04/hirsute [i386])
Conf libelf1:i386 (0.183-8 Ubuntu:21.04/hirsute [i386])
Conf libexpat1:i386 (2.2.10-2 Ubuntu:21.04/hirsute [i386])
Conf libffi8ubuntu1:i386 (3.4~20200819gead65ca871-0ubuntu5 Ubuntu:21.04/hirsute [i386])
Conf libfribidi0:i386 (1.0.8-2ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libglib2.0-0:i386 (2.68.1-1~ubuntu21.04.1 Ubuntu:21.04/hirsute-updates [i386])
Conf libnettle8:i386 (3.7-2.1ubuntu1.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Conf libhogweed6:i386 (3.7-2.1ubuntu1.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Conf libunistring2:i386 (0.9.10-4 Ubuntu:21.04/hirsute [i386])
Conf libidn2-0:i386 (2.3.0-5 Ubuntu:21.04/hirsute [i386])
Conf libp11-kit0:i386 (0.23.22-1 Ubuntu:21.04/hirsute [i386])
Conf libtasn1-6:i386 (4.16.0-2 Ubuntu:21.04/hirsute [i386])
Conf libgnutls30:i386 (3.7.1-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libkrb5support0:i386 (1.18.3-4 Ubuntu:21.04/hirsute [i386])
Conf libk5crypto3:i386 (1.18.3-4 Ubuntu:21.04/hirsute [i386])
Conf libkeyutils1:i386 (1.6.1-2ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libssl1.1:i386 (1.1.1j-1ubuntu3.2 Ubuntu:21.04/hirsute-updates [i386])
Conf libkrb5-3:i386 (1.18.3-4 Ubuntu:21.04/hirsute [i386])
Conf libgssapi-krb5-2:i386 (1.18.3-4 Ubuntu:21.04/hirsute [i386])
Conf libstdc++6:i386 (11.1.0-1ubuntu1~21.04 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Conf libicu67:i386 (67.1-6ubuntu2 Ubuntu:21.04/hirsute [i386])
Conf libtirpc3:i386 (1.3.1-1build1 Ubuntu:21.04/hirsute [i386])
Conf libnsl2:i386 (1.3.0-0ubuntu3 Ubuntu:21.04/hirsute [i386])
Conf libslang2:i386 (2.3.2-5build2 Ubuntu:21.04/hirsute [i386])
Conf libsqlite3-0:i386 (3.34.1-3 Ubuntu:21.04/hirsute [i386])
Conf libxml2:i386 (2.9.10+dfsg-6.3ubuntu0.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Conf libedit2:i386 (3.1-20191231-2 Ubuntu:21.04/hirsute [i386])
Conf libgdbm6:i386 (1.19-2 Ubuntu:21.04/hirsute [i386])
Conf libpcap0.8:i386 (1.10.0-2 Ubuntu:21.04/hirsute [i386])
Conf libpci3:i386 (1:3.7.0-5ubuntu2 Ubuntu:21.04/hirsute [i386])
Conf libpng16-16:i386 (1.6.37-3build3 Ubuntu:21.04/hirsute [i386])
Conf libpsl5:i386 (0.21.0-1.2 Ubuntu:21.04/hirsute [i386])
Conf libusb-1.0-0:i386 (2:1.0.24-3 Ubuntu:21.04/hirsute [i386])
Conf libxau6:i386 (1:1.0.9-1build3 Ubuntu:21.04/hirsute [i386])
Conf libxdmcp6:i386 (1:1.1.3-0ubuntu3 Ubuntu:21.04/hirsute [i386])
Conf libxcb1:i386 (1.14-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libx11-6:i386 (2:1.7.0-2ubuntu0.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Conf libxext6:i386 (2:1.3.4-0ubuntu3 Ubuntu:21.04/hirsute [i386])
Conf fonts-wine (5.0.3-3 Ubuntu:21.04/hirsute [all])
Conf libproxy1v5:i386 (0.4.17-1 Ubuntu:21.04/hirsute [i386])
Conf glib-networking:i386 (2.66.0-2 Ubuntu:21.04/hirsute [i386])
Conf libcdparanoia0:i386 (3.10.2+debian-13.1 Ubuntu:21.04/hirsute [i386])
Conf libdw1:i386 (0.183-8 Ubuntu:21.04/hirsute [i386])
Conf libunwind8:i386 (1.3.2-2 Ubuntu:21.04/hirsute [i386])
Conf libgstreamer1.0-0:i386 (1.18.4-1 Ubuntu:21.04/hirsute [i386])
Conf liborc-0.4-0:i386 (1:0.4.32-1 Ubuntu:21.04/hirsute [i386])
Conf libgstreamer-plugins-base1.0-0:i386 (1.18.4-1 Ubuntu:21.04/hirsute [i386])
Conf libogg0:i386 (1.3.4-0.1 Ubuntu:21.04/hirsute [i386])
Conf libopus0:i386 (1.3.1-0.1 Ubuntu:21.04/hirsute [i386])
Conf libbrotli1:i386 (1.0.9-2build2 Ubuntu:21.04/hirsute [i386])
Conf libfreetype6:i386 (2.10.4+dfsg-1build1 Ubuntu:21.04/hirsute [i386])
Conf libfontconfig1:i386 (2.13.1-4.2ubuntu3 Ubuntu:21.04/hirsute [i386])
Conf libpixman-1-0:i386 (0.40.0-1build2 Ubuntu:21.04/hirsute [i386])
Conf libxcb-render0:i386 (1.14-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libxcb-shm0:i386 (1.14-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libxrender1:i386 (1:0.9.10-1build2 Ubuntu:21.04/hirsute [i386])
Conf libcairo2:i386 (1.16.0-5ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libtheora0:i386 (1.1.1+dfsg.1-15ubuntu2 Ubuntu:21.04/hirsute [i386])
Conf libvisual-0.4-0:i386 (0.4.0-17 Ubuntu:21.04/hirsute [i386])
Conf libvorbis0a:i386 (1.3.7-1 Ubuntu:21.04/hirsute [i386])
Conf libvorbisenc2:i386 (1.3.7-1 Ubuntu:21.04/hirsute [i386])
Conf gstreamer1.0-plugins-base:i386 (1.18.4-1 Ubuntu:21.04/hirsute [i386])
Conf libgpm2:i386 (1.20.7-8 Ubuntu:21.04/hirsute [i386])
Conf libaa1:i386 (1.4p5-48 Ubuntu:21.04/hirsute [i386])
Conf libraw1394-11:i386 (2.1.2-2 Ubuntu:21.04/hirsute [i386])
Conf libavc1394-0:i386 (0.5.4-5 Ubuntu:21.04/hirsute [i386])
Conf libcaca0:i386 (0.99.beta19-2.2ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libcairo-gobject2:i386 (1.16.0-5ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libdv4:i386 (1.0.0-13 Ubuntu:21.04/hirsute [i386])
Conf libflac8:i386 (1.3.3-2 Ubuntu:21.04/hirsute [i386])
Conf libjpeg-turbo8:i386 (2.0.6-0ubuntu2 Ubuntu:21.04/hirsute [i386])
Conf libjpeg8:i386 (8c-2ubuntu8 Ubuntu:21.04/hirsute [i386])
Conf libdeflate0:i386 (1.7-1ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libjbig0:i386 (2.1-3.1build1 Ubuntu:21.04/hirsute [i386])
Conf libwebp6:i386 (0.6.1-2ubuntu0.21.04.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Conf libtiff5:i386 (4.2.0-1build1 Ubuntu:21.04/hirsute [i386])
Conf libgdk-pixbuf-2.0-0:i386 (2.42.2+dfsg-1build1 Ubuntu:21.04/hirsute [i386])
Conf libgstreamer-plugins-good1.0-0:i386 (1.18.4-1ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libgudev-1.0-0:i386 (1:234-1 Ubuntu:21.04/hirsute [i386])
Conf libiec61883-0:i386 (1.2.0-4build1 Ubuntu:21.04/hirsute [i386])
Conf libsamplerate0:i386 (0.2.1+ds0-1 Ubuntu:21.04/hirsute [i386])
Conf libjack-jackd2-0:i386 (1.9.17~dfsg-1 Ubuntu:21.04/hirsute [i386])
Conf libmp3lame0:i386 (3.100-3 Ubuntu:21.04/hirsute [i386])
Conf libmpg123-0:i386 (1.26.4-1 Ubuntu:21.04/hirsute [i386])
Conf libasyncns0:i386 (0.8-6 Ubuntu:21.04/hirsute [i386])
Conf libsndfile1:i386 (1.0.31-1ubuntu1.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Conf libwrap0:i386 (7.6.q-31 Ubuntu:21.04/hirsute [i386])
Conf libpulse0:i386 (1:14.2-1ubuntu1.1 Ubuntu:21.04/hirsute-updates [i386])
Conf libspeex1:i386 (1.2~rc1.2-1.1ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libshout3:i386 (2.4.5-1 Ubuntu:21.04/hirsute [i386])
Conf libsoup2.4-1:i386 (2.72.0-3 Ubuntu:21.04/hirsute [i386])
Conf libtag1v5-vanilla:i386 (1.11.1+dfsg.1-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libtag1v5:i386 (1.11.1+dfsg.1-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libtwolame0:i386 (0.4.0-2 Ubuntu:21.04/hirsute [i386])
Conf libv4lconvert0:i386 (1.20.0-3 Ubuntu:21.04/hirsute [i386])
Conf libv4l-0:i386 (1.20.0-3 Ubuntu:21.04/hirsute [i386])
Conf libvpx6:i386 (1.9.0-1 Ubuntu:21.04/hirsute [i386])
Conf libwavpack1:i386 (5.4.0-1 Ubuntu:21.04/hirsute [i386])
Conf libxdamage1:i386 (1:1.1.5-2 Ubuntu:21.04/hirsute [i386])
Conf libxfixes3:i386 (1:5.0.3-2build1 Ubuntu:21.04/hirsute [i386])
Conf gstreamer1.0-plugins-good:i386 (1.18.4-1ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libgraphite2-3:i386 (1.3.14-1 Ubuntu:21.04/hirsute [i386])
Conf libharfbuzz0b:i386 (2.7.4-1ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libdatrie1:i386 (0.2.13-1ubuntu2 Ubuntu:21.04/hirsute [i386])
Conf libthai0:i386 (0.1.28-4 Ubuntu:21.04/hirsute [i386])
Conf libpango-1.0-0:i386 (1.48.2-1build2 Ubuntu:21.04/hirsute [i386])
Conf libpangoft2-1.0-0:i386 (1.48.2-1build2 Ubuntu:21.04/hirsute [i386])
Conf libpangocairo-1.0-0:i386 (1.48.2-1build2 Ubuntu:21.04/hirsute [i386])
Conf libxv1:i386 (2:1.0.11-1 Ubuntu:21.04/hirsute [i386])
Conf gstreamer1.0-x:i386 (1.18.4-1 Ubuntu:21.04/hirsute [i386])
Conf icoutils (0.32.3-3 Ubuntu:21.04/hirsute [amd64])
Conf imagemagick-6.q16 (8:6.9.11.60+dfsg-1ubuntu1 Ubuntu:21.04/hirsute [amd64])
Conf imagemagick (8:6.9.11.60+dfsg-1ubuntu1 Ubuntu:21.04/hirsute [amd64])
Conf libonig5 (6.9.6-1 Ubuntu:21.04/hirsute [amd64])
Conf libjq1 (1.6-2.1ubuntu1 Ubuntu:21.04/hirsute [amd64])
Conf jq (1.6-2.1ubuntu1 Ubuntu:21.04/hirsute [amd64])
Conf libroken18-heimdal:i386 (7.7.0+dfsg-2 Ubuntu:21.04/hirsute [i386])
Conf libasn1-8-heimdal:i386 (7.7.0+dfsg-2 Ubuntu:21.04/hirsute [i386])
Conf libasound2:i386 (1.2.4-1.1ubuntu2 Ubuntu:21.04/hirsute [i386])
Conf libasound2-plugins:i386 (1.2.2-2 Ubuntu:21.04/hirsute [i386])
Conf libatomic1:i386 (11.1.0-1ubuntu1~21.04 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Conf libavahi-common-data:i386 (0.8-5ubuntu3.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Conf libavahi-common3:i386 (0.8-5ubuntu3.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Conf libavahi-client3:i386 (0.8-5ubuntu3.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Conf libcups2:i386 (2.3.3op2-3ubuntu3 Ubuntu:21.04/hirsute [i386])
Conf libheimbase1-heimdal:i386 (7.7.0+dfsg-2 Ubuntu:21.04/hirsute [i386])
Conf libhcrypto4-heimdal:i386 (7.7.0+dfsg-2 Ubuntu:21.04/hirsute [i386])
Conf libwind0-heimdal:i386 (7.7.0+dfsg-2 Ubuntu:21.04/hirsute [i386])
Conf libhx509-5-heimdal:i386 (7.7.0+dfsg-2 Ubuntu:21.04/hirsute [i386])
Conf libkrb5-26-heimdal:i386 (7.7.0+dfsg-2 Ubuntu:21.04/hirsute [i386])
Conf libheimntlm0-heimdal:i386 (7.7.0+dfsg-2 Ubuntu:21.04/hirsute [i386])
Conf libgssapi3-heimdal:i386 (7.7.0+dfsg-2 Ubuntu:21.04/hirsute [i386])
Conf libsasl2-modules-db:i386 (2.1.27+dfsg-2ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libsasl2-2:i386 (2.1.27+dfsg-2ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libldap-2.4-2:i386 (2.4.57+dfsg-2ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libnghttp2-14:i386 (1.43.0-1 Ubuntu:21.04/hirsute [i386])
Conf librtmp1:i386 (2.4+20151223.gitfa8646d.1-2build2 Ubuntu:21.04/hirsute [i386])
Conf libssh-4:i386 (0.9.5-1 Ubuntu:21.04/hirsute [i386])
Conf libcurl3-gnutls:i386 (7.74.0-1ubuntu2.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Conf libcurl4:i386 (7.74.0-1ubuntu2.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Conf libdrm2:i386 (2.4.107-1~kisak~h kisak-mesa fresh:21.04/hirsute [i386])
Conf libdrm-amdgpu1:i386 (2.4.107-1~kisak~h kisak-mesa fresh:21.04/hirsute [i386])
Conf libpciaccess0:i386 (0.16-1build2 Ubuntu:21.04/hirsute [i386])
Conf libdrm-intel1:i386 (2.4.107-1~kisak~h kisak-mesa fresh:21.04/hirsute [i386])
Conf libdrm-nouveau2:i386 (2.4.107-1~kisak~h kisak-mesa fresh:21.04/hirsute [i386])
Conf libdrm-radeon1:i386 (2.4.107-1~kisak~h kisak-mesa fresh:21.04/hirsute [i386])
Conf libexif12:i386 (0.6.22-3 Ubuntu:21.04/hirsute [i386])
Conf libwayland-server0:i386 (1.18.0-2~exp1.1 Ubuntu:21.04/hirsute [i386])
Conf libgbm1:i386 (21.2.0~kisak1~h kisak-mesa fresh:21.04/hirsute [i386])
Conf libwayland-client0:i386 (1.18.0-2~exp1.1 Ubuntu:21.04/hirsute [i386])
Conf libwayland-cursor0:i386 (1.18.0-2~exp1.1 Ubuntu:21.04/hirsute [i386])
Conf libwayland-egl1:i386 (1.18.0-2~exp1.1 Ubuntu:21.04/hirsute [i386])
Conf libxcursor1:i386 (1:1.2.0-2build2 Ubuntu:21.04/hirsute [i386])
Conf libxi6:i386 (2:1.7.10-1build2 Ubuntu:21.04/hirsute [i386])
Conf libxinerama1:i386 (2:1.1.4-2build2 Ubuntu:21.04/hirsute [i386])
Conf libxkbcommon0:i386 (1.0.3-2 Ubuntu:21.04/hirsute [i386])
Conf libxrandr2:i386 (2:1.5.2-0ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libxss1:i386 (1:1.2.3-1 Ubuntu:21.04/hirsute [i386])
Conf libxxf86vm1:i386 (1:1.1.4-1build1 Ubuntu:21.04/hirsute [i386])
Conf libsdl2-2.0-0:i386 (2.0.14+dfsg2-3 Ubuntu:21.04/hirsute [i386])
Conf libstb0:i386 (0.0~git20200713.b42009b-1 Ubuntu:21.04/hirsute [i386])
Conf libfaudio0:i386 (21.02-1 Ubuntu:21.04/hirsute [i386])
Conf libxpm4:i386 (1:3.5.12-1 Ubuntu:21.04/hirsute [i386])
Conf libgd3:i386 (2.3.0-2 Ubuntu:21.04/hirsute [i386])
Conf libgdbm-compat4:i386 (1.19-2 Ubuntu:21.04/hirsute [i386])
Conf libglapi-mesa:i386 (21.2.0~kisak1~h kisak-mesa fresh:21.04/hirsute [i386])
Conf libllvm12:i386 (1:12.0.1-1~kisak~h kisak-mesa fresh:21.04/hirsute [i386])
Conf libsensors5:i386 (1:3.6.0-7 Ubuntu:21.04/hirsute [i386])
Conf libvulkan1:i386 (1.2.162.0-1 Ubuntu:21.04/hirsute [i386])
Conf libgl1-mesa-dri:i386 (21.2.0~kisak1~h kisak-mesa fresh:21.04/hirsute [i386])
Conf libx11-xcb1:i386 (2:1.7.0-2ubuntu0.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Conf libxcb-dri2-0:i386 (1.14-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libxcb-dri3-0:i386 (1.14-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libxcb-glx0:i386 (1.14-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libxcb-present0:i386 (1.14-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libxcb-sync1:i386 (1.14-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libxcb-xfixes0:i386 (1.14-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libxshmfence1:i386 (1.3-1build2 Ubuntu:21.04/hirsute [i386])
Conf libglx-mesa0:i386 (21.2.0~kisak1~h kisak-mesa fresh:21.04/hirsute [i386])
Conf libgpg-error-l10n (1.38-2build1 Ubuntu:21.04/hirsute [all])
Conf libltdl7:i386 (2.4.6-15 Ubuntu:21.04/hirsute [i386])
Conf libgphoto2-port12:i386 (2.5.26-2 Ubuntu:21.04/hirsute [i386])
Conf libgphoto2-6:i386 (2.5.26-2 Ubuntu:21.04/hirsute [i386])
Conf libgsm1:i386 (1.0.18-2 Ubuntu:21.04/hirsute [i386])
Conf libieee1284-3:i386 (0.2.11-14 Ubuntu:21.04/hirsute [i386])
Conf libjxr0 (1.1-6build1 Ubuntu:21.04/hirsute [amd64])
Conf libjxr-tools (1.1-6build1 Ubuntu:21.04/hirsute [amd64])
Conf liblcms2-2:i386 (2.12~rc1-2 Ubuntu:21.04/hirsute [i386])
Conf libmagickcore-6.q16-6-extra (8:6.9.11.60+dfsg-1ubuntu1 Ubuntu:21.04/hirsute [amd64])
Conf libnetpbm10 (2:10.0-15.4 Ubuntu:21.04/hirsute [amd64])
Conf libnspr4:i386 (2:4.29-1 Ubuntu:21.04/hirsute [i386])
Conf libnss-nis:i386 (3.1-0ubuntu4 Ubuntu:21.04/hirsute [i386])
Conf libnss-nisplus:i386 (1.3-0ubuntu4 Ubuntu:21.04/hirsute [i386])
Conf libnss3:i386 (2:3.61-1ubuntu2 Ubuntu:21.04/hirsute [i386])
Conf libodbc1:i386 (2.3.6-0.1build1 Ubuntu:21.04/hirsute [i386])
Conf libosmesa6:i386 (21.2.0~kisak1~h kisak-mesa fresh:21.04/hirsute [i386])
Conf libperl5.32:i386 (5.32.1-3ubuntu2.1 Ubuntu:21.04/hirsute-updates, Ubuntu:21.04/hirsute-security [i386])
Conf libopenjp2-7:i386 (2.3.1-1ubuntu5 Ubuntu:21.04/hirsute [i386])
Conf libpoppler107:i386 (21.02.0-1 Ubuntu:21.04/hirsute [i386])
Conf libpoppler-glib8:i386 (21.02.0-1 Ubuntu:21.04/hirsute [i386])
Conf libsnmp40:i386 (5.9+dfsg-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libsane1:i386 (1.0.32-0ubuntu2 Ubuntu:21.04/hirsute [i386])
Conf libsasl2-modules:i386 (2.1.27+dfsg-2ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libsndio7.0:i386 (1.5.0-3 Ubuntu:21.04/hirsute [i386])
Conf libvkd3d1:i386 (1.1-5 Ubuntu:21.04/hirsute [i386])
Conf libopenal1:i386 (1:1.19.1-2 Ubuntu:21.04/hirsute [i386])
Conf ocl-icd-libopencl1:i386 (2.2.14-2 Ubuntu:21.04/hirsute [i386])
Conf libwine:i386 (5.0.3-3 Ubuntu:21.04/hirsute [i386])
Conf libxcb-randr0:i386 (1.14-3ubuntu1 Ubuntu:21.04/hirsute [i386])
Conf libxcomposite1:i386 (1:0.4.5-1 Ubuntu:21.04/hirsute [i386])
Conf libxslt1.1:i386 (1.1.34-4 Ubuntu:21.04/hirsute [i386])
Conf mesa-vulkan-drivers:i386 (21.2.0~kisak1~h kisak-mesa fresh:21.04/hirsute [i386])
Conf netpbm (2:10.0-15.4 Ubuntu:21.04/hirsute [amd64])
Conf p7zip (16.02+dfsg-8 Ubuntu:21.04/hirsute [amd64])
Conf p7zip-full (16.02+dfsg-8 Ubuntu:21.04/hirsute [amd64])
Conf python3-natsort (7.1.0-1 Ubuntu:21.04/hirsute [all])
Conf python3-wxgtk4.0 (4.0.7+dfsg-10 Ubuntu:21.04/hirsute [amd64])
Conf wine32:i386 (5.0.3-3 Ubuntu:21.04/hirsute [i386])
Conf wine (5.0.3-3 Ubuntu:21.04/hirsute [all])
Conf playonlinux (4.3.4-2 Ubuntu:21.04/hirsute [all])
Conf libcapi20-3:i386 (1:3.27-3 Ubuntu:21.04/hirsute [i386])
Conf libglvnd0:i386 (1.3.2-1 Ubuntu:21.04/hirsute [i386])
Conf libglx0:i386 (1.3.2-1 Ubuntu:21.04/hirsute [i386])
Conf libgl1:i386 (1.3.2-1 Ubuntu:21.04/hirsute [i386])
Conf libglu1-mesa:i386 (9.0.1-1build1 Ubuntu:21.04/hirsute [i386])



```

---

### Post by biite on 2021-08-18
Tried the following:
[LIST]
[*]Reinstall via CLI: ```
apt install playonlinux
```
This worked fine
[*]After that Ubuntu software showed both PlayOnLinux and Wine installed
[*]Removal via CLI: ```
apt remove playonlinux
```, followed by ```
apt autoremove
``` to cleanup
[*]Ubuntu Software shows both PlayOnLinux and Wine installed still.
[*]Removed (remnants(?) of) PlayOnLinux and Wine via Ubuntu Software
[/LIST]

Next:
[LIST]
[*]Installed PlayOnLinux via Ubuntu Software successfully
[*]It does NOT show as installed in Ubuntu Software in the 'Installed' part
[*]However when searching for PlayOnLinux in the 'Explore' part of Ubuntu Software it DOES show as installed
[*]Verified install of PlayOnlinux with ```
apt list playonlinux
``` and it shows as installed.
[/LIST]

I'm now suspecting some weird caching issue with Ubuntu Software.

So in short: installation works via both CLI and Ubuntu Software, but the results showing in Ubuntu Software are incorrect somehow

Any logs worth checking?

Regards,
Biite

---

### Post by monkeybrain20122 on 2021-08-18
> **biite said:**
> 

[LIST]
[*]Removed (remnants(?) of) PlayOnLinux and Wine via Ubuntu Software 
[/LIST]



No need to do that. If you install with apt or synaptic that is all you need. The remnants after purging the package and autoremove are typically in your $HOME which you have to remove manually (config files, cache and so on) The system tools won't touch your $HOME and that include ubuntu-software

What happened?

I think there are multiple versions of playonlinux in the software store, there is an apt version and there is a snap version. The one that didn't work was the snap. If you check the details of the package in software store you can see the provider. If it is snapcraft then it is a snap. There is an additional possibility to install with flatpak but that needs to be enabled explicitly by the user.

To install apt applications only I really recommend synaptic as a package manager gui

```
sudo apt install synaptic apt-xapian-index
```

problem with command line is you have to know the exact name of the package, you can apt search or something but synaptic is much more convenient

---

### Post by biite on 2021-08-24
> **monkeybrain20122 said:**
> 
I think there are multiple versions of playonlinux in the software store, there is an apt version and there is a snap version. The one that didn't work was the snap. If you check the details of the package in software store you can see the provider. If it is snapcraft then it is a snap. There is an additional possibility to install with flatpak but that needs to be enabled explicitly by the user.


As far as I can see there are no multiple versions of playonlinux, checked via apt search, snap find and the software store.
So still no idea as to why the message 'Unable to install PlayOnLinux as not supported' is showing in the 'Ubuntu Software' program.

Will try synaptic though :)

---


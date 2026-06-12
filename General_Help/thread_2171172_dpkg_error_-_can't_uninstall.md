---
title: "dpkg error - can't uninstall"
date: 2013-08-29
forum: General Help
---

### Post by Hungry Man on 2013-08-29
> The following packages will be REMOVED:
  libglib2.0-cil libgtk2.0-cil
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 2,697 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 207807 files and directories currently installed.)
Removing libgtk2.0-cil ...
rm: cannot remove &#8216;/usr/share/cli-common/packages.d/policy.2.6.gtk-dotnet.installcligac&#8217;: No such file or directory
dpkg: error processing libgtk2.0-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing libglib2.0-cil ...
rm: cannot remove &#8216;/usr/share/cli-common/packages.d/policy.2.6.glib-sharp.installcligac&#8217;: No such file or directory
dpkg: error processing libglib2.0-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 libgtk2.0-cil
 libglib2.0-cil
E: Sub-process /usr/bin/dpkg returned an error code (1)




I've tried various methods that I've seen online. Can't get it to work.

edit: solved:

edited [FONT=Ubuntu Mono]sudo nano /var/lib/dpkg/status  [/FONT]
removed the info related to those packages.

---

### Post by 3246251196 on 2013-08-29
> **Hungry Man said:**
> I've tried various methods that I've seen online. Can't get it to work.

Just out of curiosity show the results of:

dpkg -l | grep -v "^ii"

apt-file show libglib2.0-cil

apt-file show libgtk2.0-cil

---

### Post by Hungry Man on 2013-08-29
>  dpkg -l | grep -v "^ii"Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                      Version                              Architecture Description
+++-=========================================-====================================-============-=====================================================================================================================================================
rc  libasn1-8-heimdal:i386                    1.6~git20120403+dfsg1-2              i386         Heimdal Kerberos - ASN.1 library
rc  libasound2:i386                           1.0.25-4ubuntu3.1                    i386         shared library for ALSA applications
rc  libasyncns0:i386                          0.8-4build1                          i386         Asynchronous name service query library
rc  libavahi-client3:i386                     0.6.31-1ubuntu3                      i386         Avahi client library
rc  libavahi-common3:i386                     0.6.31-1ubuntu3                      i386         Avahi common library
rc  libcapi20-3:i386                          1:3.12.20071127-0ubuntu11            i386         libraries for CAPI support
rc  libcups2:i386                             1.6.2-1ubuntu5                       i386         Common UNIX Printing System(tm) - Core library
rc  libdrm-intel1:i386                        2.4.43-0ubuntu1.1                    i386         Userspace interface to intel-specific kernel DRM services -- runtime
rc  libdrm-nouveau2:i386                      2.4.43-0ubuntu1.1                    i386         Userspace interface to nouveau-specific kernel DRM services -- runtime
rc  libdrm-radeon1:i386                       2.4.43-0ubuntu1.1                    i386         Userspace interface to radeon-specific kernel DRM services -- runtime
rc  libexif12:i386                            0.6.21-1                             i386         library to parse EXIF files
rc  libexpat1:i386                            2.1.0-2                              i386         XML parsing C library - runtime library
rc  libflac8:i386                             1.2.1-6build1                        i386         Free Lossless Audio Codec - runtime C library
rc  libfontconfig1:i386                       2.10.2-0ubuntu2                      i386         generic font configuration library - runtime
rc  libfreetype6:i386                         2.4.11-0ubuntu1                      i386         FreeType 2 font engine, shared library files
rc  libgcrypt11:i386                          1.5.0-3ubuntu2.2                     i386         LGPL Crypto library - runtime library
rc  libgd2-xpm:i386                           2.0.36~rc1~dfsg-6.1ubuntu1           i386         GD Graphics Library version 2
rc  libgif4:i386                              4.1.6-10ubuntu1                      i386         library for GIF images (library)
rc  libgl1-mesa-dri:i386                      9.1.3-0ubuntu0.3                     i386         free implementation of the OpenGL API -- DRI modules
rc  libgl1-mesa-glx:i386                      9.1.3-0ubuntu0.3                     i386         free implementation of the OpenGL API -- GLX runtime
rc  libglapi-mesa:i386                        9.1.3-0ubuntu0.3                     i386         free implementation of the GL API -- shared library
rH  libglib2.0-cil                            2.12.10-5                            amd64        CLI binding for the GLib utility library 2.12
rc  libglu1-mesa:i386                         9.0.0-0ubuntu1                       i386         Mesa OpenGL utility library (GLU)
rc  libgnutls26:i386                          2.12.23-1ubuntu1.1                   i386         GNU TLS library - runtime library
rc  libgpg-error0:i386                        1.10-3.1ubuntu1                      i386         library for common error values and messages in GnuPG components
rc  libgphoto2-2:i386                         2.4.14-2                             i386         gphoto2 digital camera library
rc  libgphoto2-port0:i386                     2.4.14-2                             i386         gphoto2 digital camera port library
rc  libgssapi-krb5-2:i386                     1.10.1+dfsg-4+nmu1                   i386         MIT Kerberos runtime libraries - krb5 GSS-API Mechanism
rc  libgssapi3-heimdal:i386                   1.6~git20120403+dfsg1-2              i386         Heimdal Kerberos - GSSAPI support library
rc  libgstreamer-plugins-base0.10-0:i386      0.10.36-1.1ubuntu1                   i386         GStreamer libraries from the "base" set
rc  libgstreamer0.10-0:i386                   0.10.36-1ubuntu2                     i386         Core GStreamer libraries and elements
rH  libgtk2.0-cil                             2.12.10-5                            amd64        CLI binding for the GTK+ toolkit 2.12
rc  libhcrypto4-heimdal:i386                  1.6~git20120403+dfsg1-2              i386         Heimdal Kerberos - crypto library
rc  libheimbase1-heimdal:i386                 1.6~git20120403+dfsg1-2              i386         Heimdal Kerberos - Base library
rc  libheimntlm0-heimdal:i386                 1.6~git20120403+dfsg1-2              i386         Heimdal Kerberos - NTLM support library
rc  libhx509-5-heimdal:i386                   1.6~git20120403+dfsg1-2              i386         Heimdal Kerberos - X509 support library
rc  libice6:i386                              2:1.0.8-2                            i386         X11 Inter-Client Exchange library
rc  libieee1284-3:i386                        0.2.11-10build2                      i386         cross-platform library for parallel port access
rc  libjack-jackd2-0:i386                     1.9.9.5+20130127git15950eb1-1        i386         JACK Audio Connection Kit (libraries)
rc  libjbig0:i386                             2.0-2ubuntu1                         i386         JBIGkit libraries
rc  libjpeg-turbo8:i386                       1.2.1-0ubuntu2                       i386         IJG JPEG compliant runtime library.
rc  libk5crypto3:i386                         1.10.1+dfsg-4+nmu1                   i386         MIT Kerberos runtime libraries - Crypto Library
rc  libkeyutils1:i386                         1.5.5-4                              i386         Linux Key Management Utilities (library)
rc  libkrb5-26-heimdal:i386                   1.6~git20120403+dfsg1-2              i386         Heimdal Kerberos - libraries
rc  libkrb5-3:i386                            1.10.1+dfsg-4+nmu1                   i386         MIT Kerberos runtime libraries
rc  libkrb5support0:i386                      1.10.1+dfsg-4+nmu1                   i386         MIT Kerberos runtime libraries - Support library
rc  libldap-2.4-2:i386                        2.4.31-1ubuntu2.1                    i386         OpenLDAP libraries
rc  libllvm3.2:i386                           3.2-2ubuntu5                         i386         Low-Level Virtual Machine (LLVM), runtime library
rc  libltdl7:i386                             2.4.2-1.2ubuntu1                     i386         A system independent dlopen wrapper for GNU libtool
rc  libmpg123-0:i386                          1.14.4-1                             i386         MPEG layer 1/2/3 audio decoder (shared library)
rc  libodbc1:amd64                            2.2.14p2-5ubuntu4                    amd64        ODBC library for Unix
rc  libogg0:i386                              1.3.0-4                              i386         Ogg bitstream library
rc  libopenal-data                            1:1.14-4ubuntu1                      all          Software implementation of the OpenAL API (data files)
rc  libopenal1:i386                           1:1.14-4ubuntu1                      i386         Software implementation of the OpenAL API (shared library)
rc  liborc-0.4-0:i386                         1:0.4.17-1                           i386         Library of Optimized Inner Loops Runtime Compiler
rc  libosmesa6:i386                           9.1.3-0ubuntu0.3                     i386         Mesa Off-screen rendering extension
rc  libp11-kit0:i386                          0.14-1                               i386         Library for loading and coordinating access to PKCS#11 modules - runtime
rc  libpciaccess0:i386                        0.13.1-2                             i386         Generic PCI access library for X
rc  libpulse0:i386                            1:3.0-0ubuntu6                       i386         PulseAudio client libraries
rc  libroken18-heimdal:i386                   1.6~git20120403+dfsg1-2              i386         Heimdal Kerberos - roken support library
rc  libsamplerate0:i386                       0.1.8-5                              i386         Audio sample rate conversion library
rc  libsane:i386                              1.0.23-0ubuntu1                      i386         API library for scanners
rc  libsasl2-2:i386                           2.1.25.dfsg1-6                       i386         Cyrus SASL - authentication abstraction library
rc  libsm6:i386                               2:1.2.1-2                            i386         X11 Session Management library
rc  libsndfile1:i386                          1.0.25-5                             i386         Library for reading/writing audio files
rc  libspeexdsp1:i386                         1.2~rc1-7ubuntu1                     i386         The Speex extended runtime library
rc  libsqlite3-0:i386                         3.7.15.2-1ubuntu1                    i386         SQLite 3 shared library
rc  libssl1.0.0:i386                          1.0.1c-4ubuntu8.1                    i386         SSL shared libraries
rc  libstdc++6:i386                           4.7.3-1ubuntu1                       i386         GNU Standard C++ Library v3
rc  libtasn1-3:i386                           2.14-2                               i386         Manage ASN.1 structures (runtime)
rc  libtiff4:i386                             3.9.7-0ubuntu1                       i386         Tag Image File Format (TIFF) library (old version)
rc  libtiff5:i386                             4.0.2-4ubuntu2.1                     i386         Tag Image File Format (TIFF) library
rc  libtxc-dxtn-s2tc0:i386                    0~git20121227-1                      i386         Texture compression library for Mesa
rc  libunistring0:i386                        0.9.3-5build1                        i386         Unicode string library for C
rc  libusb-0.1-4:i386                         2:0.1.12-23+nmu1ubuntu1              i386         userspace USB programming library
rc  libusb-1.0-0:i386                         2:1.0.12-2ubuntu1                    i386         userspace USB programming library
rc  libv4l-0:i386                             0.8.9-1                              i386         Collection of video4linux support libraries
rc  libv4lconvert0:i386                       0.8.9-1                              i386         Video4linux frame format conversion library
rc  libvorbis0a:i386                          1.3.2-1.3                            i386         The Vorbis General Audio Compression Codec (Decoder library)
rc  libvorbisenc2:i386                        1.3.2-1.3                            i386         The Vorbis General Audio Compression Codec (Encoder library)
rc  libwind0-heimdal:i386                     1.6~git20120403+dfsg1-2              i386         Heimdal Kerberos - stringprep implementation
rc  libwrap0:i386                             7.6.q-24                             i386         Wietse Venema's TCP wrappers library
rc  libx11-6:i386                             2:1.5.0-1ubuntu1.1                   i386         X11 client-side library
rc  libx11-xcb1:i386                          2:1.5.0-1ubuntu1.1                   i386         Xlib/XCB interface library
rc  libxau6:i386                              1:1.0.7-1                            i386         X11 authorisation library
rc  libxcb-dri2-0:i386                        1.8.1-2ubuntu2.1                     i386         X C Binding, dri2 extension
rc  libxcb-glx0:i386                          1.8.1-2ubuntu2.1                     i386         X C Binding, glx extension
rc  libxcb1:i386                              1.8.1-2ubuntu2.1                     i386         X C Binding
rc  libxcomposite1:i386                       1:0.4.3-2build2                      i386         X11 Composite extension library
rc  libxcursor1:i386                          1:1.1.13-1ubuntu0.13.04.1            i386         X cursor management library
rc  libxdamage1:i386                          1:1.1.3-2build2                      i386         X11 damaged region extension library
rc  libxdmcp6:i386                            1:1.1.1-1                            i386         X11 Display Manager Control Protocol library
rc  libxext6:i386                             2:1.3.1-2ubuntu0.13.04.1             i386         X11 miscellaneous extension library
rc  libxfixes3:i386                           1:5.0-4ubuntu5.13.04.1               i386         X11 miscellaneous 'fixes' extension library
rc  libxi6:i386                               2:1.6.99.1-0ubuntu3.1                i386         X11 Input extension library
rc  libxinerama1:i386                         2:1.1.2-1ubuntu0.13.04.1             i386         X11 Xinerama extension library
rc  libxml2:i386                              2.9.0+dfsg1-4ubuntu4.3               i386         GNOME XML library
rc  libxpm4:i386                              1:3.5.10-1                           i386         X11 pixmap library
rc  libxrandr2:i386                           2:1.4.0-1ubuntu1.1                   i386         X11 RandR extension library
rc  libxrender1:i386                          1:0.9.7-1ubuntu0.13.04.1             i386         X Rendering Extension client library
rc  libxslt1.1:i386                           1.1.27-1ubuntu2                      i386         XSLT 1.0 processing library - runtime library
rc  libxt6:i386                               1:1.1.3-1ubuntu0.13.04.1             i386         X11 toolkit intrinsics library
rc  libxxf86vm1:i386                          1:1.1.2-1ubuntu0.13.04.1             i386         X11 XFree86 video mode extension library
rc  linux-image-3.8.0-27-generic              3.8.0-27.40                          amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-extra-3.8.0-27-generic        3.8.0-27.40                          amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  odbcinst                                  2.2.14p2-5ubuntu4                    amd64        Helper program for accessing odbc ini files
rc  odbcinst1debian2:amd64                    2.2.14p2-5ubuntu4                    amd64        Support library for accessing odbc ini files
rc  ttf-mscorefonts-installer                 3.4+nmu1ubuntu1                      all          Installer for Microsoft TrueType core fonts
rc  wine-browser-installer                    0.8.2~raring                         amd64        The Wine Browser Installer provides a tool for multiple packages to provide access to web services that can be run with Mozilla Firefox under Wine.
rc  wine-compholio                            1.7.0~raring1                        i386         The Compholio Edition is a special build of the popular Wine software
rc  wine-silverlight5.1-installer             0.8.2~raring                         all          wine-silverlight5.1-installer provides a convient tool that downloads and installs all of the components necessary to run Silverlight 5.1 under Wine.




apt-file isn't installed, nor can I install it until this issue is solved I guess.

---

### Post by Hungry Man on 2013-08-29
No progress.

---

### Post by Hungry Man on 2013-08-30
Bump...

---


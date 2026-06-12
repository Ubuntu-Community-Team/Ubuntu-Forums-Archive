---
title: "apt-get install error"
date: 2013-02-03
forum: General Help
---

### Post by qwertyjjj on 2013-02-03
i get the following error, any ideas how to fix?

```

j-media-centre@jmediacentre-A880G:~$ sudo apt-get install kfind
[sudo] password for j-media-centre: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 kfind : Depends: kde-runtime but it is not going to be installed
         Depends: libkfile4 (>= 4:4.8.1) but it is not going to be installed
         Depends: libkio5 (>= 4:4.8.1) but it is not going to be installed
         Depends: libkonq5abi1 (>= 4:4.6.1) but it is not going to be installed
 transmission-daemon : Depends: transmission-common (= 2.72-0ubuntu0.12.04.1) but 2.76-0ubuntu0.12.04.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
j-media-centre@jmediacentre-A880G:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libclucene0ldbl linux-headers-3.2.0-26-generic libcogl9 units libwildmidi1
  libqca2 libzbar0 libtorque2 gir1.2-json-1.0 libatlas3gf-base
  libcxsparse2.2.3 libflite1 python-mako gir1.2-gst-plugins-base-0.10 libglpk0
  libarpack2 libdiscid0 gir1.2-gstreamer-0.10 libexttextcat-data libgfortran3
  oxygen-icon-theme gir1.2-clutter-1.0 epiphany-browser-data
  linux-headers-3.2.0-26 libopenmpi1.3 libwildmidi-config libatk-wrapper-java
  phonon libopenspc0 libav-tools shared-desktop-ontologies libqrupdate1
  libhdf5-serial-1.8.4 libntrack-qt4-1 libseed-gtk3-0 libcogl-common
  libdmapsharing-3.0-2 libxml-commons-external-java octave3.2-common
  libpolkit-qt-1-1 python-markupsafe libqapt1 libparpack2 libfltk1.1
  libsoundtouch0 icedtea-netx-common linux-headers-3.2.0-26-generic-pae dkms
  libclutter-1.0-0 python-central libgme0 icoutils libspandsp2 freepats
  libcogl-pango0 libxerces2-java libntrack0 libqapt-runtime flac
  phonon-backend-gstreamer gnome-js-common python-packagekit libcholmod1.7.1
  libstreamanalyzer0 libphonon4 libclutter-1.0-common libblas3gf libnuma1
  libcdaudio1 libmimic0 libamd2.2.0 libgraphicsmagick++3 libexttextcat0
  liblapack3gf libibverbs1 filezilla-common gir1.2-cogl-1.0 libhsqldb-java
  libxml-commons-resolver1.1-java libstreams0 libservlet2.5-java
  libumfpack5.4.0 libcelt0-0 libgraphicsmagick3 libatk-wrapper-java-jni
  libqhull5 gir1.2-coglpango-1.0 libccolamd2.7.1 libofa0 ntrack-module-libnl-0
  libmms0 texinfo libmusicbrainz3-6 libavdevice53
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  transmission-daemon
The following packages will be upgraded:
  transmission-daemon
1 upgraded, 0 newly installed, 0 to remove and 156 not upgraded.
1 not fully installed or removed.
Need to get 0 B/235 kB of archives.
After this operation, 12.3 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of transmission-daemon:
 transmission-daemon depends on transmission-common (= 2.72-0ubuntu0.12.04.1); however:
  Version of transmission-common on system is 2.76-0ubuntu0.12.04.1.
dpkg: error processing transmission-daemon (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Errors were encountered while processing:
 transmission-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)
j-media-centre@jmediacentre-A880G:~$ 

```

---

### Post by qwertyjjj on 2013-02-06
bump

---

### Post by raja.genupula on 2013-02-06
type as follwing in your terminal

```
sudo dpkg -r transmission-daemon
sudo apt-get update
sudo apt-get install -f

```

---


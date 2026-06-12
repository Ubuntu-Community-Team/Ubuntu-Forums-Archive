---
title: "Libpoppler85"
date: 2019-12-16
forum: General Help
---

### Post by EmyrB on 2019-12-16
Hi Guys,

Over the last few days I have noticed that my software updater is telling me on my install of ubuntu 18.04 I have an update but it can't update. when I did a manual apt update it says that libpoppler85 is being kept back. On further investigation, according to several site libpoppler85 has been deleted from the repositories. How do I resolve this? It's a pain that the updater says I have updates to install when there isn't!

Cheers
EmyrB

---

### Post by Impavidus on 2019-12-16
libpoppler85 is part of Ubuntu 19.04. Ubuntu 18.04 comes with libpoppler73.

Can you show us```
sudo apt update
sudo apt upgrade
apt-cache policy libpoppler85 libpoppler73
```

---

### Post by EmyrB on 2019-12-16
OK. Here is the output of sudo apt update
```
Reading package lists... Done                      
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.

```

Here is the output of sudo apt upgrade
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libpoppler85
0 to upgrade, 0 to newly install, 0 to remove and 1 not to upgrade.

```

and finally, apt-cache policy libpoppler85 libpoppler73
```
libpoppler85:
  Installed: 0.74.0-0ubuntu1.2~ppa0
  Candidate: 0.74.0-0ubuntu1.2~ppa1
  Version table:
     0.74.0-0ubuntu1.2~ppa1 500
        500 http://ppa.launchpad.net/scribus/ppa/ubuntu bionic/main amd64 Packages
 *** 0.74.0-0ubuntu1.2~ppa0 100
        100 /var/lib/dpkg/status
libpoppler73:
  Installed: 0.62.0-2ubuntu2.10
  Candidate: 0.62.0-2ubuntu2.10
  Version table:
 *** 0.62.0-2ubuntu2.10 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages
        100 /var/lib/dpkg/status
     0.62.0-2ubuntu2 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/main amd64 Packages

```

Looks like it's an issue with Scribus PPA and I'm going to have to wait until the Scribus team sort this one out. Cheers Impavidus

---

### Post by Impavidus on 2019-12-16
You've both libpoppler73 (from the official repositories) and libpoppler85 (from the PPA). A new version of libpoppler85 is available from the PPA, but can't be installed, most likely because of a dependency issue. That sometimes happens with PPAs. Maybe the maintainers of the PPA fix it quickly. Else you can dig and see which dependency blocks the upgrade. But'd first wait a few days and see if the PPA maintainers fix it.

---

### Post by EmyrB on 2019-12-16
Yeah, at least I know what the cause is now. It was diving me nuts seeing it pop up all the time. Wonder if I should report it to the Scribus PPA team?

---

### Post by levry on 2019-12-31
Libpoppler85 should indeed not be upgraded. I found the same issue, and shown from apt install libpoppler85:
```
The following packages were automatically installed and are no longer required:
  gdal-data gimp-data libaec0 libamd2 libarmadillo8 libarpack2 libavdevice57 libbabl-0.1-0 libblas3 libcamd2 libccolamd2 libcholmod3 libcoin80v5
  libdap25 libdapclient6v5 libdc1394-22 libepsilon1 libfaad2 libfreexl1 libfyba0 libgdal20 libgegl-0.4-0 libgegl-common libgeos-3.6.2 libgeos-c1v5
  libgeotiff2 libgfortran4 libgimp2.0 libgraphicsmagick-q16-3 libgsl23 libgslcblas0 libgtkmm-2.4-1v5 libgtkspell0 libhdf4-0-alt libhdf5-100
  libimage-magick-perl libimage-magick-q16-perl libiso9660-10 libkmlbase1 libkmldom1 libkmlengine1 liblapack3 libmad0 libmetis5 libminizip1
  libmodplug1 libmpcdec6 libmypaint-1.3-0 libmypaint-common libnetcdf13 libodbc1 libogdi3.2 libopenthreads20 libpotrace0 libpq5 libproj12 libqhull7
  libqt5opengl5 libqt5xml5 libqxp-0.0-0 libspatialite7 libsuperlu5 libsz2 libumfpack5 liburiparser1 libvcdinfo0 libxerces-c3.2 libxine2 libxine2-bin
  libxine2-doc libxine2-ffmpeg libxine2-misc-plugins libxine2-plugins libzmf-0.0-0 odbcinst odbcinst1debian2 proj-bin proj-data python-numpy
  python-scour python3-scour scour scribus-ng-data
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  evince gimp gir1.2-poppler-0.18 inkscape libevdocument3-4 libevview3-3 libopenscenegraph-3.4-131 libpoppler-glib8 pdfbooklet scribus-ng
The following packages will be upgraded:
  libpoppler85
1 upgraded, 0 newly installed, 10 to remove and 0 not upgraded.
Need to get 914 kB of archives.
After this operation, 231 MB disk space will be freed.

```

---


---
title: "Cant update system"
date: 2017-04-23
forum: General Help
---

### Post by roma24ster on 2017-04-23
Hi

When I run dist-upgrade I get the following errors, can anyone help?

Thanks

```
jamie@jamie-ncase ~ $ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libbullet2.85 libbulletcollision2.83.6 liblinearmath2.83.6 libxnvctrl0
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed
  libbullet2.86 linux-headers-4.4.0-72 linux-headers-4.4.0-72-generic
The following packages will be upgraded:
  bind9-host distro-info-data dnsmasq-base dnsutils eject
  gir1.2-gst-plugins-base-0.10 gir1.2-gst-plugins-base-1.0 gstreamer0.10-alsa
  gstreamer0.10-gconf gstreamer0.10-gnomevfs gstreamer0.10-plugins-base:i386
  gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps
  gstreamer0.10-plugins-good:i386 gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio gstreamer0.10-x gstreamer0.10-x:i386
  gstreamer1.0-alsa gstreamer1.0-plugins-base gstreamer1.0-plugins-base-apps
  gstreamer1.0-plugins-good gstreamer1.0-pulseaudio gstreamer1.0-x haguichi
  imagemagick imagemagick-6.q16 insync libaudiofile1:i386 libbind9-140
  libdns-export162 libdns162 libgstreamer-plugins-base0.10-0
  libgstreamer-plugins-base0.10-0:i386 libgstreamer-plugins-good1.0-0
  libisc-export160 libisc160 libisccc140 libisccfg140
  libjavascriptcoregtk-4.0-18 liblwres141 libmetacity-private3a
  libmysqlclient20 libopenscenegraph-3.4-130 libpci3 libwebkit2gtk-4.0-37
  libxml2-utils libxnvctrl0 linux-headers-generic makedev metacity
  metacity-common mintupdate multiarch-support mysql-common ndiswrapper
  ndiswrapper-dkms ndiswrapper-utils-1.9 network-manager-openvpn
  network-manager-openvpn-gnome openmw openmw-data openmw-launcher pciutils
  python-imaging python-libxml2 python-pil python-samba thermald thunderbird
  thunderbird-gnome-support thunderbird-locale-en thunderbird-locale-en-us
  virtualbox-guest-dkms virtualbox-guest-utils virtualbox-guest-x11
76 to upgrade, 3 to newly install, 0 to remove and 0 not to upgrade.
18 not fully installed or removed.
Need to get 0 B/167 MB of archives.
After this operation, 102 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Extract templates from packages: 100%
(Reading database ... 373365 files and directories currently installed.)
Preparing to unpack .../python-pil_3.1.2-0ubuntu1.1_amd64.deb ...
/var/lib/dpkg/info/python-pil:amd64.prerm: 6: /var/lib/dpkg/info/python-pil:amd64.prerm: pyclean: not found
dpkg: warning: subprocess old pre-removal script returned error exit status 127
dpkg: trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: /var/lib/dpkg/tmp.ci/prerm: pyclean: not found
dpkg: error processing archive /var/cache/apt/archives/python-pil_3.1.2-0ubuntu1.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/python-pil:amd64.postinst: 6: /var/lib/dpkg/info/python-pil:amd64.postinst: pycompile: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Preparing to unpack .../python-imaging_3.1.2-0ubuntu1.1_all.deb ...
/var/lib/dpkg/info/python-imaging.prerm: 6: /var/lib/dpkg/info/python-imaging.prerm: pyclean: not found
dpkg: warning: subprocess old pre-removal script returned error exit status 127
dpkg: trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: /var/lib/dpkg/tmp.ci/prerm: pyclean: not found
dpkg: error processing archive /var/cache/apt/archives/python-imaging_3.1.2-0ubuntu1.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/python-imaging.postinst: 6: /var/lib/dpkg/info/python-imaging.postinst: pycompile: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Preparing to unpack .../python-samba_2%3a4.3.11+dfsg-0ubuntu0.16.04.6_amd64.deb ...
/var/lib/dpkg/info/python-samba.prerm: 6: /var/lib/dpkg/info/python-samba.prerm: pyclean: not found
dpkg: warning: subprocess old pre-removal script returned error exit status 127
dpkg: trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: /var/lib/dpkg/tmp.ci/prerm: pyclean: not found
dpkg: error processing archive /var/cache/apt/archives/python-samba_2%3a4.3.11+dfsg-0ubuntu0.16.04.6_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/python-samba.postinst: 6: /var/lib/dpkg/info/python-samba.postinst: pycompile: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Preparing to unpack .../multiarch-support_2.23-0ubuntu7_amd64.deb ...
Unpacking multiarch-support (2.23-0ubuntu7) over (2.23-0ubuntu5) ...
Errors were encountered while processing:
 /var/cache/apt/archives/python-pil_3.1.2-0ubuntu1.1_amd64.deb
 /var/cache/apt/archives/python-imaging_3.1.2-0ubuntu1.1_all.deb
 /var/cache/apt/archives/python-samba_2%3a4.3.11+dfsg-0ubuntu0.16.04.6_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jamie@jamie-ncase ~ $ 

```

---

### Post by ian-weisser on 2017-04-23
Reinstall the 'python-minimal' package.
pyclean and pycompile are provided by that package.

---

### Post by roma24ster on 2017-04-23
This is the error I get:

```
jamie@jamie-ncase ~ $ sudo apt-get install --reinstall python-minimalReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libbulletcollision2.83.6 liblinearmath2.83.6 libxnvctrl0
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  python-samba
The following packages will be upgraded:
  python-samba
1 to upgrade, 0 to newly install, 1 reinstalled, 0 to remove and 74 not to upgrade.
19 not fully installed or removed.
Need to get 28.2 kB/1,404 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu xenial/main amd64 python-minimal amd64 2.7.11-1 [28.2 kB]
Fetched 28.2 kB in 0s (297 kB/s)         
Setting up multiarch-support (2.23-0ubuntu7) ...
(Reading database ... 373365 files and directories currently installed.)
Preparing to unpack .../python-samba_2%3a4.3.11+dfsg-0ubuntu0.16.04.6_amd64.deb ...
/var/lib/dpkg/info/python-samba.prerm: 6: /var/lib/dpkg/info/python-samba.prerm: pyclean: not found
dpkg: warning: subprocess old pre-removal script returned error exit status 127
dpkg: trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: /var/lib/dpkg/tmp.ci/prerm: pyclean: not found
dpkg: error processing archive /var/cache/apt/archives/python-samba_2%3a4.3.11+dfsg-0ubuntu0.16.04.6_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/python-samba.postinst: 6: /var/lib/dpkg/info/python-samba.postinst: pycompile: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Preparing to unpack .../python-minimal_2.7.11-1_amd64.deb ...
Unpacking python-minimal (2.7.11-1) over (2.7.11-1) ...
Processing triggers for man-db (2.7.5-1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/python-samba_2%3a4.3.11+dfsg-0ubuntu0.16.04.6_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jamie@jamie-ncase ~ $ 



```

---

### Post by ian-weisser on 2017-04-23
You simply need to install python-minimal *before* python-samba.

One method: Use dpkg, not apt, to bypass the error and reinstall python-minimal.
Explanation:  dpkg is a low-level package installer. Apt queues package actions, downloads packages, and has dpkg install package.

After reinstalling python-minimal, most of the apt errors should vanish.

---

### Post by roma24ster on 2017-04-24
Okay that fixed it thanks

---


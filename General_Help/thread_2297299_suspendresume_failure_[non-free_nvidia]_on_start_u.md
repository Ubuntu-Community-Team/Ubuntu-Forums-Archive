---
title: "suspend/resume failure [non-free: nvidia] on start up"
date: 2015-10-02
forum: General Help
---

### Post by mike.b2 on 2015-10-02
Hello every other time I resume or turn on I get this error. I'm new to Linux, so I don&#8217;t know how to interrupt the data.

```
 Thu Oct  1 10:53:44 EDT 2015: performing suspend
Tags: resume suspend
Uname: Linux 3.19.0-30-generic x86_64
UserGroups: 
ApportVersion: 2.14.1-0ubuntu3.15
Dependencies:
 adduser 3.113+nmu3ubuntu3
 apt-utils 1.0.1ubuntu2.10
 base-passwd 3.5.33
 busybox-initramfs 1:1.21.0-1ubuntu1
 coreutils 8.21-1ubuntu5.1
 cpio 2.11+dfsg-1ubuntu1.1
 dbus 1.6.18-0ubuntu4.3
 debconf 1.5.51ubuntu2
 debconf-i18n 1.5.51ubuntu2
 debianutils 4.4
 dpkg 1.17.5ubuntu5.4
 e2fslibs 1.42.9-3ubuntu1.3
 e2fsprogs 1.42.9-3ubuntu1.3
 findutils 4.4.2-7
 gcc-4.8-base 4.8.4-2ubuntu1~14.04
 gcc-4.9-base 4.9.1-0ubuntu1
 ifupdown 0.7.47.2ubuntu4.1
 initramfs-tools 0.103ubuntu4.2
 initramfs-tools-bin 0.103ubuntu4.2
 initscripts 2.88dsf-41ubuntu6.2
 insserv 1.14.0-5ubuntu2
 iproute2 3.12.0-2ubuntu1
 isc-dhcp-client 4.2.4-7ubuntu12.3
 isc-dhcp-common 4.2.4-7ubuntu12.3
 klibc-utils 2.0.3-0ubuntu1
 kmod 15-0ubuntu6
 libacl1 2.2.52-1
 libapparmor1 2.8.95~2430-0ubuntu5.3
 libapt-inst1.5 1.0.1ubuntu2.10
 libapt-pkg4.12 1.0.1ubuntu2.10
 libattr1 1:2.4.47-1ubuntu1
 libaudit-common 1:2.3.2-2ubuntu1
 libaudit1 1:2.3.2-2ubuntu1
 libblkid1 2.20.1-5.1ubuntu20.7
 libbz2-1.0 1.0.6-5
 libc6 2.19-0ubuntu6.6
 libcap2 1:2.24-0ubuntu2
 libcgmanager0 0.24-0ubuntu7.5
 libcomerr2 1.42.9-3ubuntu1.3
 libdb5.3 5.3.28-3ubuntu3
 libdbus-1-3 1.6.18-0ubuntu4.3
 libdebconfclient0 0.187ubuntu1
 libdrm2 2.4.60-2~ubuntu14.04.1
 libexpat1 2.1.0-4ubuntu1.1
 libgcc1 1:4.9.1-0ubuntu1
 libgpm2 1.20.4-6.1
 libjson-c2 0.11-3ubuntu1.2
 libjson0 0.11-3ubuntu1.2
 libklibc 2.0.3-0ubuntu1
 libkmod2 15-0ubuntu6
 liblocale-gettext-perl 1.05-7build3
 liblzma5 5.1.1alpha+20120614-2ubuntu2
 libmount1 2.20.1-5.1ubuntu20.7
 libncurses5 5.9+20140118-1ubuntu1
 libncursesw5 5.9+20140118-1ubuntu1
 libnih-dbus1 1.0.3-4ubuntu25
 libnih1 1.0.3-4ubuntu25
 libpam-modules 1.1.8-1ubuntu2
 libpam-modules-bin 1.1.8-1ubuntu2
 libpam-runtime 1.1.8-1ubuntu2
 libpam-systemd 204-5ubuntu20.14
 libpam0g 1.1.8-1ubuntu2
 libpcre3 1:8.31-2ubuntu2.1
 libplymouth2 0.8.8-0ubuntu17.1
 libpng12-0 1.2.50-1ubuntu2
 libprocps3 1:3.3.9-1ubuntu2.2
 libselinux1 2.2.2-1ubuntu0.1
 libsemanage-common 2.2-1
 libsemanage1 2.2-1
 libsepol1 2.2-1ubuntu0.1
 libslang2 2.2.4-15ubuntu1
 libss2 1.42.9-3ubuntu1.3
 libstdc++6 4.8.4-2ubuntu1~14.04
 libsystemd-daemon0 204-5ubuntu20.14
 libsystemd-login0 204-5ubuntu20.14
 libtext-charwidth-perl 0.04-7build3
 libtext-iconv-perl 1.7-5build2
 libtext-wrapi18n-perl 0.06-7
 libtinfo5 5.9+20140118-1ubuntu1
 libudev1 204-5ubuntu20.14
 libustr-1.0-1 1.0.4-3ubuntu2
 libuuid1 2.20.1-5.1ubuntu20.7
 libxtables10 1.4.21-1ubuntu1
 lsb-base 4.1+Debian11ubuntu6
 makedev 2.3.1-93ubuntu1
 module-init-tools 15-0ubuntu6
 mount 2.20.1-5.1ubuntu20.7
 mountall 2.53
 multiarch-support 2.19-0ubuntu6.6
 netbase 5.2
 passwd 1:4.1.5.1-1ubuntu9.1
 perl-base 5.18.2-2ubuntu1
 plymouth 0.8.8-0ubuntu17.1
 plymouth-theme-ubuntu-text 0.8.8-0ubuntu17.1
 procps 1:3.3.9-1ubuntu2.2
 psmisc 22.20-1ubuntu2
 sensible-utils 0.0.9
 systemd-services 204-5ubuntu20.14
 sysv-rc 2.88dsf-41ubuntu6.2
 sysvinit-utils 2.88dsf-41ubuntu6.2
 tar 1.27.1-1
 tzdata 2015f-0ubuntu0.14.04
 udev 204-5ubuntu20.14
 upstart 1.12.1-0ubuntu4.2
 util-linux 2.20.1-5.1ubuntu20.7
 uuid-runtime 2.20.1-5.1ubuntu20.7
 zlib1g 1:1.2.8.dfsg-1ubuntu1
InstallationDate: Installed on 2015-09-30 (1 days ago)
InstallationMedia: Ubuntu 14.04.3 LTS "Trusty Tahr" - Beta amd64 (20150805)
NonfreeKernelModules: nvidia
PackageArchitecture: amd64
ProcVersionSignature: Ubuntu 3.19.0-30.33~14.04.1-generic 3.19.8-ckt6
SourcePackage: linux-lts-vivid
Title:
 suspend/resume failure [non-free: nvidia]
```


It doesn&#8217;t seem to do too much, but I would like to fix it. Does any one know how to correct this issue? I'm on a Asus-Q550LF and the card is a geforce 745m.

---

### Post by cariboo on 2015-10-02
I think you may be looking in the wrong place, as I use suspend daily on my ASUS M5A97 R2.0 powered system, with an Nvidia Geforce 210 graphics adapter without any problems. I had an Nvidia GTX760 in the system, but it died shortly after the warranty expired, the system went into suspend with that graphics adapter also. Both cards used the proprietary graphics driver.

---

### Post by pqwoerituytrueiwoq on 2015-10-02
the only issue i have have with resume failing (or appearing to fail)
results from my HDMI TV (acting as my only monitor) is off when the system wakes
this results in there being no display, which is a bit annoying but i have a workaround using my raspberry pi and ssh
if you don't use a password you could just use a keyboard shortcut to fix it
i have used nvidia 8600m (old laptop), GTX 550 TI (sold), GT 430 (put in mom's pc), and GTX 650 TI Boost (currently use) GPUs
i have had my issue from time to time with different driver versions i have had them with my old 550 ti (sold it) and 650 to boot

the output of [FONT=courier new]dmesg[/FONT] may be more helpful, [FONT=courier new]lspci -vv[/FONT] may help

---


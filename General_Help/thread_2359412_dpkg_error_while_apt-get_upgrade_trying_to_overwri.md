---
title: "dpkg error while apt-get upgrade trying to overwrite files"
date: 2017-04-23
forum: General Help
---

### Post by diskmaster23 on 2017-04-23
```

(Reading database ... 138025 files and directories currently installed.)
Preparing to unpack .../init-system-helpers_1.29ubuntu4_all.deb ...
Unpacking init-system-helpers (1.29ubuntu4) over (1.29ubuntu3) ...
dpkg: error processing archive /var/cache/apt/archives/init-system-helpers_1.29ubuntu4_all.deb (--unpack):
 trying to overwrite '/usr/sbin/invoke-rc.d', which is also in package sysv-rc 2.88dsf-59.3ubuntu2
Errors were encountered while processing:
 /var/cache/apt/archives/init-system-helpers_1.29ubuntu4_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I cannot seem to fix this. I was going to just upgrade my packages, but for some reason, I am getting all kinds of errors. The first error I got was related to ```
bsdutils
```. Some forums recommended I put it on hold, so I did. But then another I got a similar error, but with a different package. 

How do I systematically fix this?

I am running Ubuntu 16.04 server edition.

Thanks in advance.

---

### Post by Xian on 2017-04-30
[COLOR=#111111][FONT=Ubuntu]You need to force overwriting of the files causing the errors:[/FONT][/COLOR]
```
$ [COLOR=#111111][FONT=Consolas]sudo dpkg -i --force-overwrite [/FONT][/COLOR][COLOR=#000000][FONT=&amp]/var/cache/apt/archives/init-system-helpers_1.29ubuntu4_all.deb
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]$ sudo apt-get -f install[/FONT][/COLOR]
```

---

### Post by ian-weisser on 2017-04-30
I gently suggest against using --force-overwrite as the first solution.
Without understanding the problem, down that path lies a thoroughly borked system and reinstall.

The proximate cause of the problem is that you have two packages (init-system-helpers and sysv-rc) that *conflict*. You cannot not have both installed at the same time...unless you force them.
Each release of Ubuntu is carefully designed and QA'd specifically to minimize conflicts like this. Something deeper is wrong.

There are a couple possible underlying causes:
Maybe they are intended for different releases of Ubuntu...or Debian.
Maybe one or both is from a shoddy PPA or other Non-Ubuntu source.

99.9% of the time in this forum, the problem is caused by USER CHOICES. The system is not being capricious. It's not a bug. It's not a design flaw.
You must determine which of your habits is (unintentionally) telling the computer to do something impossible. Change that habit - it's not helping you.
Then you won't have the problem anymore.

---

### Post by diskmaster23 on 2017-05-01
I would be interested in removing either packages, but I am not exactly sure which package is relevant. Am I just to remove init-system-helpers or sysv-rc? 
So, I am agreement with being against --force-overwrite.

---

### Post by diskmaster23 on 2017-05-01
> **ian-weisser said:**
> 
There are a couple possible underlying causes:
Maybe they are intended for different releases of Ubuntu...or Debian.
Maybe one or both is from a shoddy PPA or other Non-Ubuntu source.


I did upgrade from a 14.04 LTS image. So, either one of those packages might be left over from 14.04?

---

### Post by Bashing-om on 2017-05-01
diskmaster23; Well ..

As I pass by .
Both are needed:
> 
sysop@x1604:~$ apt list init-system-helpers
Listing... Done
init-system-helpers/xenial-updates,xenial-updates,now 1.29ubuntu4 all [installed]
N: There is 1 additional version. Please use the '-a' switch to see it
sysop@x1604:~$ apt list sysv-rc
Listing... Done
sysv-rc/xenial,xenial,now 2.88dsf-59.3ubuntu2 all [installed]
sysop@x1604:~$ 

The question of the why the conflict; what is the origin of the packages that the package manager is complaining of ?
show:
```

apt policy init-system-helpers sysv-rc

```

[INDENT][INDENT]work'n to get to
[INDENT][INDENT][INDENT]the bottom of things
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by diskmaster23 on 2017-05-01
The output. I appreciate the help. 
```
~$ apt policy init-system-helpers sysv-rc
init-system-helpers:
  Installed: 1.29ubuntu3
  Candidate: 1.29ubuntu4
  Version table:
     1.29ubuntu4 500
        500 [https://mirror.network32.net/ubuntu](https://mirror.network32.net/ubuntu) xenial-updates/main amd64 Packages
        500 [https://mirror.network32.net/ubuntu](https://mirror.network32.net/ubuntu) xenial-updates/main i386 Packages
 *** 1.29ubuntu3 100
        100 /var/lib/dpkg/status
     1.29ubuntu1 500
        500 [https://mirror.network32.net/ubuntu](https://mirror.network32.net/ubuntu) xenial/main amd64 Packages
        500 [https://mirror.network32.net/ubuntu](https://mirror.network32.net/ubuntu) xenial/main i386 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main i386 Packages
sysv-rc:
  Installed: 2.88dsf-59.3ubuntu2
  Candidate: 2.88dsf-59.3ubuntu2
  Version table:
 *** 2.88dsf-59.3ubuntu2 500
        500 [https://mirror.network32.net/ubuntu](https://mirror.network32.net/ubuntu) xenial/main amd64 Packages
        500 [https://mirror.network32.net/ubuntu](https://mirror.network32.net/ubuntu) xenial/main i386 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main i386 Packages
        100 /var/lib/dpkg/status

```

```

Op@:~$ apt list sysv-rc
Listing... Done
sysv-rc/xenial,xenial,xenial,xenial,now 2.88dsf-59.3ubuntu2 all [installed]
Op@:~$ apt list init-system-helpers
Listing... Done
init-system-helpers/xenial-updates,xenial-updates 1.29ubuntu4 all [upgradable from: 1.29ubuntu3]
N: There are 2 additional versions. Please use the '-a' switch to see them.
Op@:~$ apt list -a init-system-helpers
Listing... Done
init-system-helpers/xenial-updates,xenial-updates 1.29ubuntu4 all [upgradable from: 1.29ubuntu3]
init-system-helpers/now 1.29ubuntu3 all [installed,upgradable to: 1.29ubuntu4]
init-system-helpers/xenial,xenial,xenial,xenial 1.29ubuntu1 all
 
```

---

### Post by Bashing-om on 2017-05-01
diskmaster23; Hummmm ..

We have an older version of init-system-helpers installed, trying to get to the later version .
And there is this:
> 
sysop@x1604:~$ apt show init-system-helpers sysv-rc
Package: init-system-helpers
Version: 1.29ubuntu4
Priority: [color=red]required[/color]
Section: admin
Origin: Ubuntu
<snip>


A system file !. and I get real real careful ! My caution brakes are on hard .

Let's take a less invasive gentle poke at it - 
```

sudo apt install --reinstall init-system-helpers

```
See how the package manager responds ( maybe a bit of cleaning ??)

[INDENT]safety is no accident
[/INDENT]

---

### Post by diskmaster23 on 2017-05-01
Just before you posted this, I did your commands from an [earlier post ]("https://ubuntuforums.org/showthread.php?t=2235716&p=13080132#post13080132"). Same result.

apt show -a init-system-helpers sysv-rc 
Commands:```

# apt show -a init-system-helpers sysv-rc
Package: init-system-helpers
Version: 1.29ubuntu4
Priority: required
Section: admin
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian systemd Maintainers <pkg-systemd-maintainers@lists.alioth.debian.org>
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Installed-Size: 114 kB
Depends: perl-base (>= 5.20.1-3)
Conflicts: file-rc (<< 0.8.17~), openrc (<= 0.18.3-1)
Breaks: systemd (<< 44-12), sysvinit-utils (<< 2.88dsf-59.3~)
Replaces: sysv-rc (<< 2.88dsf-59.3~), sysvinit-utils (<< 2.88dsf-59.3)
Task: minimal
Supported: 5y
Download-Size: 32.3 kB
APT-Sources: [https://mirror.network32.net/ubuntu](https://mirror.network32.net/ubuntu) xenial-updates/main amd64 Packages
Description: helper tools for all init systems
 This package contains helper tools that are necessary for switching between
 the various init systems that Debian contains (e. g. sysvinit or
 systemd). An example is deb-systemd-helper, a script that enables systemd unit
 files without depending on a running systemd.
 .
 It also includes the "service", "invoke-rc.d", and "update-rc.d" scripts which
 provide an abstraction for enabling, disabling, starting, and stopping
 services for all supported Debian init systems as specified by the policy.
 .
 While this package is maintained by pkg-systemd-maintainers, it is NOT
 specific to systemd at all. Maintainers of other init systems are welcome to
 include their helpers in this package.

Package: init-system-helpers
Version: 1.29ubuntu3
Status: install ok installed
Priority: required
Section: admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian systemd Maintainers <pkg-systemd-maintainers@lists.alioth.debian.org>
Installed-Size: 114 kB
Depends: perl-base (>= 5.20.1-3)
Conflicts: file-rc (<< 0.8.17~), openrc (<= 0.18.3-1)
Breaks: systemd (<< 44-12), sysvinit-utils (<< 2.88dsf-59.3~)
Replaces: sysv-rc (<< 2.88dsf-59.3~), sysvinit-utils (<< 2.88dsf-59.3)
Download-Size: unknown
APT-Manual-Installed: yes
APT-Sources: /var/lib/dpkg/status
Description: helper tools for all init systems
 This package contains helper tools that are necessary for switching between
 the various init systems that Debian contains (e. g. sysvinit or
 systemd). An example is deb-systemd-helper, a script that enables systemd unit
 files without depending on a running systemd.
 .
 It also includes the "service", "invoke-rc.d", and "update-rc.d" scripts which
 provide an abstraction for enabling, disabling, starting, and stopping
 services for all supported Debian init systems as specified by the policy.
 .
 While this package is maintained by pkg-systemd-maintainers, it is NOT
 specific to systemd at all. Maintainers of other init systems are welcome to
include their helpers in this package.

Package: init-system-helpers
Version: 1.29ubuntu1
Priority: required
Section: admin
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian systemd Maintainers <pkg-systemd-maintainers@lists.alioth.debian.org>
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Installed-Size: 113 kB
Depends: perl-base (>= 5.20.1-3)
Conflicts: file-rc (<< 0.8.17~), openrc (<= 0.18.3-1)
Breaks: systemd (<< 44-12), sysvinit-utils (<< 2.88dsf-59.3~)
Replaces: sysv-rc (<< 2.88dsf-59.3~), sysvinit-utils (<< 2.88dsf-59.3)
Task: minimal
Supported: 5y
Download-Size: 32.1 kB
APT-Sources: [https://mirror.network32.net/ubuntu](https://mirror.network32.net/ubuntu) xenial/main amd64 Packages
Description: helper tools for all init systems
 This package contains helper tools that are necessary for switching between
 the various init systems that Debian contains (e. g. sysvinit or
 systemd). An example is deb-systemd-helper, a script that enables systemd unit
 files without depending on a running systemd.
 .
 It also includes the "service", "invoke-rc.d", and "update-rc.d" scripts which
 provide an abstraction for enabling, disabling, starting, and stopping
 services for all supported Debian init systems as specified by the policy.
 .
 While this package is maintained by pkg-systemd-maintainers, it is NOT
 specific to systemd at all. Maintainers of other init systems are welcome to
 include their helpers in this package.

Package: sysv-rc
Version: 2.88dsf-59.3ubuntu2
Priority: required
Section: admin
Source: sysvinit
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian sysvinit maintainers <pkg-sysvinit-devel@lists.alioth.debian.org>
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Installed-Size: 130 kB   
Pre-Depends: init-system-helpers (>= 1.25~)
Depends: debconf (>= 0.5) | debconf-2.0, sysvinit-utils (>= 2.86.ds1-62), insserv (>> 1.12.0-10)
Recommends: lsb-base (>= 3.2-14)
Suggests: bum
Breaks: initscripts (<< 2.86.ds1-63), systemd (<< 215)
Homepage: [http://savannah.nongnu.org/projects/sysvinit](http://savannah.nongnu.org/projects/sysvinit)
Task: minimal
Supported: 5y
Download-Size: 18.2 kB
APT-Manual-Installed: yes
APT-Sources: [https://mirror.network32.net/ubuntu](https://mirror.network32.net/ubuntu) xenial/main amd64 Packages
Description: System-V-like runlevel change mechanism
 This package provides support for the System-V like system

```

```
# sudo apt install --reinstall init-system-helpers
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  init-system-helpers
1 upgraded, 0 newly installed, 0 to remove and 164 not upgraded.
Need to get 0 B/32.3 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 126962 files and directories currently installed.)
Preparing to unpack .../init-system-helpers_1.29ubuntu4_all.deb ...
Unpacking init-system-helpers (1.29ubuntu4) over (1.29ubuntu3) ...
dpkg: error processing archive /var/cache/apt/archives/init-system-helpers_1.29ubuntu4_all.deb (--unpack):
 trying to overwrite '/usr/sbin/invoke-rc.d', which is also in package sysv-rc 2.88dsf-59.3ubuntu2
Errors were encountered while processing:
 /var/cache/apt/archives/init-system-helpers_1.29ubuntu4_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Bashing-om on 2017-05-01
diskmaster23; Yukkie !


OK, as we have:
> 
 installed, 0 to remove and 164 not upgraded.


Any joy at all from :
```

sudo apt full-upgrade

```

not much hope, but ...

[INDENT][INDENT]see if we can get any help
[/INDENT][/INDENT]

---

### Post by diskmaster23 on 2017-05-01
Yeah...no love. You can see, from what I mentioned from my first post, that I had to hold bsdutils back from upgrading. Such an odd problem with no easy solution. I would hate to have to reset up the server as it is a personal production server. I am not running any kind of VM setup, so, I can't just copy it and run it in test. 
```

# sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-4.4.0-77 linux-headers-4.4.0-77-generic linux-image-4.4.0-77-generic linux-image-extra-4.4.0-77-generic
The following packages have been kept back:
  bsdutils
The following packages will be upgraded:
  apparmor apt apt-transport-https apt-utils bind9-host console-setup console-setup-linux dbus dbus-x11 desktop-file-utils distro-info-data dnsutils docker-engine dpkg-dev eject graphviz grub-common grub-pc grub-pc-bin grub2-common init
  init-system-helpers initramfs-tools initramfs-tools-bin initramfs-tools-core keyboard-configuration klibc-utils krb5-locales krb5-multidev libapparmor-perl libapparmor1 libapt-inst2.0 libapt-pkg5.0 libarchive13 libbind9-140 libblkid1
  libc-bin libc-dev-bin libc6 libc6-dev libcdt5 libcgraph6 libdbus-1-3 libdns-export162 libdns162 libdpkg-perl libdrm-amdgpu1 libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdrm2 libevent-2.0-5 libevent-core-2.0-5 libfdisk1 libfreetype6
  libfreetype6-dev libgc1c2 libgd-dev libgd3 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglib2.0-0 libglib2.0-data libgnutls-openssl27 libgnutls30 libgssapi-krb5-2 libgssrpc4 libgvc6 libgvpr2 libhogweed4 libicu55 libisc-export160
  libisc160 libisccc140 libisccfg140 libk5crypto3 libkadm5clnt-mit9 libkadm5srv-mit9 libkdb5-8 libklibc libkrb5-3 libkrb5support0 liblwres141 libmount1 libmysqlclient-dev libmysqlclient20 libnettle6 libpam-systemd libpathplan4
  libpci-dev libpci3 libpq-dev libpq5 libsmartcols1 libsmbclient libssh2-1 libssh2-1-dev libssl-dev libssl-doc libssl1.0.0 libsystemd0 libtiff5 libtiff5-dev libtiffxx5 libudev-dev libudev1 libuuid1 libwbclient0 libxml2 libxpm-dev
  libxpm4 libxslt1.1 linux-firmware linux-generic linux-headers-generic linux-image-generic linux-libc-dev locales makedev mongodb-org mongodb-org-mongos mongodb-org-server mongodb-org-shell mongodb-org-tools mount multiarch-support
  mysql-client-5.7 mysql-client-core-5.7 mysql-common mysql-server mysql-server-5.7 mysql-server-core-5.7 nano ntfs-3g ntp ntpdate openssl os-prober pciutils python-crypto python-libxml2 python-samba python3-distupgrade
  python3-update-manager resolvconf samba-common samba-common-bin samba-libs smbclient sudo systemd systemd-sysv tcpdump tftp-hpa tftpd-hpa thermald ubuntu-release-upgrader-core udev update-manager-core util-linux uuid-runtime w3m wget
164 upgraded, 4 newly installed, 0 to remove and 1 not upgraded.
Need to get 68.6 MB/260 MB of archives.
After this operation, 277 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 https://mirror.network32.net/ubuntu xenial-updates/main amd64 linux-image-4.4.0-77-generic amd64 4.4.0-77.98 [21.9 MB]
Get:2 https://mirror.network32.net/ubuntu xenial-updates/main amd64 linux-image-extra-4.4.0-77-generic amd64 4.4.0-77.98 [35.9 MB]
Get:3 https://mirror.network32.net/ubuntu xenial-updates/main amd64 linux-generic amd64 4.4.0.77.83 [1,786 B]
Get:4 https://mirror.network32.net/ubuntu xenial-updates/main amd64 linux-image-generic amd64 4.4.0.77.83 [2,306 B]
Get:5 https://mirror.network32.net/ubuntu xenial-updates/main amd64 linux-headers-4.4.0-77 all 4.4.0-77.98 [9,979 kB]
Get:6 https://mirror.network32.net/ubuntu xenial-updates/main amd64 linux-headers-4.4.0-77-generic amd64 4.4.0-77.98 [784 kB]
Get:7 https://mirror.network32.net/ubuntu xenial-updates/main amd64 linux-headers-generic amd64 4.4.0.77.83 [2,278 B]
Fetched 68.6 MB in 5s (13.4 MB/s)                  
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 126962 files and directories currently installed.)
Preparing to unpack .../init-system-helpers_1.29ubuntu4_all.deb ...
Unpacking init-system-helpers (1.29ubuntu4) over (1.29ubuntu3) ...
dpkg: error processing archive /var/cache/apt/archives/init-system-helpers_1.29ubuntu4_all.deb (--unpack):
 trying to overwrite '/usr/sbin/invoke-rc.d', which is also in package sysv-rc 2.88dsf-59.3ubuntu2
Errors were encountered while processing:
 /var/cache/apt/archives/init-system-helpers_1.29ubuntu4_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Bashing-om on 2017-05-01
diskmaster23; Himmm..

We have :

> 
Errors were encountered while processing:
 /var/cache/apt/archives/init-system-helpers_1.29ubuntu4_all.deb


Still remain extremely leery of messing about with a system file,
But can do no harm to try:
```

sudo apt autoclean
sudo apt autoremove
sudo apt clean
sudo apt update
sudo apt full upgrade
sudo apt -f install
sudo dpkg --configure -a

```
where we clean out /var/cache/apt/archives/ [  *** 1.29ubuntu3 100 >>> 100 /var/lib/dpkg/status ] and reload with the hope that init-system-helpers file will download/install  with the updated version .


[INDENT][INDENT]hope hope but .....[/INDENT][/INDENT]
[INDENT][INDENT]worth a shot
[/INDENT][/INDENT]

---

### Post by diskmaster23 on 2017-05-01
sudo apt autoclean
```
# sudo apt autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```
sudo apt autoremove
```
# sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 165 not upgraded.

```
sudo apt clean
```
# sudo apt clean

```
sudo apt update
```
# sudo apt update
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Hit:2 http://archive.ubuntu.com/ubuntu xenial InRelease  
Hit:3 https://mirror.network32.net/ubuntu xenial InRelease   
Ign:4 http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 InRelease
Get:5 https://mirror.network32.net/ubuntu xenial-updates InRelease [102 kB]
Hit:6 http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 Release
Hit:8 https://mirror.network32.net/ubuntu zesty InRelease     
Get:9 https://mirror.network32.net/ubuntu zesty-updates InRelease [89.2 kB]
Hit:10 https://apt.dockerproject.org/repo ubuntu-xenial InRelease
Fetched 293 kB in 1s (165 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
165 packages can be upgraded. Run 'apt list --upgradable' to see them.

```
sudo apt full upgrade
```

# sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-4.4.0-77 linux-headers-4.4.0-77-generic linux-image-4.4.0-77-generic linux-image-extra-4.4.0-77-generic
The following packages have been kept back:
  bsdutils
The following packages will be upgraded:
  apparmor apt apt-transport-https apt-utils bind9-host console-setup console-setup-linux dbus dbus-x11 desktop-file-utils distro-info-data dnsutils docker-engine dpkg-dev eject graphviz grub-common grub-pc grub-pc-bin grub2-common init
  init-system-helpers initramfs-tools initramfs-tools-bin initramfs-tools-core keyboard-configuration klibc-utils krb5-locales krb5-multidev libapparmor-perl libapparmor1 libapt-inst2.0 libapt-pkg5.0 libarchive13 libbind9-140 libblkid1
  libc-bin libc-dev-bin libc6 libc6-dev libcdt5 libcgraph6 libdbus-1-3 libdns-export162 libdns162 libdpkg-perl libdrm-amdgpu1 libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdrm2 libevent-2.0-5 libevent-core-2.0-5 libfdisk1 libfreetype6
  libfreetype6-dev libgc1c2 libgd-dev libgd3 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglib2.0-0 libglib2.0-data libgnutls-openssl27 libgnutls30 libgssapi-krb5-2 libgssrpc4 libgvc6 libgvpr2 libhogweed4 libicu55 libisc-export160
  libisc160 libisccc140 libisccfg140 libk5crypto3 libkadm5clnt-mit9 libkadm5srv-mit9 libkdb5-8 libklibc libkrb5-3 libkrb5support0 liblwres141 libmount1 libmysqlclient-dev libmysqlclient20 libnettle6 libpam-systemd libpathplan4
  libpci-dev libpci3 libpq-dev libpq5 libsmartcols1 libsmbclient libssh2-1 libssh2-1-dev libssl-dev libssl-doc libssl1.0.0 libsystemd0 libtiff5 libtiff5-dev libtiffxx5 libudev-dev libudev1 libuuid1 libwbclient0 libxml2 libxpm-dev
  libxpm4 libxslt1.1 linux-firmware linux-generic linux-headers-generic linux-image-generic linux-libc-dev locales makedev mongodb-org mongodb-org-mongos mongodb-org-server mongodb-org-shell mongodb-org-tools mount multiarch-support
  mysql-client-5.7 mysql-client-core-5.7 mysql-common mysql-server mysql-server-5.7 mysql-server-core-5.7 nano ntfs-3g ntp ntpdate openssl os-prober pciutils python-crypto python-libxml2 python-samba python3-distupgrade
  python3-update-manager resolvconf samba-common samba-common-bin samba-libs smbclient sudo systemd systemd-sysv tcpdump tftp-hpa tftpd-hpa thermald ubuntu-release-upgrader-core udev update-manager-core util-linux uuid-runtime w3m wget
164 upgraded, 4 newly installed, 0 to remove and 1 not upgraded.
Need to get 260 MB of archives.
After this operation, 277 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2/multiverse amd64 mongodb-org-shell amd64 3.2.13 [5,260 kB]
Get:2 https://apt.dockerproject.org/repo ubuntu-xenial/main amd64 docker-engine amd64 17.04.0~ce-0~ubuntu-xenial [18.0 MB]
Get:3 https://mirror.network32.net/ubuntu xenial-updates/main amd64 init-system-helpers all 1.29ubuntu4 [32.3 kB]
Get:4 https://mirror.network32.net/ubuntu xenial-updates/main amd64 init amd64 1.29ubuntu4 [4,624 B]       
Get:5 https://mirror.network32.net/ubuntu xenial-updates/main amd64 util-linux amd64 2.27.1-6ubuntu3.2 [848 kB]
Get:6 http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2/multiverse amd64 mongodb-org-server amd64 3.2.13 [9,973 kB]
Get:7 https://mirror.network32.net/ubuntu xenial-updates/main amd64 mount amd64 2.27.1-6ubuntu3.2 [121 kB]
Get:8 http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2/multiverse amd64 mongodb-org-mongos amd64 3.2.13 [4,664 kB]
Get:9 http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2/multiverse amd64 mongodb-org-tools amd64 3.2.13 [31.7 MB]
Get:10 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libc6-dev amd64 2.23-0ubuntu7 [2,080 kB]
Get:11 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libc-dev-bin amd64 2.23-0ubuntu7 [68.6 kB]
Get:12 https://mirror.network32.net/ubuntu xenial-updates/main amd64 linux-libc-dev amd64 4.4.0-77.98 [836 kB]
Get:13 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libc6 amd64 2.23-0ubuntu7 [2,590 kB]
Get:14 http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2/multiverse amd64 mongodb-org amd64 3.2.13 [3,564 B]
Get:15 https://mirror.network32.net/ubuntu xenial-updates/main amd64 locales all 2.23-0ubuntu7 [3,222 kB]
Get:16 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libc-bin amd64 2.23-0ubuntu7 [622 kB]
Get:17 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libapt-pkg5.0 amd64 1.2.20 [707 kB]
Get:18 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libapt-inst2.0 amd64 1.2.20 [55.6 kB]
Get:19 https://mirror.network32.net/ubuntu xenial-updates/main amd64 apt amd64 1.2.20 [1,042 kB]                                                                                                                                             
Get:20 https://mirror.network32.net/ubuntu xenial-updates/main amd64 apt-utils amd64 1.2.20 [196 kB]                                                                                                                                         
Get:21 https://mirror.network32.net/ubuntu xenial-updates/main amd64 dbus-x11 amd64 1.10.6-1ubuntu3.3 [21.4 kB]                                                                                                                              
Get:22 https://mirror.network32.net/ubuntu xenial-updates/main amd64 dbus amd64 1.10.6-1ubuntu3.3 [142 kB]                                                                                                                                   
Get:23 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libdbus-1-3 amd64 1.10.6-1ubuntu3.3 [161 kB]                                                                                                                            
Get:24 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libapparmor1 amd64 2.10.95-0ubuntu2.6 [31.7 kB]                                                                                                                         
Get:25 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libuuid1 amd64 2.27.1-6ubuntu3.2 [15.7 kB]                                                                                                                              
Get:26 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libblkid1 amd64 2.27.1-6ubuntu3.2 [107 kB]                                                                                                                              
Get:27 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libsystemd0 amd64 229-4ubuntu17 [205 kB]                                                                                                                                
Get:28 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libpam-systemd amd64 229-4ubuntu17 [115 kB]                                                                                                                             
Get:29 https://mirror.network32.net/ubuntu xenial-updates/main amd64 systemd amd64 229-4ubuntu17 [3,623 kB]                                                                                                                                  
Get:30 https://mirror.network32.net/ubuntu xenial-updates/main amd64 udev amd64 229-4ubuntu17 [992 kB]                                                                                                                                       
Get:31 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libudev-dev amd64 229-4ubuntu17 [150 kB]                                                                                                                                
Get:32 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libudev1 amd64 229-4ubuntu17 [55.3 kB]                                                                                                                                  
Get:33 https://mirror.network32.net/ubuntu xenial-updates/main amd64 klibc-utils amd64 2.0.4-8ubuntu1.16.04.3 [108 kB]                                                                                                                       
Get:34 https://mirror.network32.net/ubuntu xenial-updates/main amd64 initramfs-tools all 0.122ubuntu8.8 [8,610 B]                                                                                                                            
Get:35 https://mirror.network32.net/ubuntu xenial-updates/main amd64 initramfs-tools-core all 0.122ubuntu8.8 [42.6 kB]                                                                                                                       
Get:36 https://mirror.network32.net/ubuntu xenial-updates/main amd64 initramfs-tools-bin amd64 0.122ubuntu8.8 [9,618 B]                                                                                                                      
Get:37 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libklibc amd64 2.0.4-8ubuntu1.16.04.3 [41.3 kB]                                                                                                                         
Get:38 https://mirror.network32.net/ubuntu xenial-updates/main amd64 systemd-sysv amd64 229-4ubuntu17 [12.8 kB]                                                                                                                              
Get:39 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libmount1 amd64 2.27.1-6ubuntu3.2 [114 kB]    
.....(lost code due to Mosh)
Get:120 https://mirror.network32.net/ubuntu xenial-updates/main amd64 tcpdump amd64 4.9.0-1ubuntu1~ubuntu16.04.1 [382 kB]                                                                                                                     
Get:121 https://mirror.network32.net/ubuntu xenial-updates/main amd64 wget amd64 1.17.1-1ubuntu1.2 [298 kB]                                                                                                                                   
Get:122 https://mirror.network32.net/ubuntu xenial-updates/main amd64 desktop-file-utils amd64 0.22-1ubuntu5.1 [43.8 kB]                                                                                                                      
Get:123 https://mirror.network32.net/ubuntu xenial-updates/main amd64 dpkg-dev all 1.18.4ubuntu1.2 [584 kB]                                                                                                                                   
Get:124 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libdpkg-perl all 1.18.4ubuntu1.2 [195 kB]                                                                                                                               
Get:125 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libcdt5 amd64 2.38.0-12ubuntu2.1 [23.4 kB]                                                                                                                              
Get:126 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libcgraph6 amd64 2.38.0-12ubuntu2.1 [43.6 kB]                                                                                                                           
Get:127 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libxpm-dev amd64 1:3.5.11-1ubuntu0.16.04.1 [86.7 kB]                                                                                                                    
Get:128 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libxpm4 amd64 1:3.5.11-1ubuntu0.16.04.1 [33.8 kB]                                                                                                                       
Get:129 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libtiff5-dev amd64 4.0.6-1ubuntu0.1 [267 kB]                                                                                                                            
Get:130 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libtiff5 amd64 4.0.6-1ubuntu0.1 [146 kB]                                                                                                                                
Get:131 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libtiffxx5 amd64 4.0.6-1ubuntu0.1 [5,588 B]                                                                                                                             
Get:132 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libgd-dev amd64 2.1.1-4ubuntu0.16.04.6 [256 kB]                                                                                                                         
Get:133 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libgd3 amd64 2.1.1-4ubuntu0.16.04.6 [126 kB]                                                                                                                            
Get:134 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libpathplan4 amd64 2.38.0-12ubuntu2.1 [26.6 kB]                                                                                                                         
Get:135 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libgvc6 amd64 2.38.0-12ubuntu2.1 [591 kB]                                                                                                                               
Get:136 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libgvpr2 amd64 2.38.0-12ubuntu2.1 [170 kB]                                                                                                                             
Get:137 https://mirror.network32.net/ubuntu xenial-updates/main amd64 graphviz amd64 2.38.0-12ubuntu2.1 [680 kB]                                                                                                                             
Get:138 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libdrm-amdgpu1 amd64 2.4.70-1~ubuntu16.04.1 [16.5 kB]                                                                                                                  
Get:139 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libdrm-intel1 amd64 2.4.70-1~ubuntu16.04.1 [56.0 kB]                                                                                                                   
Get:140 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libdrm-nouveau2 amd64 2.4.70-1~ubuntu16.04.1 [16.3 kB]                                                                                                                 
Get:141 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libdrm-radeon1 amd64 2.4.70-1~ubuntu16.04.1 [21.6 kB]                                                                                                                  
Get:142 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libevent-2.0-5 amd64 2.0.21-stable-2ubuntu0.16.04.1 [114 kB]                                                                                                           
Get:143 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libgc1c2 amd64 1:7.4.2-7.3ubuntu0.1 [82.1 kB]                                                                                                                          
Get:144 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libgl1-mesa-dri amd64 12.0.6-0ubuntu0.16.04.1 [4,344 kB]                                                                                                               
Get:145 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libgl1-mesa-glx amd64 12.0.6-0ubuntu0.16.04.1 [130 kB]                                                                                                                 
Get:146 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libglapi-mesa amd64 12.0.6-0ubuntu0.16.04.1 [22.9 kB]                                                                                                                  
Get:147 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libmysqlclient-dev amd64 5.7.18-0ubuntu0.16.04.1 [1,160 kB]                                                                                                            
Get:148 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libmysqlclient20 amd64 5.7.18-0ubuntu0.16.04.1 [811 kB]                                                                                                                
Get:149 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libpq-dev amd64 9.5.6-0ubuntu0.16.04 [154 kB]                                                                                                                          
Get:150 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libpq5 amd64 9.5.6-0ubuntu0.16.04 [78.2 kB]                                                                                                                            
Get:151 https://mirror.network32.net/ubuntu xenial-updates/universe amd64 libssh2-1-dev amd64 1.5.0-2ubuntu0.1 [233 kB]                                                                                                                      
Get:152 https://mirror.network32.net/ubuntu xenial-updates/universe amd64 libssh2-1 amd64 1.5.0-2ubuntu0.1 [70.2 kB]                                                                                                                         
Get:153 https://mirror.network32.net/ubuntu xenial-updates/main amd64 libxslt1.1 amd64 1.1.28-2.1ubuntu0.1 [145 kB]                                                                                                                          
Get:154 https://mirror.network32.net/ubuntu xenial-updates/main amd64 linux-firmware all 1.157.8 [37.7 MB]                                                                                                                                   
Get:155 https://mirror.network32.net/ubuntu xenial-updates/main amd64 linux-image-4.4.0-77-generic amd64 4.4.0-77.98 [21.9 MB]                                                                                                               
Get:156 https://mirror.network32.net/ubuntu xenial-updates/main amd64 linux-image-extra-4.4.0-77-generic amd64 4.4.0-77.98 [35.9 MB]                                                                                                         
Get:157 https://mirror.network32.net/ubuntu xenial-updates/main amd64 linux-generic amd64 4.4.0.77.83 [1,786 B]                                                                                                                              
Get:158 https://mirror.network32.net/ubuntu xenial-updates/main amd64 linux-image-generic amd64 4.4.0.77.83 [2,306 B]                                                                                                                        
Get:159 https://mirror.network32.net/ubuntu xenial-updates/main amd64 linux-headers-4.4.0-77 all 4.4.0-77.98 [9,979 kB]                                                                                                                      
Get:160 https://mirror.network32.net/ubuntu xenial-updates/main amd64 linux-headers-4.4.0-77-generic amd64 4.4.0-77.98 [784 kB]                                                                                                              
Get:161 https://mirror.network32.net/ubuntu xenial-updates/main amd64 linux-headers-generic amd64 4.4.0.77.83 [2,278 B]                                                                                                                      
99% [Working]                                                                                                                                                                                                       
Get:162 https://mirror.network32.net/ubuntu xenial-updates/main amd64 mysql-server all 5.7.18-0ubuntu0.16.04.1 [10.8 kB]                                                                                           
Get:163 https://mirror.network32.net/ubuntu xenial-updates/main amd64 os-prober amd64 1.70ubuntu3.3 [19.1 kB]                                                                                                        
Get:164 https://mirror.network32.net/ubuntu xenial-updates/main amd64 python-libxml2 amd64 2.9.3+dfsg1-1ubuntu0.2 [140 kB]                                                                                           
Get:165 https://mirror.network32.net/ubuntu xenial-updates/main amd64 thermald amd64 1.5-2ubuntu4 [187 kB]                                                                                                           
Get:166 https://mirror.network32.net/ubuntu xenial-updates/universe amd64 w3m amd64 0.5.3-26ubuntu0.1 [911 kB]                                                                                                       
Get:167 https://mirror.network32.net/ubuntu xenial-updates/main amd64 tftp-hpa amd64 5.2+20150808-1ubuntu1.16.04.1 [18.0 kB]                                                                                         
Get:168 https://mirror.network32.net/ubuntu xenial-updates/main amd64 tftpd-hpa amd64 5.2+20150808-1ubuntu1.16.04.1 [39.1 kB]                                                                                        
Fetched 260 MB in 55s (4,638 kB/s)                                                                                                                                                                                   
Extracting templates from packages: 100%  
Preconfiguring packages ...  
(Reading database ... 126962 files and directories currently installed.)  
Preparing to unpack .../init-system-helpers_1.29ubuntu4_all.deb ...  
Unpacking init-system-helpers (1.29ubuntu4) over (1.29ubuntu3) ...  
dpkg: error processing archive /var/cache/apt/archives/init-system-helpers_1.29ubuntu4_all.deb (--unpack):  
 trying to overwrite '/usr/sbin/invoke-rc.d', which is also in package sysv-rc 2.88dsf-59.3ubuntu2  
Errors were encountered while processing:  
 /var/cache/apt/archives/init-system-helpers_1.29ubuntu4_all.deb  
E: Sub-process /usr/bin/dpkg returned an error code (1)  

```
sudo apt -f install
```

# sudo apt -f install init-system-helpers
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  init-system-helpers
1 upgraded, 0 newly installed, 0 to remove and 164 not upgraded.
Need to get 0 B/32.3 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 126962 files and directories currently installed.)
Preparing to unpack .../init-system-helpers_1.29ubuntu4_all.deb ...
Unpacking init-system-helpers (1.29ubuntu4) over (1.29ubuntu3) ...
dpkg: error processing archive /var/cache/apt/archives/init-system-helpers_1.29ubuntu4_all.deb (--unpack):
 trying to overwrite '/usr/sbin/invoke-rc.d', which is also in package sysv-rc 2.88dsf-59.3ubuntu2
Errors were encountered while processing:
 /var/cache/apt/archives/init-system-helpers_1.29ubuntu4_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```
sudo dpkg --configure -a
```

# sudo dpkg --configure -a


# sudo dpkg --configure -a init-system-helpers
dpkg: error: --configure --pending does not take any non-option arguments

Type dpkg --help for help about installing and deinstalling packages [*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through 'less' or 'more' !


```

---

### Post by Bashing-om on 2017-05-01
diskmaster23; welp'

Sorta kinda stuck at this point .
Lemme have a bit more time, see what I can come up with . 
system files = leery to do much !

[INDENT][INDENT]maybe, only a maybe
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2017-05-04
diskmaster23;  Yuk ..

I am still stuck at this point . I do not know of a "safe" way to proceed.
I leave it to those with the greater knowledge to advise further.

I sure would like to learn the more !

[INDENT][INDENT]sometimes, I just do not know
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2017-05-04
Okay, I was wrong in post #3 - your due diligence has conclusively shown that nothing deeper is wrong after all.
Thank you for doing that work.

Consider filing a bug against these two packages for the conflict. It is not expected behavior.

Then go ahead and use --force as Xian recommended in Post #2.

---

### Post by diskmaster23 on 2017-05-06
I am in a position to convert this machine to a VM. I had a motherboard failure, so I am going to take it the opportunity to convert the OS to VM then duplicate it to a test environment and do the --force and see what happens.

> Consider filing a bug against these two packages for the conflict. It is not expected behavior.
I've never had to file a bug report before, is there a guide? I don't want to waste individual's time here.

---

### Post by oldos2er on 2017-05-06
```
ubuntu-bug <package name>
``` will walk you through the process.

---

### Post by diskmaster23 on 2017-05-17
I made a bug report. Tried the forcing of installation of packages, but at some point I get a roadblock with problems with kernel issues. 

I decided to rebuild the system from scratch and utilize docker containers. I still have a VM of the original OS with the issue, so if someone wants to try something, we can do that.  

This issue isn't resolved, but I resolved it by just starting with 16.04.02 instead of 14.04 upgrading to 16.04. It's too bad.

---


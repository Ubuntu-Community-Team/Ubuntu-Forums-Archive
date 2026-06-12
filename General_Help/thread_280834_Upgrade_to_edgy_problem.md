---
title: "Upgrade to edgy problem"
date: 2006-10-20
forum: General Help
---

### Post by dweezil-n0xad on 2006-10-20
I was upgrading from dapper to the release candidate of edgy eft, and my system freezed. I rebooted, and now apt-get returns an error:
```
dweezil@laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libpango1.0-dev: Depends: libxft-dev but it is not installed
  tk8.5-dev: Depends: libxft-dev but it is not installed
  xserver-xorg: Depends: xkb-data but it is not installed or
                         xkb-data-legacy but it is not installed
  xserver-xorg-core: Depends: x11-common (>= 1:7.0.0) but 7.0.0-0ubuntu45 is installed
  xutils: Depends: xutils-dev but it is not installed
E: Unmet dependencies. Try using -f.
dweezil@laptop:~$ sudo apt-get dist-upgrade -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
Calculating upgrade... Done
---
<snip>
---
1162 upgraded, 174 newly installed, 24 to remove and 37 not upgraded.
43 not fully installed or removed.
---
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 135999 files and directories currently installed.)
Preparing to replace x11-common 7.0.0-0ubuntu45 (using .../x11-common_1%3a7.1.1ubuntu5_i386.deb) ...
Unpacking replacement x11-common ...
dpkg: error processing /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu5_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man5/Xsession.5.gz', which is also in package xinit
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```What should I do now? :confused:

---

### Post by kloy1334 on 2006-10-20
sudo dpkg -i --force-overwrite /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu5_i386.deb

---

### Post by dweezil-n0xad on 2006-10-20
thanks :)

---


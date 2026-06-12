---
title: "WHat is in ubuntu-minimal?"
date: 2019-05-13
forum: General Help
---

### Post by rsteinmetz70112 on 2019-05-13
I'm looking for a list of packages installed by the ubuntu-minimal metapackage.

Can someone point me to a list?

This
 [LIST]
[*][https://packages.ubuntu.com/xenial/ubuntu-minimal](https://packages.ubuntu.com/xenial/ubuntu-minimal)
[/LIST]
lists the dependencies but it doesn't seem complete.
Running the apt install -s still doesn't seem like it will install a working system but it's probably ignoring the packages I have already installed.

---

### Post by deadflowr on 2019-05-13
That's exactly what the ubuntu-minimal package installs.
It's complete as far as that particular package goes.

Isn't it already installed?
Or at least everything it depends on should already be installed.

---

### Post by #&amp;thj^% on 2019-05-13
^^^^^^^^^^^^^^^^^^ +1
```
"apt show ubuntu-minimal"

Package: ubuntu-minimal
Version: 1.431
Priority: important
Section: metapackages
Source: ubuntu-meta
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 50.2 kB
[B]Depends: adduser, apt, apt-utils, bzip2, console-setup, debconf, debconf-i18n, e2fsprogs, eject, init, initramfs-tools, iproute2, iputils-ping, isc-dhcp-client, kbd, kmod, less, locales, lsb-release, mawk, mount, netbase, netcat-openbsd, netplan.io, passwd, procps, python3, sensible-utils, sudo, tzdata, ubuntu-advantage-tools, ubuntu-keyring, udev, vim-tiny, whiptail
Recommends: rsyslog
Task: minimal[/B]
Supported: 9m
Download-Size: 4,020 B
APT-Sources: http://archive.ubuntu.com/ubuntu disco/main amd64 Packages
Description: Minimal core of Ubuntu
 This package depends on all of the packages in the Ubuntu minimal system,
 that is a functional command-line system with the following capabilities:
 .
  - Boot
  - Detect hardware
  - Connect to a network
  - Install packages
  - Perform basic diagnostics
 .
 It is also used to help ensure proper upgrades, so it is recommended that
 it not be removed.

```

---

### Post by rsteinmetz70112 on 2019-05-15
But here is my problem:

adduser is included in ubuntu-minimal its page says it depends on :

debconf
   or debconf-2.0
passwd 
perl-base

And while those should be installed on a minimal system, perl-base is not indicated as being installed with ubuntu-minimal
So I'm wondering how you get what ubuntu-minimal says it provides, a minimal command line system.

And no it isn't installed on my working system which was upgraded from previous version of Ubuntu.

It also says it depends on all of the packages in the Ubuntu minimal install, so I'm not sure why these few tools are already included.

---


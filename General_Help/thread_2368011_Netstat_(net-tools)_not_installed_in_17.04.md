---
title: "Netstat (net-tools) not installed in 17.04?"
date: 2017-08-05
forum: General Help
---

### Post by yuki2005w on 2017-08-05
Is net-tools not installed by default in Ubuntu 17.04? What alternative is there for seeing the IP addresses of active connections? I usually use [netstat -natpc]

---

### Post by yuki2005w on 2017-08-05
Looks like I can use; [FONT=monospace]watch -n 1 ss -natp / [/FONT][COLOR=#4F4F4F][FONT=verdana]while true; do ss -natp; sleep 1; done[/FONT][/COLOR]

---

### Post by vocx on 2017-08-05
> **yuki2005w said:**
> Is net-tools not installed by default in Ubuntu 17.04? What alternative is there for seeing the IP addresses of active connections? I usually use [netstat -natpc]

I guess you have to manually install it. Not a problem, is it?
```

apt policy net-tools

```
```

net-tools:
  Installed: 1.60-26ubuntu1
  Candidate: 1.60-26ubuntu1
  Version table:
 *** 1.60-26ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status

```

```

apt show net-tools

```

```

Package: net-tools
Version: 1.60-26ubuntu1
Priority: important
Section: net
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: net-tools Team <pkg-net-tools-maintainers@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 725 kB
Depends: libc6 (>= 2.14)
Conflicts: ja-trans (<= 0.8-2)
Replaces: ja-trans (<= 0.8-2), netbase (<< 4.00)
Homepage: http://net-tools.berlios.de/
Task: minimal
Supported: 5y
Download-Size: 175 kB
**APT-Manual-Installed: yes**
APT-Sources: http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
Description: NET-3 networking toolkit
 This package includes the important tools for controlling the network
 subsystem of the Linux kernel.  This includes arp, ifconfig, netstat,
 rarp, nameif and route.  Additionally, this package contains utilities
 relating to particular network hardware types (plipconfig, slattach,
 mii-tool) and advanced aspects of IP configuration (iptunnel, ipmaddr).
 .
 In the upstream package 'hostname' and friends are included. Those are
 not installed by this package, since there is a special "hostname*.deb".

```

---

### Post by yuki2005w on 2017-08-05
It it is not a problem to install it, but it gives me peace of mind to know that I am downloading from the correct mirror if I can see the ip address. Luckily I can use [ss -natp] before I have netstat installed.

---

### Post by fbukevin on 2017-09-25
It seems that this is true.

[https://lists.ubuntu.com/archives/ubuntu-devel/2017-January/039651.html](https://lists.ubuntu.com/archives/ubuntu-devel/2017-January/039651.html)

---


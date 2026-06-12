---
title: "Managed to screw up VMWare Player"
date: 2007-05-17
forum: General Help
---

### Post by dilyard on 2007-05-17
I had vmplayer running great loading my native Windows XP partition in the Feisty Beta. I've since ran the various program updates and am currently running 2.6.20-15 kernel. I've removed vmplayer and re-installed it, but I'm getting no love. Here is what I'm seeing when I run vmplayer:

> /usr/lib/vmware-player/bin/vmplayer: /usr/lib/vmware-player/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

(vmplayer:11625): Gtk-WARNING **: /usr/lib/vmware-player/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

(vmplayer:11625): Gtk-WARNING **: /usr/lib/vmware-player/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

Do these messages mean anything to anyone? Thanks in advance.

---

### Post by dexter on 2007-05-17
Try "sudo vmware-config.pl" to reconfigue vmware.

---

### Post by dilyard on 2007-05-17
I thought of that, but apparently it does not exist with the version I have installed. The only config file that included in the package is the vmware-config-network.pl script.

debtags show vmware-player:

> 

Name: vmware-player
Priority: not available
Section: multiverse/misc
Installed-Size: 31M
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 1.0.2-2
Depends: not available
Filename: pool/multiverse/v/vmware-player/vmware-player_1.0.2-2_i386.deb
Size: not available
MD5Sum: 2fdf9d0e16cf0fa1e4bb885c731aaca8


dpkg -L vmware-player|grep config:

> 
/etc/vmware/config
/usr/lib/vmware-player/config
/usr/lib/vmware-player/configurator
/usr/lib/vmware-player/configurator/vmnet-dhcpd.conf
/usr/lib/vmware-player/configurator/vmnet-nat.conf
/usr/lib/vmware-player/lib/libfontconfig.so.1
/usr/lib/vmware-player/lib/libfontconfig.so.1/libfontconfig.so.1
/usr/lib/vmware-player/share/pixmaps/startup-config.png
/usr/bin/vmware-config-network.pl


---

### Post by dilyard on 2007-05-18
I fixed the problem. I'm not sure what the issue was with the Ubuntu package, but I downloaded the latest VMware Player (version 2.0) from [http://http://www.vmware.com/download/player/download.html]("http://http://www.vmware.com/download/player/download.html"), completely removed the installed version and installed from the tarball. A bunch of <enter> keys later, I was logging into my XP installation without any problems.

---


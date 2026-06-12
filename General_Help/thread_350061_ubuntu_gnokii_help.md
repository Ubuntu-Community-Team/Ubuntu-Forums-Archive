---
title: "ubuntu gnokii help"
date: 2007-01-31
forum: General Help
---

### Post by michie86 on 2007-01-31
hello
i'm using ubuntu 6.06, i downloaded the binaries for gnokii but when I try to install it and do

sudo dpkg -i gnokii_0.6.14+cvs20070111-1_i386.deb

this is what happened

Selecting previously deselected package gnokii.
(Reading database ... 69877 files and directories currently installed.)
Unpacking gnokii (from gnokii_0.6.14+cvs20070111-1_i386.deb) ...
Adding group `gnokii' (113)...
Done.
dpkg: dependency problems prevent configuration of gnokii:
 gnokii depends on libbluetooth2 (>= 3.0); however:
  Package libbluetooth2 is not installed.
 gnokii depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 gnokii depends on libgnokii3; however:
  Package libgnokii3 is not installed.
 gnokii depends on libusb-0.1-4 (>= 2:0.1.12); however:
  Version of libusb-0.1-4 on system is 2:0.1.10a-22ubuntu1.
dpkg: error processing gnokii (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnokii

so i looked for the packages said above and got them from packages.debian.org/unstable/.. but I'm wonedring wether installing these packages would have bad effects? or is it ok to just install them? for example, will i still be able to use my gnome-bluetooth perfectly?

thanks in advance

ps. sorry if I posted this in the wrong place.. need help

---


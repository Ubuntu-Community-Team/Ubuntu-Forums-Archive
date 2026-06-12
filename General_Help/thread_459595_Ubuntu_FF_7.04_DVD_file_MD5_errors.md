---
title: "Ubuntu FF 7.04 DVD file MD5 errors"
date: 2007-05-30
forum: General Help
---

### Post by Nom DePost on 2007-05-30
i downloaded the DVD over the weekend (27 May).  the ISO MD5 checks out but the DVD's files MD5  has 11 errors:

.\install\netboot\pxelinux.cfg\default ERROR: E:\.\install\netboot\pxelinux.cfg\default does not exists.

.\install\netboot\pxelinux.0 ERROR: Checksum did not match.

.\pool\main\l\linux-source-2.6.20\firewire-core-modules-2.6.20-15-generic-di_2.6.20-15.27_i386.udeb ERROR: E:\.\pool\main\l\linux-source-2.6.20\firewire-core-modules-2.6.20-15-generic-di_2.6.20-15.27_i386.udeb does not exists.

.\pool\main\l\linux-source-2.6.20\pcmcia-storage-modules-2.6.20-15-generic-di_2.6.20-15.27_i386.udeb ERROR: E:\.\pool\main\l\linux-source-2.6.20\pcmcia-storage-modules-2.6.20-15-generic-di_2.6.20-15.27_i386.udeb does not exists.

.\pool\main\l\linux-backports-modules-2.6.20\linux-backports-modules-2.6.20-15-server-bigiron_2.6.20-15.10_i386.deb ERROR: E:\.\pool\main\l\linux-backports-modules-2.6.20\linux-backports-modules-2.6.20-15-server-bigiron_2.6.20-15.10_i386.deb does not exists.

.\pool\main\h\hplip\hplip-data_1.7.3-0ubuntu1_all.deb ERROR: Checksum did not match.

.\pool\main\t\tetex-base\tetex-base_3.0.dfsg.3-4_all.deb ERROR: Checksum did not match.

.\pool\restricted\l\linux-restricted-modules-2.6.20\nic-restricted-firmware-2.6.20-15-generic-di_2.6.20.5-15.20_i386.udeb ERROR: E:\.\pool\restricted\l\linux-restricted-modules-2.6.20\nic-restricted-firmware-2.6.20-15-generic-di_2.6.20.5-15.20_i386.udeb does not exists.

.\pool\restricted\l\linux-restricted-modules-2.6.20\nic-restricted-modules-2.6.20-15-generic-di_2.6.20.5-15.20_i386.udeb ERROR: E:\.\pool\restricted\l\linux-restricted-modules-2.6.20\nic-restricted-modules-2.6.20-15-generic-di_2.6.20.5-15.20_i386.udeb does not exists.

.\pool\restricted\l\linux-restricted-modules-2.6.20\linux-restricted-modules-2.6.20-15-generic_2.6.20.5-15.20_i386.deb ERROR: E:\.\pool\restricted\l\linux-restricted-modules-2.6.20\linux-restricted-modules-2.6.20-15-generic_2.6.20.5-15.20_i386.deb does not exists.

.\pool\restricted\l\linux-restricted-modules-2.6.20\nic-restricted-firmware-2.6.20-15-386-di_2.6.20.5-15.20_i386.udeb ERROR: E:\.\pool\restricted\l\linux-restricted-modules-2.6.20\nic-restricted-firmware-2.6.20-15-386-di_2.6.20.5-15.20_i386.udeb does not exists.

---

### Post by merlinus on 2007-05-30
These questions may be far too obvious, but perhaps are a source of your problems.

Did you burn the .iso to a cd, or dvd?

Did you burn it as a disk image, or as a data disk?  It has to be the former.

Did you burn it at as slow a speed as possible?

-merlin

---


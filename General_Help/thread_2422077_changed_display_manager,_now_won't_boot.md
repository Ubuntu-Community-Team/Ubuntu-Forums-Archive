---
title: "changed display manager, now won't boot"
date: 2019-07-01
forum: General Help
---

### Post by RogerDavis on 2019-07-01
roger@roger-desktop:~$ sudo dpkg-reconfigure gdm
[sudo] password for roger:
/usr/sbin/dpkg-reconfigure: gdm is broken or not fully installed
roger@roger-desktop:~$
===
roger@roger-desktop:~$ sudo apt-get install gdm3
[sudo] password for roger:
Reading package lists... Done
Building dependency tree
Reading state information... Done
gdm3 is already the newest version (3.28.3-0ubuntu18.04.4).
gdm3 set to manually installed.
The following packages were automatically installed and are no longer required:
libapparmor1:i386 libargon2-0:i386 libcryptsetup12:i386
libdevmapper1.02.1:i386 libgck-1-0:i386 libgcr-base-3-1:i386
libgudev-1.0-0:i386 libip4tc0:i386 libjson-c3:i386 libseccomp2:i386
libsecret-1-0:i386 libudisks2-0:i386
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
roger@roger-desktop:~$
===
roger@roger-desktop:~$ sudo dpkg-reconfigure gdm3
[sudo] password for roger:
gdm.service is not active, cannot reload.
invoke-rc.d: initscript gdm3, action "reload" failed.
roger@roger-desktop:~$ 

==========================================
I rebooted, and got big problems. It begins to boot, gets to purple screen and then just rotates the dots. Depending on what keys I beat on, I get Ubuntu with dots, stops at "created slice system -getty slice, started Gnome display manager, system log-in (but I don't know what it wants for that - can't get back there anyway... , just the password doesn't work, or logitech-hidpp device - (numbers) unable to retrieve ...(name?) of device. I'm stuck with the old computer until I can get this done.

---


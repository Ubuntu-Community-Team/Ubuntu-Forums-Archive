---
title: "My Galaxy s5 woun't mount, I can see it with lsusb."
date: 2014-08-01
forum: General Help
---

### Post by jlsplinter on 2014-08-01
The phone display connected as media device, but I don't see it mounted. How do I make it work?

jose@Laptop-52:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 005 Device 002: ID 0d8c:0103 C-Media Electronics, Inc. CM102-A+/102S+ Audio Controller
Bus 005 Device 003: ID 046d:c50e Logitech, Inc. Cordless Mouse Receiver
Bus 002 Device 008: ID 04e8:6860 Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II]
jose@Laptop-52:~$

---

### Post by jlsplinter on 2014-08-01
When I connect it the directory libmtp-2-8.1 is created under /dev.  I also ran this command and returned this:

jose@Laptop-52:/dev$ gvfs-mount  --list
Drive(0): CD/DVD Drive
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
Volume(0): SAMSUNG_Android
  Type: GProxyVolume (GProxyVolumeMonitorGPhoto2)
Volume(1): SAMSUNG_Android
  Type: GProxyVolume (GProxyVolumeMonitorGPhoto2)
jose@Laptop-52:/dev$ ls

---


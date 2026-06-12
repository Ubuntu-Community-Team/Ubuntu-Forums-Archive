---
title: "XPS13 9300 - fingerprint reader - any driver updates?"
date: 2020-05-14
forum: General Help
---

### Post by makem2 on 2020-05-14
```

makem@XPS-13-9300:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04 LTS
Release:    20.04
Codename:    focal
makem@XPS-13-9300:~$

```

```

makem@XPS-13-9300:~$ lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0bda:58fe Realtek Semiconductor Corp. Integrated_Webcam_HD
Bus 003 Device 002: ID 27c6:533c Shenzhen Goodix Technology Co.,Ltd. FingerPrint
Bus 003 Device 004: ID 8087:0026 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
makem@XPS-13-9300:~$

```

As shown above this machine has a fingerprint reader and I have installed the following packages:

```

makem@XPS-13-9300:~$ sudo apt-get install fprintd libfprint-2-2 libfprint-2-tod1 libpam-fprintd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fprintd is already the newest version (1.90.1-1ubuntu1).
libfprint-2-2 is already the newest version (1:1.90.1+tod1-0ubuntu4).
libfprint-2-2 set to manually installed.
libfprint-2-tod1 is already the newest version (1:1.90.1+tod1-0ubuntu4).
libfprint-2-tod1 set to manually installed.
libpam-fprintd is already the newest version (1.90.1-1ubuntu1).
0 to upgrade, 0 to newly install, 0 to remove and 1 not to upgrade.
makem@XPS-13-9300:~$

```

This web page: 

[URL="https://linux-hardware.org/index.php?id=usb:27c6-533c"]https://linux-hardware.org/index.php?id=usb:27c6-533c

[/URL]Says that it failed with this system and 20.04. I was wondering if this has gone any further

---


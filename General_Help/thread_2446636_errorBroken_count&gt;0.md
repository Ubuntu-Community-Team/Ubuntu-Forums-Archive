---
title: "error:Broken count&gt;0"
date: 2020-07-04
forum: General Help
---

### Post by sangam931 on 2020-07-04
sudo apt-get install -f
[sudo] password for sangam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  linux-modules-extra-5.4.0-40-generic
The following NEW packages will be installed:
  linux-modules-extra-5.4.0-40-generic
0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
7 not fully installed or removed.
Need to get 0 B/38.5 MB of archives.
After this operation, 190 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 195360 files and directories currently installed.)
Preparing to unpack .../linux-modules-extra-5.4.0-40-generic_5.4.0-40.44_amd64.deb ...
Unpacking linux-modules-extra-5.4.0-40-generic (5.4.0-40.44) ...
dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data is corrupt
dpkg-deb: error: <decompress> subprocess returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/linux-modules-extra-5.4.0-40-generic_5.4.0-40.44_amd64.deb (--unpack):
 cannot copy extracted data for './lib/modules/5.4.0-40-generic/kernel/fs/nilfs2/nilfs2.ko' to '/lib/modules/5.4.0-40-generic/kernel/fs/nilfs2/nilfs2.ko.dpkg-new': unexpected end of file or stream
Errors were encountered while processing:
 /var/cache/apt/archives/linux-modules-extra-5.4.0-40-generic_5.4.0-40.44_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Irihapeti on 2020-07-04
*Thread moved to **General Help**.*

---

### Post by dino99 on 2020-07-04
Have you first formated the device before starting the installation ?

---

### Post by Impavidus on 2020-07-05
The package file got corrupted. Delete it from cache and try again:```
sudo rm /var/cache/apt/archives/linux-modules-extra-5.4.0-40-generic_5.4.0-40.44_amd64.deb
sudo apt install -f
```

---


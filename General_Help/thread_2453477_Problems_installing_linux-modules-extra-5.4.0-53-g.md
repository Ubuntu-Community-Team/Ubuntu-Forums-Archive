---
title: "Problems installing linux-modules-extra-5.4.0-53-generic"
date: 2020-11-11
forum: General Help
---

### Post by accessd on 2020-11-11
UPDATE: It appears as though it was a corrupted download. I was able to fix it with the following:

```
sudo apt-get clean
sudo apt-get install -f
sudo apt-get upgrade
```

I encountered problems doing an apt-get upgrade this morning on Ubuntu 20.04. It returned the following error:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic : Depends: linux-modules-extra-5.4.0-53-generic but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

apt --fix-broken install returned the following:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  linux-modules-extra-5.4.0-53-generic
The following NEW packages will be installed:
  linux-modules-extra-5.4.0-53-generic
0 upgraded, 1 newly installed, 0 to remove and 16 not upgraded.
7 not fully installed or removed.
Need to get 0 B/38.6 MB of archives.
After this operation, 190 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
(Reading database ... 289890 files and directories currently installed.)
Preparing to unpack .../linux-modules-extra-5.4.0-53-generic_5.4.0-53.59_amd64.d
eb ...
Unpacking linux-modules-extra-5.4.0-53-generic (5.4.0-53.59) ...
dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data
 is corrupt
dpkg-deb: error: <decompress> subprocess returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/linux-modules-extra-5.4.0
-53-generic_5.4.0-53.59_amd64.deb (--unpack):
 cannot copy extracted data for './lib/modules/5.4.0-53-generic/kernel/drivers/g
pu/drm/radeon/radeon.ko' to '/lib/modules/5.4.0-53-generic/kernel/drivers/gpu/dr
m/radeon/radeon.ko.dpkg-new': unexpected end of file or stream
Errors were encountered while processing:
 /var/cache/apt/archives/linux-modules-extra-5.4.0-53-generic_5.4.0-53.59_amd64.
deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Does anyone have any idea what's going on?

---


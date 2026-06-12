---
title: "dpkg error and dependency problem Ubuntu 17.10 64bit"
date: 2017-11-24
forum: General Help
---

### Post by grizzlyaka on 2017-11-24
Could use a little help figuring this out please..

after running apt-get install -f this is what I get...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gir1.2-gmenu-3.0 libnih-dbus1 linux-image-4.10.0-38-generic linux-image-4.4.0-98-generic
  linux-image-extra-4.10.0-38-generic linux-image-extra-4.4.0-98-generic
  linux-signed-image-4.10.0-38-generic linux-signed-image-4.4.0-98-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-headers-4.13.0-17 linux-image-extra-4.13.0-17-generic
The following NEW packages will be installed:
  linux-image-extra-4.13.0-17-generic
The following packages will be upgraded:
  linux-headers-4.13.0-17
1 upgraded, 1 newly installed, 0 to remove and 45 not upgraded.
7 not fully installed or removed.
Need to get 0 B/42.4 MB of archives.
After this operation, 239 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 209704 files and directories currently installed.)
Preparing to unpack .../linux-image-extra-4.13.0-17-generic_4.13.0-17.20_amd64.deb ...
Unpacking linux-image-extra-4.13.0-17-generic (4.13.0-17.20) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-extra-4.13.0-17-generic_4.13.0-17.20_amd64.deb (--unpack):
 unable to open '/lib/modules/4.13.0-17-generic/kernel/drivers/net/ethernet/cavium/liquidio/liquidio.ko.dpkg-new': Operation not permitted
Preparing to unpack .../linux-headers-4.13.0-17_4.13.0-17.20_all.deb ...
Unpacking linux-headers-4.13.0-17 (4.13.0-17.20) over (4.13.0-17.20) ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-extra-4.13.0-17-generic_4.13.0-17.20_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I ran apt-get autoremove... and I got the following

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic : Depends: linux-image-extra-4.13.0-17-generic but it is not installed
 linux-signed-image-generic : Depends: linux-image-extra-4.13.0-17-generic but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

Then I tried apt-get --fix-broken install.... and I got the following

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gir1.2-gmenu-3.0 libnih-dbus1 linux-image-4.10.0-38-generic linux-image-4.4.0-98-generic
  linux-image-extra-4.10.0-38-generic linux-image-extra-4.4.0-98-generic
  linux-signed-image-4.10.0-38-generic linux-signed-image-4.4.0-98-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-image-extra-4.13.0-17-generic
The following NEW packages will be installed:
  linux-image-extra-4.13.0-17-generic
0 upgraded, 1 newly installed, 0 to remove and 45 not upgraded.
7 not fully installed or removed.
Need to get 0 B/31.5 MB of archives.
After this operation, 163 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 227563 files and directories currently installed.)
Preparing to unpack .../linux-image-extra-4.13.0-17-generic_4.13.0-17.20_amd64.deb ...
Unpacking linux-image-extra-4.13.0-17-generic (4.13.0-17.20) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-extra-4.13.0-17-generic_4.13.0-17.20_amd64.deb (--unpack):
 unable to open '/lib/modules/4.13.0-17-generic/kernel/drivers/media/v4l2-core/videobuf-dvb.ko.dpkg-new': Operation not permitted
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-extra-4.13.0-17-generic_4.13.0-17.20_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by mc4man on 2017-11-24
Are you doing something 'out of the ordinary' for internet access? (like a proxy..

---

### Post by ian-weisser on 2017-11-24
Please show us the complete output of:
```
ls -l /lib/modules/4.13.0-17-generic/kernel/drivers/media/v4l2-core/
```
Please use [code] tags to contain the output and preserve the formatting.

---

### Post by Warren_Prince on 2017-11-26
> **ian-weisser said:**
> Please show us the complete output of:
```
ls -l /lib/modules/4.13.0-17-generic/kernel/drivers/media/v4l2-core/
```


I am having a similar problem.  Following your request, while I have a /lib/modules/4.13.0-17-generic/kernel/drivers directory with 39 subdirectories, I do not have a media subdirectory.

---

### Post by ian-weisser on 2017-11-26
> **Warren_Prince said:**
> I am having a similar problem.  Following your request, while I have a /lib/modules/4.13.0-17-generic/kernel/drivers directory with 39 subdirectories, I do not have a media subdirectory.

The media directory, and much within that directory, are provided by the "linux-image-extra-4.13.0-17-generic" package.
Install it.

Here's how you can determine which package you need:
```
$ dpkg -S /lib/modules/4.13.0-17-generic/kernel/drivers/media/         <--- Directory or file
**linux-image-extra-4.13.0-17-generic**: /lib/modules/4.13.0-17-generic/kernel/drivers/media   <--- Package providing the file

```

---


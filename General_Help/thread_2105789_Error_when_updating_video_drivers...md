---
title: "Error when updating video drivers.."
date: 2013-01-17
forum: General Help
---

### Post by sir.sargento on 2013-01-17
Hello all. When I try to install "ATI/AMD proprietary FGLRX graphics driver (post-release updates)" from the "Additional Drivers" menu I get an error telling me to check '/var/log/jockey.log'.. The error output from the log is:

```

2013-01-17 00:40:41,478 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.810081
2013-01-17 00:40:41,979 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.596765
2013-01-17 00:40:42,480 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.421980
2013-01-17 00:40:42,981 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.109125
2013-01-17 00:40:43,482 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.558659
2013-01-17 00:40:43,983 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.326077
2013-01-17 00:40:44,484 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.074229
2013-01-17 00:40:44,985 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.880179
2013-01-17 00:40:45,486 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.458151
2013-01-17 00:40:45,987 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.048967
2013-01-17 00:40:46,488 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.684736
2013-01-17 00:40:46,989 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.416834
2013-01-17 00:40:47,490 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.148932
2013-01-17 00:40:47,991 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.871397
2013-01-17 00:40:48,492 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.574596
2013-01-17 00:40:48,993 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.335593
2013-01-17 00:40:49,494 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.157597
2013-01-17 00:40:49,995 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.969969
2013-01-17 00:40:50,496 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.676379
2013-01-17 00:40:50,997 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.331414
2013-01-17 00:40:51,499 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.060301
2013-01-17 00:40:52,000 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.712125
2013-01-17 00:40:52,501 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.402480
2013-01-17 00:40:53,002 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.121734
2013-01-17 00:40:53,503 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.824933
2013-01-17 00:40:54,004 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.772165
2013-01-17 00:40:54,086 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.957549
2013-01-17 00:40:54,086 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.957549
2013-01-17 00:40:54,087 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.957549
2013-01-17 00:40:54,588 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.017331
2013-01-17 00:40:55,089 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.999883
2013-01-17 00:40:55,590 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.011334
2013-01-17 00:40:56,091 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.144801
2013-01-17 00:40:56,592 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.220471
2013-01-17 00:40:57,093 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.305774
2013-01-17 00:40:57,594 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.538781
2013-01-17 00:40:58,095 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.999766
2013-01-17 00:40:58,596 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.502493
2013-01-17 00:40:59,097 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.992376
2013-01-17 00:40:59,453 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 100.000000
2013-01-17 00:41:00,083 DEBUG: install progress dpkg-exec 0.000000
2013-01-17 00:41:05,385 DEBUG: install progress fglrx-amdcccle 0.000000
2013-01-17 00:41:05,385 DEBUG: install progress fglrx-amdcccle 6.250000
2013-01-17 00:41:05,461 DEBUG: install progress fglrx-amdcccle 12.500000
2013-01-17 00:41:05,697 DEBUG: install progress fglrx-amdcccle 18.750000
2013-01-17 00:41:06,089 DEBUG: install progress fglrx 18.750000
2013-01-17 00:41:06,091 DEBUG: install progress fglrx 25.000000
2013-01-17 00:41:38,138 DEBUG: install progress fglrx 31.250000
2013-01-17 00:41:38,924 DEBUG: install progress fglrx 37.500000
2013-01-17 00:41:39,059 DEBUG: install progress bamfdaemon 37.500000
2013-01-17 00:41:39,394 DEBUG: install progress ureadahead 37.500000
2013-01-17 00:41:39,562 DEBUG: install progress initramfs-tools 37.500000
2013-01-17 00:41:53,171 DEBUG: install progress libc-bin 37.500000
2013-01-17 00:41:53,552 DEBUG: install progress dpkg-exec 37.500000
2013-01-17 00:41:54,572 DEBUG: install progress fglrx-updates 37.500000
2013-01-17 00:41:54,572 DEBUG: install progress fglrx-updates 43.750000
2013-01-17 00:41:58,350 DEBUG: install progress fglrx-updates 50.000000
2013-01-17 00:41:58,426 DEBUG: install progress fglrx-updates 56.250000
2013-01-17 00:41:58,678 DEBUG: install progress fglrx-amdcccle-updates 56.250000
2013-01-17 00:41:58,680 DEBUG: install progress fglrx-amdcccle-updates 62.500000
2013-01-17 00:41:59,336 DEBUG: install progress fglrx-amdcccle-updates 68.750000
2013-01-17 00:41:59,409 DEBUG: install progress fglrx-amdcccle-updates 75.000000
2013-01-17 00:41:59,500 DEBUG: install progress ureadahead 75.000000
2013-01-17 00:41:59,832 DEBUG: install progress dpkg-exec 75.000000
2013-01-17 00:41:59,913 DEBUG: install progress fglrx-updates 75.000000
2013-01-17 00:42:00,268 DEBUG: install progress fglrx-updates 81.250000
2013-01-17 00:42:21,025 DEBUG: install progress fglrx-updates 87.500000
2013-01-17 00:42:21,378 DEBUG: install progress bamfdaemon 87.500000
2013-01-17 00:42:21,572 DEBUG: install progress fglrx-amdcccle-updates 87.500000
2013-01-17 00:42:21,656 DEBUG: install progress fglrx-amdcccle-updates 93.750000
2013-01-17 00:42:21,715 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2013-01-17 00:42:21,775 DEBUG: install progress initramfs-tools 100.000000
2013-01-17 00:42:31,707 DEBUG: install progress libc-bin 100.000000
2013-01-17 00:42:33,211 DEBUG: (Reading database ... 449054 files and directories currently installed.)
Removing fglrx-amdcccle ...
Removing fglrx ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/i386-linux-gnu/xorg/extra-modules with a link.
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: not replacing /usr/lib/i386-linux-gnu/xorg/extra-modules with a link.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for ureadahead ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-35-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package fglrx-updates.
(Reading database ... 448814 files and directories currently installed.)
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.960-0ubuntu1.1_i386.deb) ...
Selecting previously unselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.960-0ubuntu1.1_i386.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx-updates (2:8.960-0ubuntu1.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group i386-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.960 DKMS files...
Building only for 3.2.0-35-generic-pae
Building for architecture i686
Building initial module for 3.2.0-35-generic-pae
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-35-generic-pae/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle-updates (2:8.960-0ubuntu1.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-35-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2013-01-17 00:42:33,649 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2013-01-17 00:42:54,483 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-01-17 00:42:54,483 DEBUG: fglrx_updates is not the alternative in use
2013-01-17 00:42:54,500 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-01-17 00:42:54,501 DEBUG: fglrx_updates is not the alternative in use
2013-01-17 00:43:02,576 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-01-17 00:43:02,576 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-01-17 00:43:02,854 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-01-17 00:43:02,854 DEBUG: fglrx_updates is not the alternative in use
2013-01-17 00:43:02,871 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-01-17 00:43:02,872 DEBUG: fglrx_updates is not the alternative in use
2013-01-17 00:43:02,910 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-01-17 00:43:02,910 DEBUG: fglrx_updates is not the alternative in use
2013-01-17 00:43:02,935 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-01-17 00:43:02,936 DEBUG: fglrx_updates is not the alternative in use
2013-01-17 00:43:02,982 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-01-17 00:43:02,982 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-01-17 00:43:03,247 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-01-17 00:43:03,247 DEBUG: fglrx_updates is not the alternative in use
2013-01-17 00:43:03,265 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-01-17 00:43:03,265 DEBUG: fglrx_updates is not the alternative in use
2013-01-17 00:43:03,982 DEBUG: Shutting down

```

Those are like the last 150 lines or so.. Let me know if you need the earlier part of the log. Any help would be appreciated. Thanks

---

### Post by sir.sargento on 2013-01-17
Anyone?

---

### Post by Laiquendi on 2013-01-17
Which version/model of ati card do you have?

I have similiar problems all the time with my older model since the officially stopped supporting any older models than 7xxx or so, so I just resigned from using this driver on ati, and ati altogether ever again.

---

### Post by QIII on 2013-01-17
HD 4xxx and prior cards have been moved to a legacy driver path and that driver does not work with X Server 1.13.  Those cards work perfectly fine with X Server 1.12, which is what Precise uses, and the legacy driver.   HD 5xxx cards and later are fine for X Server 1.13 and beyond with the newer ATI drivers..

For the OP:

The "updates" version is often problematic.  I would advise against its use and suggest the normal version.  Uninstall the "updates" version before installing the normal version.

It should also be noted that the graphical "Additional Drivers" method will fail on occasion.  If that is the case, then use the terminal

Make sure there are not bits and pieces lying around:
```
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates
```Reinstall the driver
```
sudo apt-get install fglrx fglrx-amdcccle
```And, although some say this is unnecessary, initialize:
```
sudo amdconfig --initial
```Notice the use of amdconfig rather than aticonfig.  AMD has deprecated aticonfig.  I believe that should be the case in Catalyst 12.4 (which is what is in the Precise repo).  If amdconfig does not work, use aticonfig.

---

### Post by sir.sargento on 2013-01-17
I am using a older card for sure. It is a Radeon HD 3450.. I am using the drivers that aren't post release now.. Although I am still having trouble getting trine, shadowgrounds, and tfc via steam on linux to even open. Never had any of these issues on previous installs of Ubuntu. I'll download the packages you recommended.. Although on the computer I am buying soon I will be steering clear of ATI/AMD and going the way of Nvidia.

Thanks

---


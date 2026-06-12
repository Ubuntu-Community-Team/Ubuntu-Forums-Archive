---
title: "can I use a MacOS printer driver in Ubuntu?"
date: 2020-12-03
forum: General Help
---

### Post by salamilimos on 2020-12-03
My printer is a Canon PIXMA iP2770 and the [official Linux driver]("https://asia.canon/en/support/0100272002/1?model=4103B") from Canon is only available for 32-bit Linux. They also have a [driver for MacOS]("https://asia.canon/en/support/0100564002/11?model=4103B") available.

I've downloaded the MacOS driver and extracted the dmg file. I've found the PPD file on there: [https://paste.ubuntu.com/p/tkJWnS6hCQ/](https://paste.ubuntu.com/p/tkJWnS6hCQ/)

I've noticed these paths:

```
*cupsFilter: "application/vnd.cups-raster 0 /Library/Printers/Canon/BJPrinter/Filters/Raster2CanonIJ/Raster2CanonIJ.bundle/Contents/MacOS/Raster2CanonIJ"
*cupsFilter: "application/vnd.cups-command 0 /Library/Printers/Canon/BJPrinter/Filters/Command2CanonIJ.bundle/Contents/MacOS/Command2CanonIJ"
*APDialogExtension: "/Library/Printers/Canon/BJPrinter/PDEs/CanonIJPDE.bundle"
*APPrinterIconPath: "/Library/Printers/Canon/BJPrinter/Resources/CIJIcons/CIJiP2700series.icns"
*APPrinterUtilityPath: "/Library/Printers/Canon/BJPrinter/Utilities/CanonIJPrinterUtility.app"
*APAutoSetupTool: "/Library/Printers/Canon/BJPrinter/Utilities/CIJAutoSetupTool.app/Contents/MacOS/CIJAutoSetupTool"
*cupsICCProfile RGB16.1./CanonIJPrinter2005.icc: "/Library/Printers/Canon/BJPrinter/Resources/ICCProfiles/CanonIJPrinter2005.icc"
*cupsICCProfile RGB16.2./Canon iP2700 series MP2.icc: "/Library/Printers/Canon/BJPrinter/Resources/ICCProfiles/iP2700series.canonicc/Contents/Resources/Canon iP2700 series MP2.icc"
*cupsICCProfile RGB16.3./Canon iP2700 series GL2 SG2.icc: "/Library/Printers/Canon/BJPrinter/Resources/ICCProfiles/iP2700series.canonicc/Contents/Resources/Canon iP2700 series GL2 SG2.icc"
*cupsICCProfile RGB16.4./Canon iP2700 series PT2.icc: "/Library/Printers/Canon/BJPrinter/Resources/ICCProfiles/iP2700series.canonicc/Contents/Resources/Canon iP2700 series PT2.icc"
*cupsICCProfile RGB16.5./Canon iP2700 series PR1.icc: "/Library/Printers/Canon/BJPrinter/Resources/ICCProfiles/iP2700series.canonicc/Contents/Resources/Canon iP2700 series PR1.icc"
*cupsICCProfile RGB16.6./Canon iP2700 series PR2.icc: "/Library/Printers/Canon/BJPrinter/Resources/ICCProfiles/iP2700series.canonicc/Contents/Resources/Canon iP2700 series PR2.icc"
```

Can I convert these paths to this?

```
*cupsFilter: "application/vnd.cups-raster 0 /home/salamilimos/Library/Printers/Canon/BJPrinter/Filters/Raster2CanonIJ/Raster2CanonIJ.bundle/Contents/MacOS/Raster2CanonIJ"
*cupsFilter: "application/vnd.cups-command 0 /home/salamilimos/Library/Printers/Canon/BJPrinter/Filters/Command2CanonIJ.bundle/Contents/MacOS/Command2CanonIJ"
*APDialogExtension: "/home/salamilimos/Library/Printers/Canon/BJPrinter/PDEs/CanonIJPDE.bundle"
*APPrinterIconPath: "/home/salamilimos/Library/Printers/Canon/BJPrinter/Resources/CIJIcons/CIJiP2700series.icns"
*APPrinterUtilityPath: "/home/salamilimos/Library/Printers/Canon/BJPrinter/Utilities/CanonIJPrinterUtility.app"
*APAutoSetupTool: "/home/salamilimos/Library/Printers/Canon/BJPrinter/Utilities/CIJAutoSetupTool.app/Contents/MacOS/CIJAutoSetupTool"
*cupsICCProfile RGB16.1./CanonIJPrinter2005.icc: "/home/salamilimos/Library/Printers/Canon/BJPrinter/Resources/ICCProfiles/CanonIJPrinter2005.icc"
*cupsICCProfile RGB16.2./Canon iP2700 series MP2.icc: "/home/salamilimos/Library/Printers/Canon/BJPrinter/Resources/ICCProfiles/iP2700series.canonicc/Contents/Resources/Canon iP2700 series MP2.icc"
*cupsICCProfile RGB16.3./Canon iP2700 series GL2 SG2.icc: "/home/salamilimos/Library/Printers/Canon/BJPrinter/Resources/ICCProfiles/iP2700series.canonicc/Contents/Resources/Canon iP2700 series GL2 SG2.icc"
*cupsICCProfile RGB16.4./Canon iP2700 series PT2.icc: "/home/salamilimos/Library/Printers/Canon/BJPrinter/Resources/ICCProfiles/iP2700series.canonicc/Contents/Resources/Canon iP2700 series PT2.icc"
*cupsICCProfile RGB16.5./Canon iP2700 series PR1.icc: "/home/salamilimos/Library/Printers/Canon/BJPrinter/Resources/ICCProfiles/iP2700series.canonicc/Contents/Resources/Canon iP2700 series PR1.icc"
*cupsICCProfile RGB16.6./Canon iP2700 series PR2.icc: "/home/salamilimos/Library/Printers/Canon/BJPrinter/Resources/ICCProfiles/iP2700series.canonicc/Contents/Resources/Canon iP2700 series PR2.icc"
```

Will this work?

---

### Post by kurt18947 on 2020-12-04
I assume you've tried just connecting the printer and see if it's recognized? I've seen some reports with Canon printers and multifunctions that simply connecting them and turning them on was all that was required. There is a movement toward "driverless printing" though I don't know the status. I have a Brother MFD and the drivers for it are 32 bit as well. The Brother installer script downloads required software to enable 32 bit drivers to work on 64 bit OSs. I don't know if Canon install scripts do the same thing or not. I'll be interested to see how you get on, my Brother inkjet multifunction machine is 12+ years old so I may be in the printer market in the not-so-distant future.

---

### Post by salamilimos on 2020-12-04
I've tried to install the printer through the PPD file and this is the result:

```
Idle - "File "/home/salamilimos/Library/Printers/Canon/BJPrinter/Filters/Command2CanonIJ.bundle/Contents/MacOS/Command2CanonIJ" has insecure permissions (0100664/uid=1000/gid=1000)."
```

> I assume you've tried just connecting the printer and see if it's recognized?

Yes, it does connect and there's a driver available in CUPS, it's called Canon iP2700 series - CUPS+Gutenprint v5.3.3, however, this driver doesn't have draft mode though. I bought this printer back in 2016, and because of the lack of draft mode from the CUPS driver, I ended up wasting lots of ink. I followed this tutorial to install the official Canon drivers: [https://ubuntuforums.org/showthread.php?t=2395967](https://ubuntuforums.org/showthread.php?t=2395967).

From 16.04 to 18.04, my printer worked with the Canon drivers thanks to the tutorial, I was able to enable draft mode printing, but in 20.04, the driver became uninstallable due to dependency issues.

---

### Post by TheFu on 2020-12-04
> **salamilimos said:**
> I've tried to install the printer through the PPD file and this is the result:

```
Idle - "File "/home/salamilimos/Library/Printers/Canon/BJPrinter/Filters/Command2CanonIJ.bundle/Contents/MacOS/Command2CanonIJ" has insecure permissions (0100664/uid=1000/gid=1000)."
```



Yes, it does connect and there's a driver available in CUPS, it's called Canon iP2700 series - CUPS+Gutenprint v5.3.3, however, this driver doesn't have draft mode though. I bought this printer back in 2016, and because of the lack of draft mode from the CUPS driver, I ended up wasting lots of ink. I followed this tutorial to install the official Canon drivers: [https://ubuntuforums.org/showthread.php?t=2395967](https://ubuntuforums.org/showthread.php?t=2395967).

From 16.04 to 18.04, my printer worked with the Canon drivers thanks to the tutorial, I was able to enable draft mode printing, but in 20.04, the driver became uninstallable due to dependency issues.

You could spin up an 18.04 container, pass through the USB port from the printer, and install the 18.04 drivers, the use that IP as a print server for all your systems to access the printer. Containers are really light.  That would be supported for a few more years.  If you locked down the IPP port to just your LAN and only started the container when you needed to print, you could have an indefinite solution for printing to this printer.

I don't know much about printer drivers. If they are binary and compiled for the specific OS, then the Mac driver will not work. OSX is BSD and not the same binary format as Linux on x86.

Next time you need a printer, if you always get one that supports postscript, then you won't need any driver. Just something to consider. Any postscript printer I've heard of can take a PS stream thrown at them and print it. Even better if it supports the IPP protocol, but that really isn't too important. I have a couple of printers with drivers that are provided with the distro and have been at least a decade.  Last desktop I setup, the printer-system-config (or some permutation of that) found the printers automatically on the network. I just needed to pick the vendor and model - might have taken 20 seconds before I was printing.

---

### Post by salamilimos on 2020-12-04
> You could spin up an 18.04 container, pass through the USB port from the  printer, and install the 18.04 drivers, the use that IP as a print  server for all your systems to access the printer. Containers are really  light.  That would be supported for a few more years.  If you locked  down the IPP port to just your LAN and only started the container when  you needed to print, you could have an indefinite solution for printing  to this printer.

What's a container? Is it the same as a Virtualbox VM? If not, how do I set it up?

---

### Post by TheFu on 2020-12-04
> **salamilimos said:**
> What's a container? Is it the same as a Virtualbox VM? If not, how do I set it up?

Not the same as a VM.  100x lighter.
"How" is a huge question.  [https://ubuntu.com/server/docs/containers-lxd](https://ubuntu.com/server/docs/containers-lxd)

---

### Post by DuckHook on 2020-12-04
> **salamilimos said:**
> What's a container? Is it the same as a Virtualbox VM? If not, how do I set it up?
A VM is probably the easiest way for someone unfamiliar with the more esoteric ways of containers.

There are other methods: Docker is one.

If you are game for delving into Ubuntu's native container solution, click the link in my sig: *Sandboxing Apps with LXD*

Just a word of caution that this is not for newbies. In fact, it is quite involved. You will also have to research some changes since your objective is not sandboxing but mapping a USB port.

---

### Post by CatKiller on 2020-12-04
> **salamilimos said:**
> My printer is a Canon PIXMA iP2770 and the [official Linux driver]("https://asia.canon/en/support/0100272002/1?model=4103B") from Canon is only available for 32-bit Linux.
> **salamilimos said:**
> From 16.04 to 18.04, my printer worked with the Canon drivers thanks to the tutorial, I was able to enable draft mode printing, but in 20.04, the driver became uninstallable due to dependency issues.
While Ubuntu decided not to support 32-bit versions of *everything*, they did commit to supporting 32-bit versions of some things. The tardy and inadequate 64-bit support from some printer manufacturers was something that they were specifically concerned about.

If your printer manufacturer needs even more libraries than everyone else, you can [request that Ubuntu adds those 32-bit libraries back in](https://discourse.ubuntu.com/t/community-process-for-32-bit-compatibility/12598). You can also contact your printer manufacturer and try to get them to pull their finger out.

---

### Post by salamilimos on 2020-12-05
> While Ubuntu decided not to support 32-bit versions of *everything*,  they did commit to supporting 32-bit versions of some things. The tardy  and inadequate 64-bit support from some printer manufacturers was  something that they were specifically concerned about.

If your printer manufacturer needs even more libraries than everyone else, you can [request that Ubuntu adds those 32-bit libraries back in]("https://discourse.ubuntu.com/t/community-process-for-32-bit-compatibility/12598"). You can also contact your printer manufacturer and try to get them to pull their finger out.

Thank you, I'll try to request that.

These are my attempts to install the dependencies of the official Canon drivers:

Enabled 32-bit support:
```
sudo dpkg --add-architecture i386
sudo apt-get update
```

I downloaded the following dependencies:
> _multiarch-support_2.27-3ubuntu1.2_amd64.deb_ - [http://security.ubuntu.com/ubuntu/pool/main/g/glibc/multiarch-support_2.27-3ubuntu1.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/g/glibc/multiarch-support_2.27-3ubuntu1.2_amd64.deb)

_multiarch-support_2.27-3ubuntu1.2_i386.deb_ - [http://security.ubuntu.com/ubuntu/pool/main/g/glibc/multiarch-support_2.27-3ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/glibc/multiarch-support_2.27-3ubuntu1.2_i386.deb)
[U]
libtiff4_3.9.7-2ubuntu1_i386.deb[/U] - [http://old-releases.ubuntu.com/ubuntu/pool/universe/t/tiff3/libtiff4_3.9.7-2ubuntu1_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/universe/t/tiff3/libtiff4_3.9.7-2ubuntu1_i386.deb)
[U]
libpng12-0_1.2.54-1ubuntu1.1_i386.deb[/U] - [https://packages.ubuntu.com/xenial/i386/libpng12-0/download](https://packages.ubuntu.com/xenial/i386/libpng12-0/download)

Tried to install libtiff4:
```
sudo gdebi libtiff4_3.9.7-2ubuntu1_i386.deb
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading state information... Done
This package is uninstallable
Dependency is not satisfiable: multiarch-support

sudo gdebi multiarch-support_2.27-3ubuntu1.2_amd64.deb
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading state information... Done

Transitional package to ensure multiarch compatibility
 This is a transitional package used to ensure multiarch support is present
 in ld.so before unpacking libraries to the multiarch directories.  It can
 be removed once nothing on the system depends on it.
Do you want to install the software package? [y/N]:y
/usr/bin/gdebi:113: FutureWarning: Possible nested set at position 1
  c = findall("[[(](\S+)/\S+[])]", msg)[0].lower()
Selecting previously unselected package multiarch-support.
(Reading database ... 229736 files and directories currently installed.)
Preparing to unpack multiarch-support_2.27-3ubuntu1.2_amd64.deb ...
Unpacking multiarch-support (2.27-3ubuntu1.2) ...
Setting up multiarch-support (2.27-3ubuntu1.2) ...

sudo gdebi libtiff4_3.9.7-2ubuntu1_i386.deb
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading state information... Done
This package is uninstallable
Dependency is not satisfiable: multiarch-support

sudo gdebi multiarch-support_2.27-3ubuntu1.2_i386.deb
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading state information... Done
Requires the installation of the following packages: gcc-10-base gcc-10-base:i386 libc6 libc6:i386 libcrypt1:i386 libgcc-s1 libgcc-s1:i386 libgomp1 libidn2-0:i386 libobjc4 libstdc++6 libunistring2:i386 

Transitional package to ensure multiarch compatibility
 This is a transitional package used to ensure multiarch support is present
 in ld.so before unpacking libraries to the multiarch directories.  It can
 be removed once nothing on the system depends on it.
Do you want to install the software package? [y/N]:y
/usr/bin/gdebi:113: FutureWarning: Possible nested set at position 1
  c = findall("[[(](\S+)/\S+[])]", msg)[0].lower()
Get:1 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 libc6 amd64 2.31-0ubuntu9.1 [2712 kB]
Get:2 http://security.ubuntu.com/ubuntu focal-security/universe amd64 libobjc4 amd64 10.2.0-5ubuntu1~20.04 [42.8 kB]
Get:3 http://archive.ubuntu.com/ubuntu focal/main i386 libcrypt1 i386 1:4.4.10-10ubuntu4 [90.9 kB]
Get:4 http://archive.ubuntu.com/ubuntu focal-updates/main i386 libc6 i386 2.31-0ubuntu9.1 [2571 kB]
Get:5 http://security.ubuntu.com/ubuntu focal-security/main amd64 gcc-10-base amd64 10.2.0-5ubuntu1~20.04 [19.7 kB]
Get:6 http://security.ubuntu.com/ubuntu focal-security/main amd64 libstdc++6 amd64 10.2.0-5ubuntu1~20.04 [503 kB]
Get:7 http://archive.ubuntu.com/ubuntu focal/main i386 libunistring2 i386 0.9.10-2 [377 kB]
Get:8 http://archive.ubuntu.com/ubuntu focal/main i386 libidn2-0 i386 2.2.0-2 [51.4 kB]
Get:9 http://security.ubuntu.com/ubuntu focal-security/main amd64 libgomp1 amd64 10.2.0-5ubuntu1~20.04 [102 kB]
Get:10 http://security.ubuntu.com/ubuntu focal-security/main amd64 libgcc-s1 amd64 10.2.0-5ubuntu1~20.04 [41.6 kB]
Get:11 http://security.ubuntu.com/ubuntu focal-security/main i386 gcc-10-base i386 10.2.0-5ubuntu1~20.04 [19.7 kB]
Get:12 http://security.ubuntu.com/ubuntu focal-security/main i386 libgcc-s1 i386 10.2.0-5ubuntu1~20.04 [49.8 kB]
Fetched 6580 kB in 6s (317 kB/s)                                            
Preconfiguring packages ...
Preconfiguring packages ...
(Reading database ... 229739 files and directories currently installed.)
Preparing to unpack .../libobjc4_10.2.0-5ubuntu1~20.04_amd64.deb ...
Unpacking libobjc4:amd64 (10.2.0-5ubuntu1~20.04) over (10-20200411-0ubuntu1) ...
Preparing to unpack .../gcc-10-base_10.2.0-5ubuntu1~20.04_amd64.deb ...
Unpacking gcc-10-base:amd64 (10.2.0-5ubuntu1~20.04) over (10-20200411-0ubuntu1) ...
Selecting previously unselected package gcc-10-base:i386.
Preparing to unpack .../gcc-10-base_10.2.0-5ubuntu1~20.04_i386.deb ...
Unpacking gcc-10-base:i386 (10.2.0-5ubuntu1~20.04) ...
Setting up gcc-10-base:amd64 (10.2.0-5ubuntu1~20.04) ...
Setting up gcc-10-base:i386 (10.2.0-5ubuntu1~20.04) ...
(Reading database ... 229740 files and directories currently installed.)
Preparing to unpack .../libstdc++6_10.2.0-5ubuntu1~20.04_amd64.deb ...
Unpacking libstdc++6:amd64 (10.2.0-5ubuntu1~20.04) over (10-20200411-0ubuntu1) ...
Setting up libstdc++6:amd64 (10.2.0-5ubuntu1~20.04) ...
(Reading database ... 229740 files and directories currently installed.)
Preparing to unpack .../libgomp1_10.2.0-5ubuntu1~20.04_amd64.deb ...
Unpacking libgomp1:amd64 (10.2.0-5ubuntu1~20.04) over (10-20200411-0ubuntu1) ...
Preparing to unpack .../libgcc-s1_10.2.0-5ubuntu1~20.04_amd64.deb ...
Unpacking libgcc-s1:amd64 (10.2.0-5ubuntu1~20.04) over (10-20200411-0ubuntu1) ...
Selecting previously unselected package libgcc-s1:i386.
Preparing to unpack .../libgcc-s1_10.2.0-5ubuntu1~20.04_i386.deb ...
Unpacking libgcc-s1:i386 (10.2.0-5ubuntu1~20.04) ...
Setting up libgcc-s1:amd64 (10.2.0-5ubuntu1~20.04) ...
(Reading database ... 229742 files and directories currently installed.)
Preparing to unpack .../libc6_2.31-0ubuntu9.1_amd64.deb ...
Unpacking libc6:amd64 (2.31-0ubuntu9.1) over (2.31-0ubuntu9) ...
Selecting previously unselected package libc6:i386.
Preparing to unpack .../libc6_2.31-0ubuntu9.1_i386.deb ...
Unpacking libc6:i386 (2.31-0ubuntu9.1) ...
Selecting previously unselected package libcrypt1:i386.
Preparing to unpack .../libcrypt1_1%3a4.4.10-10ubuntu4_i386.deb ...
Unpacking libcrypt1:i386 (1:4.4.10-10ubuntu4) ...
Setting up libc6:amd64 (2.31-0ubuntu9.1) ...
Setting up libgcc-s1:i386 (10.2.0-5ubuntu1~20.04) ...
Setting up libcrypt1:i386 (1:4.4.10-10ubuntu4) ...
Setting up libc6:i386 (2.31-0ubuntu9.1) ...
Selecting previously unselected package libunistring2:i386.
(Reading database ... 230044 files and directories currently installed.)
Preparing to unpack .../libunistring2_0.9.10-2_i386.deb ...
Unpacking libunistring2:i386 (0.9.10-2) ...
Selecting previously unselected package libidn2-0:i386.
Preparing to unpack .../libidn2-0_2.2.0-2_i386.deb ...
Unpacking libidn2-0:i386 (2.2.0-2) ...
Setting up libunistring2:i386 (0.9.10-2) ...
Setting up libobjc4:amd64 (10.2.0-5ubuntu1~20.04) ...
Setting up libidn2-0:i386 (2.2.0-2) ...
Setting up libgomp1:amd64 (10.2.0-5ubuntu1~20.04) ...
Processing triggers for libc-bin (2.31-0ubuntu9) ...
(Reading database ... 230048 files and directories currently installed.)
Preparing to unpack multiarch-support_2.27-3ubuntu1.2_i386.deb ...
Unpacking multiarch-support:i386 (2.27-3ubuntu1.2) over (2.27-3ubuntu1.2) ...
Setting up multiarch-support:i386 (2.27-3ubuntu1.2) ...

sudo gdebi libtiff4_3.9.7-2ubuntu1_i386.deb
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading state information... Done
This package is uninstallable
Dependency is not satisfiable: multiarch-support
```

Tried to install libpng12:
```
sudo gdebi libpng12-0_1.2.54-1ubuntu1.1_i386.deb
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading state information... Done
Requires the installation of the following packages: gcc-10-base gcc-10-base:i386 libc6 libc6:i386 libcrypt1:i386 libgcc-s1 libgcc-s1:i386 libgomp1 libidn2-0:i386 libobjc4 libstdc++6 libunistring2:i386 zlib1g zlib1g:i386 

PNG library - runtime
 libpng is a library implementing an interface for reading and writing
 PNG (Portable Network Graphics) format files.
 .
 This package contains the runtime library files needed to run software
 using libpng.
Do you want to install the software package? [y/N]:y
/usr/bin/gdebi:113: FutureWarning: Possible nested set at position 1
  c = findall("[[(](\S+)/\S+[])]", msg)[0].lower()
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main amd64 libc6 amd64 2.31-0ubuntu9.1 [2712 kB]
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe amd64 libobjc4 amd64 10.2.0-5ubuntu1~20.04 [42.8 kB]
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 gcc-10-base amd64 10.2.0-5ubuntu1~20.04 [19.7 kB]
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 libstdc++6 amd64 10.2.0-5ubuntu1~20.04 [503 kB]
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 libgomp1 amd64 10.2.0-5ubuntu1~20.04 [102 kB]
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 libgcc-s1 amd64 10.2.0-5ubuntu1~20.04 [41.6 kB]
Get:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main i386 gcc-10-base i386 10.2.0-5ubuntu1~20.04 [19.7 kB]
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main i386 libgcc-s1 i386 10.2.0-5ubuntu1~20.04 [49.8 kB]
Get:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main amd64 zlib1g amd64 1:1.2.11.dfsg-2ubuntu1.2 [53.6 kB]
Get:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal/main i386 libcrypt1 i386 1:4.4.10-10ubuntu4 [90.9 kB]
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main i386 libc6 i386 2.31-0ubuntu9.1 [2571 kB]
Get:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main i386 zlib1g i386 1:1.2.11.dfsg-2ubuntu1.2 [56.5 kB]
Get:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal/main i386 libunistring2 i386 0.9.10-2 [377 kB]
Get:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal/main i386 libidn2-0 i386 2.2.0-2 [51.4 kB]
Fetched 6690 kB in 6s (577 kB/s)                                            
Preconfiguring packages ...
Preconfiguring packages ...
(Reading database ... 229736 files and directories currently installed.)
Preparing to unpack .../libobjc4_10.2.0-5ubuntu1~20.04_amd64.deb ...
Unpacking libobjc4:amd64 (10.2.0-5ubuntu1~20.04) over (10-20200411-0ubuntu1) ...
Preparing to unpack .../gcc-10-base_10.2.0-5ubuntu1~20.04_amd64.deb ...
Unpacking gcc-10-base:amd64 (10.2.0-5ubuntu1~20.04) over (10-20200411-0ubuntu1) ...
Selecting previously unselected package gcc-10-base:i386.
Preparing to unpack .../gcc-10-base_10.2.0-5ubuntu1~20.04_i386.deb ...
Unpacking gcc-10-base:i386 (10.2.0-5ubuntu1~20.04) ...
Setting up gcc-10-base:amd64 (10.2.0-5ubuntu1~20.04) ...
Setting up gcc-10-base:i386 (10.2.0-5ubuntu1~20.04) ...
(Reading database ... 229737 files and directories currently installed.)
Preparing to unpack .../libstdc++6_10.2.0-5ubuntu1~20.04_amd64.deb ...
Unpacking libstdc++6:amd64 (10.2.0-5ubuntu1~20.04) over (10-20200411-0ubuntu1) ...
Setting up libstdc++6:amd64 (10.2.0-5ubuntu1~20.04) ...
(Reading database ... 229737 files and directories currently installed.)
Preparing to unpack .../libgomp1_10.2.0-5ubuntu1~20.04_amd64.deb ...
Unpacking libgomp1:amd64 (10.2.0-5ubuntu1~20.04) over (10-20200411-0ubuntu1) ...
Preparing to unpack .../libgcc-s1_10.2.0-5ubuntu1~20.04_amd64.deb ...
Unpacking libgcc-s1:amd64 (10.2.0-5ubuntu1~20.04) over (10-20200411-0ubuntu1) ...
Selecting previously unselected package libgcc-s1:i386.
Preparing to unpack .../libgcc-s1_10.2.0-5ubuntu1~20.04_i386.deb ...
Unpacking libgcc-s1:i386 (10.2.0-5ubuntu1~20.04) ...
Setting up libgcc-s1:amd64 (10.2.0-5ubuntu1~20.04) ...
(Reading database ... 229739 files and directories currently installed.)
Preparing to unpack .../libc6_2.31-0ubuntu9.1_amd64.deb ...
Unpacking libc6:amd64 (2.31-0ubuntu9.1) over (2.31-0ubuntu9) ...
Selecting previously unselected package libc6:i386.
Preparing to unpack .../libc6_2.31-0ubuntu9.1_i386.deb ...
Unpacking libc6:i386 (2.31-0ubuntu9.1) ...
Selecting previously unselected package libcrypt1:i386.
Preparing to unpack .../libcrypt1_1%3a4.4.10-10ubuntu4_i386.deb ...
Unpacking libcrypt1:i386 (1:4.4.10-10ubuntu4) ...
Setting up libc6:amd64 (2.31-0ubuntu9.1) ...
Setting up libgcc-s1:i386 (10.2.0-5ubuntu1~20.04) ...
Setting up libcrypt1:i386 (1:4.4.10-10ubuntu4) ...
Setting up libc6:i386 (2.31-0ubuntu9.1) ...
(Reading database ... 230041 files and directories currently installed.)
Preparing to unpack .../zlib1g_1%3a1.2.11.dfsg-2ubuntu1.2_amd64.deb ...
Unpacking zlib1g:amd64 (1:1.2.11.dfsg-2ubuntu1.2) over (1:1.2.11.dfsg-2ubuntu1) ...
Selecting previously unselected package zlib1g:i386.
Preparing to unpack .../zlib1g_1%3a1.2.11.dfsg-2ubuntu1.2_i386.deb ...
Unpacking zlib1g:i386 (1:1.2.11.dfsg-2ubuntu1.2) ...
Setting up zlib1g:amd64 (1:1.2.11.dfsg-2ubuntu1.2) ...
Setting up zlib1g:i386 (1:1.2.11.dfsg-2ubuntu1.2) ...
Selecting previously unselected package libunistring2:i386.
(Reading database ... 230043 files and directories currently installed.)
Preparing to unpack .../libunistring2_0.9.10-2_i386.deb ...
Unpacking libunistring2:i386 (0.9.10-2) ...
Selecting previously unselected package libidn2-0:i386.
Preparing to unpack .../libidn2-0_2.2.0-2_i386.deb ...
Unpacking libidn2-0:i386 (2.2.0-2) ...
Setting up libunistring2:i386 (0.9.10-2) ...
Setting up libobjc4:amd64 (10.2.0-5ubuntu1~20.04) ...
Setting up libidn2-0:i386 (2.2.0-2) ...
Setting up libgomp1:amd64 (10.2.0-5ubuntu1~20.04) ...
Processing triggers for libc-bin (2.31-0ubuntu9) ...
Selecting previously unselected package libpng12-0:i386.
(Reading database ... 230047 files and directories currently installed.)
Preparing to unpack libpng12-0_1.2.54-1ubuntu1.1_i386.deb ...
Unpacking libpng12-0:i386 (1.2.54-1ubuntu1.1) ...
dpkg: error processing archive libpng12-0_1.2.54-1ubuntu1.1_i386.deb (--install):
 unable to install new version of '/lib/i386-linux-gnu/libpng12.so.0': No such file or directory
Processing triggers for libc-bin (2.31-0ubuntu9) ...
Errors were encountered while processing:
 libpng12-0_1.2.54-1ubuntu1.1_i386.deb
```

This is as far as I got trying to install these dependencies and they failed. I'll be including this with my request.

---

### Post by salamilimos on 2020-12-05
> **CatKiller said:**
> If your printer manufacturer needs even more libraries than everyone else, you can [request that Ubuntu adds those 32-bit libraries back in]("https://discourse.ubuntu.com/t/community-process-for-32-bit-compatibility/12598").

I've already added my input into that discussion, I hope I'm heard: [https://discourse.ubuntu.com/t/community-process-for-32-bit-compatibility/12598/100?u=salamilimos](https://discourse.ubuntu.com/t/community-process-for-32-bit-compatibility/12598/100?u=salamilimos)

> You can also contact your printer manufacturer and try to get them to pull their finger out.

I doubt that will make a difference, since Linux market share is low, they have no incentive to do so.

---


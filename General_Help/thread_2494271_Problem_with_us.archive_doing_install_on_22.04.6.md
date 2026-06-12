---
title: "Problem with us.archive doing install on 22.04.6"
date: 2024-01-10
forum: General Help
---

### Post by deerehunter on 2024-01-10
Hi,
New to using Ubuntu Server.  Trying to install net-tools. I get this error :

[http://us.archives.ubuntu.com/ubuntu/pool/main/n/net-tools_1.60%2bgit20181103.Oeebece-1ubuntu5_amd64.deb](http://us.archives.ubuntu.com/ubuntu/pool/main/n/net-tools_1.60%2bgit20181103.Oeebece-1ubuntu5_amd64.deb)

Is this a current archive ?  My windows machine can't hit it either.
I have been having problems with any installations of any kind since trying to install gnome and failing.  Had to install a HDMI controller to get the system back since I was using VGA monitor and it would no longer work.  Dumb Me. Haa Haa!

Trying to set up server for house and man cave computers to access common documents and download directories instead of duplicates in each and varying version. Running general farm business, household stuff and Amateur Radio digital mode on Ubuntu desktop 22.04, windows 7 (Yeeek), Raspberry Pi 400 Ubuntu 22.04. Tired of all computers having duplicate documents and downloads.
I think I need a real basic book that gets me to a basic windows / Ubuntu file and print server.

Any help would be terrific.

Thanks
Stan W8SRD

---

### Post by MAFoElffen on 2024-01-10
I can tell you that was not any kind of error message... That is a link to a .deb file... Ad the highest point release for 22.04 is 24.04.3...

'net-tools' right?
```

mafoelffen@Mikes-ThinkPad-T520:~$ apt-cache show net-tools
Package: net-tools
Architecture: amd64
Version: 1.60+git20181103.0eebece-1ubuntu5
Multi-Arch: foreign
Priority: optional
Section: net
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: net-tools Team <team+net-tools@tracker.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 800
Depends: libc6 (>= 2.34), libselinux1 (>= 3.1~)
Filename: pool/main/n/net-tools/net-tools_1.60+git20181103.0eebece-1ubuntu5_amd64.deb
Size: 204308
MD5sum: 4def95f207c168728f36d3ada2f8d32f
SHA1: 77d99e2fcef0cd65299ffdaba37d7c0b9c4973e2
SHA256: 93f0f3af968b1e7e256178ef27ee7e3316df22ee711fc8f4d603d361e3944a23
SHA512: 4e40591323e2a90fc2098b45c890c366389455efda95d66f4cc934bf4772a6709f184e19a80b405cc4f559f99de84703f1faf16ac5063a9d2a67790df39f4355
Homepage: http://sourceforge.net/projects/net-tools/
Description-en: NET-3 networking toolkit
 This package includes the important tools for controlling the network
 subsystem of the Linux kernel.  This includes arp, ifconfig, netstat,
 rarp, nameif and route.  Additionally, this package contains utilities
 relating to particular network hardware types (plipconfig, slattach,
 mii-tool) and advanced aspects of IP configuration (iptunnel, ipmaddr).
 .
 In the upstream package 'hostname' and friends are included. Those are
 not installed by this package, since there is a special "hostname*.deb".
Description-md5: 08f345ee19e62d4fd85e960d3a061a33
Task: ubuntukylin-desktop

mafoelffen@Mikes-ThinkPad-T520:~$ apt list net-tools -a
Listing... Done
net-tools/jammy,now 1.60+git20181103.0eebece-1ubuntu5 amd64 [installed]

net-tools/jammy 1.60+git20181103.0eebece-1ubuntu5 i386

```
It's there...

Please try
```

sudo apt install net-tools

```

---

### Post by deadflowr on 2024-01-11
> Is this a current archive ? 
No, not an archive.
No such repository as us.archives.ubuntu.com
drop the s in archives.
Should only be us.archive.ubuntu.com

---

### Post by MAFoElffen on 2024-01-11
Oh Dang... LOL. Didn't even notice the extra "s"

---

### Post by SeijiSensei on 2024-01-11
I use local mirrors whenever possible. The MIT repository is a lot faster on average than what I get from us.archive.

---

### Post by MAFoElffen on 2024-01-11
I do the same. My suggests is to look at the Mirrors page: [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

Eval the services they say they offer, their speed, and ensure they are up-to-date. All those are listed in the different columns there.

---

### Post by kole19 on 2024-01-12
Hey Stan! It seems like there might be an issue with the archive link. For a smoother setup, consider using a different mirror. Also, editing tutorials with CapCut can make your Ubuntu journey more visually appealing and easier to follow. Please follow : [https://itscapcutapk.com/camera-lenta-capcut-template/](https://itscapcutapk.com/camera-lenta-capcut-template/)

---


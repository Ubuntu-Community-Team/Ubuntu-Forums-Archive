---
title: "LibreOffice OpenClipArt breaks LibreOffice-Common - why ?"
date: 2022-05-21
forum: General Help
---

### Post by Anquietas on 2022-05-21
Hello,

I have the following situation:

```

mainframe [~] # apt install openclipart
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 openclipart : Depends: openclipart-libreoffice (= 1:0.18+dfsg-16) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
mainframe [~] # apt install openclipart-libreoffice
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libreoffice-common : Breaks: openclipart-libreoffice (<= 1:0.18+dfsg-17) but 1:0.18+dfsg-16 is to be installed
                      Recommends: python3-uno (>= 4.4.0~beta2) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

I want those beautiful ClipArt drawings in Libreoffice, however it conflicts with the LibreOffice-Common package which, I believe, is something important to LibreOffice.
Why is this happening and why should a couple of nice drawings conflict with a suite of applications ?

Also, does this mean I have broken packages ? I issued an "apt-get install -f" and no packages were in that list...

Thank you.

---

### Post by Impavidus on 2022-05-21
There's only a conflict with a particular version of the package. Which version of Ubuntu are you running? Try
```
apt-cache policy libreoffice-common openclipart-libreoffice openclipart
```and show the results.

---

### Post by Anquietas on 2022-05-22
```

mainframe [~] # apt-cache policy libreoffice-common openclipart-libreoffice openclipart
libreoffice-common:
  Installed: 1:7.3.3~rc2-0ubuntu0.20.04.1~lo1
  Candidate: 1:7.3.3~rc2-0ubuntu0.20.04.1~lo1
  Version table:
 *** 1:7.3.3~rc2-0ubuntu0.20.04.1~lo1 500
        500 http://ppa.launchpad.net/libreoffice/ppa/ubuntu focal/main amd64 Packages
        500 http://ppa.launchpad.net/libreoffice/ppa/ubuntu focal/main i386 Packages
        100 /var/lib/dpkg/status
     1:7.2.7-0ubuntu0.21.10.1~bpo20.04.1 100
        100 http://archive.ubuntu.com/ubuntu focal-backports/main amd64 Packages
        100 http://archive.ubuntu.com/ubuntu focal-backports/main i386 Packages
     1:7.2.6-0ubuntu0.21.10.1~bpo20.04.1 100
        100 http://archive.ubuntu.com/ubuntu focal-backports/main amd64 Packages
        100 http://archive.ubuntu.com/ubuntu focal-backports/main i386 Packages
     1:6.4.7-0ubuntu0.20.04.4 500
        500 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu focal-updates/main i386 Packages
        500 http://archive.ubuntu.com/ubuntu focal-security/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu focal-security/main i386 Packages
     1:6.4.2-0ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu focal/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu focal/main i386 Packages
openclipart-libreoffice:
  Installed: (none)
  Candidate: 1:0.18+dfsg-16
  Version table:
     1:0.18+dfsg-16 500
        500 http://archive.ubuntu.com/ubuntu focal/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu focal/universe i386 Packages
openclipart:
  Installed: (none)
  Candidate: 1:0.18+dfsg-16
  Version table:
     1:0.18+dfsg-16 500
        500 http://archive.ubuntu.com/ubuntu focal/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu focal/universe i386 Packages
mainframe [~] #

```

---

### Post by Impavidus on 2022-05-23
I need a little more information on the version conflicts.```
apt -a show libreoffice-common
apt show openclipart-libreoffice
```The first of those commands can produce quite a lot of output.

---

### Post by Anquietas on 2022-05-23
```

vbridge [~] # apt -a show libreoffice-common
Package: libreoffice-common
Version: 1:7.3.3~rc2-0ubuntu0.20.04.1~lo1
Priority: optional
Section: editors
Source: libreoffice
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian LibreOffice Maintainers <debian-openoffice@lists.debian.org>
Bugs: mailto:libreoffice@lists.launchpad.net
Installed-Size: 59,1 MB
Provides: libreoffice-l10n-en-us
Depends: libreoffice-style-colibre, ure, ucf (>= 0.8)
Recommends: fonts-liberation2 | ttf-mscorefonts-installer, apparmor (>= 2.13.1~), poppler-data, xdg-utils, python3-uno (>= 4.4.0~beta2), libexttextcat-data
Suggests: libreoffice-style
Conflicts: broffice, libreoffice-base (<< 1:7.0.0~alpha~), libreoffice-base-nogui (<< 1:7.0.0~alpha~), libreoffice-calc (<< 1:7.0.0~alpha~), libreoffice-calc-nogui (<< 1:7.0.0~alpha~), libreoffice-draw (<< 1:7.0.0~alpha~), libreoffice-draw-nogui (<< 1:7.0.0~alpha~), libreoffice-evolution (<< 1:7.0.0~alpha~), libreoffice-filter-mobiledev, libreoffice-gnome (<< 1:7.0.0~alpha~), libreoffice-impress (<< 1:7.0.0~alpha~), libreoffice-impress-nogui (<< 1:7.0.0~alpha~), libreoffice-l10n (<< 7.0), libreoffice-l10n-4.3, libreoffice-l10n-4.4, libreoffice-librelogo (<< 1:7.0.0~alpha~), libreoffice-math (<< 1:7.0.0~alpha~), libreoffice-math-nogui (<< 1:7.0.0~alpha~), libreoffice-report-builder (<< 1:7.0.0~alpha~), libreoffice-sdbc-postgresql (<< 1:7.0.0~alpha~), libreoffice-wiki-publisher (<< 1.2.0+LibO5.4.0~rc2), libreoffice-writer (<< 1:7.0.0~alpha~), libreoffice-writer-nogui (<< 1:7.0.0~alpha~), openoffice.org-unbundled, python3-uno (<< 1:7.0.0~alpha~)
Breaks: libreoffice-base (<< 1:6.4.0~beta1-2~), libreoffice-core (>= 1:7.4~), libreoffice-core (<< 1:7.3~), libreoffice-evolution (<< 1:7.0.0~alpha), libreoffice-gnome (<< 1:7.0.0~alpha), libreoffice-help (<< 5.4), libreoffice-help-5.2, libreoffice-l10n (<< 7.0), libreoffice-librelogo (<< 1:7.0.0~alpha), libreoffice-report-builder (<< 1:7.0.0~alpha), libreoffice-sdbc-postgresql (<< 1:7.0.0~alpha), libreoffice-style-andromeda (<< 1:7.3~), libreoffice-style-crystal (>= 1:7.4~), libreoffice-style-crystal (<< 1:7.3~), libreoffice-style-galaxy (>= 1:7.4~), libreoffice-style-galaxy (<< 1:7.3~), libreoffice-style-hicontrast (>= 1:7.4~), libreoffice-style-hicontrast (<< 1:7.3~), libreoffice-style-tango (<< 1:7.0.0~alpha), libreoffice-writer2latex (<< 1.0.2-9), libreoffice-writer2xhtml (<< 1.0.2-9), openclipart-libreoffice (<= 1:0.18+dfsg-17), python3-uno (<< 1:7.0.0~alpha)
Replaces: libreoffice-base (<< 1:6.4.0~beta1-2~), libreoffice-pdfimport (<< 1:5.4~), openclipart-libreoffice (<= 1:0.18+dfsg-17)
Download-Size: 23,7 MB
APT-Manual-Installed: no
APT-Sources: http://ppa.launchpad.net/libreoffice/ppa/ubuntu focal/main amd64 Packages
Description: office productivity suite -- arch-independent files
 LibreOffice is a full-featured office productivity suite that provides
 a near drop-in replacement for Microsoft(R) Office.
 .
 This package contains the architecture-independent files of
 LibreOffice.

Package: libreoffice-common
Version: 1:7.2.7-0ubuntu0.21.10.1~bpo20.04.1
Priority: optional
Section: editors
Source: libreoffice
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian LibreOffice Maintainers <debian-openoffice@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 59,7 MB
Provides: libreoffice-l10n-en-us
Depends: libreoffice-style-colibre, ure, ucf (>= 0.8)
Recommends: fonts-liberation2 | ttf-mscorefonts-installer, apparmor (>= 2.13.1~), poppler-data, xdg-utils, python3-uno (>= 4.4.0~beta2), libexttextcat-data
Suggests: libreoffice-style
Conflicts: broffice, libreoffice-base (<< 1:7.0.0~alpha~), libreoffice-base-nogui (<< 1:7.0.0~alpha~), libreoffice-calc (<< 1:7.0.0~alpha~), libreoffice-calc-nogui (<< 1:7.0.0~alpha~), libreoffice-draw (<< 1:7.0.0~alpha~), libreoffice-draw-nogui (<< 1:7.0.0~alpha~), libreoffice-evolution (<< 1:7.0.0~alpha~), libreoffice-filter-mobiledev, libreoffice-gnome (<< 1:7.0.0~alpha~), libreoffice-impress (<< 1:7.0.0~alpha~), libreoffice-impress-nogui (<< 1:7.0.0~alpha~), libreoffice-l10n (<< 7.0), libreoffice-l10n-4.3, libreoffice-l10n-4.4, libreoffice-librelogo (<< 1:7.0.0~alpha~), libreoffice-math (<< 1:7.0.0~alpha~), libreoffice-math-nogui (<< 1:7.0.0~alpha~), libreoffice-report-builder (<< 1:7.0.0~alpha~), libreoffice-sdbc-postgresql (<< 1:7.0.0~alpha~), libreoffice-wiki-publisher (<< 1.2.0+LibO5.4.0~rc2), libreoffice-writer (<< 1:7.0.0~alpha~), libreoffice-writer-nogui (<< 1:7.0.0~alpha~), openoffice.org-unbundled, python3-uno (<< 1:7.0.0~alpha~)
Breaks: libreoffice-base (<< 1:6.4.0~beta1-2~), libreoffice-core (>= 1:7.3~), libreoffice-core (<< 1:7.2~), libreoffice-evolution (<< 1:7.0.0~alpha), libreoffice-gnome (<< 1:7.0.0~alpha), libreoffice-help (<< 5.4), libreoffice-help-5.2, libreoffice-l10n (<< 7.0), libreoffice-librelogo (<< 1:7.0.0~alpha), libreoffice-report-builder (<< 1:7.0.0~alpha), libreoffice-sdbc-postgresql (<< 1:7.0.0~alpha), libreoffice-style-andromeda (<< 1:7.2~), libreoffice-style-crystal (>= 1:7.3~), libreoffice-style-crystal (<< 1:7.2~), libreoffice-style-galaxy (>= 1:7.3~), libreoffice-style-galaxy (<< 1:7.2~), libreoffice-style-hicontrast (>= 1:7.3~), libreoffice-style-hicontrast (<< 1:7.2~), libreoffice-style-tango (<< 1:7.0.0~alpha), libreoffice-writer2latex (<< 1.0.2-9), libreoffice-writer2xhtml (<< 1.0.2-9), openclipart-libreoffice (<= 1:0.18+dfsg-17), python3-uno (<< 1:7.0.0~alpha)
Replaces: libreoffice-base (<< 1:6.4.0~beta1-2~), libreoffice-pdfimport (<< 1:5.4~), openclipart-libreoffice (<= 1:0.18+dfsg-17)
Homepage: http://www.libreoffice.org
Task: ubuntu-desktop, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, kubuntu-desktop, kubuntu-full, xubuntu-desktop, lubuntu-desktop, ubuntustudio-desktop, ubuntukylin-desktop, ubuntu-mate-desktop, ubuntu-budgie-desktop
Download-Size: 23,2 MB
APT-Sources: http://archive.ubuntu.com/ubuntu focal-backports/main amd64 Packages
Description: office productivity suite -- arch-independent files
 LibreOffice is a full-featured office productivity suite that provides
 a near drop-in replacement for Microsoft(R) Office.
 .
 This package contains the architecture-independent files of
 LibreOffice.

Package: libreoffice-common
Version: 1:6.4.7-0ubuntu0.20.04.4
Priority: optional
Section: editors
Source: libreoffice
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian LibreOffice Maintainers <debian-openoffice@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 56,5 MB
Provides: libreoffice-l10n-en-us
Depends: libreoffice-style-colibre, libreoffice-style-tango, ure
Recommends: fonts-liberation2 | ttf-mscorefonts-installer, apparmor (>= 2.13.1~), xdg-utils, python3-uno (>= 4.4.0~beta2), libexttextcat-data
Suggests: libreoffice-style
Conflicts: apparmor (<< 2.13.1~), broffice, libreoffice-filter-mobiledev, libreoffice-l10n-4.3, libreoffice-l10n-4.4, libreoffice-wiki-publisher (<< 1.2.0+LibO5.4.0~rc2), openoffice-unbundled
Breaks: libreoffice-base (<< 1:6.4.0~beta1-2~), libreoffice-core (>= 1:6.5~), libreoffice-core (<< 1:6.4.2~rc1), libreoffice-help (<< 5.4), libreoffice-help-5.2, libreoffice-style-andromeda (<< 1:6.4~), libreoffice-style-crystal (>= 1:6.5~), libreoffice-style-crystal (<< 1:6.4~), libreoffice-style-galaxy (>= 1:6.5~), libreoffice-style-galaxy (<< 1:6.4~), libreoffice-style-hicontrast (>= 1:6.5~), libreoffice-style-hicontrast (<< 1:6.4~), libreoffice-style-tango (>= 1:6.5~), libreoffice-style-tango (<< 1:6.4~), libreoffice-writer2latex (<< 1.0.2-9), libreoffice-writer2xhtml (<< 1.0.2-9)
Replaces: libreoffice-base (<< 1:6.4.0~beta1-2~), libreoffice-pdfimport (<< 1:5.4~)
Homepage: http://www.libreoffice.org
Task: ubuntu-desktop, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, kubuntu-desktop, kubuntu-full, xubuntu-desktop, lubuntu-desktop, ubuntustudio-desktop, ubuntukylin-desktop, ubuntu-mate-desktop, ubuntu-budgie-desktop
Download-Size: 23,5 MB
APT-Sources: http://archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
Description: office productivity suite -- arch-independent files
 LibreOffice is a full-featured office productivity suite that provides
 a near drop-in replacement for Microsoft(R) Office.
 .
 This package contains the architecture-independent files of
 LibreOffice.

Package: libreoffice-common
Version: 1:6.4.2-0ubuntu3
Priority: optional
Section: editors
Source: libreoffice
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian LibreOffice Maintainers <debian-openoffice@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 56,4 MB
Provides: libreoffice-l10n-en-us
Depends: libreoffice-style-colibre, libreoffice-style-tango, ure
Recommends: fonts-liberation2 | ttf-mscorefonts-installer, apparmor (>= 2.13.1~), xdg-utils, python3-uno (>= 4.4.0~beta2), libexttextcat-data
Suggests: libreoffice-style
Conflicts: apparmor (<< 2.13.1~), broffice, libreoffice-filter-mobiledev, libreoffice-l10n-4.3, libreoffice-l10n-4.4, libreoffice-wiki-publisher (<< 1.2.0+LibO5.4.0~rc2), openoffice-unbundled
Breaks: libreoffice-base (<< 1:6.4.0~beta1-2~), libreoffice-core (>= 1:6.5~), libreoffice-core (<< 1:6.4.2~rc1), libreoffice-help (<< 5.4), libreoffice-help-5.2, libreoffice-style-andromeda (<< 1:6.4~), libreoffice-style-crystal (>= 1:6.5~), libreoffice-style-crystal (<< 1:6.4~), libreoffice-style-galaxy (>= 1:6.5~), libreoffice-style-galaxy (<< 1:6.4~), libreoffice-style-hicontrast (>= 1:6.5~), libreoffice-style-hicontrast (<< 1:6.4~), libreoffice-style-tango (>= 1:6.5~), libreoffice-style-tango (<< 1:6.4~), libreoffice-writer2latex (<< 1.0.2-9), libreoffice-writer2xhtml (<< 1.0.2-9)
Replaces: libreoffice-pdfimport (<< 1:5.4~)
Homepage: http://www.libreoffice.org
Task: ubuntu-desktop, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, kubuntu-desktop, kubuntu-full, xubuntu-desktop, lubuntu-desktop, ubuntustudio-desktop, ubuntukylin-desktop, ubuntu-mate-desktop, ubuntu-budgie-desktop
Download-Size: 23,5 MB
APT-Sources: http://archive.ubuntu.com/ubuntu focal/main amd64 Packages
Description: office productivity suite -- arch-independent files
 LibreOffice is a full-featured office productivity suite that provides
 a near drop-in replacement for Microsoft(R) Office.
 .
 This package contains the architecture-independent files of
 LibreOffice.

vbridge [~] # apt show openclipart-libreoffice
Package: openclipart-libreoffice
Version: 1:0.18+dfsg-16
Priority: extra
Section: universe/graphics
Source: openclipart
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian QA Group <packages@qa.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 28,3 MB
Depends: openclipart-png (= 1:0.18+dfsg-16)
Recommends: libreoffice
Conflicts: libreoffice-common (<< 1:3.5.0~beta~), openclipart (<< 0.10+dfsg-3)
Homepage: http://www.openclipart.org
Download-Size: 20,0 MB
APT-Sources: http://archive.ubuntu.com/ubuntu focal/universe amd64 Packages
Description: clip art for OpenOffice.org/LibreOffice gallery
 The Open Clip Art Library is a collection of 100% license-free,
 royalty-free, and restriction-free art that you can use for any purpose.
 .
 The clip art in this package is sorted by subject (e.g. sports). Openclipart 2
 is sorted by artist (who created the clip art) and is much larger.
 .
 This package contains the OpenOffice.org/LibreOffice Gallery info files.

vbridge [~] # 

```

---

### Post by Holger_Gehrke on 2022-05-23
You've got your LibreOffice from the ppa of the LibreOffice developers. That version is newer than the version from the repositories (it's about the same version which is in the repositories for Jammy/22.04) and wants a newer version of the clip-art package (and it says that it breaks the older version; unlikely but it says it does ...). I'd try downloading the clipart packages for Jammy from packages.ubuntu.com and try to install those.

Holger

---

### Post by Impavidus on 2022-05-23
Not only the libreoffice-common from the PPA, but also the one from focal-backports claims to break openclipart-libreoffice. The right versions of the openclipart packages are apparently not present in the PPA or the focal-backports repos. As Holger mentions, you could fetch the correct version of of the openclipart packages (at least openclipart-libreoffice, openclipart-png, openclipart, openclipart-svg) from jammy. It will probably work. Or you could downgrade your entire libreoffice to the standard version for focal (6.4) or upgrade your entire system to 22.04 (upgrade not released yet). Neither of those are very nice options.

---

### Post by Anquietas on 2022-05-23
If I manually download the DEB file package, I might be able to install it, however, it will not upgrade along with my entire system on an "apt full-upgrade" event...

---

### Post by Holger_Gehrke on 2022-05-23
> **Anquietas said:**
> If I manually download the DEB file package, I might be able to install it, however, it will not upgrade along with my entire system on an "apt full-upgrade" event...

As Impavidus said, none of the option are really nice. But considering the fact that updates are only done for critical bugs, how likely is an update to a clip-art package ?

Holger

---


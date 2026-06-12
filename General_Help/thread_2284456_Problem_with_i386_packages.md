---
title: "Problem with i386 packages"
date: 2015-06-29
forum: General Help
---

### Post by max-disselnmeyer on 2015-06-29
Hi, when trying to install 32bit packages, e.g. wine i get following problem:
```

:~$ sudo apt-get install wine package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 wine : Depends: wine1.6
E: Unable to correct problems, you have held broken packages.
:~$ sudo apt-get install wine1.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 wine1.6 : Depends: wine1.6-i386 (= 1:1.6.2-0ubuntu8)
E: Unable to correct problems, you have held broken packages.

```

I already asked in a German Forum for help, but no one was able to help me.
As they were interested whats in my etc/apt/source.list i will post it here too:

```

deb http://archive.ubuntu.com/ubuntu vivid main universe restricted multiverse
deb http://archive.canonical.com/ubuntu vivid partner
#deb-src http://archive.canonical.com/ubuntu vivid partner
deb http://archive.ubuntu.com/ubuntu/ vivid-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ vivid-security main restricted universe multiverse

```

already tried ```
Sudo dpkg --add-architecture i386
``` but this didn't solve the problem.
I have Ubuntu 15.04 64bit and would really appreciate it if someone could help me.

---

### Post by deadflowr on 2015-06-29
Post the output for 
```
apt-cache policy wine1.6
```

---

### Post by max-disselnmeyer on 2015-06-29
```

wine1.6:  Installed: (none)
  Candidate: 1:1.6.2-0ubuntu8
  Version table:
     1:1.6.2-0ubuntu8 0
        500 http://archive.ubuntu.com/ubuntu/ vivid/universe amd64 Packages

```
I have this problem with all 32Bit packages, not only wine 1.6

So here the Output for the same command without wine1.6:
```
sudo apt-cache policy
Package files:
 100 /var/lib/dpkg/status
     release a=now
 500 http://ppa.launchpad.net/pipelight/stable/ubuntu/ vivid/main Translation-en
 500 http://ppa.launchpad.net/pipelight/stable/ubuntu/ vivid/main i386 Packages
     release v=15.04,o=LP-PPA-pipelight-stable,a=vivid,n=vivid,l=pipelight-stable,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/pipelight/stable/ubuntu/ vivid/main amd64 Packages
     release v=15.04,o=LP-PPA-pipelight-stable,a=vivid,n=vivid,l=pipelight-stable,c=main
     origin ppa.launchpad.net
 500 http://archive.ubuntu.com/ubuntu/ vivid-security/universe Translation-en
 500 http://archive.ubuntu.com/ubuntu/ vivid-security/restricted Translation-en
 500 http://archive.ubuntu.com/ubuntu/ vivid-security/multiverse Translation-en
 500 http://archive.ubuntu.com/ubuntu/ vivid-security/main Translation-en
 500 http://archive.ubuntu.com/ubuntu/ vivid-security/multiverse i386 Packages
     release v=15.04,o=Ubuntu,a=vivid-security,n=vivid,l=Ubuntu,c=multiverse
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu/ vivid-security/universe i386 Packages
     release v=15.04,o=Ubuntu,a=vivid-security,n=vivid,l=Ubuntu,c=universe
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu/ vivid-security/restricted i386 Packages
     release v=15.04,o=Ubuntu,a=vivid-security,n=vivid,l=Ubuntu,c=restricted
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu/ vivid-security/main i386 Packages
     release v=15.04,o=Ubuntu,a=vivid-security,n=vivid,l=Ubuntu,c=main
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu/ vivid-security/multiverse amd64 Packages
     release v=15.04,o=Ubuntu,a=vivid-security,n=vivid,l=Ubuntu,c=multiverse
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu/ vivid-security/universe amd64 Packages
     release v=15.04,o=Ubuntu,a=vivid-security,n=vivid,l=Ubuntu,c=universe
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu/ vivid-security/restricted amd64 Packages
     release v=15.04,o=Ubuntu,a=vivid-security,n=vivid,l=Ubuntu,c=restricted
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu/ vivid-security/main amd64 Packages
     release v=15.04,o=Ubuntu,a=vivid-security,n=vivid,l=Ubuntu,c=main
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu/ vivid-updates/universe Translation-en
 500 http://archive.ubuntu.com/ubuntu/ vivid-updates/restricted Translation-en
 500 http://archive.ubuntu.com/ubuntu/ vivid-updates/multiverse Translation-en
 500 http://archive.ubuntu.com/ubuntu/ vivid-updates/main Translation-en
 500 http://archive.ubuntu.com/ubuntu/ vivid-updates/multiverse i386 Packages
     release v=15.04,o=Ubuntu,a=vivid-updates,n=vivid,l=Ubuntu,c=multiverse
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu/ vivid-updates/universe i386 Packages
     release v=15.04,o=Ubuntu,a=vivid-updates,n=vivid,l=Ubuntu,c=universe
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu/ vivid-updates/restricted i386 Packages
     release v=15.04,o=Ubuntu,a=vivid-updates,n=vivid,l=Ubuntu,c=restricted
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu/ vivid-updates/main i386 Packages
     release v=15.04,o=Ubuntu,a=vivid-updates,n=vivid,l=Ubuntu,c=main
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu/ vivid-updates/multiverse amd64 Packages
     release v=15.04,o=Ubuntu,a=vivid-updates,n=vivid,l=Ubuntu,c=multiverse
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu/ vivid-updates/universe amd64 Packages
     release v=15.04,o=Ubuntu,a=vivid-updates,n=vivid,l=Ubuntu,c=universe
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu/ vivid-updates/restricted amd64 Packages
     release v=15.04,o=Ubuntu,a=vivid-updates,n=vivid,l=Ubuntu,c=restricted
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu/ vivid-updates/main amd64 Packages
     release v=15.04,o=Ubuntu,a=vivid-updates,n=vivid,l=Ubuntu,c=main
     origin archive.ubuntu.com
 500 http://archive.canonical.com/ubuntu/ vivid/partner Translation-en
 500 http://archive.canonical.com/ubuntu/ vivid/partner i386 Packages
     release v=15.04,o=Canonical,a=vivid,n=vivid,l=Partner archive,c=partner
     origin archive.canonical.com
 500 http://archive.canonical.com/ubuntu/ vivid/partner amd64 Packages
     release v=15.04,o=Canonical,a=vivid,n=vivid,l=Partner archive,c=partner
     origin archive.canonical.com
 500 http://archive.ubuntu.com/ubuntu/ vivid/universe Translation-en
 500 http://archive.ubuntu.com/ubuntu/ vivid/universe Translation-de
 500 http://archive.ubuntu.com/ubuntu/ vivid/restricted Translation-en
 500 http://archive.ubuntu.com/ubuntu/ vivid/restricted Translation-de
 500 http://archive.ubuntu.com/ubuntu/ vivid/multiverse Translation-en
 500 http://archive.ubuntu.com/ubuntu/ vivid/multiverse Translation-de
 500 http://archive.ubuntu.com/ubuntu/ vivid/main Translation-en
 500 http://archive.ubuntu.com/ubuntu/ vivid/main Translation-de
 500 http://archive.ubuntu.com/ubuntu/ vivid/multiverse i386 Packages
     release v=15.04,o=Ubuntu,a=vivid,n=vivid,l=Ubuntu,c=multiverse
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu/ vivid/restricted i386 Packages
     release v=15.04,o=Ubuntu,a=vivid,n=vivid,l=Ubuntu,c=restricted
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu/ vivid/universe i386 Packages
     release v=15.04,o=Ubuntu,a=vivid,n=vivid,l=Ubuntu,c=universe
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu/ vivid/main i386 Packages
     release v=15.04,o=Ubuntu,a=vivid,n=vivid,l=Ubuntu,c=main
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu/ vivid/multiverse amd64 Packages
     release v=15.04,o=Ubuntu,a=vivid,n=vivid,l=Ubuntu,c=multiverse
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu/ vivid/restricted amd64 Packages
     release v=15.04,o=Ubuntu,a=vivid,n=vivid,l=Ubuntu,c=restricted
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu/ vivid/universe amd64 Packages
     release v=15.04,o=Ubuntu,a=vivid,n=vivid,l=Ubuntu,c=universe
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu/ vivid/main amd64 Packages
     release v=15.04,o=Ubuntu,a=vivid,n=vivid,l=Ubuntu,c=main
     origin archive.ubuntu.com
Pinned packages:



```

---

### Post by matt_symes on 2015-06-29
Hi

Can you also post the output of these commands as well please.

```

uname -a
cat /etc/lsb-release
dpkg -l multiarch-support
apt-cache show wine1.6

```

Kind regards

---

### Post by max-disselnmeyer on 2015-06-29
```

:~$ sudo uname -a
Linux MaDi 3.19.0-21-generic #21-Ubuntu SMP Sun Jun 14 18:31:11 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.04
DISTRIB_CODENAME=vivid
DISTRIB_DESCRIPTION="Ubuntu 15.04"
:~$ dpkg -l multiarch-support
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                         Version             Architecture        Description
+++-============================-===================-===================-=============================================================
ii  multiarch-support            2.21-0ubuntu4       amd64               Transitional package to ensure multiarch compatibility
:~$ apt-cache show wine 1.6
Package: wine
Priority: extra
Section: universe/otherosfs
Installed-Size: 21
Maintainer: Scott Ritchie <scottritchie@ubuntu.com>
Architecture: amd64
Source: wine1.6
Version: 1:1.6.2-0ubuntu8
Depends: wine1.6
Filename: pool/universe/w/wine1.6/wine_1.6.2-0ubuntu8_amd64.deb
Size: 1018
MD5sum: 96481a5e28b630de13be63f93f2046a3
SHA1: 0df0b2128a37dfa19838cc23fa86a0d7ed911743
SHA256: 0052dae4dcea6da5e5050fd40e00129bec5ebfa28ab0335cbcd409a51e4345b6
Description-en: Microsoft Windows Compatibility Layer (meta-package)
 Wine is a compatibility layer for running Windows applications on Linux.
 Applications are run at full speed without the need of cpu emulation. Wine
 does not require Microsoft Windows, however it can use native system dll
 files in place of its own if they are available.
 .
 This meta-package always depends on the default version of Wine.
Description-md5: 6474b3e541944944e61aec502ceb28f2
Multi-Arch: foreign
Homepage: http://www.winehq.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu


Package: libx11-6
Priority: standard
Section: libs
Installed-Size: 1383
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Architecture: amd64
Source: libx11
Version: 2:1.6.2-2ubuntu2
Depends: libc6 (>= 2.15), libxcb1 (>= 1.2), libx11-data
Pre-Depends: multiarch-support
Filename: pool/main/libx/libx11/libx11-6_1.6.2-2ubuntu2_amd64.deb
Size: 570876
MD5sum: 93037207fe73e72e1641c7f0c5642580
SHA1: 75da84d59d8530a887b886c089be8b272e6709bc
SHA256: 26ac0c8296ee4ca8a80e310d7630e415ac2f75bea6cb57d3c9304a4c01b1e89b
Description-en: X11 client-side library
 This package provides a client interface to the X Window System, otherwise
 known as 'Xlib'.  It provides a complete API for the basic functions of the
 window system.
 .
 More information about X.Org can be found at:
 <URL:http://www.X.org>
 .
 This module can be found at
 git://anongit.freedesktop.org/git/xorg/lib/libX11
Description-md5: d75c895abf6eca234f7480813aaa95ec
Multi-Arch: same
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 9m
Task: standard, kubuntu-active, mythbuntu-frontend, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-slave, mythbuntu-backend-master, mythbuntu-backend-master, ubuntu-sdk-libs, ubuntu-touch



```

after this the last command lists every package that wine depends on, it has approximately around 2000 lines, if you want i can post that too

thank you guys for your help!

---

### Post by matt_symes on 2015-06-29
Hi

You had 2000+ lines because you put a space between wine and 1.6.

Not much to go on from the existing terminal output so can you post the output of these commands.

```
ls /usr/lib/i386-Linux-gnu | wc -l
apt-cache search wine1.6
```

Let's try to install the 32bit version of wine. Post back all the terminal output.

```
sudo apt-get install wine1.6:i386
```

Kind regards

---

### Post by max-disselnmeyer on 2015-06-29
Oh, yeah my mistake
```

:~$ apt-cache search wine1.6
wine1.6 - Microsoft Windows Compatibility Layer (Binary Emulator and Library)
wine1.6-amd64 - Microsoft Windows Compatibility Layer (64-bit support)
wine1.6-dbg - Microsoft Windows Compatibility Layer (debugging symbols)
wine1.6-dev - Microsoft Windows Compatibility Layer (Development files)
wine1.6-i386 - Microsoft Windows Compatibility Layer (32-bit support)
wine-staging-compat - special build of the popular Wine software
max@MaDi:~$ sudo apt-get install wine1.6:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 wine1.6:i386 : Depends: wine1.6-i386:i386 (= 1:1.6.2-0ubuntu8)
                Recommends: winetricks:i386
E: Unable to correct problems, you have held broken packages.
max@MaDi:~$ apt-cache show wine1.6
Package: wine1.6
Priority: optional
Section: universe/otherosfs
Installed-Size: 3052
Maintainer: Scott Ritchie <scottritchie@ubuntu.com>
Architecture: amd64
Version: 1:1.6.2-0ubuntu8
Replaces: wine, wine1.0, wine1.2, wine1.3, wine1.4, wine1.5
Provides: wine
Depends: debconf (>= 0.5) | debconf-2.0, libc6 (>= 2.17), wine1.6-amd64 (= 1:1.6.2-0ubuntu8), binfmt-support (>= 1.1.2), procps, wine1.6-i386 (= 1:1.6.2-0ubuntu8)
Pre-Depends: dpkg (>= 1.15.7.2~)
Recommends: cups-bsd, gnome-exe-thumbnailer | kde-runtime, fonts-droid, fonts-liberation, ttf-mscorefonts-installer, fonts-horai-umefont, fonts-unfonts-core, ttf-wqy-microhei, winetricks, xdg-utils
Suggests: dosbox:any, winbind
Conflicts: wine1.0, wine1.2, wine1.3
Filename: pool/universe/w/wine1.6/wine1.6_1.6.2-0ubuntu8_amd64.deb
Size: 864898
MD5sum: 627271fc669bb133bd5f91771c6faa4e
SHA1: ec43bfc2647bc572eaa35e42bc15dd73d39682e0
SHA256: 50a070b9e936d87c3966a383720714786a4a3b70cae3af78c1dc5fe347c026bb
Description-en: Microsoft Windows Compatibility Layer (Binary Emulator and Library)
 Wine is a compatibility layer for running Windows applications on Linux.
 Applications are run at full speed without the need of cpu emulation. Wine
 does not require Microsoft Windows, however it can use native system dll
 files in place of its own if they are available.
 .
 This package includes a program loader for running unmodified Windows
 executables as well as the Wine project's free version of the Windows API for
 running programs ported from Windows.
Description-md5: 06ea04f761f0f961a93a88bc585f4ba8
Multi-Arch: allowed
Homepage: http://www.winehq.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

```

```

:~$ ls /usr/lib/i386-Linux-gnu | wc -l
ls: cannot access /usr/lib/i386-Linux-gnu: No such file or directory
0

```

```

:~$ apt-cache search wine1.6
wine1.6 - Microsoft Windows Compatibility Layer (Binary Emulator and Library)
wine1.6-amd64 - Microsoft Windows Compatibility Layer (64-bit support)
wine1.6-dbg - Microsoft Windows Compatibility Layer (debugging symbols)
wine1.6-dev - Microsoft Windows Compatibility Layer (Development files)
wine1.6-i386 - Microsoft Windows Compatibility Layer (32-bit support)
wine-staging-compat - special build of the popular Wine software

```

```

:~$ sudo apt-get install wine1.6:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 wine1.6:i386 : Depends: wine1.6-i386:i386 (= 1:1.6.2-0ubuntu8)
                Recommends: winetricks:i386
E: Unable to correct problems, you have held broken packages.

```

---

### Post by matt_symes on 2015-06-29
Hi

Sorry. My phone keeps trying to auto correct my typing.

Please post

```
ls /usr/lib/i386-linux-gnu | wc -l
```

Can you also post the output of this command to check all your source files.

```
grep "^[^#]" /etc/apt/sources.list{,.d/*}
```

Kind regards

---

### Post by max-disselnmeyer on 2015-06-29
```

:~$ ls /usr/lib/i386-linux-gnu | wc -l
16
:~$ grep "^[^#]" /etc/apt/sources.list{,.d/*}
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu vivid main universe restricted multiverse
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu vivid partner
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu/ vivid-updates main restricted universe multiverse
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu/ vivid-security main restricted universe multiverse
/etc/apt/sources.list.d/diesch-testing-trusty.list.distUpgrade:deb http://ppa.launchpad.net/diesch/testing/ubuntu trusty main
/etc/apt/sources.list.d/diesch-testing-trusty.list.save:deb http://ppa.launchpad.net/diesch/testing/ubuntu trusty main
/etc/apt/sources.list.d/fingerprint-fingerprint-gui-trusty.list.distUpgrade:deb http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu trusty main
/etc/apt/sources.list.d/fingerprint-fingerprint-gui-trusty.list.save:deb http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu trusty main
/etc/apt/sources.list.d/getdeb.list.distUpgrade:deb http://archive.getdeb.net/ubuntu utopic-getdeb apps
/etc/apt/sources.list.d/google-chrome.list.distUpgrade:deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.save:deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/jd-team-jdownloader-trusty.list.distUpgrade:deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu trusty main
/etc/apt/sources.list.d/jd-team-jdownloader-trusty.list.save:deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu trusty main
/etc/apt/sources.list.d/kilian-f_lux-trusty.list.distUpgrade:deb http://ppa.launchpad.net/kilian/f.lux/ubuntu trusty main
/etc/apt/sources.list.d/kilian-f_lux-trusty.list.save:deb http://ppa.launchpad.net/kilian/f.lux/ubuntu trusty main
/etc/apt/sources.list.d/linrunner-tlp-trusty.list.distUpgrade:deb http://ppa.launchpad.net/linrunner/tlp/ubuntu trusty main
/etc/apt/sources.list.d/linrunner-tlp-trusty.list.save:deb http://ppa.launchpad.net/linrunner/tlp/ubuntu trusty main
/etc/apt/sources.list.d/mono-xamarin.list.distUpgrade:deb http://download.mono-project.com/repo/debian wheezy main
/etc/apt/sources.list.d/mono-xamarin.list.save:deb http://download.mono-project.com/repo/debian wheezy main
/etc/apt/sources.list.d/oibaf-graphics-drivers-trusty.list.distUpgrade:deb http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu trusty main
/etc/apt/sources.list.d/pipelight-stable-trusty.list.distUpgrade:deb http://ppa.launchpad.net/pipelight/stable/ubuntu trusty main
/etc/apt/sources.list.d/pipelight-stable-trusty.list.save:deb http://ppa.launchpad.net/pipelight/stable/ubuntu trusty main
/etc/apt/sources.list.d/pipelight-ubuntu-stable-vivid.list:deb http://ppa.launchpad.net/pipelight/stable/ubuntu vivid main
/etc/apt/sources.list.d/playdeb.list.distUpgrade:deb http://archive.getdeb.net/ubuntu utopic-getdeb games
/etc/apt/sources.list.d/playonlinux.list.distUpgrade:deb http://deb.playonlinux.com/ trusty main
/etc/apt/sources.list.d/playonlinux.list.save:deb http://deb.playonlinux.com/ trusty main
/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.distUpgrade:deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/steam/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf
/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.save:deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/steam/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf
/etc/apt/sources.list.d/raof-aubergine-trusty.list.distUpgrade:deb http://ppa.launchpad.net/raof/aubergine/ubuntu trusty main
/etc/apt/sources.list.d/raof-aubergine-trusty.list.save:deb http://ppa.launchpad.net/raof/aubergine/ubuntu trusty main
/etc/apt/sources.list.d/steam.list.distUpgrade:deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
/etc/apt/sources.list.d/steam.list.distUpgrade:deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
/etc/apt/sources.list.d/steam.list.save:deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
/etc/apt/sources.list.d/steam.list.save:deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
/etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list.distUpgrade:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main
/etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list.save:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main
/etc/apt/sources.list.d/ubuntu-wine-ubuntu-ppa-utopic.list.distUpgrade:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu utopic main
/etc/apt/sources.list.d/webupd8team-java-trusty.list.distUpgrade:deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
/etc/apt/sources.list.d/webupd8team-java-trusty.list.save:deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
/etc/apt/sources.list.d/webupd8team-jupiter-trusty.list.distUpgrade:deb http://ppa.launchpad.net/webupd8team/jupiter/ubuntu trusty main
/etc/apt/sources.list.d/webupd8team-jupiter-trusty.list.save:deb http://ppa.launchpad.net/webupd8team/jupiter/ubuntu trusty main
/etc/apt/sources.list.d/webupd8team-ubuntu-y-ppa-manager-utopic.list.distUpgrade:deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu utopic main
/etc/apt/sources.list.d/webupd8team-ubuntu-y-ppa-manager-utopic.list.distUpgrade:deb-src http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu utopic main

```

---

### Post by matt_symes on 2015-06-29
Hi

You only have 16 32bit libraries on your system. I have 253 !

Also, you have source files in /etc/apt/sources.list.d/ for trusty and precise (and maybe others) yet you are runnig vivid.

I suspect that is at least part of the reason you are having problems if you have installed software from those PPAs.

Remove all those old programs you installed using ppa-purge and we can take it from there.

Kind regards

---

### Post by mc4man on 2015-06-29
I would install and then try with aptitude, it sometimes provides better info about what the issue is compared to apt-get. (likely from updated package(s) from one of your various prior? ppa's, 

Seems you have a number of trusty ppa's, how did that occur?

---

### Post by max-disselnmeyer on 2015-06-29
Well thank you for this advice, but i cant figure out how to work with the ppa-purge command.. can you perhaps give me an example for one of the above listed PPAs?

---

### Post by max-disselnmeyer on 2015-06-29
@mc4man
i cant find packages like in this example wine at the application center. They just dont appear if i search for them. Even tried to download the .deb file (not sure if it was .deb but the one which you can open with application center and then install it) but that didnt worked as well.

I had 14.04 first then upgraded to 14.10, forgot the reason but i think i had any problem.
And then my computer just didnt wanted to install i386 packages. Now i tried it with a distro upgrade to 15.04 but as you can see this didnt fixed the problem...

---

### Post by matt_symes on 2015-06-29
Hi

> **max-disselnmeyer said:**
> @mc4man
I had 14.04 first then upgraded to 14.10, forgot the reason but i think i had any problem.
And then my computer just didnt wanted to install i386 packages. Now i tried it with a distro upgrade to 15.04 but as you can see this didnt fixed the problem...

That explains how most of your sources are distUpgrade and why you had problems in 14.04/14.10.

I would expect that you copied instructions from the internet to add PPAs for software ? If you do this then you have to make sure you add the correct source for your version of Ubuntu installed. Don't worry. We've all done it &#128512;

I can't really help you with ppa-purge until tomorrow due to Internet issues; hence my phone. Others may jump in though.

Kind regards

---

### Post by mc4man on 2015-06-29
```
sudo apt-get install aptitude
```
```
sudo aptitude install wine1.6
```
It's likely to fail & present a "Accept this solution? [Y/n/q/?]" option. Choose q then post complete terminal output.

It's possible that upgrading without first ppa-purging the oibaf ppa was one mistake, some other ppa's are also suspect.

---

### Post by max-disselnmeyer on 2015-06-29
I now deleted the files in the directory etc/apt/source.list.d 
```

:~$ grep "^[^#]" /etc/apt/sources.list{,.d/*}
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu vivid main universe restricted multiverse
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu vivid partner
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu/ vivid-updates main restricted universe multiverse
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu/ vivid-security main restricted universe multiverse
/etc/apt/sources.list.d/getdeb.list.distUpgrade:deb http://archive.getdeb.net/ubuntu utopic-getdeb apps
/etc/apt/sources.list.d/google-chrome.list.distUpgrade:deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.save:deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/pipelight-ubuntu-stable-vivid.list:deb http://ppa.launchpad.net/pipelight/stable/ubuntu vivid main
/etc/apt/sources.list.d/playdeb.list.distUpgrade:deb http://archive.getdeb.net/ubuntu utopic-getdeb games

```
Do you see anything that i should delete too?

Yes i copied instructions from the internet :D 
Came well along with linux until this problem and never thought really deep into these ppa things :D

---

### Post by max-disselnmeyer on 2015-06-29
```

:~$ sudo apt-get install aptitudeReading package lists... Done
Building dependency tree       
Reading state information... Done
aptitude is already the newest version.
aptitude set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
```

:~$ sudo aptitude install wine1.6
The following NEW packages will be installed:
  fonts-horai-umefont{a} fonts-unfonts-core{a} libasn1-8-heimdal:i386{a} libasound2:i386{a} libasound2-plugins:i386{a} 
  libasyncns0:i386{a} libavahi-client3:i386{a} libavahi-common-data:i386{a} libavahi-common3:i386{a} libcapi20-3{a} 
  libcapi20-3:i386{a} libcups2:i386{a} libdbus-1-3:i386{a} libdrm-intel1:i386{ab} libdrm-nouveau2:i386{ab} libdrm-radeon1:i386{ab} 
  libdrm2:i386{ab} libedit2:i386{a} libelf1:i386{a} libexif12:i386{a} libexpat1:i386{a} libffi6:i386{a} libflac8:i386{a} 
  libfontconfig1:i386{a} libfreetype6:i386{a} libgcrypt20:i386{a} libgd3:i386{a} libgif4:i386{a} libgl1-mesa-dri:i386{a} 
  libgl1-mesa-glx:i386{a} libglapi-mesa:i386{a} libglib2.0-0:i386{a} libglu1-mesa:i386{a} libgmp10:i386{a} 
  libgnutls-deb0-28:i386{a} libgpg-error0:i386{a} libgphoto2-6:i386{a} libgphoto2-port10:i386{a} libgssapi-krb5-2:i386{a} 
  libgssapi3-heimdal:i386{a} libgstreamer-plugins-base0.10-0:i386{a} libgstreamer0.10-0:i386{a} libhcrypto4-heimdal:i386{a} 
  libheimbase1-heimdal:i386{a} libheimntlm0-heimdal:i386{a} libhogweed2:i386{a} libhx509-5-heimdal:i386{a} libice6:i386{a} 
  libicu52:i386{a} libieee1284-3:i386{a} libjack-jackd2-0:i386{a} libjbig0:i386{a} libjpeg-turbo8:i386{a} libjpeg8:i386{a} 
  libjson-c2:i386{a} libk5crypto3:i386{a} libkeyutils1:i386{a} libkrb5-26-heimdal:i386{a} libkrb5-3:i386{a} libkrb5support0:i386{a} 
  liblcms2-2:i386{a} libldap-2.4-2:i386{a} libllvm3.6:i386{a} libltdl7:i386{a} libmpg123-0:i386{a} libnettle4:i386{a} 
  libogg0:i386{a} libopenal1:i386{a} liborc-0.4-0:i386{a} libosmesa6:i386{a} libp11-kit-gnome-keyring:i386{a} libp11-kit0:i386{a} 
  libpciaccess0:i386{a} libpng12-0:i386{a} libpulse0:i386{a} libroken18-heimdal:i386{a} libsamplerate0:i386{a} libsane:i386{a} 
  libsasl2-2:i386{a} libsasl2-modules:i386{a} libsasl2-modules-db:i386{a} libsm6:i386{a} libsndfile1:i386{a} libspeexdsp1:i386{a} 
  libsqlite3-0:i386{a} libssl1.0.0:i386{a} libsystemd0:i386{a} libtasn1-6:i386{a} libtiff5:i386{a} libtxc-dxtn-s2tc0:i386{a} 
  libudev1:i386{a} libusb-1.0-0:i386{a} libv4l-0:i386{a} libv4lconvert0:i386{a} libvorbis0a:i386{a} libvorbisenc2:i386{a} 
  libvpx1:i386{a} libwind0-heimdal:i386{a} libwrap0:i386{a} libx11-6:i386{a} libx11-xcb1:i386{a} libxau6:i386{a} 
  libxcb-dri2-0:i386{a} libxcb-dri3-0:i386{a} libxcb-glx0:i386{a} libxcb-present0:i386{a} libxcb-sync1:i386{a} libxcb1:i386{a} 
  libxcomposite1:i386{a} libxcursor1:i386{a} libxdamage1:i386{a} libxdmcp6:i386{a} libxext6:i386{a} libxfixes3:i386{a} 
  libxi6:i386{a} libxinerama1:i386{a} libxml2:i386{a} libxpm4:i386{a} libxrandr2:i386{a} libxrender1:i386{a} libxshmfence1:i386{a} 
  libxslt1.1:i386{a} libxt6:i386{a} libxxf86vm1:i386{a} ocl-icd-libopencl1:i386{a} p11-kit-modules:i386{a} wine-gecko2.21{a} 
  wine-gecko2.21:i386{a} wine-mono0.0.8{a} wine1.6 wine1.6-amd64{a} wine1.6-i386:i386{a} 
0 packages upgraded, 132 newly installed, 0 to remove and 0 not upgraded.
Need to get 181 MB/181 MB of archives. After unpacking 605 MB will be used.
The following packages have unmet dependencies:
 libdrm-intel1 : Breaks: libdrm-intel1:i386 (!= 2.4.61+git1505070630.b23606~gd~t) but 2.4.60-2 is to be installed.
 libdrm-intel1:i386 : Breaks: libdrm-intel1 (!= 2.4.60-2) but 2.4.61+git1505070630.b23606~gd~t is installed.
 libdrm-radeon1 : Breaks: libdrm-radeon1:i386 (!= 2.4.61+git1505070630.b23606~gd~t) but 2.4.60-2 is to be installed.
 libdrm-radeon1:i386 : Breaks: libdrm-radeon1 (!= 2.4.60-2) but 2.4.61+git1505070630.b23606~gd~t is installed.
 libdrm-nouveau2 : Breaks: libdrm-nouveau2:i386 (!= 2.4.61+git1505070630.b23606~gd~t) but 2.4.60-2 is to be installed.
 libdrm-nouveau2:i386 : Breaks: libdrm-nouveau2 (!= 2.4.60-2) but 2.4.61+git1505070630.b23606~gd~t is installed.
 libdrm2 : Breaks: libdrm2:i386 (!= 2.4.61+git1505070630.b23606~gd~t) but 2.4.60-2 is to be installed.
 libdrm2:i386 : Breaks: libdrm2 (!= 2.4.60-2) but 2.4.61+git1505070630.b23606~gd~t is installed.
The following actions will resolve these dependencies:


      Keep the following packages at their current version:
1)      libdrm-intel1:i386 [Not Installed]                 
2)      libdrm-nouveau2:i386 [Not Installed]               
3)      libdrm-radeon1:i386 [Not Installed]                
4)      libdrm2:i386 [Not Installed]                       
5)      libgl1-mesa-dri:i386 [Not Installed]               
6)      libgl1-mesa-glx:i386 [Not Installed]               
7)      libglu1-mesa:i386 [Not Installed]                  
8)      wine1.6 [Not Installed]                            
9)      wine1.6-amd64 [Not Installed]                      
10)     wine1.6-i386:i386 [Not Installed]                  






Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.

```

---

### Post by mc4man on 2015-06-29
If this was me I' copy out any wanted files to a flash or other drive & do a fresh 14.04 install. (I've no great love for these interim 9 month releases such as 14.10 or 15.04 but's that's your choice there.
Otherwise I'd remove & then add back the oibaf ppa, update your sources & **simulate** a dist-upgrade to see what would happen

to try - 
```
sudo add-apt-repository -r ppa:oibaf/graphics-drivers
```
```
sudo add-apt-repository  ppa:oibaf/graphics-drivers
```
```
sudo apt-get update
```
```
sudo apt-get -s dist-upgrade
```
post the complete results of the simulated dist-upgrade

---

### Post by max-disselnmeyer on 2015-06-29
Well i think it is not necessary, after the 3. Command you posted i tried to install wine once again and now it is working, thank you guys so much! 

simulated dist upgrade says 0 upgraded... nothing interesting, however thank you guys so much!!! :D

---

### Post by matt_symes on 2015-06-29
Hi

mac4man's post above may well fix your problem if it will update your drm and Mesa packages to vivid.

It's a good call and well worth a try.

Try to make sure any PPAs you add in the future match the version of Ubuntu you have installed.

EDIT:

Excellent. I'm glad it's fixed. Please mark this thread as SOLVED for others in the future.

Kind regards

---

### Post by mc4man on 2015-06-29
The oibaf ppa uses not even close to standard package names so it really should be purged before doing an Ubuntu release upgrade. You can recover in most cases by re-adding it but better to get rid of *before* the release upgrade

---


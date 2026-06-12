---
title: "Unable to install wxWidgets library in Ubuntu 23.10"
date: 2024-01-25
forum: General Help
---

### Post by fckwan on 2024-01-25
When I run the following command in Ubuntu 23.10

$ sudo apt info libwxgtk-webview3.0-gtk3-devN: Unable to locate package libwxgtk-webview3.0-gtk3-dev
N: Couldn't find any package by glob 'libwxgtk-webview3.0-gtk3-dev'
N: Unable to locate package libwxgtk-webview3.0-gtk3-dev
N: Couldn't find any package by glob 'libwxgtk-webview3.0-gtk3-dev'
E: No packages found

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 23.10
Release:	23.10
Codename:	mantic



--------------------------------------------------------------------------------------------------

If I run the same command n Ubuntu 22.04 LTS. I can find the package

[COLOR=#000000][FONT=&quot] sudo apt info libwxgtk-webview3.0-gtk3-dev    [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Package: libwxgtk-webview3.0-gtk3-dev[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Version: 3.0.5.1+dfsg-4[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Priority: optional[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Section: universe/libdevel[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Source: wxwidgets3.0[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Origin: Ubuntu[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Original-Maintainer: wxWidgets Maintainers <team+wx@tracker.debian.org>[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Installed-Size: 143 kB[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Depends: wx-common, wx3.0-headers (= 3.0.5.1+dfsg-4), libwxgtk-webview3.0-gtk3-0v5 (= 3.0.5.1+dfsg-4), libwxgt[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]k3.0-gtk3-dev (= 3.0.5.1+dfsg-4)[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Suggests: wx3.0-doc, gettext[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Homepage: [https://www.wxwidgets.org/](https://www.wxwidgets.org/)[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Download-Size: 8,804 B[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]APT-Manual-Installed: yes[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]APT-Sources: [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) jammy/universe arm64 Packages[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Description: wxWidgets Cross-platform C++ GUI toolkit (GTK 3 webview library development)[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]wxWidgets (formerly known as wxWindows) is a class library for C++ providing[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]GUI components and other facilities on several popular platforms (and some[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]unpopular ones as well).[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot].[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]This package provides files needed to compile wxWidgets programs using the[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]wxWebView class.[/FONT][/COLOR]


[COLOR=#000000][FONT=&quot]$ lsb_release -a[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]No LSB modules are available.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Distributor ID: Ubuntu[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Description:    Ubuntu 22.04.3 LTS[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Release:        22.04[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Codename:       jammy[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]

---

### Post by tea for one on 2024-01-25
Is it this one (with a slightly different name)?
[https://packages.ubuntu.com/mantic/libs/libwxgtk-webview3.2-1](https://packages.ubuntu.com/mantic/libs/libwxgtk-webview3.2-1)

---

### Post by fckwan on 2024-01-25
I was tying to compile BOINC client 
During the process I need to configure the build process.
I got the error "No suitable wxWidgets library foound"

[https://boinc.berkeley.edu/dev/forum_thread.php?id=13933&postid=100664#100664](https://boinc.berkeley.edu/dev/forum_thread.php?id=13933&postid=100664#100664)

The above website recommend me to solve the problem by running.

sudo apt install libwxgtk-webview3.0-gtk3-dev

---

### Post by fckwan on 2024-01-25
[https://packages.ubuntu.com/jammy/libwxgtk-webview3.0-gtk3-dev](https://packages.ubuntu.com/jammy/libwxgtk-webview3.0-gtk3-dev)

Is the above package no longer supported after Ubuntu 22.04?

---

### Post by deadflowr on 2024-01-25
Looks like a new package is supported for newer releases.
Look at the package  libwxgtk-webview3.2-dev
[https://packages.ubuntu.com/mantic/libwxgtk-webview3.2-dev]("https://packages.ubuntu.com/mantic/libwxgtk-webview3.2-dev")
See if that one works.
Looks like it has the same stuff, only difference is the name.

---

### Post by fckwan on 2024-01-25
On Ubuntu 23.10 I already have this package 

sudo apt info libwxgtk-webview3.2-dev

Package: libwxgtk-webview3.2-dev
Version: 3.2.2+dfsg-4
Priority: optional
Section: universe/libdevel
Source: wxwidgets3.2
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: wxWidgets Maintainers <team+wx@tracker.debian.org>
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Installed-Size: 199 kB
Depends: libwxgtk-webview3.2-1 (= 3.2.2+dfsg-4), libwxgtk3.2-dev (= 3.2.2+dfsg-4), wx-common, wx3.2-headers (= 3.2.2+dfsg-4)
Suggests: gettext, wx3.2-doc
Homepage: [https://www.wxwidgets.org/](https://www.wxwidgets.org/)
Download-Size: 26.6 kB
APT-Sources: [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) mantic/universe arm64 Packages
Description: wxWidgets Cross-platform C++ GUI toolkit (GTK 3 webview library development)
 wxWidgets (formerly known as wxWindows) is a class library for C++ providing
 GUI components and other facilities on several popular platforms (and some
 unpopular ones as well).
 .
 This package provides files needed to compile wxWidgets programs using the
 wxWebView class.


But the BOINC confiuration is still giving eror message of "No suitable wxWidgets library found"

I think I will try to compile the BOINC Client in a Ubuntu 22.04 system to avoid this problem.

---


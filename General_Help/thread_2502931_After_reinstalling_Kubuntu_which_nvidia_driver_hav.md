---
title: "After reinstalling Kubuntu which nvidia driver have I to select?"
date: 2024-12-06
forum: General Help
---

### Post by nilovsergey on 2024-12-06
[COLOR=#000000]I reinstalled Kubuntu 22.04 and installing


nvidia driver I do not know which driver have I to select ?


I see :

[IMG]https://img001.prntscr.com/file/img001/tdWHEGdPQSqzWFs_eU825g.png[/IMG]






Usually I installed 525 (proprietary) - but I do not see in the listing and how to install nvidia driver ?


I have in my OS :
```

uname -a
Linux master-at-home 6.8.0-49-generic #49~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Wed Nov 6 17:42:15 UTC 2 x86_64 x86_64 x86_64 GNU/Linux


 dpkg -s nvidia-settings
Package: nvidia-settings
Status: install ok installed
Priority: optional
Section: contrib/x11
Installed-Size: 3012
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: amd64
Version: 510.47.03-0ubuntu1
Replaces: nvidia-settings-binary
Provides: nvidia-settings-binary
Depends: pkg-config, screen-resolution-extra (>= 0.18~), libvdpau1, libgtk-3-0 (>= 3.0.0) | libgtk2.0-0 (>= 2.14.0), libc6 (>= 2.34), libcairo2 (>= 1.2.4), libgdk-pixbuf-2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.33.14), libjansson4 (>= 2.3), libpango-1.0-0 (>= 1.14.0), libpangocairo-1.0-0 (>= 1.14.0), libx11-6, libxnvctrl0, libxxf86vm1
Conflicts: nvidia-settings-binary
Conffiles:
/etc/xdg/autostart/nvidia-settings-autostart.desktop 017c45e084f0cf1051baf9bf5db37d4c
Description: Tool for configuring the NVIDIA graphics driver
The nvidia-settings utility is a tool for configuring the NVIDIA
Linux graphics driver. It operates by communicating with the NVIDIA
X driver, querying and updating state as appropriate. This
communication is done with the NV-CONTROL X extension.
.
Values such as brightness and gamma, XVideo attributes, temperature,
and OpenGL settings can be queried and configured via nvidia-settings.
Original-Maintainer: Debian NVIDIA Maintainers <pkg-nvidia-devel@lists.alioth.debian.org>

```


I try next. After Running commands :


```
sudo apt-get update
sudo apt-get upgrade

```

I run with errors :


 ```
ubuntu-drivers install
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
dpkg-dev : Depends: libdpkg-perl (= 1.21.1ubuntu2) but 1.21.1ubuntu2.2 is to be installed
Recommends: build-essential but it is not going to be installed
Recommends: libalgorithm-merge-perl but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

That is fresh installation.


I try to install manually :

```

 dpkg -s libdpkg-perl
Package: libdpkg-perl
Status: install ok installed
Priority: optional
Section: perl
Installed-Size: 2340
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Multi-Arch: foreign
Source: dpkg
Version: 1.21.1ubuntu2.2
Depends: perl:any, dpkg (>= 1.18.11)
Recommends: libfile-fcntllock-perl, liblocale-gettext-perl, bzip2, xz-utils
Suggests: debian-keyring, gnupg, gpgv, gcc | c-compiler, binutils, patch, sensible-utils, git, bzr
Breaks: dgit (<< 3.13~), pkg-kde-tools (<< 0.15.28~)
Description: Dpkg perl modules
This package provides the perl modules used by the scripts
in dpkg-dev. They cover a wide range of functionality. Among them
there are the following public modules:
.
- Dpkg: core variables
- Dpkg::Arch: architecture handling functions
- Dpkg::Build::Info: build information functions
- Dpkg::BuildFlags: set, modify and query compilation build flags
- Dpkg::BuildOptions: parse and manipulate DEB_BUILD_OPTIONS
- Dpkg::BuildProfiles: parse and manipulate build profiles
- Dpkg::Changelog: parse changelogs
- Dpkg::Changelog::Entry: represents a changelog entry
- Dpkg::Changelog:****: generic changelog parser for dpkg-parsechangelog
- Dpkg::Checksums: generate and parse checksums
- Dpkg::Compression: simple database of available compression methods
- Dpkg::Compression::FileHandle: transparently (de)compress files
- Dpkg::Compression:rocess: wrapper around compression tools
- Dpkg::Conf: parse dpkg configuration files
- Dpkg::Control: parse and manipulate Debian control information
(.dsc, .changes, Packages/Sources entries, etc.)
- Dpkg::Control::Changelog: represent fields output by dpkg-parsechangelog
- Dpkg::Control::Fields: manage (list of known) control fields
- Dpkg::Control::Hash: parse and manipulate a block of RFC822-like fields
- Dpkg::Control::Info: parse files like debian/control
- Dpkg::Control::Tests: parse files like debian/tests/control
- Dpkg::Control::Tests::Entry: represents a debian/tests/control stanza
- Dpkg:eps: parse and manipulate dependencies
- Dpkg:eps::Simple: represents a single dependency statement
- Dpkg:eps::Multiple: base module to represent multiple dependencies
- Dpkg:eps::Union: list of unrelated dependencies
- Dpkg:eps::AND: list of AND dependencies
- Dpkg:eps::OR: list of OR dependencies
- Dpkg:eps::KnownFacts: list of installed and virtual packages
- Dpkg::Exit: push, pop and run exit handlers
- Dpkg::Gettext: wrapper around Locale::gettext
- Dpkg::IPC: spawn sub-processes and feed/retrieve data
- Dpkg::Index: collections of Dpkg::Control (Packages/Sources files for
example)
- Dpkg::Interface::Storable: base object serializer
- Dpkg:ath: common path handling functions
- Dpkg::Source::Format: manipulate debian/source/format files
- Dpkg::Source:ackage: extract Debian source packages
- Dpkg::Substvars: substitute variables in strings
- Dpkg::Vendor: identify current distribution vendor
- Dpkg::Version: parse and manipulate Debian package versions
.
All the packages listed in Suggests or Recommends are used by some of the
modules.
Homepage: [https://wiki.debian.org/Teams/Dpkg](https://wiki.debian.org/Teams/Dpkg)
Original-Maintainer: Dpkg Developers <debian-dpkg@lists.debian.org>

```

How to fix this issue ?


PS. I have installed PHP 8.2 as I work with it. Could it be the reason that some packages are of lower verions ?
[/COLOR]

---

### Post by TheFu on 2024-12-06
The proprietary nvidia driver to install would depend on the kernel and exact GPU model you have.

If you install any non-standard tools, like a different version of perl or python, you need to use a version management system for those specific tools.  I use **perlbrew** to keep my desired perl versions and all modules separate from the OS version of perl. Allowing them to mix leads to problems.  I'd expect the same for php, python, ruby. They all have version managers to keep them separate from the OS versions.  Use one for each scripting language, if you can't use the system version.

I'm not a php guy, so I know nothing about it, except that whenever I install a webapp dependent on php, I ensure it is completely separate from everything else either by using a linux container or a VM just for that need.  If php v8.2 isn't the normal installed version on your OS release, you'll want to re-think how you installed it, I'd bet.

About 10 yrs ago, I tried to keep 2 php-based webapps working well inside the same VM. This failed terribly and I ended up moving 1 of them out to a different VM over dependency differences.  Perhaps if I knew more about php, I'd have figured out how to make them co-exist, but creating a linux container for each is really easy these days and has about 10x less overhead than running a single VM.  You may have heard of Docker.  That's an "app linux container."  I use lxc, which is an "OS linux container."   LXC feels almost like a VM, but without the overhead and without the ability to use some kernel modules unless we allow the container to be run "privileged".  In my mind, allowing privileged container defeats 90% of the security that linux containers provide, so I won't to it. In lxc, non-privileged containers are the default.  I don't know about Docker, but I do know that privileged containers was the default for far too long in Docker.  Running docker and lxc on the same OS is difficult, not recommended. They conflict.  Of course, we can setup a VM for lxc containers and a different VM for docker containers;  that should work fine.  Also, Linux containers don't need VT-x CPU support, so even the smallest raspberry pi can run a Linux container. It is all kernel code and most of the require features for Linux Containers was added in the 2.6.x time - long, long, long, ago.  We're on 6.x kernels now.

Anyway, the days of running 10-50 services on the same OS install are long gone.  Where I worked stopped doing that around 2002, so definitely look into containers or VMs for your different dependency requirements. It will make support much easier.

---


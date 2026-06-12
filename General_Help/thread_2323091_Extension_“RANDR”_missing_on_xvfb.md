---
title: "Extension “RANDR” missing on xvfb"
date: 2016-05-02
forum: General Help
---

### Post by kekit on 2016-05-02
**Ubuntu:**

```
$lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:        14.04
Codename:       trusty
```

**Xvfb:**

```
$ dpkg -s xvfb
Package: xvfb
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 2140
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: foreign
Source: xorg-server
Version: 2:1.15.1-0ubuntu2.7
Provides: xserver
```

**Current problem:**

Xvfb do not support RANDR extension, even if I add the flag:

```
+extension RANDR
```

If I run xdpyinfo, RANDR is not on the list. It's a missing feature or a bug. I found a reference here with a patch: [https://bugzilla.novell.com/show_bug.cgi?id=823410](https://bugzilla.novell.com/show_bug.cgi?id=823410)

And looks like that in other distros like debian, there is already a testing build of Xvfb with support: [http://unix.stackexchange.com/questions/205509/running-firefox-in-xvfb-extension-randr-missing-on-display](http://unix.stackexchange.com/questions/205509/running-firefox-in-xvfb-extension-randr-missing-on-display)

I am trying to run a program throught Xvfb, and it returns the following error:

```
Xlib:  extension "RANDR" missing on display ":99".
```

The program works if I run it via ssh/command line. The problem appears to be the the lack of support for "RANDR" in xvfb.

**My question is:** what is the easiest way to get xvfb with "RANDR" support in my system?

---


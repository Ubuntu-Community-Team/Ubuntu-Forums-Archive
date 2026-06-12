---
title: "Problem in wrapper-2.0"
date: 2023-03-25
forum: General Help
---

### Post by him610 on 2023-03-25
Received a dialogue box with this heading, Problem in wrapper-2.0

[https://imgur.com/Qxbw8mR.png]("https://imgur.com/Qxbw8mR.png")

Checked to see if it is installed....
```
$ apt show wrapper-2.0
N: Unable to locate package wrapper-2.0
N: Couldn't find any package by glob 'wrapper-2.0'
N: Unable to locate package wrapper-2.0
N: Couldn't find any package by glob 'wrapper-2.0'
E: No packages found

```

Current release info....
```
$ Uld
Linux h270m 5.19.0-35-generic #36~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Fri Feb 17 15:17:25 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.2 LTS
Release:	22.04
Codename:	jammy
XFCE

```

System memory....
```
~$ free -hm
               total        used        free      shared  buff/cache   available
Mem:           7.7Gi       2.1Gi       1.6Gi        88Mi       4.0Gi       5.3Gi
Swap:          2.0Gi       764Mi       1.3Gi

```

What is going on here? 
Should I be concerned?

---

### Post by Holger_Gehrke on 2023-03-25
Try 'dpgk -S $(locate wrapper-2.0)'. It's part of libxfce4panel-2.0-4.

Holger

---

### Post by him610 on 2023-03-25
Holger, thanks for the rapid response. Here are my results...
```

hugh@h270m:~$ dpkg -S $(locate wrapper-2.0)
libxfce4panel-2.0-4: /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-2.0
dpkg-query: no path found matching pattern /var/crash/_usr_lib_x86_64-linux-gnu_xfce4_panel_wrapper-2.0.1000.crash

```
The dialogue box said there was "...not enough memory to analyze the problem and send a report to the developers"
So is this a reportible discrepancy?

---

### Post by Holger_Gehrke on 2023-03-25
I might be misunderstanding the role of this wrapper, but a look at 'ps ax|grep [w]rapper' is quite suggestive. It looks like it's an executable used to start plugins to the panel which are themselves libraries and can therefore not be started by themselves. The problem is in my opinion more likely to be with the plugin than with the wrapper.

Holger

---

### Post by MAFoElffen on 2023-03-25
@Holger_Genrke --
I think you are right in that it helps run other things... From the description...
```

mafoelffen@Mikes-ThinkPad-T520:~$ apt-cache show wrapper*
Package: wrapperfactory.app
Architecture: amd64
Version: 0.1.0-5build4
Priority: optional
Section: universe/x11
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNUstep maintainers <pkg-gnustep-maintainers@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 436
Depends: gnustep-back0.29 (>= 0.29.0), gnustep-base-runtime (>= 1.28.0), gnustep-gui-runtime (>= 0.29.0), libc6 (>= 2.34), libgcc-s1 (>= 3.0), libgnustep-base1.28 (>= 1.28.0), libgnustep-gui0.29 (>= 0.29.0), libobjc4 (>= 4.2.1)
Recommends: gworkspace.app
Filename: pool/universe/w/wrapperfactory.app/wrapperfactory.app_0.1.0-5build4_amd64.deb
Size: 85444
MD5sum: a959e0c20eb6ebdbb1e8ef53ba4a9abb
SHA1: d9fb7d9bf54d4c4d8993f66306348e82bfc5471e
SHA256: d14ee20cd4f4dbd80c4f54dd9788f2863fb5722c9f1a772aa588433df6eb720b
SHA512: 01d997ee64c800666b7d67feb3cbac4fc9c14cd247ae75855885481557be7c3d048fd2d7c753fd67975b7070f347282ef72badd49b5ff728dd97ae07aa182ea8
[COLOR=#ff0000]Description-en: Application wrappers configuration tool for GNUstep
 This provides an easy way to create GNUstep app-wrappers of non-GNUstep
 applications. It is the most useful in conjunction with GWorkspace
 environment.[/COLOR]
Description-md5: 079236d1cd161860774967e9a6ee5394

```
Which, to me says that it might be a problem with whatever application it was trying to run at the time(?)

---

### Post by Holger_Gehrke on 2023-03-25
Sorry, MAFoElffen, but the wrapperfactory.app is for GnuStep, completely different thing. The wrapper-2.0 we're talking about is part of XFCE and is packaged in libxfce4panel-2.0.4.

On a XFCE4 desktop with several panel plugins you usually have multiple instances of wrapper-2.0 running; an example of the command running it (taken from 'ps ax|grep [w]rapper') looks like
```

/usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-2.0 /usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/libxkb.so 20 23068681 xkb Tastaturbelegung Erweiterung zum Einstellen und Umschalten der Tastaturbelegung

```
The first parameter is a shared object file with a plugin for the XFCE panel, the second is probably some kind of numerical identifier / handle, the third parameter is a window id (did an 'xwininfo -children' on my main panel to verify that one ...), the rest are three strings (two of one word each, the rest of the line only makes sense if its reassembled into one "thing" (a descriptive text for the plugin)).

Holger

---

### Post by MAFoElffen on 2023-03-26
Sorry. My mistake. I don't work much with XFCE...

---


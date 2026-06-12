---
title: "A question about GLIBC_2.3.4"
date: 2005-10-28
forum: General Help
---

### Post by PatrickMay16 on 2005-10-28
Hello, my friends.

Recently, I've been using the new version of wine, 0.9. Though I've noticed when a program running in wine crashes, and wine tries to start the wine debugger, it does this:
> 
err:module:load_builtin_dll failed to load .so lib for builtin L"dbghelp.dll": /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.3.4' not found (required by /usr/lib/wine/dbghelp.dll.so)
err:module:import_dll Loading library dbghelp.dll (which is needed by L"c:\\windows\\system32\\winedbg.exe") failed (error c000007a).
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\winedbg.exe" failed, status c0000135

I guess this is because I don't have the required version of GLIBC to run the wine debugger. Apart from the wine debugger not working, wine seems to work fine. Though it'd be nice to have the wine debugger work anyway, because since it doesn't run, instead of the crashed application's window vanishing, it just sits there all frozen up, and I need to click on it for a while to get the "force quit?" window to appear. A bit less convienient. 

I looked for libc using synaptic, but I found that the most recent version available for Hoary was 2.3.2 or something. Then, I found this.
[http://packages.debian.org/testing/libs/libc6](http://packages.debian.org/testing/libs/libc6)
Would it be safe to download the deb package from there and install that, or would I risk breaking things by doing that? If that's dangerous, is there a safer way of installing this required version of GLIBC?
Or, would it be just a good idea to put up with the wine debugger not working?

Thanks in advance.

---

### Post by Alexander Kirillov on 2005-10-28
[QUOTE=PatrickMay16]Hello, my friends.

Recently, I've been using the new version of wine, 0.9. Though I've noticed when a program running in wine crashes, and wine tries to start the wine debugger, it does this:

I guess this is because I don't have the required version of GLIBC to run the wine debugger. Apart from the wine debugger not working, wine seems to work fine. Though it'd be nice to have the wine debugger work anyway, because since it doesn't run, instead of the crashed application's window vanishing, it just sits there all frozen up, and I need to click on it for a while to get the "force quit?" window to appear. A bit less convienient. 

I looked for libc using synaptic, but I found that the most recent version available for Hoary was 2.3.2 or something. Then, I found this.
[http://packages.debian.org/testing/libs/libc6](http://packages.debian.org/testing/libs/libc6)
Would it be safe to download the deb package from there and install that, or would I risk breaking things by doing that? If that's dangerous, is there a safer way of installing this required version of GLIBC?
Or, would it be just a good idea to put up with the wine debugger not working?

Thanks in advance.[/QUOTE]


My 2 cents: don't do it. glibc is one of the key packages - everything depends on it. In theory, they should be backwards compatible - everything complied for 2.3.2 should work for 2.3.4 as well - but still,  risking messing your system just for the benefit of debugger is not worth it, IMHO.

By the way: can it be that the wine problem is caused by using wine complied for a differetn glibc (or with a differetn version of gcc) than the one you have on your system?

---

### Post by PatrickMay16 on 2005-10-28
Thanks very much for replying.

[QUOTE=Alexander Kirillov]My 2 cents: don't do it. glibc is one of the key packages - everything depends on it. In theory, they should be backwards compatible - everything complied for 2.3.2 should work for 2.3.4 as well - but still,  risking messing your system just for the benefit of debugger is not worth it, IMHO.

By the way: can it be that the wine problem is caused by using wine complied for a differetn glibc (or with a differetn version of gcc) than the one you have on your system?[/QUOTE]
Hmm... Maybe it could. Here's the version information gcc gives:
> 
patrick@ubuntu:~$ gcc --version
gcc (GCC) 3.3.5 (Debian 1:3.3.5-8ubuntu2)
Copyright (C) 2003 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

patrick@ubuntu:~$ 

Though I'm not sure what version of gcc wine 0.9 was compiled with.

And to get wine to work at all, I needed to install the package libstdc++6 or it would complain about not being able to find libstdc++.so.6.

---

### Post by PatrickMay16 on 2005-11-03
OK, since then, I've decided that maybe compiling wine from source would fix that problem. Though there's a problem with that, too.
> 
patrick@ubuntu:~$ sudo apt-get build-dep wine
Password:
Reading package lists... Done
Building dependency tree... Done
[b]The following packages will be REMOVED:
  ubuntu-desktop x-window-system-core xlibmesa-dri xlibmesa-gl xlibmesa-gl-dev
  xlibmesa-glu[/b]
The following NEW packages will be installed:
  bison docbook-to-man docbook-utils docbook-xsl flex fontforge jadetex
  libarts1-dev libartsc0-dev libasound2-dev libaudio-dev libaudiofile-dev
  libcapi20-2 libcapi20-dev libcupsys2-dev libesd0-dev libgcrypt11-dev
  libglu1-mesa libglu1-mesa-dev libgnutls11-dev libgpg-error-dev libicu28
  libicu28-dev libjack0.80.0-dev libjpeg-mmx-dev libjpeg62-dev libkpathsea3
  liblcms1-dev libmng-dev libopencdk8-dev libpng12-dev libqt3-headers
  libqt3-mt-dev libsgmls-perl libsp1 libtasn1-2-dev libungif4-dev libwww-ssl0
  libxcursor-dev libxinerama-dev mesa-common-dev mesag-dev mesag3
  qt3-dev-tools sgmlspl sp tetex-base tetex-bin tetex-extra texinfo
0 upgraded, 50 newly installed, 6 to remove and 0 not upgraded.
Need to get 54.4MB/54.5MB of archives.
After unpacking 168MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
patrick@ubuntu:~$


It threatens to remove a load of important packages. 
Does anyone know what's going on with this?

---


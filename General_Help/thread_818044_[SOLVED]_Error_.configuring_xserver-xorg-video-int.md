---
title: "[SOLVED] Error ./configuring xserver-xorg-video-intel source"
date: 2008-06-04
forum: General Help
---

### Post by Zorael on 2008-06-04
So I thought I'd compile the latest xserver-xorg-video-intel driver from the source available through the repositories, after patching it to enable the correct XV attribute setting. Without it patched, I get [horribly oversaturated and over-contrasted image](http://pusscats.net/totemvideobug.jpg) when playing video files with the Xv output plugin. And I figured I might well learn something from doing this.

The patch can be found here: [http://linux.pengin.de/#xvattr](http://linux.pengin.de/#xvattr).

So I downloaded it, went to a suitable directory with write permissions and got to work.
```
$ apt-get source xserver-xorg-video-intel
*<apt doing its thing>*

$ patch -p0 < intel_xv_attr.diff
patching file xserver-xorg-video-intel-2.2.1/src/i830_video.c

$ cd xserver-xorg-video-intel-2.2.1
$ ./configure
*<furious wall of text, ending with the following:>*
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for XORG... configure: error: Package requirements (xorg-server xproto xvmc fontsproto ) were not met:

No package 'xorg-server' found
No package 'xvmc' found
No package 'fontsproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```
These packages do not exist in the repositories.
```
$ apt-cache policy xorg-server xproto xvmc fontsproto
W: Unable to locate package xorg-server
W: Unable to locate package xproto
W: Unable to locate package xvmc
W: Unable to locate package fontsproto
```

I'm confused. What should I do?

---

### Post by Zorael on 2008-06-04
Nevermind. Turns out that there's a **build-dep** argument to use with apt-get.

---


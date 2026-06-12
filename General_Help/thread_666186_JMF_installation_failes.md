---
title: "JMF installation failes"
date: 2008-01-13
forum: General Help
---

### Post by DaVinciXL on 2008-01-13
After using OpenOffice for a couple of years for doing my presentations, I now have to do a presentation which includes sounds for the first time and was shocked to see, that this seems not to be supported "out of the box".

So I've been trying to install this friggin' JMF thing for almost eight hours straight - with hardly any success.
The most annoying thing is that I'm getting stuck right at the beginning over and over again - without any idea what to do, without finding any solution on the web.

Well... I downloaded the JMF-Package from the official site.
Then did a "chmod u+x <packagename>.bin", followed by a "./<packagename>.bin" (i also tried to add a "sudo" infront of that command.

This, however, results in:

> 
Unpacking...
tail: Warning: "+number" syntax is deprecated, please use "-n +number"
Extracting...
UnZipSFX 5.40 of 28 November 1998, by Info-ZIP (Zip-Bugs@lists.wku.edu).
   creating: JMF-2.1.1e/
   creating: JMF-2.1.1e/bin/
  inflating: JMF-2.1.1e/bin/jmfinit
  inflating: JMF-2.1.1e/bin/jmfregistry
  inflating: JMF-2.1.1e/bin/jmstudio
   creating: JMF-2.1.1e/doc/
  inflating: JMF-2.1.1e/doc/attributions.html
  inflating: JMF-2.1.1e/doc/formats.html
  inflating: JMF-2.1.1e/doc/readme.html
   creating: JMF-2.1.1e/lib/
  inflating: JMF-2.1.1e/lib/libjmcvid.so
  inflating: JMF-2.1.1e/lib/libjmdaud.so
  inflating: JMF-2.1.1e/lib/libjmfjawt.so
  inflating: JMF-2.1.1e/lib/libjmg723.so
  inflating: JMF-2.1.1e/lib/libjmgsm.so
  inflating: JMF-2.1.1e/lib/libjmh261.so
  inflating: JMF-2.1.1e/lib/libjmh263enc.so
  inflating: JMF-2.1.1e/lib/libjmjpeg.so
  inflating: JMF-2.1.1e/lib/libjmmpa.so
  inflating: JMF-2.1.1e/lib/libjmmpegv.so
  inflating: JMF-2.1.1e/lib/libjmmpx.so
  inflating: JMF-2.1.1e/lib/libjmutil.so
  inflating: JMF-2.1.1e/lib/libjmv4l.so
  inflating: JMF-2.1.1e/lib/libjmxlib.so
  inflating: JMF-2.1.1e/lib/jmf.properties
  inflating: JMF-2.1.1e/lib/jmf.jar
  inflating: JMF-2.1.1e/lib/mediaplayer.jar
  inflating: JMF-2.1.1e/lib/multiplayer.jar
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb3931767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb39318b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xaad8429d]
#3 /usr/lib/j2se/1.4/jre/lib/i386/libawt.so(XineramaQueryScreens+0xc5) [0xab214925]
java: xcb_xlib.c:82: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.
Aborted (core dumped)
Done.


I really need help here. I don't want to get to install Windows all over again for this one presentation. I'd even be willing to use KPresenter - but I didn't find any way to embed sounds there either. :(

---


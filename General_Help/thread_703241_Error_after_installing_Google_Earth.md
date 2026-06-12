---
title: "Error after installing Google Earth"
date: 2008-02-21
forum: General Help
---

### Post by TRANQU111TY on 2008-02-21
I double clicked on the bin and this comes up in terminal:
```
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.2.205.5730..............................................................
Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...
Xlib:  extension "XFree86-DRI" missing on display ":1.0".

```
The Google Earth Splash screen has frozen. What do I do?

Thanks

---

### Post by meho_r on 2008-02-21
Try here: [http://ubuntuforums.org/showthread.php?t=520952&highlight=googleearth](http://ubuntuforums.org/showthread.php?t=520952&highlight=googleearth)

Kilz posted a file, libGL.tar.gz which solved this problem for many (including me;))

---

### Post by TRANQU111TY on 2008-02-21
Thanks but I have run into a really simple problem when I try to copy those files into the googleearth dir:
```
Error while copying to "/opt/google-earth".
You do not have permissions to write to this folder.
```

---

### Post by meho_r on 2008-02-21
You mean files from libGL.tar.gz?

Try running Nautilus with root privileges and then copy/paste files. 

Press Alt+F2 and type: gksudo nautilus

Or, if using Terminal, try "sudo cp" command instead of "cp" alone

---

### Post by TRANQU111TY on 2008-02-22
Fantastic thank you :)

Now when I'm scrolling the globe, I get some graphic corruption on my side menus.

I'm not sure if this will help but this is what comes up in terminal after starting GoogleEarth:
```
j@j-desktop:~$ googleearth
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
Google Earth has caught signal 11.

Stacktrace from glibc:
  ./googleearth-bin(__gxx_personality_v0+0x1e8) [0x8057fb4]
  ./googleearth-bin [0x8058399]
  [0xffffe420]
  ./libbase.so(_ZN5earth8SpinLock4lockEj+0x22) [0xb7ea93fc]
  ./libbase.so(_ZN5earth9LockGuardC1ERNS_8SpinLockE+0x1f) [0xb7e8f27f]
  ./libnet.so(_ZN5earth3net18CurlHttpConnection13removeRequestEPNS0_15CurlHttpRequestE+0x25) [0xb7a2c45b]
  ./libnet.so(_ZN5earth3net15CurlHttpRequest4stopEv+0x20) [0xb7a2c4aa]
  ./libnet.so(_ZN5earth3net15CurlHttpRequestD0Ev+0x25) [0xb7a2c4d7]
  ./libnet.so(_ZN5earth3net11HttpRequest5unrefEv+0x35) [0xb7a24701]
  ./libnet.so(_ZN5earth6RefPtrINS_3net11HttpRequestEED1Ev+0x1e) [0xb7a1b9c2]
  ./libnet.so(_ZN5earth3net14NetworkRequestD0Ev+0x28) [0xb7a1ca70]
  ./libbase.so(_ZN5earth8Referent8orphanedEv+0x10) [0xb7e844fe]
  ./libbase.so(_ZN5earth8Referent5unrefEv+0x17) [0xb7eab1d5]
  ./libnet.so(_ZN5earth3net7FetcherD0Ev+0x42) [0xb7a20332]
  ./libbase.so(_ZN5earth8Referent8orphanedEv+0x10) [0xb7e844fe]
  ./libbase.so(_ZN5earth8Referent5unrefEv+0x17) [0xb7eab1d5]
  ./libwmsbase.so(_ZN5earth6RefPtrINS_3net7FetcherEED1Ev+0x1e) [0xb7a7e0ba]
  ./libcommon.so(_ZN5earth6common10HtmlRenderD0Ev+0x52) [0xb62eec46]
  ./libgoogleearth.so(_ZN10scoped_ptrIN5earth6common10HtmlRenderEED1Ev+0x12) [0xb7623b56]
  ./libgoogleearth.so(_ZN16StartupTipWidgetD0Ev+0x73) [0xb7622ca1]
  ./libgoogleearth.so(_ZN10scoped_ptrI16StartupTipWidgetE5resetEPS0_+0x1b) [0xb762cea5]
  ./libgoogleearth.so(_ZN5earth6client11ApplicationD1Ev+0x60) [0xb7627a48]
  ./googleearth-bin(main+0x155) [0x805884d]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb5fcf050]
  ./googleearth-bin(__gxx_personality_v0+0x75) [0x8057e41]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/j/.googleearth/crashlogs/crashlog-FE05C3A2.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.
```

Thanks

---


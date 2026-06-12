---
title: "[SOLVED] Google Earth short lived"
date: 2008-03-22
forum: General Help
---

### Post by neilg4rqn on 2008-03-22
Hi, I installed the new (linux version) of Google Earth and all appeared well until I clicked on the conducted tour. GE went to two locations in London and then dropped out. I have attempted to re-run it but it gets as far as 70% or so streaming and then drops out. (drops out = stops running and appears as if I had closed the application).
I have un-installed it and re-installed but now the problem remains where it gets to about 70% or so streamed and then drops out - closes down call it what you will.
I am running 7.1 with a Nvidia card bags of ram etc.  and the machine is otherwise OK.
Thanks for your time
Neil

---

### Post by kellemes on 2008-03-22
Run "googleearth" from the terminal, now see what the output is (if any) when this issue occurs.

---

### Post by neilg4rqn on 2008-03-22
Ah, thanks for that I have tried it from the command line and now I know at least it is not my fault. I have included the GE response for completeness, hope that's ok Should I now mark this 'solved'?

Neil

neil@neil-ubuntu:~$ googleearth
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
  /opt/google-earth/libevll.so(_ZN5earth4evll10StreamTile19internalGetMipLevelEiib+0x6e) [0xb2d62cae]
  /opt/google-earth/libevll.so(_ZN5earth4evll10StreamTile11getMipLevelEii+0x1f) [0xb2d6397f]
  /opt/google-earth/libevll.so(_ZN5earth4evll9ImageTile13requestLevelsEbbi+0x56) [0xb2d67a80]
  /opt/google-earth/libevll.so(_ZN5earth4evll9ImageTile7requestERNS0_7TileTexEbi+0x4c) [0xb2d67b80]
  /opt/google-earth/libevll.so(_ZN5earth4evll6UniTex10getTileTexEibRKNS_4Vec2IiEEiRb+0x16e) [0xb2d67ef6]
  /opt/google-earth/libevll.so(_ZN5earth4evll6UniTex17processTexRequestERNS0_10TexRequestEiNS_4RectIdNS_5Vec2dEEEb+0x86) [0xb2d67f8a]
  /opt/google-earth/libevll.so(_ZN5earth4evll6UniTex18processTexRequestsEi+0x297) [0xb2d68285]
  /opt/google-earth/libevll.so(_ZN5earth4evll14TerrainManager13prepareUniTexERNS0_6UniTexEii+0x14c) [0xb2d22b62]
  /opt/google-earth/libevll.so(_ZN5earth4evll14TerrainManager11drawTerrainEPNS0_6UniTexEfii+0x60) [0xb2d24ae6]
  /opt/google-earth/libevll.so(_ZN5earth4evll12SideDatabase14DrawTerrainAllERKNS0_6ViewerERNS0_12MainDatabaseEi+0x1bc) [0xb2c8c266]
  /opt/google-earth/libevll.so(_ZN5earth4evll12MainDatabase11drawTerrainERKNS0_6ViewerE+0x61) [0xb2c5db7b]
  /opt/google-earth/libevll.so(_ZN5earth4evll13VisualContext6renderEb+0x801) [0xb2d513ed]
  /opt/google-earth/libevll.so(_ZN5earth4evll13VisualContext4drawEbb+0xa1) [0xb2d519e7]
  /opt/google-earth/libevll.so(_ZN5earth4evll17RenderContextImpl4drawEv+0xa1) [0xb2d0bb51]
  ./librender.so(_ZN12RenderWidget10paintEventEP11QPaintEvent+0x24) [0xb627f7d0]
  ./librender.so(_ZN5earth6render11RenderTimer4fireEv+0x14) [0xb626c60c]
  ./libbase.so(_ZN5earth5Timer10timerEventEP11QTimerEvent+0x31) [0xb7ee69bb]
  ./libqt-mt.so.3(_ZN7QObject5eventEP6QEvent+0x82) [0xb6d5afc2]
  ./libqt-mt.so.3(_ZN12QApplication14internalNotifyEP7QObjectP6QEvent+0xa1) [0xb6cef9a1]
  ./libqt-mt.so.3(_ZN12QApplication6notifyEP7QObjectP6QEvent+0xef) [0xb6cf04af]
  ./libqt-mt.so.3(_ZN10QEventLoop14activateTimersEv+0x1ed) [0xb6ce343d]
  ./libqt-mt.so.3(_ZN10QEventLoop13processEventsEj+0x57b) [0xb6c9524b]
  ./libqt-mt.so.3(_ZN10QEventLoop9enterLoopEv+0xa9) [0xb6d094e9]
  ./libqt-mt.so.3(_ZN10QEventLoop4execEv+0x26) [0xb6d093e6]
  ./libqt-mt.so.3(_ZN12QApplication4execEv+0x1f) [0xb6cef39f]
  ./libgoogleearth.so(_ZN5earth6client11Application3runEv+0x24f) [0xb768e821]
  ./googleearth-bin(main+0x11f) [0x8058817]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb602d050]
  ./googleearth-bin(__gxx_personality_v0+0x75) [0x8057e41]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/neil/.googleearth/crashlogs/crashlog-EE67A372.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.

---

### Post by neilg4rqn on 2008-03-23
It lasts a bit longer if it doesn't open the splash screen but then bombs out when zooming into the globe.

---

### Post by kellemes on 2008-03-23
The crash log looks like Chinese to me ;-)

What version of GE do you use?
The version I use is 4.2.0205.5730 and the tour seems to be fine..
How did you install? Using the Multiverse repository?

---

### Post by neilg4rqn on 2008-03-23
What I have downloaded is "Google Earth for GNU/Linux 4.2.205.5730" from [http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html) -but- possibly I should have paid a little more atention to the line on that page that reads "Download Google Earth 4.2 (beta) for PC, Mac or Linux", yep it's a beta!

I am now looking at [http://groups.google.com/group/earth-linux/topics?start=10&sa=N](http://groups.google.com/group/earth-linux/topics?start=10&sa=N) which at a glance appears interesting. More postings when I have something useful, LOL.

Thanks for your comments so far.

Neil

---

### Post by kellemes on 2008-03-23
Yes, keep us posted..
You can always use the standard repository if Beta doesn't work..
[http://packages.ubuntu.com/gutsy/googleearth-package]("http://packages.ubuntu.com/gutsy/googleearth-package")

---

### Post by neilg4rqn on 2008-03-23
I have tried uninstalling GE by clicking on the uninstall icon in (I think it was) usr/lib but although it all dissapeared I have just found that I could still run it as it was installed in a directory called "opt". I have now uninstalled it from there also and will now try to reinstall using synaptic which offers the version you are using. If thet fails then its back to the old version.
Neil

---

### Post by neilg4rqn on 2008-03-23
| Just tried the 4.2.0205.5730 via synaptic and the result is the same (bombs out when zooming into the globe) so I am going to sit on it for a while and see if any updates come along. More as it happens.
Neil

---

### Post by unutbu on 2008-03-23
> I installed the new (linux version) of Google Earth and all appeared well until I clicked on the conducted tour. 

Where is the conducted tour?
I'm running ver. 4.2.0205.5730

---

### Post by oldos2er on 2008-03-23
Tour is under the Tools menu.

---

### Post by neilg4rqn on 2008-03-23
Hi, sorry I called it conducted tour as I couldn't get back in to check my memory. I have run GE on my windowz box and it's called "sightseeing". Can't get the ubuntu GE to run long enough to get to that anymore.

---

### Post by kellemes on 2008-03-23
Another thought..
Have you tried tweaking the settings under Tools -> Options -> Touring?
Maybe a little slower or something?
As a reference.. My settings are..
Fly-To Speed = 0.1710
Tour Speed = 0.1710
Can't imagine the other settings are relevant.

---

### Post by neilg4rqn on 2008-03-23
I would love to be able to tweak GE but it doesn't last that long. It starts, displays the globe which rotates to show europe, begins to zoom ind stops. No time to select anything.

---

### Post by tgalati4 on 2008-03-23
How much video RAM do you have?  Perhaps it runs out of video RAM then crashes badly.  Try lowering your resolution to something really low like 800 by 600 and see if it runs better.  What kind of graphics card?

---

### Post by neilg4rqn on 2008-03-24
Hi tgalati4. I will try it at a lower resolution later but for the moment the answers to your questions on my setup.
How much video RAM do you have? 256 
What kind of graphics card?              GEForce 7300gs
Processor is			                   Intel 3 Gig dual core
RAM				                      4 Gig
Ta
Neil

---

### Post by neilg4rqn on 2008-03-26
GE will not run below 1024*768. Tried that - no better.

---

### Post by neilg4rqn on 2008-04-19
I had more or less given up on GE and juat happened to try it. Surprise it is OK (so far), and it's still  showing version 4.2.0205.5730
:confused:

cheers all

Neil

---

### Post by El Viejo Lobo on 2008-06-22
I installed GE v 4.3 on Ubuntu 8.04 and it did not worked it zoomed like crazy so I went back to v 4.2  and it is working only by terminal and crashes leaving me in the terminal this attached screenshot telling me about a bug......  any news about it?

---


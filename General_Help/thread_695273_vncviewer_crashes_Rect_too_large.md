---
title: "vncviewer crashes: Rect too large"
date: 2008-02-12
forum: General Help
---

### Post by phillfri on 2008-02-12
Error Message: "vncviewer Rect too large: 62976x512 at (0, 1294)"

Trying to use vncviewer 3.3.7-14 to remote into a local PCLinuxOS MiniMe 2008 server machine. Workstation has 22" monitor at 1280x1024. Server is headless, but set up for 15" monitor at 1024x768. Anyone have any ideas how to fix this?

TERMINAL OUTPUT:
phillfri@Study:~$ vncviewer
VNC viewer version 3.3.7 - built May 24 2007 12:45:44
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.3 (viewer 3.3)
No authentication needed
Desktop name "phillfri@dhcppc2 (shared desktop)"
Connected to VNC server, using protocol version 3.3
VNC server default format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Using default colormap and visual, TrueColor, depth 24.
Got 256 exact BGR233 colours out of 256
Using BGR233 pixel format:
  8 bits per pixel.
  True colour: max red 7 green 7 blue 3, shift red 0 green 3 blue 6
Using shared memory PutImage
Throughput 6258 kbit/s - changing from 8bit
Using viewer's native pixel format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Rect too large: 62976x512 at (0, 1294)
ShmCleanup called

---

### Post by phillfri on 2008-02-13
xtightvncviewer works - same issue and same messages, but tight bypassess a 0 screen size result according to its ouput, whereas that bypass message does not show up with vncviewer.

---


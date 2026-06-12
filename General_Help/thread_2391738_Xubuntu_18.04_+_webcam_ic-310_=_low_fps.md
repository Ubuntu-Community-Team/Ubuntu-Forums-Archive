---
title: "Xubuntu 18.04 + webcam ic-310 = low fps"
date: 2018-05-12
forum: General Help
---

### Post by tsnvictor on 2018-05-12
[SIZE=3][COLOR=#000000][FONT=arial]Hello! Is it possible to increase the fps of the web camera, if in the program settings(V4L2, guvcview and other) only available: [/FONT][FONT=&amp][FONT=arial]320×240 fps5, 160×120 fps10 ?
[/FONT]
[/FONT][/COLOR][/SIZE][COLOR=#444444][FONT=&amp][SIZE=3][COLOR=#000000][FONT=arial]Terminal:

user@user:~$ lsusb
Bus 004 Device 002: ID 1871:0141 Aveo Technology Corp.

[/FONT][/COLOR][/SIZE][/FONT][/COLOR]
[COLOR=#444444][FONT=&amp][SIZE=3][COLOR=#000000][FONT=arial]user@user:~$uvcdynctrl -f
Listing available frame formats for device video0:
Pixel format: YUYV (YUYV 4:2:2; MIME type: video/x-raw-yuv)
Frame size: 320×240
Frame rates: 5
Frame size: 160×120
Frame rates: 10

[/FONT][/COLOR][/SIZE][/FONT][/COLOR]
[COLOR=#444444][FONT=&amp][SIZE=3][COLOR=#000000][FONT=arial]Xubuntu 18.04
web camera: NEC ic-310[/FONT][/COLOR][/SIZE][/FONT][/COLOR]

---


---
title: "Playing DVDs with xine-ui and Totem - Won't work!"
date: 2005-06-04
forum: General Help
---

### Post by sebgate20 on 2005-06-04
I'm having several problems trying to get DVDs to play on my Toshiba A60 laptop. Sound works. The packages I have installed are:

totem-xine
xine-ui
libdvdcss2
libdvdnav4
libdvdplay0
libdvread3

When I run xine-ui and select DVD, the output error is:

The source can't be read. Error reading NAV packet

Howeverm xine-ui from the Terminal, I get this error:

libdvdread: Using libdvdcss version 1.2.8 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000b50
libdvdread: Error cracking CSS key for /VIDEO_TS/VIDEO_TS.VOB (0x00000b50)
libdvdread: Elapsed time 4
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00001106
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00001106)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000ebf2
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x0000ebf2)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00302f69
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 4


And when I run Totem, I get this error:

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000b50
libdvdread: Error cracking CSS key for /VIDEO_TS/VIDEO_TS.VOB (0x00000b50)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00001106
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00001106)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000ebf2
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x0000ebf2)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00302f69
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0


Any ideas? Thanks

Seb

---


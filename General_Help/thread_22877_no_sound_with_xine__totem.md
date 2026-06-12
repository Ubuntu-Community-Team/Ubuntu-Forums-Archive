---
title: "no sound with xine / totem"
date: 2005-03-30
forum: General Help
---

### Post by MikehBar on 2005-03-30
Hi,

My problem is I can't hear sounds when I play dvd's or cd's from totem unless it is launched from a terminal. Image is perfect for dvd's. Xine doesn't have any sound either. System sounds are ok. Already checked volume controls, everything looks fine. Cd's sound well from cd player.  Any idea why this happens?

---

### Post by dusu on 2005-03-30
Can you give vlc a try and see if you get sound when you play DVDs with it ?

---

### Post by MikehBar on 2005-03-30
hi dusu,

gave vlc a try and it works fine. I tried to open an mp3 file and it doesn't work either. Something else happens to totem. Everytime I open it for the first time, I get a blue screen and can't see anything, but when I reopen it, it works fine, or if I open xine first.

---

### Post by MikehBar on 2005-03-30
noticed something else. When I pause the movie and then play it again I get an error saying the sound device is busy and asks me if any other application is using it. After a few attempts it works again. I'm printing what I get on my terminal when I open a reprudce a dvd with totem.

libdvdnav: Using dvdnav version 1-rc7 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdnav: DVD Title: KILLBILL_VOL1
libdvdnav: DVD Serial Number: 30620e77
libdvdnav: DVD Title (Alternative): KILLBILL_VOL1
libdvdnav: Unable to find map file '/home/mike/.dvdnav/KILLBILL_VOL1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0001fe6e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00030564
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002abbaf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00345873
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0036ba08
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0036cc43
libdvdread: Elapsed time 0
libdvdread: Found 5 VTS's
libdvdread: Elapsed time 0

---

### Post by lorap on 2005-03-30
hi friend!
the buddies're right!
get a VLC or XMMS try!
pavel

p.s.:
i use VLC for the movies and XMMS for mp3 try them both you'll like it,trust me :-)

---

### Post by dusu on 2005-03-30
[QUOTE=lorap]hi friend!
the buddies're right!
get a VLC or XMMS try!
pavel

p.s.:
i use VLC for the movies and XMMS for mp3 try them both you'll like it,trust me :-)[/QUOTE]

Yep, I do exactly the same as you : vlc + XMMS and I like that  :shock:

---

### Post by MikehBar on 2005-04-04
Well I finally got sound working from totem launched from the desktop. I just disabled esd. I liked vcl and all, but I just wanted totem to work. Thanks all. Now I just have to figure how to make em both work together. Hmmm.

---


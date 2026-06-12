---
title: "DVD sends vlc into a spin"
date: 2013-01-16
forum: General Help
---

### Post by t0p on 2013-01-16
Weird.  All my other movie DVDs work fine with vlc.  But if I try to use vlc to play The Dark Knight, it goes all unresponsive, CPU (one of the 2 cores) ratchets up to 100% and I have to kill it!

I can use other program (eg totem) to play that DVD.  But I wanna use vlc to rip it.  Any ideas why this one disk sends vlc loopy?

---

### Post by 3246251196 on 2013-01-16
> **t0p said:**
> Weird.  All my other movie DVDs work fine with vlc.  But if I try to use vlc to play The Dark Knight, it goes all unresponsive, CPU (one of the 2 cores) ratchets up to 100% and I have to kill it!

I can use other program (eg totem) to play that DVD.  But I wanna use vlc to rip it.  Any ideas why this one disk sends vlc loopy?

You can get VLC to spit out the errors it encounters if you open a terminal, and type "vlc" and run vlc - this will open vlc, just like usual, but this time things are printed to your standard out/error - you can see them.

I have problems with VLC with certain episodes of Frasier - library issues. Does not happen often.

Maybe someone can help more if you copy the errors here.

---

### Post by t0p on 2013-01-17
Thanks for that.  Here are the messages to terminal when I opened vlc in terminal and told it to play the disk.  CPU1 maxed out, vlc became unresponsive and I had to Kill it through System Monitor:

```
t0p@mars:~$ vlc
VLC media player 2.0.3 Twoflower (revision 2.0.2-93-g77aa89e)
[0x844108] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.2.0
libdvdread: Using libdvdcss version 1.2.12 for DVD access
libdvdnav: DVD Title: THE_DARK_KNIGHT
libdvdnav: DVD Serial Number: 39476298
libdvdnav: DVD Title (Alternative): THE_DARK_KNIGHT
libdvdnav: Unable to find map file '/home/t0p/.dvdnav/THE_DARK_KNIGHT.map'
libdvdnav: DVD disk reports itself with Region mask 0x00ed0000. Regions: 2 5

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00036000
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000367da
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00048717
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x003a7750
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x003a77f4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003b41ba
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003b6d3a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003c0fb3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003dcd05
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003dcd15
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003dcd65
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003dcd75
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003dcdc5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003dcdd5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003dce25
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x003dce35
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x003dce85
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x003dce95
libdvdread: Elapsed time 0
libdvdread: Found 10 VTS's
libdvdread: Elapsed time 0

*** libdvdread: CHECK_VALUE failed in /build/buildd/libdvdread-4.2.0/src/ifo_read.c:1986 ***
*** for pgci_ut->nr_of_lus < 100 ***

Killed
t0p@mars:~$ 

```

The same kind of thing happens when  try to use dvd::rip to rip that disk.  One of the CPUs maxes out, I have to Kill dvd::rip.

Incidentally, why does only one CPU max out?  Why isn't it shared equally between both CPUs?

---

### Post by t0p on 2013-01-17
bump

---


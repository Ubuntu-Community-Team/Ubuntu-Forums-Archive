---
title: "Problems with Totem and libdvdcss2"
date: 2004-11-09
forum: General Help
---

### Post by JonAtkinson on 2004-11-09
Hi,

I've installed libdvdcss2 and totem-xine from marillat unstable, and I'm having problems with playing DVDs.

Using: 
```
$ totem dvd://
```
to play a DVD, I get the opening studio credits, then the menu. When I try to click on an episode (this is a Simpsons DVD ;-) I get the following dialogue from totem:

"The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"

I have installed libdvdcss2, and I can verify that the files are in /usr/lib:
```
$ ls /usr/lib | grep "dvdcss"
libdvdcss.so.2
libdvdcss.so.2.0.7
```
If it helps, totem outputs the following if I run it from the command line:
```
jonathan@supra:~ $ totem dvd://
libhal.c 2213 : Error sending msg: Message did not receive a reply

** (totem:17872): WARNING **: Can't read /proc/scsi/sg/device_strs
libdvdnav: Using dvdnav version 1-rc5 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdnav: DVD Title: SIMP S3_D2
libdvdnav: DVD Serial Number: 32E9D35801C3C40B
libdvdnav: DVD Title (Alternative): PrassiPrassiPrassi
libdvdnav: Unable to find map file '/home/jonathan/.dvdnav/SIMP S3_D2.map'
libdvdnav: DVD disk reports itself with Region mask 0x00c00000. Regions: 1 2 3 4 5 6

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000014d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000352
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000003aa
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00000404
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002125ee
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00212a2b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0021320f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00213266
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00213f5d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00214d8d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00214dfb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0021a583
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x00229c4c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x00229cb7
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 0
libdvdnav: RANDOM or SHUFFLE titles are NOT handled yet.
jonathan@supra:~ $
```It looks like to me it's scanning through the chapters to find the decryption key, but I'm suspicious that they all take zero seconds, which makes me think that something is wrong with libdvdcss...

I've also tried to use ogle (failed) and mplayer-common from multiverse, which wouldn't recognise the -dvd-device=/dev/dvd parameter. I also user regionset to check that the region is set correctly (it is, region 2, the UK). I'm really quite stuck...

Any help would be much appreciated.

--Jon

---

### Post by wallijonn on 2004-11-09
I have seen two versions of the css plugins. Did you install the latest versions? 

Is "The Simpsons" the only DVD wich plays this way? There may not be anything which you can do - many new DVDs are strengthening their encryption. I had to buy a new DVD player because certain movies could not be played. Lately some of my DVDs (on my Panasonic DVD-S55 home player) take over a minute to get to the 0000 timer play screen.

---

### Post by JonAtkinson on 2004-11-10
Well, it seems that I've solved it. I looked at the libdvdcss2 documentation, and I did the following:```
$ export DVDCSS_METHOD=disc
```before I ran Totem. Everything seems to work right now.

Thanks for your suggestions.

--Jon

---


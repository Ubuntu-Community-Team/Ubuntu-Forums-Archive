---
title: "Kb3 error message"
date: 2014-08-07
forum: General Help
---

### Post by UncleMonty on 2014-08-07
"K3b uses transcode to rip Video DVDs. Please make sure it is installed"

How can I rectify this please?

---

### Post by claracc on 2014-08-07
Do you have transcode package installed?, you can see it with synaptic.

To install transcode, open a xterm: ctrl+alt+t and run ```
sudo apt-get install transcode
```

---

### Post by UncleMonty on 2014-08-07
I tried that, but the output only reached 50% - here is the output error file. 
```

Devices
-----------------------
MATSHITA DVD-RAM UJ880AS 1.20 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, Restricted Overwrite, Layer Jump] [%7]

System
-----------------------
K3b Version: 2.0.2
KDE Version: 4.13.2
QT Version:  4.8.6
Kernel:      3.13.0-32-generic

Used versions
-----------------------
transcode: 1.1.7

transcode
-----------------------
transcode v1.1.7 (C) 2001-2003 Thomas Oestreich, 2003-2010 Transcode Team
[[34;1mdvd_reader.c[0m] DVD title 23/28: 1 chapter(s), 1 angle(s), title set 13
[[34;1mdvd_reader.c[0m] title playback time: 00:00:10.00  11 sec
[[34;1mdvd_reader.c[0m] DVD title 23/28: 1 chapter(s), 1 angle(s), title set 13
[[34;1mdvd_reader.c[0m] title playback time: 00:00:10.00  11 sec
[transcode] V: auto-probing     | /dev/sr0 (OK)
[transcode] V: import format    | MPEG 2 program stream in DVD PAL (module=dvd)
[transcode] A: auto-probing     | /dev/sr0 (OK)
[transcode] A: import format    | AC3 in DVD PAL (module=dvd)
[transcode] V: AV demux/sync    | (1) sync AV at initial MPEG sequence
[transcode] V: import frame     | 720x576  1.25:1  encoded @ 4:3
[transcode] V: clip frame (<-)  | 720x576
[transcode] V: zoom             | 752x576  1.31:1 (Lanczos3)
[transcode] V: bits/pixel       | 0.111 (low)
[transcode] V: decoding fps,frc | 25.000,3
[transcode] V: multi-pass       | (mode=1) writing data (pass 1) to /tmp/kde-steve/k3b_0.log
[transcode] V: video format     | YUV420 (4:2:0) aka I420
[transcode] A: import format    | 0x2000  AC3          [48000,16,2]
[transcode] A: export           | disabled
[transcode] V: encoding fps,frc | 25.000,3
[transcode] A: language         | en
[transcode] A: bytes per frame  | 7680 (7680.000000)
[transcode] A: adjustment       | 0@1000
[transcode] V: IA32/AMD64 accel | ssse3 sse3 sse2 sse mmx cmove asm 
[transcode] V: video buffer     | 10 @ 752x576 [0x2]
[transcode] A: audio buffer     | 10 @ 48000x2x16
[import_dvd.so] v0.4.1 (2007-07-15) (video) DVD | (audio) MPEG/AC3/PCM
[export_null.so] v0.1.2 (2001-08-17) (video) null | (audio) null
[export_ffmpeg.so] v0.3.18 (2008-11-29) (video) Lavc54.35.0 | (audio) MPEG/AC3/PCM
[import_dvd.so] tccat -T 23,-1,1 -i "/dev/sr0" -t dvd -d 0 | tcdemux -a 0 -x ac3 -S 0 -M 1 -d 0 | tcextract -t vob -x ac3 -a 0 -d 0 | tcdecode -x ac3 -d 0 -s 1.000000,1.000000,1.000000 -A 0
[import_dvd.so] tccat -T 23,-1,1 -i "/dev/sr0" -t dvd -d 0 | tcdemux -s 0x80 -x mpeg2 -S 0 -M 1 -d 0 | tcextract -t vob -a 0 -x mpeg2 -d 0 | tcdecode -x mpeg2 -d 0 -y yuv420p
[import_dvd.so] delaying DVD access by 3 seconds
[import_dvd.so] waiting...
libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient
libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000178
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000202
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000101ac
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001013a3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001013f0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x001f3105
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001f3152
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x002f05bc
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x002f0609
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003117a6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003117f3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00329668
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003296b5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00348438
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00348485
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x00368478
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003684c5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003d504d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x003d509a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x003d646c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x003d64b9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x003d6906
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x003d6953
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x003d7173
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x003d71c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x003d7b57
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x003d7ba4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x003d7d62
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x003d7daf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_0.VOB at 0x003d82e3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x003d8330
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_0.VOB at 0x003d88cb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_1.VOB at 0x003d8918
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_0.VOB at 0x003d8e28
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_1.VOB at 0x003d8e75
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_18_0.VOB at 0x003dbe92
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_18_1.VOB at 0x003dbedf
libdvdread: Elapsed time 0
libdvdread: Found 18 VTS's
libdvdread: Elapsed time 0
[import_dvd.so] waiting...
=== last message repeated 2 times. ===
[export_ffmpeg.so] Using FFMPEG codec 'mpeg4' (FourCC 'DIVX', MPEG4 compliant video).
[export_ffmpeg.so] No profile selected
[export_ffmpeg.so] Error opening configuration file ./ffmpeg.cfg: No such file or directory
[export_ffmpeg.so] Starting 1 thread(s)
[export_ffmpeg.so] Set display aspect ratio to input
[mpeg4 @ 0x83ab1e0] removing common factors from framerate
[[34;1mdecode_mpeg2.c[0m] libmpeg2 acceleration: mmxext
libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient
libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000178
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000202
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000101ac
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001013a3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001013f0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x001f3105
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001f3152
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x002f05bc
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x002f0609
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003117a6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003117f3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00329668
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003296b5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00348438
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00348485
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x00368478
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003684c5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003d504d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x003d509a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x003d646c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x003d64b9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x003d6906
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x003d6953
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x003d7173
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x003d71c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x003d7b57
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x003d7ba4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x003d7d62
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x003d7daf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_0.VOB at 0x003d82e3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x003d8330
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_0.VOB at 0x003d88cb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_1.VOB at 0x003d8918
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_0.VOB at 0x003d8e28
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_1.VOB at 0x003d8e75
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_18_0.VOB at 0x003dbe92
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_18_1.VOB at 0x003dbedf
libdvdread: Elapsed time 0
libdvdread: Found 18 VTS's
libdvdread: Elapsed time 0
encoding=1 frame=1 first=0 last=-1 fps=129.535 done=-1.000000 timestamp=0.040 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=2 first=0 last=-1 fps=114.065 done=-1.000000 timestamp=0.080 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=3 first=0 last=-1 fps=104.734 done=-1.000000 timestamp=0.120 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=4 first=0 last=-1 fps=92.685 done=-1.000000 timestamp=0.160 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=5 first=0 last=-1 fps=89.070 done=-1.000000 timestamp=0.200 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=6 first=0 last=-1 fps=78.878 done=-1.000000 timestamp=0.240 timeleft=-1 decodebuf=1 filterbuf=8 encodebuf=11
encoding=1 frame=7 first=0 last=-1 fps=80.434 done=-1.000000 timestamp=0.280 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=8 first=0 last=-1 fps=79.378 done=-1.000000 timestamp=0.320 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=9 first=0 last=-1 fps=76.329 done=-1.000000 timestamp=0.360 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=10 first=0 last=-1 fps=77.452 done=-1.000000 timestamp=0.400 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=11 first=0 last=-1 fps=70.438 done=-1.000000 timestamp=0.440 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=12 first=0 last=-1 fps=73.599 done=-1.000000 timestamp=0.480 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=13 first=0 last=-1 fps=74.338 done=-1.000000 timestamp=0.520 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=14 first=0 last=-1 fps=74.573 done=-1.000000 timestamp=0.560 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=15 first=0 last=-1 fps=75.430 done=-1.000000 timestamp=0.600 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=16 first=0 last=-1 fps=73.381 done=-1.000000 timestamp=0.640 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=17 first=0 last=-1 fps=75.421 done=-1.000000 timestamp=0.680 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=18 first=0 last=-1 fps=74.994 done=-1.000000 timestamp=0.720 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=19 first=0 last=-1 fps=75.531 done=-1.000000 timestamp=0.760 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=20 first=0 last=-1 fps=77.114 done=-1.000000 timestamp=0.800 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=21 first=0 last=-1 fps=75.388 done=-1.000000 timestamp=0.840 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=22 first=0 last=-1 fps=76.062 done=-1.000000 timestamp=0.880 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=23 first=0 last=-1 fps=76.355 done=-1.000000 timestamp=0.920 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=24 first=0 last=-1 fps=77.199 done=-1.000000 timestamp=0.960 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=25 first=0 last=-1 fps=76.930 done=-1.000000 timestamp=1.000 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=26 first=0 last=-1 fps=75.485 done=-1.000000 timestamp=1.040 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=27 first=0 last=-1 fps=75.085 done=-1.000000 timestamp=1.080 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=28 first=0 last=-1 fps=75.770 done=-1.000000 timestamp=1.120 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=29 first=0 last=-1 fps=75.919 done=-1.000000 timestamp=1.160 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=30 first=0 last=-1 fps=76.741 done=-1.000000 timestamp=1.200 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=31 first=0 last=-1 fps=75.685 done=-1.000000 timestamp=1.240 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=32 first=0 last=-1 fps=75.719 done=-1.000000 timestamp=1.280 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=33 first=0 last=-1 fps=76.034 done=-1.000000 timestamp=1.320 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=34 first=0 last=-1 fps=75.258 done=-1.000000 timestamp=1.360 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=35 first=0 last=-1 fps=75.805 done=-1.000000 timestamp=1.400 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=36 first=0 last=-1 fps=74.880 done=-1.000000 timestamp=1.440 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=37 first=0 last=-1 fps=74.750 done=-1.000000 timestamp=1.480 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=38 first=0 last=-1 fps=74.904 done=-1.000000 timestamp=1.520 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=39 first=0 last=-1 fps=74.787 done=-1.000000 timestamp=1.560 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=40 first=0 last=-1 fps=75.407 done=-1.000000 timestamp=1.600 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=41 first=0 last=-1 fps=74.392 done=-1.000000 timestamp=1.640 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=42 first=0 last=-1 fps=74.198 done=-1.000000 timestamp=1.680 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=43 first=0 last=-1 fps=74.477 done=-1.000000 timestamp=1.720 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=44 first=0 last=-1 fps=74.450 done=-1.000000 timestamp=1.760 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=45 first=0 last=-1 fps=74.945 done=-1.000000 timestamp=1.800 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=46 first=0 last=-1 fps=74.358 done=-1.000000 timestamp=1.840 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=47 first=0 last=-1 fps=74.501 done=-1.000000 timestamp=1.880 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=48 first=0 last=-1 fps=74.545 done=-1.000000 timestamp=1.920 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=49 first=0 last=-1 fps=74.547 done=-1.000000 timestamp=1.960 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=50 first=0 last=-1 fps=74.980 done=-1.000000 timestamp=2.000 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=51 first=0 last=-1 fps=74.477 done=-1.000000 timestamp=2.040 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=52 first=0 last=-1 fps=73.509 done=-1.000000 timestamp=2.080 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=53 first=0 last=-1 fps=74.310 done=-1.000000 timestamp=2.120 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=54 first=0 last=-1 fps=74.352 done=-1.000000 timestamp=2.160 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=55 first=0 last=-1 fps=74.847 done=-1.000000 timestamp=2.200 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=56 first=0 last=-1 fps=74.120 done=-1.000000 timestamp=2.240 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=57 first=0 last=-1 fps=74.242 done=-1.000000 timestamp=2.280 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=58 first=0 last=-1 fps=73.971 done=-1.000000 timestamp=2.320 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=59 first=0 last=-1 fps=73.813 done=-1.000000 timestamp=2.360 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=60 first=0 last=-1 fps=73.915 done=-1.000000 timestamp=2.400 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=61 first=0 last=-1 fps=73.511 done=-1.000000 timestamp=2.440 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=62 first=0 last=-1 fps=73.523 done=-1.000000 timestamp=2.480 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=63 first=0 last=-1 fps=73.582 done=-1.000000 timestamp=2.520 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=64 first=0 last=-1 fps=73.578 done=-1.000000 timestamp=2.560 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=65 first=0 last=-1 fps=73.703 done=-1.000000 timestamp=2.600 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=66 first=0 last=-1 fps=73.288 done=-1.000000 timestamp=2.640 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=67 first=0 last=-1 fps=73.369 done=-1.000000 timestamp=2.680 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=68 first=0 last=-1 fps=73.436 done=-1.000000 timestamp=2.720 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=69 first=0 last=-1 fps=73.313 done=-1.000000 timestamp=2.760 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=70 first=0 last=-1 fps=73.644 done=-1.000000 timestamp=2.800 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=71 first=0 last=-1 fps=73.330 done=-1.000000 timestamp=2.840 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=72 first=0 last=-1 fps=73.277 done=-1.000000 timestamp=2.880 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=73 first=0 last=-1 fps=73.474 done=-1.000000 timestamp=2.920 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=74 first=0 last=-1 fps=73.608 done=-1.000000 timestamp=2.960 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=75 first=0 last=-1 fps=73.850 done=-1.000000 timestamp=3.000 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=76 first=0 last=-1 fps=72.870 done=-1.000000 timestamp=3.040 timeleft=-1 decodebuf=0 filterbuf=8 encodebuf=12
encoding=1 frame=77 first=0 last=-1 fps=73.553 done=-1.000000 timestamp=3.080 timeleft=-1 decodebuf=1 filterbuf=8 encodebuf=11
encoding=1 frame=78 first=0 last=-1 fps=73.641 done=-1.000000 timestamp=3.120 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=79 first=0 last=-1 fps=73.542 done=-1.000000 timestamp=3.160 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=80 first=0 last=-1 fps=73.627 done=-1.000000 timestamp=3.200 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=81 first=0 last=-1 fps=73.246 done=-1.000000 timestamp=3.240 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=82 first=0 last=-1 fps=73.543 done=-1.000000 timestamp=3.280 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=83 first=0 last=-1 fps=73.412 done=-1.000000 timestamp=3.320 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=84 first=0 last=-1 fps=73.260 done=-1.000000 timestamp=3.360 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=85 first=0 last=-1 fps=73.686 done=-1.000000 timestamp=3.400 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=86 first=0 last=-1 fps=73.096 done=-1.000000 timestamp=3.440 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=87 first=0 last=-1 fps=73.407 done=-1.000000 timestamp=3.480 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=88 first=0 last=-1 fps=73.627 done=-1.000000 timestamp=3.520 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=89 first=0 last=-1 fps=73.737 done=-1.000000 timestamp=3.560 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=90 first=0 last=-1 fps=73.688 done=-1.000000 timestamp=3.600 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=91 first=0 last=-1 fps=73.302 done=-1.000000 timestamp=3.640 timeleft=-1 decodebuf=2 filterbuf=7 encodebuf=11
encoding=1 frame=92 first=0 last=-1 fps=73.607 done=-1.000000 timestamp=3.680 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=93 first=0 last=-1 fps=73.870 done=-1.000000 timestamp=3.720 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=94 first=0 last=-1 fps=73.760 done=-1.000000 timestamp=3.760 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=95 first=0 last=-1 fps=73.846 done=-1.000000 timestamp=3.800 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=96 first=0 last=-1 fps=73.267 done=-1.000000 timestamp=3.840 timeleft=-1 decodebuf=2 filterbuf=7 encodebuf=11
encoding=1 frame=97 first=0 last=-1 fps=73.376 done=-1.000000 timestamp=3.880 timeleft=-1 decodebuf=0 filterbuf=8 encodebuf=12
encoding=1 frame=98 first=0 last=-1 fps=73.812 done=-1.000000 timestamp=3.920 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=99 first=0 last=-1 fps=74.024 done=-1.000000 timestamp=3.960 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=100 first=0 last=-1 fps=74.069 done=-1.000000 timestamp=4.000 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=101 first=0 last=-1 fps=73.816 done=-1.000000 timestamp=4.040 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=102 first=0 last=-1 fps=73.738 done=-1.000000 timestamp=4.080 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=103 first=0 last=-1 fps=73.788 done=-1.000000 timestamp=4.120 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=104 first=0 last=-1 fps=73.798 done=-1.000000 timestamp=4.160 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=105 first=0 last=-1 fps=74.006 done=-1.000000 timestamp=4.200 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=106 first=0 last=-1 fps=73.579 done=-1.000000 timestamp=4.240 timeleft=-1 decodebuf=0 filterbuf=8 encodebuf=12
encoding=1 frame=107 first=0 last=-1 fps=73.722 done=-1.000000 timestamp=4.280 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=108 first=0 last=-1 fps=74.096 done=-1.000000 timestamp=4.320 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=109 first=0 last=-1 fps=74.006 done=-1.000000 timestamp=4.360 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=110 first=0 last=-1 fps=74.059 done=-1.000000 timestamp=4.400 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=111 first=0 last=-1 fps=73.548 done=-1.000000 timestamp=4.440 timeleft=-1 decodebuf=0 filterbuf=8 encodebuf=12
encoding=1 frame=112 first=0 last=-1 fps=73.952 done=-1.000000 timestamp=4.480 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=113 first=0 last=-1 fps=74.118 done=-1.000000 timestamp=4.520 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=114 first=0 last=-1 fps=74.107 done=-1.000000 timestamp=4.560 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=115 first=0 last=-1 fps=74.186 done=-1.000000 timestamp=4.600 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=116 first=0 last=-1 fps=73.836 done=-1.000000 timestamp=4.640 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=117 first=0 last=-1 fps=73.831 done=-1.000000 timestamp=4.680 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=118 first=0 last=-1 fps=73.919 done=-1.000000 timestamp=4.720 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=119 first=0 last=-1 fps=73.864 done=-1.000000 timestamp=4.760 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=120 first=0 last=-1 fps=73.931 done=-1.000000 timestamp=4.800 timeleft=-1 decodebuf=1 filterbuf=8 encodebuf=11
encoding=1 frame=121 first=0 last=-1 fps=73.692 done=-1.000000 timestamp=4.840 timeleft=-1 decodebuf=2 filterbuf=7 encodebuf=11
encoding=1 frame=122 first=0 last=-1 fps=73.630 done=-1.000000 timestamp=4.880 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=123 first=0 last=-1 fps=73.856 done=-1.000000 timestamp=4.920 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=124 first=0 last=-1 fps=73.864 done=-1.000000 timestamp=4.960 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=125 first=0 last=-1 fps=73.943 done=-1.000000 timestamp=5.000 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=126 first=0 last=-1 fps=73.675 done=-1.000000 timestamp=5.040 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=127 first=0 last=-1 fps=73.705 done=-1.000000 timestamp=5.080 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=128 first=0 last=-1 fps=73.772 done=-1.000000 timestamp=5.120 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=129 first=0 last=-1 fps=73.826 done=-1.000000 timestamp=5.160 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=130 first=0 last=-1 fps=74.022 done=-1.000000 timestamp=5.200 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=131 first=0 last=-1 fps=73.813 done=-1.000000 timestamp=5.240 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=132 first=0 last=-1 fps=73.707 done=-1.000000 timestamp=5.280 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=133 first=0 last=-1 fps=73.706 done=-1.000000 timestamp=5.320 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=134 first=0 last=-1 fps=73.741 done=-1.000000 timestamp=5.360 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=135 first=0 last=-1 fps=73.885 done=-1.000000 timestamp=5.400 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=136 first=0 last=-1 fps=73.657 done=-1.000000 timestamp=5.440 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=137 first=0 last=-1 fps=73.709 done=-1.000000 timestamp=5.480 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=138 first=0 last=-1 fps=73.695 done=-1.000000 timestamp=5.520 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=139 first=0 last=-1 fps=73.705 done=-1.000000 timestamp=5.560 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=140 first=0 last=-1 fps=73.876 done=-1.000000 timestamp=5.600 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=141 first=0 last=-1 fps=73.607 done=-1.000000 timestamp=5.640 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=142 first=0 last=-1 fps=73.687 done=-1.000000 timestamp=5.680 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=143 first=0 last=-1 fps=73.757 done=-1.000000 timestamp=5.720 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=144 first=0 last=-1 fps=73.657 done=-1.000000 timestamp=5.760 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=145 first=0 last=-1 fps=73.820 done=-1.000000 timestamp=5.800 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=146 first=0 last=-1 fps=73.252 done=-1.000000 timestamp=5.840 timeleft=-1 decodebuf=0 filterbuf=8 encodebuf=12
encoding=1 frame=147 first=0 last=-1 fps=73.531 done=-1.000000 timestamp=5.880 timeleft=-1 decodebuf=0 filterbuf=8 encodebuf=12
encoding=1 frame=148 first=0 last=-1 fps=73.877 done=-1.000000 timestamp=5.920 timeleft=-1 decodebuf=1 filterbuf=8 encodebuf=11
encoding=1 frame=149 first=0 last=-1 fps=73.879 done=-1.000000 timestamp=5.960 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=150 first=0 last=-1 fps=73.898 done=-1.000000 timestamp=6.000 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=151 first=0 last=-1 fps=73.692 done=-1.000000 timestamp=6.040 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=152 first=0 last=-1 fps=73.705 done=-1.000000 timestamp=6.080 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=153 first=0 last=-1 fps=73.621 done=-1.000000 timestamp=6.120 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=154 first=0 last=-1 fps=73.386 done=-1.000000 timestamp=6.160 timeleft=-1 decodebuf=1 filterbuf=7 encodebuf=12
encoding=1 frame=155 first=0 last=-1 fps=73.706 done=-1.000000 timestamp=6.200 timeleft=-1 decodebuf=2 filterbuf=8 encodebuf=10
encoding=1 frame=156 first=0 last=-1 fps=73.470 done=-1.000000 timestamp=6.240 timeleft=-1 decodebuf=2 filterbuf=7 encodebuf=11
encoding=1 frame=157 first=0 last=-1 fps=73.036 done=-1.000000 timestamp=6.280 timeleft=-1 decodebuf=0 filterbuf=8 encodebuf=12
encoding=1 frame=158 first=0 last=-1 fps=72.846 done=-1.000000 timestamp=6.320 timeleft=-1 decodebuf=0 filterbuf=7 encodebuf=13
encoding=1 frame=159 first=0 last=-1 fps=72.873 done=-1.000000 timestamp=6.360 timeleft=-1 decodebuf=1 filterbuf=7 encodebuf=12
encoding=1 frame=160 first=0 last=-1 fps=70.948 done=-1.000000 timestamp=6.400 timeleft=-1 decodebuf=0 filterbuf=2 encodebuf=18
encoding=1 frame=161 first=0 last=-1 fps=70.211 done=-1.000000 timestamp=6.440 timeleft=-1 decodebuf=0 filterbuf=2 encodebuf=18
encoding=1 frame=162 first=0 last=-1 fps=70.458 done=-1.000000 timestamp=6.480 timeleft=-1 decodebuf=0 filterbuf=3 encodebuf=17
encoding=1 frame=163 first=0 last=-1 fps=70.696 done=-1.000000 timestamp=6.520 timeleft=-1 decodebuf=0 filterbuf=3 encodebuf=17
encoding=1 frame=164 first=0 last=-1 fps=70.719 done=-1.000000 timestamp=6.560 timeleft=-1 decodebuf=0 filterbuf=3 encodebuf=17
encoding=1 frame=165 first=0 last=-1 fps=70.973 done=-1.000000 timestamp=6.600 timeleft=-1 decodebuf=0 filterbuf=4 encodebuf=16
encoding=1 frame=166 first=0 last=-1 fps=70.752 done=-1.000000 timestamp=6.640 timeleft=-1 decodebuf=0 filterbuf=3 encodebuf=17
encoding=1 frame=167 first=0 last=-1 fps=70.766 done=-1.000000 timestamp=6.680 timeleft=-1 decodebuf=0 filterbuf=3 encodebuf=17
encoding=1 frame=168 first=0 last=-1 fps=71.034 done=-1.000000 timestamp=6.720 timeleft=-1 decodebuf=0 filterbuf=3 encodebuf=17
encoding=1 frame=169 first=0 last=-1 fps=71.275 done=-1.000000 timestamp=6.760 timeleft=-1 decodebuf=1 filterbuf=3 encodebuf=16
encoding=1 frame=170 first=0 last=-1 fps=71.475 done=-1.000000 timestamp=6.800 timeleft=-1 decodebuf=1 filterbuf=4 encodebuf=15
encoding=1 frame=171 first=0 last=-1 fps=71.664 done=-1.000000 timestamp=6.840 timeleft=-1 decodebuf=2 filterbuf=4 encodebuf=14
encoding=1 frame=172 first=0 last=-1 fps=71.627 done=-1.000000 timestamp=6.880 timeleft=-1 decodebuf=0 filterbuf=6 encodebuf=14
encoding=1 frame=173 first=0 last=-1 fps=71.814 done=-1.000000 timestamp=6.920 timeleft=-1 decodebuf=0 filterbuf=7 encodebuf=13
encoding=1 frame=174 first=0 last=-1 fps=71.998 done=-1.000000 timestamp=6.960 timeleft=-1 decodebuf=1 filterbuf=6 encodebuf=13
encoding=1 frame=175 first=0 last=-1 fps=72.182 done=-1.000000 timestamp=7.000 timeleft=-1 decodebuf=0 filterbuf=8 encodebuf=12
encoding=1 frame=176 first=0 last=-1 fps=72.364 done=-1.000000 timestamp=7.040 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=177 first=0 last=-1 fps=72.272 done=-1.000000 timestamp=7.080 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=178 first=0 last=-1 fps=72.324 done=-1.000000 timestamp=7.120 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=179 first=0 last=-1 fps=72.304 done=-1.000000 timestamp=7.160 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=180 first=0 last=-1 fps=72.381 done=-1.000000 timestamp=7.200 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=181 first=0 last=-1 fps=72.203 done=-1.000000 timestamp=7.240 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=182 first=0 last=-1 fps=72.268 done=-1.000000 timestamp=7.280 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=183 first=0 last=-1 fps=72.356 done=-1.000000 timestamp=7.320 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=184 first=0 last=-1 fps=72.286 done=-1.000000 timestamp=7.360 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=185 first=0 last=-1 fps=72.387 done=-1.000000 timestamp=7.400 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=186 first=0 last=-1 fps=72.170 done=-1.000000 timestamp=7.440 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=187 first=0 last=-1 fps=72.368 done=-1.000000 timestamp=7.480 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=188 first=0 last=-1 fps=72.319 done=-1.000000 timestamp=7.520 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=189 first=0 last=-1 fps=72.279 done=-1.000000 timestamp=7.560 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=190 first=0 last=-1 fps=72.365 done=-1.000000 timestamp=7.600 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=191 first=0 last=-1 fps=72.139 done=-1.000000 timestamp=7.640 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=192 first=0 last=-1 fps=72.322 done=-1.000000 timestamp=7.680 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=193 first=0 last=-1 fps=72.263 done=-1.000000 timestamp=7.720 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=194 first=0 last=-1 fps=72.333 done=-1.000000 timestamp=7.760 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=195 first=0 last=-1 fps=72.434 done=-1.000000 timestamp=7.800 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=196 first=0 last=-1 fps=72.228 done=-1.000000 timestamp=7.840 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=197 first=0 last=-1 fps=72.186 done=-1.000000 timestamp=7.880 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=198 first=0 last=-1 fps=72.257 done=-1.000000 timestamp=7.920 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=199 first=0 last=-1 fps=72.249 done=-1.000000 timestamp=7.960 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=200 first=0 last=-1 fps=72.299 done=-1.000000 timestamp=8.000 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=201 first=0 last=-1 fps=72.054 done=-1.000000 timestamp=8.040 timeleft=-1 decodebuf=0 filterbuf=8 encodebuf=12
encoding=1 frame=202 first=0 last=-1 fps=72.253 done=-1.000000 timestamp=8.080 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=203 first=0 last=-1 fps=72.261 done=-1.000000 timestamp=8.120 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=204 first=0 last=-1 fps=72.202 done=-1.000000 timestamp=8.160 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=205 first=0 last=-1 fps=72.267 done=-1.000000 timestamp=8.200 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=206 first=0 last=-1 fps=72.189 done=-1.000000 timestamp=8.240 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=207 first=0 last=-1 fps=72.216 done=-1.000000 timestamp=8.280 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=208 first=0 last=-1 fps=72.256 done=-1.000000 timestamp=8.320 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=209 first=0 last=-1 fps=72.178 done=-1.000000 timestamp=8.360 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=210 first=0 last=-1 fps=72.251 done=-1.000000 timestamp=8.400 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=211 first=0 last=-1 fps=72.093 done=-1.000000 timestamp=8.440 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=212 first=0 last=-1 fps=72.081 done=-1.000000 timestamp=8.480 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=213 first=0 last=-1 fps=72.226 done=-1.000000 timestamp=8.520 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=214 first=0 last=-1 fps=72.169 done=-1.000000 timestamp=8.560 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=215 first=0 last=-1 fps=72.243 done=-1.000000 timestamp=8.600 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=216 first=0 last=-1 fps=72.142 done=-1.000000 timestamp=8.640 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=217 first=0 last=-1 fps=72.097 done=-1.000000 timestamp=8.680 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=218 first=0 last=-1 fps=72.224 done=-1.000000 timestamp=8.720 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=219 first=0 last=-1 fps=72.185 done=-1.000000 timestamp=8.760 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=220 first=0 last=-1 fps=72.199 done=-1.000000 timestamp=8.800 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=221 first=0 last=-1 fps=72.010 done=-1.000000 timestamp=8.840 timeleft=-1 decodebuf=1 filterbuf=7 encodebuf=12
encoding=1 frame=222 first=0 last=-1 fps=72.233 done=-1.000000 timestamp=8.880 timeleft=-1 decodebuf=1 filterbuf=8 encodebuf=11
encoding=1 frame=223 first=0 last=-1 fps=72.083 done=-1.000000 timestamp=8.920 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=224 first=0 last=-1 fps=72.140 done=-1.000000 timestamp=8.960 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=225 first=0 last=-1 fps=72.180 done=-1.000000 timestamp=9.000 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=226 first=0 last=-1 fps=71.982 done=-1.000000 timestamp=9.040 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=227 first=0 last=-1 fps=72.058 done=-1.000000 timestamp=9.080 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=228 first=0 last=-1 fps=72.076 done=-1.000000 timestamp=9.120 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=229 first=0 last=-1 fps=72.076 done=-1.000000 timestamp=9.160 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=230 first=0 last=-1 fps=72.146 done=-1.000000 timestamp=9.200 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=231 first=0 last=-1 fps=71.967 done=-1.000000 timestamp=9.240 timeleft=-1 decodebuf=1 filterbuf=7 encodebuf=12
encoding=1 frame=232 first=0 last=-1 fps=72.021 done=-1.000000 timestamp=9.280 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=233 first=0 last=-1 fps=72.170 done=-1.000000 timestamp=9.320 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=234 first=0 last=-1 fps=72.201 done=-1.000000 timestamp=9.360 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=235 first=0 last=-1 fps=72.165 done=-1.000000 timestamp=9.400 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=236 first=0 last=-1 fps=71.987 done=-1.000000 timestamp=9.440 timeleft=-1 decodebuf=0 filterbuf=8 encodebuf=12
encoding=1 frame=237 first=0 last=-1 fps=72.173 done=-1.000000 timestamp=9.480 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=238 first=0 last=-1 fps=72.163 done=-1.000000 timestamp=9.520 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=239 first=0 last=-1 fps=72.217 done=-1.000000 timestamp=9.560 timeleft=-1 decodebuf=0 filterbuf=9 encodebuf=11
encoding=1 frame=240 first=0 last=-1 fps=72.249 done=-1.000000 timestamp=9.600 timeleft=-1 decodebuf=1 filterbuf=9 encodebuf=10
encoding=1 frame=241 first=0 last=-1 fps=72.077 done=-1.000000 timestamp=9.640 timeleft=-1 decodebuf=2 filterbuf=8 encodebuf=10
encoding=1 frame=242 first=0 last=-1 fps=72.274 done=-1.000000 timestamp=9.680 timeleft=-1 decodebuf=4 filterbuf=8 encodebuf=8
encoding=1 frame=243 first=0 last=-1 fps=72.346 done=-1.000000 timestamp=9.720 timeleft=-1 decodebuf=6 filterbuf=7 encodebuf=7
encoding=1 frame=244 first=0 last=-1 fps=72.356 done=-1.000000 timestamp=9.760 timeleft=-1 decodebuf=8 filterbuf=6 encodebuf=6
encoding=1 frame=245 first=0 last=-1 fps=72.449 done=-1.000000 timestamp=9.800 timeleft=-1 decodebuf=10 filterbuf=5 encodebuf=5
encoding=1 frame=246 first=0 last=-1 fps=72.384 done=-1.000000 timestamp=9.840 timeleft=-1 decodebuf=12 filterbuf=4 encodebuf=4
encoding=1 frame=247 first=0 last=-1 fps=72.498 done=-1.000000 timestamp=9.880 timeleft=-1 decodebuf=14 filterbuf=3 encodebuf=3
*** Error in `/usr/bin/transcode': munmap_chunk(): invalid pointer: 0xa55170ba ***

transcode command:
-----------------------
/usr/bin/transcode --nice 19 --log_no_color --progress_meter 2 --progress_rate 1 -i /dev/sr0 -x dvd -T 23,-1,1 -a 0 -j 0,0,0,0 -R 1,/tmp/kde-steve/k3b_0.log -y ffmpeg,null -o /dev/null -F mpeg4 -w 1200 -Z 752x576
```

---

### Post by stalkingwolf on 2014-08-07
check in synaptic package manager and see if it or any of its packages are installed.  If not try installing it there.   Under the edit tab click fix broken packages. that might solve the issue.

If it doesnt reboot and select the recovery mode then fix broken packages.  that sometimes will let the installation complete.

---

### Post by SeijiSensei on 2014-08-07
Did you run /usr/share/doc/libdvdread4/install-css.sh?

You can also try installing kubuntu-restricted-extras which includes encumbered software that works with KDE applications.

---

### Post by UncleMonty on 2014-08-07
Thanks I tried all that but it made no difference. 

Solution: Select format xvid instead of MPEG.

---

### Post by SeijiSensei on 2014-08-07
XviD doesn't have very good quality, though.  Why not use something like Handbrake instead of K3b?  The best source for Handbrake is [John Stebbins's PPA]("https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-snapshots").

---


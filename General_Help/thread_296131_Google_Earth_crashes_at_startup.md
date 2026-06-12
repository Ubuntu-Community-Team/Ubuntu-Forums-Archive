---
title: "Google Earth crashes at startup"
date: 2006-11-09
forum: General Help
---

### Post by Eremit on 2006-11-09
> raiden@Skynet:~/google-earth$ ./googleearth
Google Earth has caught signal 11.

Stacktrace from glibc:
  ./googleearth-bin(__gxx_personality_v0+0x1b8) [0x804b154]
  ./googleearth-bin [0x804b53b]
  [0xffffe420]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/raiden/.googleearth/crashlogs/crashlog-F1C5E43F.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.
> raiden@Skynet:~/.googleearth/crashlogs$ cat crashlog-F1C5E43F.txt 
CRASHLOGVER 1
CRASHLOGID 0xF1C5E43F
APPVERMAJOR 4
APPVERMINOR 0
APPVERBUILD 2413
APPBUILDDATE Oct 31 2006
APPBUILDTIME 15:32:52
OSTYPE 10
OSVERMAJOR 2
OSVERMINOR 6
OSVERBUILD 17
OSVERPATCH 0
PID 8572
CRASHSIGNAL 11
CRASHTIME 1163071849
PROGRAMUPTIME 1

STACK 0x804b154
STACK 0x804b53b
STACK 0xffffe420

DSO googleearth-bin/0x8048000/22502
DSO linux-gate.so.1/0xffffe000/1580
DSO libbase.so/0xb7ec2000/463533
DSO libcomponent.so/0xb7eab000/86805
DSO libfusion.so/0xb7ea6000/13060
DSO libgeobase.so/0xb7bb7000/2972487
DSO libmath.so/0xb7ba7000/61006
DSO libwmsbase.so/0xb7b45000/380092
DSO libnet.so/0xb7b06000/248887
DSO libalchemyext.so/0xb7b01000/15228
DSO libcollada.so/0xb77dd000/3194101
DSO libgoogleearth.so/0xb7694000/1301527
DSO libGLU.so.1/0xb7615000/507779
DSO libcrypto.so.0.9.8/0xb74ef000/1103016
DSO libcurl.so.3/0xb74c6000/159800
DSO libfreeimage.so.3/0xb7403000/770245
DSO libgcc_s.so.1/0xb73f8000/39096
DSO libjpeg.so.62/0xb73d3000/139688
DSO libmng.so.1/0xb7376000/364312
DSO libpng12.so.0/0xb734e000/156964
DSO libqt-mt.so.3/0xb6b13000/8348421
DSO libqui.so.1/0xb6ad2000/256348
DSO libssl.so.0.9.8/0xb6a96000/221460
DSO libstdc++.so.6/0xb69bc000/849472
DSO libtiff.so.3/0xb6960000/364328
DSO libz.so.1/0xb6949000/86972
DSO libIGCore.so/0xb6852000/950676
DSO libIGGfx.so/0xb6790000/742740
DSO libIGAttrs.so/0xb672f000/362932
DSO libIGDisplay.so/0xb671b000/70352
DSO libIGGui.so/0xb66d9000/246068
DSO libIGSg.so/0xb65cc000/1035492
DSO libIGCollision.so/0xb65bc000/55044
DSO libIGMath.so/0xb6573000/277228
DSO libIGUtils.so/0xb654c000/146568
DSO libIGOpt.so/0xb6471000/841288
DSO libIGExportCommon.so/0xb63e9000/517224
DSO libcommon.so/0xb6314000/836951
DSO librender.so/0xb62bd000/337859
DSO libauth.so/0xb6240000/490183
DSO libframework.so/0xb622a000/85475
DSO libm.so.6/0x428af000/143984
DSO libc.so.6/0x42773000/1232400
DSO libpthread.so.0/0x428d7000/61216
DSO libdl.so.2/0x428a9000/7472
DSO libXrender.so.1/0x42b5a000/26580
DSO libXcursor.so.1/0x42be2000/30340
DSO libXft.so.2/0x43347000/66484
DSO libfreetype.so.6/0x42a87000/420484
DSO libfontconfig.so.1/0x42ba0000/165512
DSO libXext.so.6/0x429d9000/48296
DSO libX11.so.6/0x42909000/809328
DSO libSM.so.6/0x42c08000/28932
DSO libICE.so.6/0x42c13000/82048
DSO libGL.so.1/0x41081000/501183
DSO libGL.so.1/0x410fc5c0/106592
DSO ld-linux.so.2/0x41f38000/100116
DSO libXfixes.so.3/0x42bd6000/12400
DSO libexpat.so.1/0x42b0b000/113720
DSO libXau.so.6/0x429d4000/5700
DSO libXdmcp.so.6/0x42902000/14916
DSO libGLcore.so.1/0x43bf3000/9079873
DSO libGLcore.so.1/0x4449c000/232320
DSO libnvidia-tls.so.1/0x4107d000/1332
DSO xlibi18n.so.2/0xb587a000/17088
DSO ximcp.so.2/0xb585c000/111268
DSO libnss_compat.so.2/0xb5842000/25496
DSO libnsl.so.1/0x42af3000/70976
DSO libnss_nis.so.2/0xb5838000/31488
DSO libnss_files.so.2/0xb582d000/34604
DSO libnss_dns.so.2/0xb5854000/14812
DSO libresolv.so.2/0x42bf3000/60416
DSO libevll.so/0xb3b02000/4289631
DSO libnavigate.so/0xb1216000/928287
DSO liblayer.so/0xb0fdf000/2251383
DSO libmeasure.so/0xafb32000/675603
DSO libgps.so/0xafa99000/604961
DSO libbasicIngest.so/0xaf9c1000/836451
DSO libgooglesearch.so/0xaf911000/695391

Any ideas? (It's Google Earth (Version 4 - BETA))

---

### Post by taurus on 2006-11-09
Are you using Breezy, Dapper, or Edgy?  And did you install googleearth by hand or did you install it from automatix2?

---

### Post by Atomic Dog on 2006-11-09
Google Earth is really twitchy for me.  It does start but is all messed up till I rezise the screen.  I guess there's a reason they are calling it a beta!

---

### Post by Eremit on 2006-11-10
I'm using edgy and installed it by hand.

Seems the problem is the nvidia-glx + modified kernel-modules from the amaranth repos.

I switched back to packages from ubuntu repos and now google-earth works without problems - the drawback is no beryl anymore :(

---

### Post by gala on 2006-11-16
The solution at following link solved the problem.

[http://bbs.keyhole.com/ubb/showthreaded.php/Cat/0/Number/683541/page/vc/vc/1]("http://bbs.keyhole.com/ubb/showthreaded.php/Cat/0/Number/683541/page/vc/vc/1")

---

### Post by tortsto on 2008-05-02
That fixed my problems with the old Google earth, but make sure to remove the file when upgrading to the current version (4.3).  And i'm referring to the post right above, where we rename libGL.so.1

---


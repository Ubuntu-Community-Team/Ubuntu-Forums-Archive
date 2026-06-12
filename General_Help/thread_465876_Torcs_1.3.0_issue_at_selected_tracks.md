---
title: "Torcs 1.3.0 issue at selected tracks"
date: 2007-06-06
forum: General Help
---

### Post by Miguel on 2007-06-06
Dear folks,

I've been racing somewhat in torcs, basically against Andrew Summers' nice robot, but I've found an issue. Whenever a session (practice/qualy/race) ends in a certain circuit, the game crashes. This wouldn't bother me much if it weren't for the fact that racing the AI in long championships requires qualy (crash) and two races (crash - crash) and that one of my favourite tracks and the best oval are amongst the "crashy tracks". So this is basically what I have done:
[list][*] I run torcs version 1.3.0, either vanilla or with trb1 car package and Andrew Summers'  bot.
[*] I have compiled it myself, with/without aggresive optimizations with/without architecture optimizations with/without -mfpmath=387 and with/without debugging symbols.
[*] To check my torcs tarball, I redownloaded (sourceforge), but md5 checksums coincide, so a corrupted download is bloody unlikely.
[*] I have also tested the binary package, which installs itself in /usr/local/games/torcs and you have to edit a file in there.
[/list]

And this is what happens:[list]
[*] Select any mode. 2 lap practice, with results only display is the most comfortable (the quickest), but this also happens in "quick race", "non-champ race", and "championship".
[*] Select one of these tracks: E-track 2, E-track 3, E-road, Michigan speedway. 
[*] The driver can be either you (human) or any berniw or Andrew's robots
[*] The race will run as normal but when the race ends (I'm not sure if it's the first or last driver, should check), torcs wil crash.
[/list]

 It seems to crash when unloading the driver's library, right after unloading simuv2.so. I fear this is either an issue of my system or an issue with Ubuntu's (I'm running Feisty) glibc, since the game crashes under such different conditions. In case anyone is interested, I have console logs from a normal run and a crash. I also have the full gdb log of a crash. Any clues? Does let's say e-track 3 work OK for you?

I should note that if you downloaded it, Andrew Summers' "Brondehach" will also crash, although Olethros Road 2 works OK.

*EDIT:* I will try to run torcs on my university's Debian Etch PC and report the results.

*EDIT 2:* Yes, I have tested every single track available in default torcs.

---

### Post by Miguel on 2007-06-07
I'm bumping this one. However, to make the bump more interesting, I'll post my logs.

This is what I get after a normal race in a normal track:
```

Merging "" and "drivers/berniw/4/g-track-1.xml" (SRC - DST)
parmReleaseHandle: release "" (0x925f470)
parmReleaseHeader: refcount null free ""
parmReleaseHandle: release "drivers/berniw/4/g-track-1.xml" (0x925f180)
parmReleaseHeader: refcount null free "drivers/berniw/4/g-track-1.xml"
1 drivers ready to race
Cars per pit: 1
Pit 0, Team: berniw, 0: berniw 4 
GfParmReadFile: Openning "/home/miguel/.torcs/config/screen.xml" (0x925f5b0)
parmReleaseHandle: release "/home/miguel/.torcs/config/screen.xml" (0x925f5b0)
Initializing Driver berniw 4...
Running Prestart...
Ready.
GfParmReadFile: Openning "/home/miguel/.torcs/config/graph.xml" (0x926d6f0)
RaceEngine: state = RE_STATE_RACE_END
parmReleaseHandle: release "drivers/berniw/berniw.xml" (0x8b43c20)
parmReleaseHeader: refcount null free "drivers/berniw/berniw.xml"
<<< /usr/local/lib/torcs/modules/simu/simuv2.so unloaded <<<
<<< /usr/local/lib/torcs/drivers/berniw/berniw.so unloaded <<<
GfParmReadFile: Openning "/home/miguel/.torcs/config/screen.xml" (0x8b43948)
parmReleaseHandle: release "/home/miguel/.torcs/config/screen.xml" (0x8b43948)

```

And this is what I get after finishing the race in the tracks mentioned in the first post:
```
Merging "" and "drivers/berniw/4/eroad.xml" (SRC - DST)
parmReleaseHandle: release "" (0x8d722f8)
parmReleaseHeader: refcount null free ""
parmReleaseHandle: release "drivers/berniw/4/eroad.xml" (0x8d72520)
parmReleaseHeader: refcount null free "drivers/berniw/4/eroad.xml"
1 drivers ready to race
Cars per pit: 1
Pit 0, Team: berniw, 0: berniw 4 
GfParmReadFile: Openning "/home/miguel/.torcs/config/screen.xml" (0x925f5b0)
parmReleaseHandle: release "/home/miguel/.torcs/config/screen.xml" (0x925f5b0)
Initializing Driver berniw 4...
Running Prestart...
Ready.
GfParmReadFile: Openning "/home/miguel/.torcs/config/graph.xml" (0x926f3f8)
RaceEngine: state = RE_STATE_RACE_END
parmReleaseHandle: release "drivers/berniw/berniw.xml" (0x8d72058)
parmReleaseHeader: refcount null free "drivers/berniw/berniw.xml"
<<< /usr/local/lib/torcs/modules/simu/simuv2.so unloaded <<<
*** glibc detected *** /usr/local/lib/torcs/torcs-bin: free(): invalid pointer: 0x08059cc0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb75b87cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb75bbe30]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb777ad11]
/usr/local/lib/torcs/modules/simu/simuv2.so[0xad5fa246]
/lib/tls/i686/cmov/libc.so.6(__cxa_finalize+0xa9)[0xb757dcc9]
/usr/local/lib/torcs/modules/simu/simuv2.so[0xad5f2343]
/usr/local/lib/torcs/modules/simu/simuv2.so[0xad60764c]
/lib/ld-linux.so.2[0xb7f94afd]
/lib/ld-linux.so.2[0xb7f95287]
/lib/tls/i686/cmov/libdl.so.2[0xb798fcc4]
/lib/ld-linux.so.2[0xb7f8ffa6]
/lib/tls/i686/cmov/libdl.so.2[0xb79902ac]
/lib/tls/i686/cmov/libdl.so.2(dlclose+0x2a)[0xb798fcfa]
/usr/local/lib/torcs/torcs-bin[0x804a1e8]
/usr/local/lib/torcs/lib/libtgf.so(_Z15GfModUnloadListPP7ModList+0x2c)[0xb7f3ffbc]
/usr/local/lib/torcs/lib/libraceengine.so(_Z18ReRaceCleanDriversv+0xe6)[0xb7ef9036]
/usr/local/lib/torcs/lib/libraceengine.so(_Z13ReRaceCleanupv+0x53)[0xb7ef9173]
/usr/local/lib/torcs/lib/libraceengine.so(_Z9ReRaceEndv+0x30)[0xb7efb320]
/usr/local/lib/torcs/lib/libraceengine.so(_Z13ReStateManagev+0x223)[0xb7efd873]
/usr/local/lib/torcs/lib/libraceengine.so[0xb7efdbf7]
/usr/lib/libglut.so.3[0xb7afe066]
/usr/lib/libglut.so.3(fgEnumWindows+0x42)[0xb7b0135e]
/usr/lib/libglut.so.3(glutMainLoopEvent+0x582)[0xb7afe8c5]
/usr/lib/libglut.so.3(glutMainLoop+0x51)[0xb7afed55]
/usr/local/lib/torcs/torcs-bin(__gxx_personality_v0+0x1a8)[0x8048ea0]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7566ebc]
/usr/local/lib/torcs/torcs-bin(__gxx_personality_v0+0x79)[0x8048d71]
======= Memory map: ========
08048000-0804b000 r-xp 00000000 03:03 264814     /usr/local/lib/torcs/torcs-bin
0804b000-0804c000 rw-p 00002000 03:03 264814     /usr/local/lib/torcs/torcs-bin
0804c000-0942c000 rw-p 0804c000 00:00 0          [heap]
acc39000-ace3b000 rw-p acc39000 00:00 0 
ad200000-ad221000 rw-p ad200000 00:00 0 
ad221000-ad300000 ---p ad221000 00:00 0 
ad33d000-ad37c000 rw-p ae260000 00:00 0 
ad46d000-ad48d000 rw-s 02fd9000 00:0d 16960      /dev/dri/card0
ad4cd000-ad4ed000 rw-s 02fe8000 00:0d 16960      /dev/dri/card0
ad56d000-ad58d000 rw-s 02fe2000 00:0d 16960      /dev/dri/card0
ad59f000-ad5af000 rw-s 0325b000 00:0d 16960      /dev/dri/card0
ad5af000-ad5b0000 rw-p ad5af000 00:00 0 
ad5bb000-ad5db000 rw-s 0325a000 00:0d 16960      /dev/dri/card0
ad5db000-ad5ea000 r-xp 00000000 03:03 263444     /usr/local/lib/torcs/drivers/berniw/berniw.so
ad5ea000-ad5eb000 rw-p 0000e000 03:03 263444     /usr/local/lib/torcs/drivers/berniw/berniw.so
ad5eb000-ad60b000 r-xp 00000000 03:03 476773     /usr/local/lib/torcs/modules/simu/simuv2.so
ad60b000-ad60c000 rw-p 0001f000 03:03 476773     /usr/local/lib/torcs/modules/simu/simuv2.so
ad60c000-ad60d000 rw-p ad60c000 00:00 0 
ad60d000-ad70d000 rw-s 00000000 00:12 72771      /dev/shm/ATISHM00
ad70e000-ad72e000 rw-s 02fe7000 00:0d 16960      /dev/dri/card0
ad72f000-ad730000 rw-p ad72f000 00:00 0 
ad730000-ad770000 rw-s 03259000 00:0d 16960      /dev/dri/card0
ad770000-ad7b0000 rw-s 0312d000 00:0d 16960      /dev/dri/card0
ad7b0000-ad7f0000 rw-s 02fde000 00:0d 16960      /dev/dri/card0
ad7f0000-ad83b000 r-xp 00000000 03:03 476771     /usr/local/lib/torcs/modules/graphic/ssggraph.so
ad83b000-ad83d000 rw-p 0004b000 03:03 476771     /usr/local/lib/torcs/modules/graphic/ssggraph.so
ad83d000-ad842000 rw-p ad83d000 00:00 0 
ad842000-ad862000 rw-s 02fdd000 00:0d 16960      /dev/dri/card0
ad862000-ad882000 rw-s 02fdc000 00:0d 16960      /dev/dri/card0
ad882000-ad8a2000 rw-s 02fdb000 00:0d 16960      /dev/dri/card0
ad8a2000-ad8e2000 rw-s 02fda000 00:0d 16960      /dev/dri/card0
ad8e2000-adcca000 rw-s 0000b000 00:0d 16960      /dev/dri/card0
adcca000-ae0b2000 rw-s 0000a000 00:0d 16960      /dev/dri/card0
ae0b2000-ae217000 rw-p ae0b2000 00:00 0 
ae219000-ae228000 r-xp 00000000 03:03 476779     /usr/local/lib/torcs/modules/track/track.so
ae228000-ae229000 rw-p 0000e000 03:03 476779     /usr/local/lib/torcs/modules/track/track.so
ae229000-ae22a000 rw-p ae229000 00:00 0 
ae231000-ae24b000 rw-p ae231000 00:00 0 
ae24b000-ae25d000 rw-p ae24b000 00:00 0 
ae25d000-ae260000 rw-s 02fd5000 00:0d 16960      /dev/dri/card0
ae260000-ae2a6000 rw-p ae260000 00:00 0 
ae2a6000-ae3e6000 rw-s 02fd2000 00:0d 16960      /dev/dri/card0
ae3e6000-aea26000 rw-s 00007000 00:0d 16960      /dev/dri/card0
aea26000-aeb26000 rw-s 00006000 00:0d 16960      /dev/dri/card0
aeb26000-aeb36000 rw-s 00004000 00:0d 16960      /dev/dri/card0
aeb36000-b6b36000 rw-s 00003000 00:0d 16960      /dev/dri/card0
b6b36000-b6be6000 r-xp 00000000 03:03 34993      /usr/lib/libstdc++.so.5.0.7
b6be6000-b6beb000 rw-p 000af000 03:03 34993      /usr/lib/libstdc++.so.5.0.7
b6beb000-b6bf1000 rw-p b6beb000 00:00 0 
b6bf1000-b6bf7000 rw-p b6bf1000 00:00 0 
b6bf7000-b6bfe000 rwxp b6bf7000 00:00 0 
b6bfe000-b745b000 r-xp 00000000 03:03 1261572    /usr/lib/dri/fglrx_dri.so
b745b000-b74a5000 rw-p 0085d000 03:03 1261572    /usr/lib/dri/fglrx_dri.so
b74a5000-b7532000 rw-p b74a5000 00:00 0 
b7532000-b7536000 r-xp 00000000 03:03 34297      /usr/lib/libXdmcp.so.6.0.0
b7536000-b7537000 rw-p 00003000 03:03 34297      /usr/lib/libXdmcp.so.6.0.0
b7537000-b7539000 r-xp 00000000 03:03 34286      /usr/lib/libXau.so.6.0.0
b7539000-b753a000 rw-p 00001000 03:03 34286      /usr/lib/libXau.so.6.0.0
b753a000-b754d000 r-xp 00000000 03:03 164722     /lib/tls/i686/cmov/libpthread-2.5.so
b754d000-b754f000 rw-p 00013000 03:03 164722     /lib/tls/i686/cmov/libpthread-2.5.so
b754f000-b7551000 rw-p b754f000 00:00 0 
b7551000-b768c000 r-xp 00000000 03:03 164159     /lib/tls/i686/cmov/libc-2.5.so
b768c000-b768d000 r--p 0013b000 03:03 164159     /lib/tls/i686/cmov/libc-2.5.so
b768d000-b768f000 rw-p 0013c000 03:03 164159     /lib/tls/i686/cmov/libc-2.5.so
b768f000-b7693000 rw-p b768f000 00:00 0 
b7693000-b769e000 r-xp 00000000 03:03 166746     /lib/libgcc_s.so.1
b769e000-b769f000 rw-p 0000a000 03:03 166746     /lib/libgcc_s.so.1
b769f000-b76c4000 r-xp 00000000 03:03 164163     /lib/tls/i686/cmov/libm-2.5.so
b76c4000-b76c6000 rw-p 00024000 03:03 164163     /lib/tls/i686/cmov/libm-2.5.so
b76c6000-b77a5000 r-xp 00000000 03:03 33084      /usr/lib/libstdc++.so.6.0.8
b77a5000-b77a8000 r--p 000de000 03:03 33084      /usr/lib/libstdc++.so.6.0.8
b77a8000-b77aa000 rw-p 000e1000 03:03 33084      /usr/lib/libstdc++.so.6.0.8
b77aa000-b77b0000 rw-p b77aa000 00:00 0 
b77b0000-b789d000 r-xp 00000000 03:03 35909      /usr/lib/libX11.so.6.2.0
b789d000-b78a1000 rw-p 000ed000 03:03 35909      /usr/lib/libX11.so.6.2.0
b78a1000-b78ae000 r-xp 00000000 03:03 34301      /usr/lib/libXext.so.6.4.0
b78ae000-b78af000 rw-p 0000d000 03:03 34301      /usr/lib/libXext.so.6.4.0
b78af000-b78c4000 r-xp 00000000 03:03 34258      /usr/lib/libICE.so.6.3.0
b78c4000-b78c6000 rw-p 00014000 03:03 34258      /usr/lib/libICE.so.6.3.0
b78c6000-b78c8000 rw-p b78c6000 00:00 0 
b78c8000-b78d0000 r-xp 00000000 03:03 34276      /usr/lib/libSM.so.6.0.0
b78d0000-b78d1000 rw-p 00007000 03:03 34276      /usr/lib/libSM.so.6.0.0
b78d1000-b791e000 r-xp 00000000 03:03 34327      /usr/lib/libXt.so.6.0.0
b791e000-b7922000 rw-p 0004c000 03:03 34327      /usr/lib/libXt.so.6.0.0
b7922000-b7929000 r-xp 00000000 03:03 34309      /usr/lib/libXi.so.6.0.0
b7929000-b792a000 rw-p 00006000 03:03 34309      /usr/lib/libXi.so.6.0.0
b792a000-b793f000 r-xp 00000000 03:03 33754      /usr/lib/libXmu.so.6.2.0
b793f000-b7940000 rw-p 00015000 03:03 33754      /usr/lib/libXmu.so.6.2.0
b7940000-b7944000 r-xp 00000000 03:03 34337      /usr/lib/libXxf86vm.so.1.0.0
b7944000-b7945000 rw-p 00003000 03:03 34337      /usr/lib/libXxf86vm.so.1.0.0
b7945000-b794c000 r-xp 00000000 03:03 34323      /usr/lib/libXrender.so.1.3.0
b794c000-b794d000 rw-p 00006000 03:03 34323      /usr/lib/libXrender.so.1.3.0
b794d000-b794e000 rw-p b794d000 00:00 0 
b794e000-b7953000 r-xp 00000000 03:03 34321      /usr/lib/libXrandr.so.2.1.0
b7953000-b7954000 rw-p 00005000 03:03 34321      /usr/lib/libXrandr.so.2.1.0
b7954000-b798a000 r-xp 00000000 03:03 38771      /usr/lib/libopenal.so.0.0.0
b798a000-b798b000 rw-p 00036000 03:03 38771      /usr/lib/libopenal.so.0.0.0
b798b000-b798f000 rw-p b798b000 00:00 0 
b798f000-b7991000 r-xp 00000000 03:03 164162     /lib/tls/i686/cmov/libdl-2.5.so
b7991000-b7993000 rw-p 00001000 03:03 164162     /lib/tls/i686/cmov/libdl-2.5.so
b7993000-b79a6000 r-xp 00000000 03:03 32799      /usr/lib/libz.so.1.2.3
b79a6000-b79a7000 rw-p 00012000 03:03 32799      /usr/lib/libz.so.1.2.3
b79a7000-b79c9000 r-xp 00000000 03:03 34913      /usr/lib/libpng12.so.0.15.0
b79c9000-b79ca000 rw-p 00021000 03:03 34913      /usr/lib/libpng12.so.0.15.0
b79ca000-b7a62000 r-xp 00000000 03:03 1441800    /usr/lib/libGL.so.1.2
b7a62000-b7a67000 rw-p 00098000 03:03 1441800    /usr/lib/libGL.so.1.2
b7a67000-b7a6b000 rw-p b7a67000 00:00 0 
b7a6b000-b7aea000 r-xp 00000000 03:03 35410      /usr/lib/libGLU.so.1.3.060502
b7aea000-b7aeb000 rw-p 0007e000 03:03 35410      /usr/lib/libGLU.so.1.3.060502
b7aeb000-b7b18000 r-xp 00000000 03:03 34601      /usr/lib/libglut.so.3.8.0
b7b18000-b7b1d000 rw-p 0002c000 03:03 34601      /usr/lib/libglut.so.3.8.0
b7b1d000-b7b2e000 r-xp 00000000 03:03 39434      /usr/lib/libplibsg.so.1.8.4
b7b2e000-b7b2f000 rw-p 00010000 03:03 39434      /usr/lib/libplibsg.so.1.8.4
b7b2f000-b7b3e000 r-xp 00000000 03:03 39435      /usr/lib/libplibsl.so.1.8.4
b7b3e000-b7b3f000 rw-p 0000e000 03:03 39435      /usr/lib/libplibsl.so.1.8.4
b7b3f000-b7b4e000 rw-p b7b3f000 00:00 0 
b7b4e000-b7b50000 r-xp 00000000 03:03 39436      /usr/lib/libplibsm.so.1.8.4
b7b50000-b7b51000 rw-p 00001000 03:03 39436      /usr/lib/libplibsm.so.1.8.4
b7b51000-b7bed000 r-xp 00000000 03:03 39441      /usr/lib/libplibssg.so.1.8.4
b7bed000-b7bf2000 rw-p 0009c000 03:03 39441      /usr/lib/libplibssg.so.1.8.4
b7bf2000-b7eb0000 rw-p b7bf2000 00:00 0 
b7eb0000-b7ed9000 r-xp 00000000 03:03 39444      /usr/lib/libplibssgaux.so.1.8.4
b7ed9000-b7ee3000 rw-p 00029000 03:03 39444      /usr/lib/libplibssgaux.so.1.8.4
b7ee3000-b7ef3000 r-xp 00000000 03:03 476755     /usr/local/lib/torcs/lib/liblearning.so
b7ef3000-b7ef4000 rw-p 00010000 03:03 476755     /usr/local/lib/torcs/lib/liblearning.so
b7ef4000-b7ef6000 rw-p b7ef4000 00:00 0 
b7ef6000-b7f04000 r-xp 00000000 03:03 476759     /usr/local/lib/torcs/lib/libraceengine.so
b7f04000-b7f05000 rw-p 0000d000 03:03 476759     /usr/local/lib/torcs/lib/libraceengine.so
b7f05000-b7f08000 rw-p b7f05000 00:00 0 
b7f08000-b7f0c000 r-xp 00000000 03:03 39442      /usr/lib/libplibul.so.1.8.4
b7f0c000-b7f0d000 rw-p 00003000 03:03 39442      /usr/lib/libplibul.so.1.8.4
b7f0d000-b7f24000 r-xp 00000000 03:03 476766     /usr/local/lib/torcs/lib/libtxml.so
b7f24000-b7f25000 rw-p 00017000 03:03 476766     /usr/local/lib/torcs/lib/libtxml.so
b7f25000-b7f26000 rw-p b7f25000 00:00 0 
b7f26000-b7f3c000 r-xp 00000000 03:03 476765     /usr/local/lib/torcs/lib/libtgfclient.so
b7f3c000-b7f3d000 rw-p 00016000 03:03 476765     /usr/local/lib/torcs/lib/libtgfclient.so
b7f3d000-b7f3e000 rw-p b7f3d000 00:00 0 
b7f3e000-b7f47000 r-xp 00000000 03:03 476763     /usr/local/lib/torcs/lib/libtgf.so
b7f47000-b7f48000 rw-p 00009000 03:03 476763     /usr/local/lib/torcs/lib/libtgf.so
b7f48000-b7f53000 r-xp 00000000 03:03 476754     /usr/local/lib/torcs/lib/libconfscreens.so
b7f53000-b7f55000 rw-p 0000a000 03:03 476754     /usr/local/lib/torcs/lib/libconfscreens.so
b7f55000-b7f56000 rw-p b7f55000 00:00 0 
b7f56000-b7f58000 r-xp 00000000 03:03 476753     /usr/local/lib/torcs/lib/libclient.so
b7f58000-b7f59000 rw-p 00002000 03:03 476753     /usr/local/lib/torcs/lib/libclient.so
b7f59000-b7f5c000 r-xp 00000000 03:03 476761     /usr/local/lib/torcs/lib/librobottools.so
b7f5c000-b7f5d000 rw-p 00002000 03:03 476761     /usr/local/lib/torcs/lib/librobottools.so
b7f5d000-b7f5e000 rw-p b7f5d000 00:00 0 
b7f5e000-b7f69000 r-xp 00000000 03:03 476760     /usr/local/lib/torcs/lib/libracescreens.so
b7f69000-b7f6a000 rw-p 0000a000 03:03 476760     /usr/local/lib/torcs/lib/libracescreens.so
b7f6a000-b7f6c000 rw-p b7f6a000 00:00 0 
b7f6c000-b7f70000 r-xp 00000000 03:03 38773      /usr/lib/libalut.so.0.0.0
b7f70000-b7f73000 rw-p 00003000 03:03 38773      /usr/lib/libalut.so.0.0.0
b7f73000-b7f74000 rw-p b7f73000 00:00 0 
b7f74000-b7f75000 rw-s 00005000 00:0d 16960      /dev/dri/card0
b7f75000-b7f77000 rw-s 00002000 00:0d 16960      /dev/dri/card0
b7f77000-b7f7e000 r-xp 00000000 03:03 164724     /lib/tls/i686/cmov/librt-2.5.so
b7f7e000-b7f80000 rw-p 00006000 03:03 164724     /lib/tls/i686/cmov/librt-2.5.so
b7f80000-b7f83000 rw-p b7f80000 00:00 0 
b7f83000-b7f9c000 r-xp 00000000 03:03 164047     /lib/ld-2.5.so
b7f9c000-b7f9e000 rw-p 00019000 03:03 164047     /lib/ld-2.5.so
bff5a000-bff6e000 rwxp bff5a000 00:00 0          [stack]
bff6e000-bff6f000 rw-p bff6e000 00:00 0 
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
/usr/local/bin/torcs: line 52: 22557 Cancelado               $LIBDIR/torcs-bin -l $LOCAL_CONF -L $LIBDIR -D $DATADIR $*

```

Note there is lots of debugging garbage. The error message seems to be "*** glibc detected *** /usr/local/lib/torcs/torcs-bin: free(): invalid pointer: 0x08059cc0 ***" I also have the gdb output, but that is a bit too much, and I don't want to scare any potential helper.

Thanks in advance,

Miguel

---

### Post by Miguel on 2007-06-07
Well, I have additional info. I have installed the precompiled binary in my Debian Lenny (Testing) pc and it works OK. Not only it doesn't crash in the previously mentioned tracks, but it runs much faster in "results only" mode. Actually, it runs as fast as it used to run in my laptop (the buggy machine).

Fearing it would be an issue with either libc6 or my memory, I have reinstalled libc6, libc6-dev and libc6-i686. I have also run memtest, although it's been one pass only. The result? Same place, same crash. Shall I move this thread elsewhere?

Could anyone install torcs 1.3.0 and tell me their behaviour? Thanks in advance,

Miguel

Oh!, and in case you wonder, the speed difference isn't due to different processors, as both machines run my DFT code (FORTRAN 90, floating point) at a very similar pace.

---

### Post by Miguel on 2007-06-09
Is there anybody interested in the gdb output? Else I think I'd better contact Bernhard and the other Torcs developers. Thanks in advance,

Miguel

---

### Post by Miguel on 2007-06-18
Hi guys,

Just thought I'll bump this once more before reporting a bug.

---

### Post by Miguel on 2007-06-20
Good news!

I've solved it with the help from the guy. It is a conflict between these tracks and the version of fglrx available on the repositories. I'm off to fill a launchpad bug and then I will try to see if the issue also appears with the newest fglrx.

---


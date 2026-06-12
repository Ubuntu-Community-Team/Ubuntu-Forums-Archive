---
title: "Cheese Webcam Recording Issues"
date: 2012-12-21
forum: General Help
---

### Post by coreybell on 2012-12-21
Hey I am having issues with my cheese webcam in Ubuntu 12.10. Here is the issue I am having, I can open the program fine, and take photos without a problem, but when I go to record a video, I press record and it crashes all of the sudden. Can anyone help me with this. I am using a external webcam, when I had Ubuntu 12.04 cheese worked fine, no problems? 

I have opened it from the terminal, and it did the same thing, but here is the code that I copied to see if I can get some help with it, please see below: 

Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started

(cheese:5321): cheese-WARNING **: Jack server not found


(cheese:5321): cheese-WARNING **: Could not initialize supporting library.

*** glibc detected *** cheese: free(): invalid pointer: 0xb7798759 ***
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(+0x75ee2)[0xb6b13ee2]
/lib/i386-linux-gnu/libglib-2.0.so.0(+0x4cb3b)[0xb6cafb3b]
/lib/i386-linux-gnu/libglib-2.0.so.0(g_free+0x20)[0xb6cafcb0]
cheese[0x8055247]
/lib/i386-linux-gnu/libglib-2.0.so.0(+0x476bf)[0xb6caa6bf]
/lib/i386-linux-gnu/libglib-2.0.so.0(g_main_context_dispatch+0x143)[0xb6ca99e3]
/lib/i386-linux-gnu/libglib-2.0.so.0(+0x46d80)[0xb6ca9d80]
/lib/i386-linux-gnu/libglib-2.0.so.0(g_main_context_iteration+0x41)[0xb6ca9e61]
/usr/lib/i386-linux-gnu/libgio-2.0.so.0(g_application_run+0x1cc)[0xb6e6cb3c]
cheese(_vala_main+0xb2)[0x805da72]
cheese(main+0x2c)[0x80518ac]
/lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xf3)[0xb6ab74d3]
cheese[0x80518d1]
======= Memory map: ========
08048000-08069000 r-xp 00000000 08:01 527959     /usr/bin/cheese
08069000-0806a000 r--p 00020000 08:01 527959     /usr/bin/cheese
0806a000-0806b000 rw-p 00021000 08:01 527959     /usr/bin/cheese
09212000-09be9000 rw-p 00000000 00:00 0          [heap]
a4452000-a4453000 ---p 00000000 00:00 0 
a4453000-a44d3000 rw-p 00000000 00:00 0 
a44d3000-a46d3000 rw-s 1c402000 00:05 7440       /dev/dri/card0
a46d3000-a48d3000 rw-s 1c202000 00:05 7440       /dev/dri/card0
a48d3000-a4ad3000 rw-s 1bff5000 00:05 7440       /dev/dri/card0
a4ad3000-a4cd3000 rw-s 1bdf5000 00:05 7440       /dev/dri/card0
a4cd3000-a4e00000 rw-p 00000000 00:00 0 
a4e46000-a4e94000 r-xp 00000000 08:01 529427     /usr/lib/i386-linux-gnu/libjack.so.0.1.0
a4e94000-a4e96000 r--p 0004d000 08:01 529427     /usr/lib/i386-linux-gnu/libjack.so.0.1.0
a4e96000-a4e97000 rw-p 0004f000 08:01 529427     /usr/lib/i386-linux-gnu/libjack.so.0.1.0
a4e97000-a4ea7000 rw-s 00000000 08:01 1310763    /tmp/orcexec.4Hqe13 (deleted)
a4ea7000-a4eb7000 r-xs 00000000 08:01 1310763    /tmp/orcexec.4Hqe13 (deleted)
a4eb7000-a4fe4000 rw-p 00000000 00:00 0 
a501f000-a5027000 r-xp 00000000 08:01 526929     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstossaudio.so
a5027000-a5028000 r--p 00007000 08:01 526929     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstossaudio.so
a5028000-a5029000 rw-p 00008000 08:01 526929     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstossaudio.so
a5029000-a507b000 r--p 00000000 08:01 1184873    /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-B.ttf
a507b000-a5111000 rw-s 001c2000 00:05 78215      /dev/video0
a5111000-a51a7000 rw-s 0012c000 00:05 78215      /dev/video0
a51a7000-a523d000 rw-s 00096000 00:05 78215      /dev/video0
a523d000-a52d3000 rw-s 00000000 00:05 78215      /dev/video0
a52d3000-a5cd3000 rwxp 00000000 00:00 0 
a5cd3000-a5d16000 r-xp 00000000 08:01 527755     /usr/lib/i386-linux-gnu/libibus-1.0.so.0.401.0
a5d16000-a5d17000 r--p 00043000 08:01 527755     /usr/lib/i386-linux-gnu/libibus-1.0.so.0.401.0
a5d17000-a5d18000 rw-p 00044000 08:01 527755     /usr/lib/i386-linux-gnu/libibus-1.0.so.0.401.0
a5d18000-a5d6a000 r--p 00000000 08:01 1178188    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
a5d6a000-a5d6b000 ---p 00000000 00:00 0 
a5d6b000-a656b000 rw-p 00000000 00:00 0          [stack:5333]
a656b000-a656c000 ---p 00000000 00:00 0 
a656c000-a6d6c000 rw-p 00000000 00:00 0          [stack:5332]
a6d6c000-a6d6d000 ---p 00000000 00:00 0 
a6d6d000-a756d000 rw-p 00000000 00:00 0          [stack:5331]
a756d000-a756e000 ---p 00000000 00:00 0 
a756e000-a7d6e000 rw-p 00000000 00:00 0          [stack:5330]
a7d6e000-a7d6f000 ---p 00000000 00:00 0 
a7d6f000-a856f000 rw-p 00000000 00:00 0          [stack:5329]
a856f000-a8570000 ---p 00000000 00:00 0 
a8570000-a8d70000 rw-p 00000000 00:00 0          [stack:5328]
a8d70000-a8d71000 ---p 00000000 00:00 0 
a8d71000-a9571000 rw-p 00000000 00:00 0          [stack:5327]
a9571000-a9572000 ---p 00000000 00:00 0 
a9572000-a9d72000 rw-p 00000000 00:00 0          [stack:5326]
a9d72000-a9d78000 r-xp 00000000 08:01 528173     /usr/lib/i386-linux-gnu/liborc-test-0.4.so.0.16.0
a9d78000-a9d79000 r--p 00005000 08:01 528173     /usr/lib/i386-linux-gnu/liborc-test-0.4.so.0.16.0
a9d79000-a9d7a000 rw-p 00006000 08:01 528173     /usr/lib/i386-linux-gnu/liborc-test-0.4.so.0.16.0
a9d83000-a9d8e000 r-xp 00000000 08:01 526984     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstoss4audio.so
a9d8e000-a9d8f000 r--p 0000a000 08:01 526984     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstoss4audio.so
a9d8f000-a9d90000 rw-p 0000b000 08:01 526984     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstoss4audio.so
a9d90000-a9d9f000 r-xp 00000000 08:01 526361     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudioresample.so
a9d9f000-a9da0000 r--p 0000e000 08:01 526361     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudioresample.so
a9da0000-a9da2000 rw-p 0000f000 08:01 526361     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudioresample.so
a9da2000-a9dba000 r-xp 00000000 08:01 526330     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudioconvert.so
a9dba000-a9dbb000 r--p 00017000 08:01 526330     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudioconvert.so
a9dbb000-a9dbc000 rw-p 00018000 08:01 526330     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudioconvert.so
a9dbc000-a9f22000 r-xp 00000000 08:01 527749     /usr/lib/i386-linux-gnu/libvorbisenc.so.2.0.8
a9f22000-a9f33000 r--p 00165000 08:01 527749     /usr/lib/i386-linux-gnu/libvorbisenc.so.2.0.8
a9f33000-a9f34000 rw-p 00176000 08:01 527749     /usr/lib/i386-linux-gnu/libvorbisenc.so.2.0.8
a9f34000-a9f40000 r-xp 00000000 08:01 527132     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjack.so
a9f40000-a9f41000 r--p 0000b000 08:01 527132     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjack.so
a9f41000-a9f42000 rw-p 0000c000 08:01 527132     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjack.so
a9f42000-a9f48000 r-xp 00000000 08:01 523785     /usr/lib/i386-linux-gnu/gtk-3.0/3.0.0/immodules/im-ibus.so
a9f48000-a9f49000 r--p 00005000 08:01 523785     /usr/lib/i386-linux-gnu/gtk-3.0/3.0.0/immodules/im-ibus.so
a9f49000-a9f4a000 rw-p 00006000 08:01 523785     /usr/lib/i386-linux-gnu/gtk-3.0/3.0.0/immodules/im-ibus.so
a9f4a000-a9f55000 r-xp 00000000 08:01 526367     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvorbis.so
a9f55000-a9f56000 r--p 0000a000 08:01 526367     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvorbis.so
a9f56000-a9f57000 rw-p 0000b000 08:01 526367     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvorbis.so
a9f57000-a9f66000 r-xp 00000000 08:01 2094017    /lib/i386-linux-gnu/libbz2.so.1.0.4
a9f66000-a9f67000 r--p 0000e000 08:01 2094017    /lib/i386-linux-gnu/libbz2.so.1.0.4
a9f67000-a9f68000 rw-p 0000f000 08:01 2094017    /lib/i386-linux-gnu/libbz2.so.1.0.4
a9f68000-a9f75000 r-xp 00000000 08:01 526212     /usr/lib/i386-linux-gnu/libgstriff-1.0.so.0.1.0
a9f75000-a9f76000 r--p 0000c000 08:01 526212     /usr/lib/i386-linux-gnu/libgstriff-1.0.so.0.1.0
a9f76000-a9f77000 rw-p 0000d000 08:01 526212     /usr/lib/i386-linux-gnu/libgstriff-1.0.so.0.1.0
a9f79000-a9f7f000 r-xp 00000000 08:01 526789     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideocrop.so
a9f7f000-a9f80000 r--p 00005000 08:01 526789     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideocrop.so
a9f80000-a9f81000 rw-p 00006000 08:01 526789     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideocrop.so
a9f81000-a9f8b000 r-xp 00000000 08:01 527302     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjpeg.so
a9f8b000-a9f8c000 r--p 00009000 08:01 527302     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjpeg.so
a9f8c000-a9f8d000 rw-p 0000a000 08:01 527302     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjpeg.so
a9f8d000-a9fd2000 r-xp 00000000 08:01 526519     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstmatroska.so
a9fd2000-a9fd3000 r--p 00044000 08:01 526519     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstmatroska.so
a9fd3000-a9fd4000 rw-p 00045000 08:01 526519     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstmatroska.so
a9fd4000-a9fdf000 r-xp 00000000 08:01 526460     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstmultifile.so
a9fdf000-a9fe0000 r--p 0000a000 08:01 526460     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstmultifile.so
a9fe0000-a9fe1000 rw-p 0000b000 08:01 526460     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstmultifile.so
a9fe1000-a9ff0000 r-xp 00000000 08:01 526401     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstencodebin.so
a9ff0000-a9ff1000 r--p 0000e000 08:01 526401     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstencodebin.so
a9ff1000-a9ff2000 rw-p 0000f000 08:01 526401     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstencodebin.so
a9ff2000-aa094000 r-xp 00000000 08:01 529384     /usr/lib/i386-linux-gnu/libvpx.so.1.1.0
aa094000-aa095000 r--p 000a1000 08:01 529384     /usr/lib/i386-linux-gnu/libvpx.so.1.1.0
aa095000-aa096000 rw-p 000a2000 08:01 529384     /usr/lib/i386-linux-gnu/libvpx.so.1.1.0
aa096000-aa098000 rw-p 00000000 00:00 0 
aa09b000-aa0a0000 r-xp 00000000 08:01 526409     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudiorate.so
aa0a0000-aa0a1000 r--p 00004000 08:01 526409     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudiorate.so
aa0a1000-aa0a2000 rw-p 00005000 08:01 526409     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudiorate.so
aa0a2000-aa0ab000 r-xp 00000000 08:01 527303     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideofilter.so
aa0ab000-aa0ac000 ---p 00009000 08:01 527303     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideofilter.so
aa0ac000-aa0ad000 r--p 00009000 08:01 527303     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideofilter.so
aa0ad000-aa0ae000 rw-p 0000a000 08:01 527303     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideofilter.so
aa0ae000-aa0bb000 r-xp 00000000 08:01 526446     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvpx.so
aa0bb000-aa0bc000 r--p 0000c000 08:01 526446     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvpx.so
aa0bc000-aa0bd000 rw-p 0000d000 08:01 526446     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvpx.so
aa0bd000-aa0da000 r-xp 00000000 08:01 526370     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideoscale.so
aa0da000-aa0db000 r--p 0001c000 08:01 526370     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideoscale.so
aa0db000-aa0dc000 rw-p 0001d000 08:01 526370     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideoscale.so
aa0dc000-aa0fa000 r-xp 00000000 08:01 526329     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideoconvert.so
aa0fa000-aa0fb000 ---p 0001e000 08:01 526329     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideoconvert.so
aa0fb000-aa0fc000 r--p 0001e000 08:01 526329     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideoconvert.so
aa0fc000-aa0fd000 rw-p 0001f000 08:01 526329     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideoconvert.so
aa0fd000-aa108000 r-xp 00000000 08:01 526238     /usr/lib/i386-linux-gnu/libgstapp-1.0.so.0.1.0
aa108000-aa109000 r--p 0000a000 08:01 526238     /usr/lib/i386-linux-gnu/libgstapp-1.0.so.0.1.0
aa109000-aa10a000 rw-p 0000b000 08:01 526238     /usr/lib/i386-linux-gnu/libgstapp-1.0.so.0.1.0
aa10a000-aa110000 r-xp 00000000 08:01 527309     /usr/lib/i386-linux-gnu/libgstbasecamerabinsrc-1.0.so.0.1.0
aa110000-aa111000 r--p 00005000 08:01 527309     /usr/lib/i386-linux-gnu/libgstbasecamerabinsrc-1.0.so.0.1.0
aa111000-aa112000 rw-p 00006000 08:01 527309     /usr/lib/i386-linux-gnu/libgstbasecamerabinsrc-1.0.so.0.1.0
aa112000-aa118000 r-xp 00000000 08:01 527306     /usr/lib/i386-linux-gnu/libgstphotography-1.0.so.0.1.0
aa118000-aa119000 r--p 00005000 08:01 527306     /usr/lib/i386-linux-gnu/libgstphotography-1.0.so.0.1.0
aa119000-aa11a000 rw-p 00006000 08:01 527306     /usr/lib/i386-linux-gnu/libgstphotography-1.0.so.0.1.0
aa11b000-aa123000 r-xp 00000000 08:01 526983     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstautodetect.so
aa123000-aa124000 r--p 00007000 08:01 526983     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstautodetect.so
aa124000-aa125000 rw-p 00008000 08:01 526983     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstautodetect.so
aa125000-aa12e000 r-xp 00000000 08:01 526340     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvolume.so
aa12e000-aa12f000 r--p 00008000 08:01 526340     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvolume.so
aa12f000-aa130000 rw-p 00009000 08:01 526340     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvolume.so
aa130000-aa17a000 r-xp 00000000 08:01 526157     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstcoreelements.so
aa17a000-aa17b000 r--p 00049000 08:01 526157     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstcoreelements.so
aa17b000-aa17c000 rw-p 0004a000 08:01 526157     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstcoreelements.so
aa17c000-aa1c1000 r-xp 00000000 08:01 528939     /usr/lib/i386-linux-gnu/libjpeg.so.8.0.2
aa1c1000-aa1c2000 r--p 00044000 08:01 528939     /usr/lib/i386-linux-gnu/libjpeg.so.8.0.2
aa1c2000-aa1c3000 rw-p 00045000 08:01 528939     /usr/lib/i386-linux-gnu/libjpeg.so.8.0.2
aa1c3000-aa1d3000 rw-p 00000000 00:00 0 
aa1d3000-aa1f7000 r-xp 00000000 08:01 528335     /usr/lib/i386-linux-gnu/libv4lconvert.so.0
aa1f7000-aa1f8000 r--p 00024000 08:01 528335     /usr/lib/i386-linux-gnu/libv4lconvert.so.0
aa1f8000-aa1f9000 rw-p 00025000 08:01 528335     /usr/lib/i386-linux-gnu/libv4lconvert.so.0
aa1f9000-aa24b000 rw-p 00000000 00:00 0 
aa24b000-aa34b000 rw-s 1cad4000 00:05 7440       /dev/dri/card0
aa34d000-aa356000 r-xp 00000000 08:01 527750     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjpegformat.so
aa356000-aa357000 r--p 00008000 08:01 527750     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjpegformat.so
aa357000-aa358000 rw-p 00009000 08:01 527750     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjpegformat.so
aa358000-aa360000 r-xp 00000000 08:01 528304     /usr/lib/i386-linux-gnu/libv4l2.so.0
aa360000-aa361000 r--p 00007000 08:01 528304     /usr/lib/i386-linux-gnu/libv4l2.so.0
aa361000-aa365000 rw-p 00008000 08:01 528304     /usr/lib/i386-linux-gnu/libv4l2.so.0
aa365000-aa369000 r-xp 00000000 08:01 524502     /usr/lib/i386-linux-gnu/libXv.so.1.0.0
aa369000-aa36a000 r--p 00003000 08:01 524502     /usr/lib/i386-linux-gnu/libXv.so.1.0.0
aa36a000-aa36b000 rw-p 00004000 08:01 524502     /usr/lib/i386-linux-gnu/libXv.so.1.0.0
aa36d000-aa37f000 r-xp 00000000 08:01 527386     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstcamerabin2.so
aa37f000-aa380000 r--p 00011000 08:01 527386     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstcamerabin2.so
aa380000-aa381000 rw-p 00012000 08:01 527386     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstcamerabin2.so
aa381000-aa3a5000 r-xp 00000000 08:01 526777     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideo4linux2.so
aa3a5000-aa3a6000 r--p 00023000 08:01 526777     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideo4linux2.so
aa3a6000-aa3a7000 rw-p 00024000 08:01 526777     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideo4linux2.so
aa3a7000-aa44c000 r--p 00000000 08:01 1178185    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
aa44c000-aa4fc000 r--p 00000000 08:01 1178186    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
aa4fc000-aa553000 r--p 00000000 08:01 1184874    /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf
aa553000-aa555000 r-xp 00000000 08:01 537535     /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
aa555000-aa556000 r--p 00001000 08:01 537535     /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
aa556000-aa557000 rw-p 00002000 08:01 537535     /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
aa557000-aa558000 r--s 00000000 08:01 927423     /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
aa558000-aa55e000 r--s 00000000 08:01 916230     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3Aborted

---

### Post by ajgreeny on 2012-12-21
This does not answer your question, but I have never ever managed to get cheese to record a video; photos, no problem, but video just gives me a still picture when played in totem, with an occasional but pointless slight movement in the picture showing.  I do not know if this is a result of my oldish slow machine, my logitech webcam (cheap and simple) or the old ATI video card using the open source driver.

However, if I use wxcam it produces great video at the same resolution as cheese is trying to produce.  Running cheese from terminal gives me no output at all, and therefore does not give any clues about why it is not working.

If you can't get cheese to work it could be worth trying wxcam, though a quick search that I've done does not find it for precise nor quantal, only for lucid which I'm still on at the moment..

---

### Post by BicyclerBoy on 2012-12-21
Another option is "guvcview".

Cheese has never worked very well, best thing to do with it is purge/remove.

Have you tried to capture audio from "jack" server?

You can test your webcam/gstreamer with "gstreamer-properties"

The lowest overhead webcam recording is likely ffmpeg:
ffmpeg -f alsa -i hw:0 -f video4linux2 -framerate 30 -video_size 640x480 -i /dev/video0 tmp.mpg

---

### Post by offgridguy on 2012-12-21
I have found cheese to be very hit and miss, when i start having issues i remove
it then reinstall , usually works for a while.

---

### Post by Filip II on 2012-12-22
I had the same problem with Cheese. It would crash when I wanted to record a video.
 I downloaded "guvcview" but it is not working properly either. When I play a captured video, the video itself is faster 50% in my case. If the video is 10 sec long, the saved video will finish in 5 sec and go on for 5 sec more(displaying only the ending of the video). 
 Did anyone have a similar problem?

---

### Post by BicyclerBoy on 2012-12-22
What format did you record in?
And what did you play it back with ?

---

### Post by coreybell on 2013-03-21
I Keep trying to use cheese webcam to take some videos, it takes photos fine, but every time I try to take a video, it crashes, can some one help please. Below is the Code I get when trying to run cheese video:

Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started


(cheese:14574): cheese-WARNING **: Jack server not found




(cheese:14574): cheese-WARNING **: Could not initialize supporting library.


*** glibc detected *** cheese: free(): invalid pointer: 0xb776b759 ***
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(+0x75ee2)[0xb6ae6ee2]
/lib/i386-linux-gnu/libglib-2.0.so.0(+0x4cb3b)[0xb6c82b3b]
/lib/i386-linux-gnu/libglib-2.0.so.0(g_free+0x20)[0xb6c82cb0]
cheese[0x8055247]
/lib/i386-linux-gnu/libglib-2.0.so.0(+0x476bf)[0xb6c7d6bf]
/lib/i386-linux-gnu/libglib-2.0.so.0(g_main_context_dispatch+0x143)[0xb6c7c9e3]
/lib/i386-linux-gnu/libglib-2.0.so.0(+0x46d80)[0xb6c7cd80]
/lib/i386-linux-gnu/libglib-2.0.so.0(g_main_context_iteration+0x41)[0xb6c7ce61]
/usr/lib/i386-linux-gnu/libgio-2.0.so.0(g_application_run+0x1cc)[0xb6e3fb3c]
cheese(_vala_main+0xb2)[0x805da72]
cheese(main+0x2c)[0x80518ac]
/lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xf3)[0xb6a8a4d3]
cheese[0x80518d1]
======= Memory map: ========
08048000-08069000 r-xp 00000000 fc:01 1185651    /usr/bin/cheese
08069000-0806a000 r--p 00020000 fc:01 1185651    /usr/bin/cheese
0806a000-0806b000 rw-p 00021000 fc:01 1185651    /usr/bin/cheese
08a4d000-095fa000 rw-p 00000000 00:00 0          [heap]
a7353000-a7517000 rw-p 00000000 00:00 0 
a7517000-a7518000 ---p 00000000 00:00 0 
a7518000-a7598000 rw-p 00000000 00:00 0 
a7598000-a7798000 rw-s 1b507000 00:05 7051       /dev/dri/card0
a7798000-a7998000 rw-s 136f7000 00:05 7051       /dev/dri/card0
a7998000-a7b98000 rw-s 1b307000 00:05 7051       /dev/dri/card0
a7b98000-a7d98000 rw-s 1b107000 00:05 7051       /dev/dri/card0
a7f0b000-a7f59000 r-xp 00000000 fc:01 1184907    /usr/lib/i386-linux-gnu/libjack.so.0.1.0
a7f59000-a7f5b000 r--p 0004d000 fc:01 1184907    /usr/lib/i386-linux-gnu/libjack.so.0.1.0
a7f5b000-a7f5c000 rw-p 0004f000 fc:01 1184907    /usr/lib/i386-linux-gnu/libjack.so.0.1.0
a7f5c000-a7f6c000 rw-s 00000000 fc:01 1572965    /tmp/orcexec.z19D0K (deleted)
a7f6c000-a7f7c000 r-xs 00000000 fc:01 1572965    /tmp/orcexec.z19D0K (deleted)
a80e4000-a80ec000 r-xp 00000000 fc:01 1185196    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstossaudio.so
a80ec000-a80ed000 r--p 00007000 fc:01 1185196    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstossaudio.so
a80ed000-a80ee000 rw-p 00008000 fc:01 1185196    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstossaudio.so
a80ee000-a8140000 r--p 00000000 fc:01 1839422    /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-B.ttf
a8140000-a81d6000 rw-s 001c2000 00:05 143949     /dev/video0
a81d6000-a826c000 rw-s 0012c000 00:05 143949     /dev/video0
a826c000-a8302000 rw-s 00096000 00:05 143949     /dev/video0
a8302000-a8398000 rw-s 00000000 00:05 143949     /dev/video0
a8398000-a8d98000 rwxp 00000000 00:00 0 
a8d98000-a8ddb000 r-xp 00000000 fc:01 1184878    /usr/lib/i386-linux-gnu/libibus-1.0.so.0.401.0
a8ddb000-a8ddc000 r--p 00043000 fc:01 1184878    /usr/lib/i386-linux-gnu/libibus-1.0.so.0.401.0
a8ddc000-a8ddd000 rw-p 00044000 fc:01 1184878    /usr/lib/i386-linux-gnu/libibus-1.0.so.0.401.0
a8de4000-a8df0000 r-xp 00000000 fc:01 1185556    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjack.so
a8df0000-a8df1000 r--p 0000b000 fc:01 1185556    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjack.so
a8df1000-a8df2000 rw-p 0000c000 fc:01 1185556    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjack.so
a8df2000-a8e44000 r--p 00000000 fc:01 1839398    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
a8e44000-a8e45000 ---p 00000000 00:00 0 
a8e45000-a9645000 rw-p 00000000 00:00 0          [stack:14585]
a9645000-a9646000 ---p 00000000 00:00 0 
a9646000-a9e46000 rw-p 00000000 00:00 0          [stack:14584]
a9e46000-a9e47000 ---p 00000000 00:00 0 
a9e47000-aa647000 rw-p 00000000 00:00 0          [stack:14583]
aa647000-aa648000 ---p 00000000 00:00 0 
aa648000-aae48000 rw-p 00000000 00:00 0          [stack:14582]
aae48000-aae49000 ---p 00000000 00:00 0 
aae49000-ab649000 rw-p 00000000 00:00 0          [stack:14581]
ab649000-ab64a000 ---p 00000000 00:00 0 
ab64a000-abe4a000 rw-p 00000000 00:00 0          [stack:14580]
abe4a000-abe4b000 ---p 00000000 00:00 0 
abe4b000-ac64b000 rw-p 00000000 00:00 0          [stack:14579]
ac64b000-ac64c000 ---p 00000000 00:00 0 
ac64c000-ace4c000 rw-p 00000000 00:00 0          [stack:14578]
ace4c000-ace5b000 r-xp 00000000 fc:01 1184399    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudioresample.so
ace5b000-ace5c000 r--p 0000e000 fc:01 1184399    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudioresample.so
ace5c000-ace5e000 rw-p 0000f000 fc:01 1184399    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudioresample.so
ace5e000-ace76000 r-xp 00000000 fc:01 1183633    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudioconvert.so
ace76000-ace77000 r--p 00017000 fc:01 1183633    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudioconvert.so
ace77000-ace78000 rw-p 00018000 fc:01 1183633    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudioconvert.so
ace78000-acfde000 r-xp 00000000 fc:01 1185209    /usr/lib/i386-linux-gnu/libvorbisenc.so.2.0.8
acfde000-acfef000 r--p 00165000 fc:01 1185209    /usr/lib/i386-linux-gnu/libvorbisenc.so.2.0.8
acfef000-acff0000 rw-p 00176000 fc:01 1185209    /usr/lib/i386-linux-gnu/libvorbisenc.so.2.0.8
acff0000-acffb000 r-xp 00000000 fc:01 1185297    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstoss4audio.so
acffb000-acffc000 r--p 0000a000 fc:01 1185297    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstoss4audio.so
acffc000-acffd000 rw-p 0000b000 fc:01 1185297    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstoss4audio.so
acffd000-ad003000 r-xp 00000000 fc:01 1186001    /usr/lib/i386-linux-gnu/gtk-3.0/3.0.0/immodules/im-ibus.so
ad003000-ad004000 r--p 00005000 fc:01 1186001    /usr/lib/i386-linux-gnu/gtk-3.0/3.0.0/immodules/im-ibus.so
ad004000-ad005000 rw-p 00006000 fc:01 1186001    /usr/lib/i386-linux-gnu/gtk-3.0/3.0.0/immodules/im-ibus.so
ad005000-ad010000 r-xp 00000000 fc:01 1184400    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvorbis.so
ad010000-ad011000 r--p 0000a000 fc:01 1184400    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvorbis.so
ad011000-ad012000 rw-p 0000b000 fc:01 1184400    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvorbis.so
ad012000-ad01b000 r-xp 00000000 fc:01 1185628    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjpegformat.so
ad01b000-ad01c000 r--p 00008000 fc:01 1185628    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjpegformat.so
ad01c000-ad01d000 rw-p 00009000 fc:01 1185628    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjpegformat.so
ad01d000-ad02c000 r-xp 00000000 fc:01 656053     /lib/i386-linux-gnu/libbz2.so.1.0.4
ad02c000-ad02d000 r--p 0000e000 fc:01 656053     /lib/i386-linux-gnu/libbz2.so.1.0.4
ad02d000-ad02e000 rw-p 0000f000 fc:01 656053     /lib/i386-linux-gnu/libbz2.so.1.0.4
ad02e000-ad03b000 r-xp 00000000 fc:01 1179846    /usr/lib/i386-linux-gnu/libgstriff-1.0.so.0.1.0
ad03b000-ad03c000 r--p 0000c000 fc:01 1179846    /usr/lib/i386-linux-gnu/libgstriff-1.0.so.0.1.0
ad03c000-ad03d000 rw-p 0000d000 fc:01 1179846    /usr/lib/i386-linux-gnu/libgstriff-1.0.so.0.1.0
ad03e000-ad044000 r-xp 00000000 fc:01 1185081    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideocrop.so
ad044000-ad045000 r--p 00005000 fc:01 1185081    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideocrop.so
ad045000-ad046000 rw-p 00006000 fc:01 1185081    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideocrop.so
ad046000-ad050000 r-xp 00000000 fc:01 1185566    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjpeg.so
ad050000-ad051000 r--p 00009000 fc:01 1185566    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjpeg.so
ad051000-ad052000 rw-p 0000a000 fc:01 1185566    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjpeg.so
ad052000-ad097000 r-xp 00000000 fc:01 1184667    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstmatroska.so
ad097000-ad098000 r--p 00044000 fc:01 1184667    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstmatroska.so
ad098000-ad099000 rw-p 00045000 fc:01 1184667    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstmatroska.so
ad099000-ad0a4000 r-xp 00000000 fc:01 1184624    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstmultifile.so
ad0a4000-ad0a5000 r--p 0000a000 fc:01 1184624    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstmultifile.so
ad0a5000-ad0a6000 rw-p 0000b000 fc:01 1184624    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstmultifile.so
ad0a6000-ad0b5000 r-xp 00000000 fc:01 1184581    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstencodebin.so
ad0b5000-ad0b6000 r--p 0000e000 fc:01 1184581    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstencodebin.so
ad0b6000-ad0b7000 rw-p 0000f000 fc:01 1184581    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstencodebin.so
ad0b7000-ad159000 r-xp 00000000 fc:01 1194248    /usr/lib/i386-linux-gnu/libvpx.so.1.1.0
ad159000-ad15a000 r--p 000a1000 fc:01 1194248    /usr/lib/i386-linux-gnu/libvpx.so.1.1.0
ad15a000-ad15b000 rw-p 000a2000 fc:01 1194248    /usr/lib/i386-linux-gnu/libvpx.so.1.1.0
ad15b000-ad15d000 rw-p 00000000 00:00 0 
ad15e000-ad164000 r-xp 00000000 fc:01 1185007    /usr/lib/i386-linux-gnu/liborc-test-0.4.so.0.16.0
ad164000-ad165000 r--p 00005000 fc:01 1185007    /usr/lib/i386-linux-gnu/liborc-test-0.4.so.0.16.0
ad165000-ad166000 rw-p 00006000 fc:01 1185007    /usr/lib/i386-linux-gnu/liborc-test-0.4.so.0.16.0
ad166000-ad16f000 r-xp 00000000 fc:01 1185567    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideofilter.so
ad16f000-ad170000 ---p 00009000 fc:01 1185567    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideofilter.so
ad170000-ad171000 r--p 00009000 fc:01 1185567    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideofilter.so
ad171000-ad172000 rw-p 0000a000 fc:01 1185567    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideofilter.so
ad172000-ad17f000 r-xp 00000000 fc:01 1184605    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvpx.so
ad17f000-ad180000 r--p 0000c000 fc:01 1184605    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvpx.so
ad180000-ad181000 rw-p 0000d000 fc:01 1184605    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvpx.so
ad181000-ad19e000 r-xp 00000000 fc:01 1184401    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideoscale.so
ad19e000-ad19f000 r--p 0001c000 fc:01 1184401    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideoscale.so
ad19f000-ad1a0000 rw-p 0001d000 fc:01 1184401    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideoscale.so
ad1a0000-ad1be000 r-xp 00000000 fc:01 1183631    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideoconvert.so
ad1be000-ad1bf000 ---p 0001e000 fc:01 1183631    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideoconvert.so
ad1bf000-ad1c0000 r--p 0001e000 fc:01 1183631    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideoconvert.so
ad1c0000-ad1c1000 rw-p 0001f000 fc:01 1183631    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideoconvert.so
ad1c1000-ad1cc000 r-xp 00000000 fc:01 1180287    /usr/lib/i386-linux-gnu/libgstapp-1.0.so.0.1.0
ad1cc000-ad1cd000 r--p 0000a000 fc:01 1180287    /usr/lib/i386-linux-gnu/libgstapp-1.0.so.0.1.0
ad1cd000-ad1ce000 rw-p 0000b000 fc:01 1180287    /usr/lib/i386-linux-gnu/libgstapp-1.0.so.0.1.0
ad1ce000-ad1d4000 r-xp 00000000 fc:01 1185570    /usr/lib/i386-linux-gnu/libgstbasecamerabinsrc-1.0.so.0.1.0
ad1d4000-ad1d5000 r--p 00005000 fc:01 1185570    /usr/lib/i386-linux-gnu/libgstbasecamerabinsrc-1.0.so.0.1.0
ad1d5000-ad1d6000 rw-p 00006000 fc:01 1185570    /usr/lib/i386-linux-gnu/libgstbasecamerabinsrc-1.0.so.0.1.0
ad1d6000-ad1dc000 r-xp 00000000 fc:01 1185568    /usr/lib/i386-linux-gnu/libgstphotography-1.0.so.0.1.0
ad1dc000-ad1dd000 r--p 00005000 fc:01 1185568    /usr/lib/i386-linux-gnu/libgstphotography-1.0.so.0.1.0
ad1dd000-ad1de000 rw-p 00006000 fc:01 1185568    /usr/lib/i386-linux-gnu/libgstphotography-1.0.so.0.1.0
ad1e1000-ad1e6000 r-xp 00000000 fc:01 1184582    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudiorate.so
ad1e6000-ad1e7000 r--p 00004000 fc:01 1184582    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudiorate.so
ad1e7000-ad1e8000 rw-p 00005000 fc:01 1184582    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudiorate.so
ad1e8000-ad1f1000 r-xp 00000000 fc:01 1183890    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvolume.so
ad1f1000-ad1f2000 r--p 00008000 fc:01 1183890    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvolume.so
ad1f2000-ad1f3000 rw-p 00009000 fc:01 1183890    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvolume.so
ad1f3000-ad23d000 r-xp 00000000 fc:01 1195080    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstcoreelements.so
ad23d000-ad23e000 r--p 00049000 fc:01 1195080    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstcoreelements.so
ad23e000-ad23f000 rw-p 0004a000 fc:01 1195080    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstcoreelements.so
ad23f000-ad284000 r-xp 00000000 fc:01 1184915    /usr/lib/i386-linux-gnu/libjpeg.so.8.0.2
ad284000-ad285000 r--p 00044000 fc:01 1184915    /usr/lib/i386-linux-gnu/libjpeg.so.8.0.2
ad285000-ad286000 rw-p 00045000 fc:01 1184915    /usr/lib/i386-linux-gnu/libjpeg.so.8.0.2
ad286000-ad296000 rw-p 00000000 00:00 0 
ad296000-ad2ba000 r-xp 00000000 fc:01 1185199    /usr/lib/i386-linux-gnu/libv4lconvert.so.0
ad2ba000-ad2bb000 r--p 00024000 fc:01 1185199    /usr/lib/i386-linux-gnu/libv4lconvert.so.0
ad2bb000-ad2bc000 rw-p 00025000 fc:01 1185199    /usr/lib/i386-linux-gnu/libv4lconvert.so.0
ad2bc000-ad30e000 rw-p 00000000 00:00 0 
ad30e000-ad40e000 rw-s 16d02000 00:05 7051       /dev/dri/card0
ad412000-ad41a000 r-xp 00000000 fc:01 1185296    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstautodetect.so
ad41a000-ad41b000 r--p 00007000 fc:01 1185296    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstautodetect.so
ad41b000-ad41c000 rw-p 00008000 fc:01 1185296    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstautodetect.so
ad41c000-ad424000 r-xp 00000000 fc:01 1185198    /usr/lib/i386-linux-gnu/libv4l2.so.0
ad424000-ad425000 r--p 00007000 fc:01 1185198    /usr/lib/i386-linux-gnu/libv4l2.so.0
ad425000-ad429000 rw-p 00008000 fc:01 1185198    /usr/lib/i386-linux-gnu/libv4l2.so.0
ad429000-ad42d000 r-xp 00000000 fc:01 1184524    /usr/lib/i386-linux-gnu/libXv.so.1.0.0
ad42d000-ad42e000 r--p 00003000 fc:01 1184524    /usr/lib/i386-linux-gnu/libXv.so.1.0.0
ad42e000-ad42f000 rw-p 00004000 fc:01 1184524    /usr/lib/i386-linux-gnu/libXv.so.1.0.0
ad430000-ad442000 r-xp 00000000 fc:01 1185593    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstcamerabin2.so
ad442000-ad443000 r--p 00011000 fc:01 1185593    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstcamerabin2.so
ad443000-ad444000 rw-p 00012000 fc:01 1185593    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstcamerabin2.so
ad444000-ad468000 r-xp 00000000 fc:01 1184989    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideo4linux2.so
ad468000-ad469000 r--p 00023000 fc:01 1184989    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideo4linux2.so
ad469000-ad46a000 rw-p 00024000 fc:01 1184989    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideo4linux2.so
ad46a000-ad50f000 r--p 00000000 fc:01 1839395    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttfAborted

---

### Post by ajgreeny on 2013-03-21
Cheese never worked for me either.

Try gvcview from the repos.  It works very well.

---

### Post by coreybell on 2013-03-21
> **ajgreeny said:**
> Cheese never worked for me either.

Try gvcview from the repos.  It works very well.

Thanks I will give it a try.

---

### Post by Moose on 2013-03-21
I have this issue too, it would be much better if someone actually recommended a solution instead of telling us to try something entirely different.

---

### Post by coreybell on 2013-03-21
I know, that is what I was hoping for, because I am using 12.10 now, but when I was using 12.04 it cheese worked just fine.

---

### Post by Moose on 2013-03-21
Ah, to be honest I haven't used 12.04. Been pretty happy with 12.10 at the moment. I might try it, I have numerous (minor) issues coming up in 12.10 that might be resolved in 12.04.

---

### Post by lisati on 2013-03-22
Threads merged.

---


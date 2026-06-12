---
title: "cheese webcam booth crashes on video"
date: 2012-11-04
forum: General Help
---

### Post by bobo1993324 on 2012-11-04
I am using ubuntu 12.10. 
Cheese closed just after I pressed the taking video button.
How can it be fixed
The following are what shows on terminal:

luke@luke-Inspiron-N5110:~/install/ubuntu$ cheese
Fontconfig warning: "/etc/fonts/conf.d/99-language-selector-zh.conf", line 11: Having multiple values in <test> isn't supported and may not works as expected

(cheese:30015): cheese-WARNING **: Jack server not found


(cheese:30015): cheese-WARNING **: Could not initialize supporting library.

*** glibc detected *** cheese: free(): invalid pointer: 0xb7796759 ***
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(+0x75ee2)[0xb6b11ee2]
/lib/i386-linux-gnu/libglib-2.0.so.0(+0x4cb3b)[0xb6cadb3b]
/lib/i386-linux-gnu/libglib-2.0.so.0(g_free+0x20)[0xb6cadcb0]
cheese[0x8055247]
/lib/i386-linux-gnu/libglib-2.0.so.0(+0x476bf)[0xb6ca86bf]
/lib/i386-linux-gnu/libglib-2.0.so.0(g_main_context_dispatch+0x143)[0xb6ca79e3]
/lib/i386-linux-gnu/libglib-2.0.so.0(+0x46d80)[0xb6ca7d80]
/lib/i386-linux-gnu/libglib-2.0.so.0(g_main_context_iteration+0x41)[0xb6ca7e61]
/usr/lib/i386-linux-gnu/libgio-2.0.so.0(g_application_run+0x1cc)[0xb6e69a9c]
cheese(_vala_main+0xb2)[0x805da72]
cheese(main+0x2c)[0x80518ac]
/lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xf3)[0xb6ab54d3]
cheese[0x80518d1]
======= Memory map: ========
08048000-08069000 r-xp 00000000 08:06 659838     /usr/bin/cheese
08069000-0806a000 r--p 00020000 08:06 659838     /usr/bin/cheese
0806a000-0806b000 rw-p 00021000 08:06 659838     /usr/bin/cheese
0852d000-09342000 rw-p 00000000 00:00 0          [heap]
a45b3000-a4a65000 rw-p 00000000 00:00 0 
a4a65000-a4a66000 ---p 00000000 00:00 0 
a4a66000-a5266000 rw-p 00000000 00:00 0 
a5266000-a53a6000 rw-s 3052c000 00:05 8459       /dev/dri/card0
a543c000-a5556000 rw-p 00000000 00:00 0 
a5556000-a5696000 rw-s 3066c000 00:05 8459       /dev/dri/card0
a56bc000-a58f0000 rw-p 00000000 00:00 0 
a58f0000-a58f1000 rw-s 30acf000 00:05 8459       /dev/dri/card0
a58f1000-a58f2000 rw-s 30ace000 00:05 8459       /dev/dri/card0
a58f2000-a5ab4000 rw-s 00546000 00:05 9395       /dev/video0
a5ab4000-a5c76000 rw-s 00384000 00:05 9395       /dev/video0
a5c76000-a5e38000 rw-s 001c2000 00:05 9395       /dev/video0
a5e38000-a5ffa000 rw-s 00000000 00:05 9395       /dev/video0
a5ffa000-a7500000 rw-p 00000000 00:00 0 
a7500000-a7563000 rw-p 00000000 00:00 0 
a7563000-a7600000 ---p 00000000 00:00 0 
a7672000-a76ff000 rw-p 00000000 00:00 0 
a76ff000-a7700000 ---p 00000000 00:00 0 
a7700000-a7f00000 rw-p 00000000 00:00 0          [stack:30028]
a7f00000-a7f21000 rw-p 00000000 00:00 0 
a7f21000-a8000000 ---p 00000000 00:00 0 
a8072000-a80ff000 rw-p 00000000 00:00 0 
a80ff000-a8100000 ---p 00000000 00:00 0 
a8100000-a8900000 rw-p 00000000 00:00 0          [stack:30027]
a8900000-a892a000 rw-p 00000000 00:00 0 
a892a000-a8a00000 ---p 00000000 00:00 0 
a8a72000-a8aff000 rw-p 00000000 00:00 0 
a8aff000-a8b00000 ---p 00000000 00:00 0 
a8b00000-a9300000 rw-p 00000000 00:00 0          [stack:30026]
a9300000-a9321000 rw-p 00000000 00:00 0 
a9321000-a9400000 ---p 00000000 00:00 0 
a941c000-a94fe000 rw-p 00000000 00:00 0 
a94fe000-a94ff000 ---p 00000000 00:00 0 
a94ff000-a9cff000 rw-p 00000000 00:00 0          [stack:30025]
a9cff000-a9d00000 ---p 00000000 00:00 0 
a9d00000-aa500000 rw-p 00000000 00:00 0          [stack:30024]
aa500000-aa521000 rw-p 00000000 00:00 0 
aa521000-aa600000 ---p 00000000 00:00 0 
aa600000-aa6a7000 rw-p 00000000 00:00 0 
aa6a7000-aa700000 ---p 00000000 00:00 0 
aa700000-aa721000 rw-p 00000000 00:00 0 
aa721000-aa800000 ---p 00000000 00:00 0 
aa800000-aa8fe000 rw-p 00000000 00:00 0 
aa8fe000-aa8ff000 ---p 00000000 00:00 0 
aa8ff000-ab0ff000 rw-p 00000000 00:00 0          [stack:30023]
ab0ff000-ab100000 ---p 00000000 00:00 0 
ab100000-ab900000 rw-p 00000000 00:00 0          [stack:30022]
ab900000-ab921000 rw-p 00000000 00:00 0 
ab921000-aba00000 ---p 00000000 00:00 0 
aba16000-aba68000 r--p 00000000 08:06 1445123    /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-B.ttf
aba68000-abaab000 r-xp 00000000 08:06 656946     /usr/lib/i386-linux-gnu/libibus-1.0.so.0.401.0
abaab000-abaac000 r--p 00043000 08:06 656946     /usr/lib/i386-linux-gnu/libibus-1.0.so.0.401.0
abaac000-abaad000 rw-p 00044000 08:06 656946     /usr/lib/i386-linux-gnu/libibus-1.0.so.0.401.0
abaad000-abaff000 r--p 00000000 08:06 1445167    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
abaff000-abb00000 ---p 00000000 00:00 0 
abb00000-ac300000 rw-p 00000000 00:00 0          [stack:30021]
ac300000-ac321000 rw-p 00000000 00:00 0 
ac321000-ac400000 ---p 00000000 00:00 0 
ac419000-ac429000 rw-s 00000000 08:06 1971724    /tmp/orcexec.XhghK1 (deleted)
ac429000-ac439000 r-xs 00000000 08:06 1971724    /tmp/orcexec.XhghK1 (deleted)
ac439000-ac43a000 ---p 00000000 00:00 0 
ac43a000-acc3a000 rw-p 00000000 00:00 0          [stack:30020]
acc3a000-acc40000 r-xp 00000000 08:06 656959     /usr/lib/i386-linux-gnu/liborc-test-0.4.so.0.16.0
acc40000-acc41000 r--p 00005000 08:06 656959     /usr/lib/i386-linux-gnu/liborc-test-0.4.so.0.16.0
acc41000-acc42000 rw-p 00006000 08:06 656959     /usr/lib/i386-linux-gnu/liborc-test-0.4.so.0.16.0
acc4f000-acc55000 r-xp 00000000 08:06 788048     /usr/lib/i386-linux-gnu/gtk-3.0/3.0.0/immodules/im-ibus.so
acc55000-acc56000 r--p 00005000 08:06 788048     /usr/lib/i386-linux-gnu/gtk-3.0/3.0.0/immodules/im-ibus.so
acc56000-acc57000 rw-p 00006000 08:06 788048     /usr/lib/i386-linux-gnu/gtk-3.0/3.0.0/immodules/im-ibus.so
acc57000-acc5d000 r-xp 00000000 08:06 800314     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideocrop.so
acc5d000-acc5e000 r--p 00005000 08:06 800314     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideocrop.so
acc5e000-acc5f000 rw-p 00006000 08:06 800314     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideocrop.so
acc5f000-acc6e000 r-xp 00000000 08:06 790089     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudioresample.so
acc6e000-acc6f000 r--p 0000e000 08:06 790089     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudioresample.so
acc6f000-acc71000 rw-p 0000f000 08:06 790089     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudioresample.so
acc71000-acdd7000 r-xp 00000000 08:06 659030     /usr/lib/i386-linux-gnu/libvorbisenc.so.2.0.8
acdd7000-acde8000 r--p 00165000 08:06 659030     /usr/lib/i386-linux-gnu/libvorbisenc.so.2.0.8
acde8000-acde9000 rw-p 00176000 08:06 659030     /usr/lib/i386-linux-gnu/libvorbisenc.so.2.0.8
acdec000-ace04000 r-xp 00000000 08:06 790078     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudioconvert.so
ace04000-ace05000 r--p 00017000 08:06 790078     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudioconvert.so
ace05000-ace06000 rw-p 00018000 08:06 790078     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudioconvert.so
ace06000-ace11000 r-xp 00000000 08:06 790090     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvorbis.so
ace11000-ace12000 r--p 0000a000 08:06 790090     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvorbis.so
ace12000-ace13000 rw-p 0000b000 08:06 790090     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvorbis.so
ace13000-ace1b000 r-xp 00000000 08:06 804577     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstautodetect.so
ace1b000-ace1c000 r--p 00007000 08:06 804577     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstautodetect.so
ace1c000-ace1d000 rw-p 00008000 08:06 804577     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstautodetect.so
ace1d000-ace2c000 r-xp 00000000 08:06 131411     /lib/i386-linux-gnu/libbz2.so.1.0.4
ace2c000-ace2d000 r--p 0000e000 08:06 131411     /lib/i386-linux-gnu/libbz2.so.1.0.4
ace2d000-ace2e000 rw-p 0000f000 08:06 131411     /lib/i386-linux-gnu/libbz2.so.1.0.4
ace2e000-ace3b000 r-xp 00000000 08:06 660721     /usr/lib/i386-linux-gnu/libgstriff-1.0.so.0.1.0
ace3b000-ace3c000 r--p 0000c000 08:06 660721     /usr/lib/i386-linux-gnu/libgstriff-1.0.so.0.1.0
ace3c000-ace3d000 rw-p 0000d000 08:06 660721     /usr/lib/i386-linux-gnu/libgstriff-1.0.so.0.1.0
ace43000-ace4c000 r-xp 00000000 08:06 788126     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjpegformat.so
ace4c000-ace4d000 r--p 00008000 08:06 788126     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjpegformat.so
ace4d000-ace4e000 rw-p 00009000 08:06 788126     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjpegformat.so
ace4e000-ace58000 r-xp 00000000 08:06 821030     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjpeg.so
ace58000-ace59000 r--p 00009000 08:06 821030     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjpeg.so
ace59000-ace5a000 rw-p 0000a000 08:06 821030     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjpeg.so
ace5a000-ace9f000 r-xp 00000000 08:06 799908     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstmatroska.so
ace9f000-acea0000 r--p 00044000 08:06 799908     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstmatroska.so
acea0000-acea1000 rw-p 00045000 08:06 799908     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstmatroska.so
acea1000-aceac000 r-xp 00000000 08:06 799893     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstmultifile.so
aceac000-acead000 r--p 0000a000 08:06 799893     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstmultifile.so
acead000-aceae000 rw-p 0000b000 08:06 799893     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstmultifile.so
aceae000-acf50000 r-xp 00000000 08:06 658671     /usr/lib/i386-linux-gnu/libvpx.so.1.1.0
acf50000-acf51000 r--p 000a1000 08:06 658671     /usr/lib/i386-linux-gnu/libvpx.so.1.1.0
acf51000-acf52000 rw-p 000a2000 08:06 658671     /usr/lib/i386-linux-gnu/libvpx.so.1.1.0
acf52000-acf54000 rw-p 00000000 00:00 0 
acf59000-acf5e000 r-xp 00000000 08:06 790964     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudiorate.so
acf5e000-acf5f000 r--p 00004000 08:06 790964     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudiorate.so
acf5f000-acf60000 rw-p 00005000 08:06 790964     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstaudiorate.so
acf60000-acf6f000 r-xp 00000000 08:06 790957     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstencodebin.so
acf6f000-acf70000 r--p 0000e000 08:06 790957     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstencodebin.so
acf70000-acf71000 rw-p 0000f000 08:06 790957     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstencodebin.so
acf71000-acf7e000 r-xp 00000000 08:06 795130     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvpx.so
acf7e000-acf7f000 r--p 0000c000 08:06 795130     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvpx.so
acf7f000-acf80000 rw-p 0000d000 08:06 795130     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvpx.so
acf80000-acf9d000 r-xp 00000000 08:06 790091     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideoscale.so
acf9d000-acf9e000 r--p 0001c000 08:06 790091     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideoscale.so
acf9e000-acf9f000 rw-p 0001d000 08:06 790091     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideoscale.so
acf9f000-acfbd000 r-xp 00000000 08:06 788725     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideoconvert.so
acfbd000-acfbe000 ---p 0001e000 08:06 788725     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideoconvert.so
acfbe000-acfbf000 r--p 0001e000 08:06 788725     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideoconvert.so
acfbf000-acfc0000 rw-p 0001f000 08:06 788725     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideoconvert.so
acfc0000-acfcb000 r-xp 00000000 08:06 675011     /usr/lib/i386-linux-gnu/libgstapp-1.0.so.0.1.0
acfcb000-acfcc000 r--p 0000a000 08:06 675011     /usr/lib/i386-linux-gnu/libgstapp-1.0.so.0.1.0
acfcc000-acfcd000 rw-p 0000b000 08:06 675011     /usr/lib/i386-linux-gnu/libgstapp-1.0.so.0.1.0
acfcd000-acfd3000 r-xp 00000000 08:06 659638     /usr/lib/i386-linux-gnu/libgstbasecamerabinsrc-1.0.so.0.1.0
acfd3000-acfd4000 r--p 00005000 08:06 659638     /usr/lib/i386-linux-gnu/libgstbasecamerabinsrc-1.0.so.0.1.0
acfd4000-acfd5000 rw-p 00006000 08:06 659638     /usr/lib/i386-linux-gnu/libgstbasecamerabinsrc-1.0.so.0.1.0
acfd5000-acfdb000 r-xp 00000000 08:06 659632     /usr/lib/i386-linux-gnu/libgstphotography-1.0.so.0.1.0
acfdb000-acfdc000 r--p 00005000 08:06 659632     /usr/lib/i386-linux-gnu/libgstphotography-1.0.so.0.1.0
acfdc000-acfdd000 rw-p 00006000 08:06 659632     /usr/lib/i386-linux-gnu/libgstphotography-1.0.so.0.1.0
acfdd000-ad027000 r-xp 00000000 08:06 790059     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstcoreelements.so
ad027000-ad028000 r--p 00049000 08:06 790059     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstcoreelements.so
ad028000-ad029000 rw-p 0004a000 08:06 790059     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstcoreelements.so
ad029000-ad06e000 r-xp 00000000 08:06 659668     /usr/lib/i386-linux-gnu/libjpeg.so.8.0.2
ad06e000-ad06f000 r--p 00044000 08:06 659668     /usr/lib/i386-linux-gnu/libjpeg.so.8.0.2
ad06f000-ad070000 rw-p 00045000 08:06 659668     /usr/lib/i386-linux-gnu/libjpeg.so.8.0.2
ad070000-ad080000 rw-p 00000000 00:00 0 
ad080000-ad0a4000 r-xp 00000000 08:06 662091     /usr/lib/i386-linux-gnu/libv4lconvert.so.0
ad0a4000-ad0a5000 r--p 00024000 08:06 662091     /usr/lib/i386-linux-gnu/libv4lconvert.so.0
ad0a5000-ad0a6000 rw-p 00025000 08:06 662091     /usr/lib/i386-linux-gnu/libv4lconvert.so.0
ad0a6000-ad0f8000 rw-p 00000000 00:00 0 
ad11a000-ad1b1000 rw-p 00000000 00:00 0 
ad1b1000-ad1c3000 r-xp 00000000 08:06 656997     /usr/lib/i386-linux-gnu/libjack.so.0.0.28
ad1c3000-ad1c4000 r--p 00011000 08:06 656997     /usr/lib/i386-linux-gnu/libjack.so.0.0.28
ad1c4000-ad1c5000 rw-p 00012000 08:06 656997     /usr/lib/i386-linux-gnu/libjack.so.0.0.28
ad1c5000-ad1ce000 rw-p 00000000 00:00 0 
ad1d3000-ad1d4000 rw-p 00000000 00:00 0 
ad1d4000-ad1dc000 r-xp 00000000 08:06 804565     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstossaudio.so
ad1dc000-ad1dd000 r--p 00007000 08:06 804565     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstossaudio.so
ad1dd000-ad1de000 rw-p 00008000 08:06 804565     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstossaudio.so
ad1de000-ad1e9000 r-xp 00000000 08:06 804581     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstoss4audio.so
ad1e9000-ad1ea000 r--p 0000a000 08:06 804581     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstoss4audio.so
ad1ea000-ad1eb000 rw-p 0000b000 08:06 804581     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstoss4audio.so
ad1eb000-ad1f7000 r-xp 00000000 08:06 805057     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjack.so
ad1f7000-ad1f8000 r--p 0000b000 08:06 805057     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjack.so
ad1f8000-ad1f9000 rw-p 0000c000 08:06 805057     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstjack.so
ad1f9000-ad1fa000 rw-p 00000000 00:00 0 
ad1fa000-ad1fb000 r--p 00000000 08:06 4470608    /etc/localtime
ad1fb000-ad1fc000 rw-s 307ad000 00:05 8459       /dev/dri/card0
ad1fc000-ad1fe000 rw-s 00000000 00:04 480002     /drm mm object (deleted)
ad1fe000-ad206000 r-xp 00000000 08:06 661024     /usr/lib/i386-linux-gnu/libv4l2.so.0
ad206000-ad207000 r--p 00007000 08:06 661024     /usr/lib/i386-linux-gnu/libv4l2.so.0
ad207000-ad20b000 rw-p 00008000 08:06 661024     /usr/lib/i386-linux-gnu/libv4l2.so.0
ad20b000-ad20f000 r-xp 00000000 08:06 658316     /usr/lib/i386-linux-gnu/libXv.so.1.0.0
ad20f000-ad210000 r--p 00003000 08:06 658316     /usr/lib/i386-linux-gnu/libXv.so.1.0.0
ad210000-ad211000 rw-p 00004000 08:06 658316     /usr/lib/i386-linux-gnu/libXv.so.1.0.0
ad211000-ad212000 rw-s 307ac000 00:05 8459       /dev/dri/card0
ad212000-ad213000 rw-s 30ad1000 00:05 8459       /dev/dri/card0
ad213000-ad214000 rw-s 00000000 00:04 471755     /drm mm object (deleted)
ad214000-ad215000 rw-s 30ad0000 00:05 8459       /dev/dri/card0
ad215000-ad216000 rw-s 00000000 00:04 471749     /drm mm object (deleted)
ad216000-ad217000 rw-s 00000000 00:04 482616     /drm mm object (deleted)
ad217000-ad220000 r-xp 00000000 08:06 821034     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideofilter.so
ad220000-ad221000 ---p 00009000 08:06 821034     /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstvideofilter.soAborted

---

### Post by bobo1993324 on 2012-11-04
ok, my ubuntu was upgraded from 12.04.
So I am going to try it on a fresh 12.10

---

### Post by bobo1993324 on 2012-11-05
ney, still has such problem on a fresh ubuntu 12.10.
I guess I will just use 12.04 for a while

---

### Post by EmmaSystem76chick on 2012-11-06
Hi,
I'm experiencing the same issue with Cheese. My friend found a bug in launchpad if you want to mark that it affects you and subscribe to the changes. Here's the link: [https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/1062282](https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/1062282)

Hope there's a fix soon!

---


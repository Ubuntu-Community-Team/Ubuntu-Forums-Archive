---
title: "Unable to update"
date: 2017-08-16
forum: General Help
---

### Post by robelli on 2017-08-16
I have just installed Ubuntu 16.04 but when I go to update this is what happens

```
mal@Compaq:~$ sudo apt-get update
[sudo] password for mal: 
Hit:1 [http://mirrors.us.kernel.org/ubuntu](http://mirrors.us.kernel.org/ubuntu) xenial InRelease                     
Hit:2 [http://mirrors.us.kernel.org/ubuntu](http://mirrors.us.kernel.org/ubuntu) xenial-updates InRelease             
Hit:3 [http://mirrors.us.kernel.org/ubuntu](http://mirrors.us.kernel.org/ubuntu) xenial-backports InRelease    
Hit:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease              
Hit:5 [http://mirrors.us.kernel.org/ubuntu](http://mirrors.us.kernel.org/ubuntu) xenial-security InRelease     
*** Error in `appstreamcli': double free or corruption (fasttop): 0x00000000023e0b50 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x77725)[0x7ff5c8b7a725]
/lib/x86_64-linux-gnu/libc.so.6(+0x7ff4a)[0x7ff5c8b82f4a]
/lib/x86_64-linux-gnu/libc.so.6(cfree+0x4c)[0x7ff5c8b86abc]
/usr/lib/x86_64-linux-gnu/libappstream.so.3(as_component_complete+0x439)[0x7ff5c8efed19]
/usr/lib/x86_64-linux-gnu/libappstream.so.3(as_data_pool_update+0x44a)[0x7ff5c8efff0a]
/usr/lib/x86_64-linux-gnu/libappstream.so.3(as_cache_builder_refresh+0x1c2)[0x7ff5c8ef5272]
appstreamcli(ascli_refresh_cache+0x12e)[0x4049de]
appstreamcli(as_client_run+0x6fb)[0x403ceb]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf0)[0x7ff5c8b23830]
appstreamcli(_start+0x29)[0x403519]
======= Memory map: ========
00400000-00408000 r-xp 00000000 fc:00 786482                             /usr/bin/appstreamcli
00607000-00608000 r--p 00007000 fc:00 786482                             /usr/bin/appstreamcli
00608000-00609000 rw-p 00008000 fc:00 786482                             /usr/bin/appstreamcli
016f8000-03253000 rw-p 00000000 00:00 0                                  [heap]
7ff5bc000000-7ff5bc021000 rw-p 00000000 00:00 0 
7ff5bc021000-7ff5c0000000 ---p 00000000 00:00 0 
7ff5c32d1000-7ff5c32dc000 r-xp 00000000 fc:00 1051872                    /usr/lib/x86_64-linux-gnu/gio/modules/libdconfsettings.so
7ff5c32dc000-7ff5c34dc000 ---p 0000b000 fc:00 1051872                    /usr/lib/x86_64-linux-gnu/gio/modules/libdconfsettings.so
7ff5c34dc000-7ff5c34dd000 r--p 0000b000 fc:00 1051872                    /usr/lib/x86_64-linux-gnu/gio/modules/libdconfsettings.so
7ff5c34dd000-7ff5c34de000 rw-p 0000c000 fc:00 1051872                    /usr/lib/x86_64-linux-gnu/gio/modules/libdconfsettings.so
7ff5c34de000-7ff5c3514000 r-xp 00000000 fc:00 1052369                    /usr/lib/x86_64-linux-gnu/gvfs/libgvfscommon.so
7ff5c3514000-7ff5c3714000 ---p 00036000 fc:00 1052369                    /usr/lib/x86_64-linux-gnu/gvfs/libgvfscommon.so
7ff5c3714000-7ff5c3719000 r--p 00036000 fc:00 1052369                    /usr/lib/x86_64-linux-gnu/gvfs/libgvfscommon.so
7ff5c3719000-7ff5c371a000 rw-p 0003b000 fc:00 1052369                    /usr/lib/x86_64-linux-gnu/gvfs/libgvfscommon.so
7ff5c371a000-7ff5c3733000 r-xp 00000000 fc:00 1051876                    /usr/lib/x86_64-linux-gnu/gio/modules/libgioremote-volume-monitor.so
7ff5c3733000-7ff5c3933000 ---p 00019000 fc:00 1051876                    /usr/lib/x86_64-linux-gnu/gio/modules/libgioremote-volume-monitor.so
7ff5c3933000-7ff5c3936000 r--p 00019000 fc:00 1051876                    /usr/lib/x86_64-linux-gnu/gio/modules/libgioremote-volume-monitor.so
7ff5c3936000-7ff5c3937000 rw-p 0001c000 fc:00 1051876                    /usr/lib/x86_64-linux-gnu/gio/modules/libgioremote-volume-monitor.so
7ff5c3937000-7ff5c42f6000 r--p 00000000 fc:00 793683                     /usr/lib/locale/locale-archive
7ff5c42f6000-7ff5c5bac000 r-xp 00000000 fc:00 795339                     /usr/lib/x86_64-linux-gnu/libicudata.so.55.1
7ff5c5bac000-7ff5c5dab000 ---p 018b6000 fc:00 795339                     /usr/lib/x86_64-linux-gnu/libicudata.so.55.1
7ff5c5dab000-7ff5c5dac000 r--p 018b5000 fc:00 795339                     /usr/lib/x86_64-linux-gnu/libicudata.so.55.1
7ff5c5dac000-7ff5c5dad000 rw-p 018b6000 fc:00 795339                     /usr/lib/x86_64-linux-gnu/libicudata.so.55.1
7ff5c5dad000-7ff5c5db1000 r-xp 00000000 fc:00 3150516                    /lib/x86_64-linux-gnu/libuuid.so.1.3.0
7ff5c5db1000-7ff5c5fb0000 ---p 00004000 fc:00 3150516                    /lib/x86_64-linux-gnu/libuuid.so.1.3.0
7ff5c5fb0000-7ff5c5fb1000 r--p 00003000 fc:00 3150516                    /lib/x86_64-linux-gnu/libuuid.so.1.3.0
7ff5c5fb1000-7ff5c5fb2000 rw-p 00004000 fc:00 3150516                    /lib/x86_64-linux-gnu/libuuid.so.1.3.0
7ff5c5fb2000-7ff5c60ba000 r-xp 00000000 fc:00 3150402                    /lib/x86_64-linux-gnu/libm-2.23.so
7ff5c60ba000-7ff5c62b9000 ---p 00108000 fc:00 3150402                    /lib/x86_64-linux-gnu/libm-2.23.so
7ff5c62b9000-7ff5c62ba000 r--p 00107000 fc:00 3150402                    /lib/x86_64-linux-gnu/libm-2.23.so
7ff5c62ba000-7ff5c62bb000 rw-p 00108000 fc:00 3150402                    /lib/x86_64-linux-gnu/libm-2.23.so
7ff5c62bb000-7ff5c62dc000 r-xp 00000000 fc:00 3150399                    /lib/x86_64-linux-gnu/liblzma.so.5.0.0
7ff5c62dc000-7ff5c64db000 ---p 00021000 fc:00 3150399                    /lib/x86_64-linux-gnu/liblzma.so.5.0.0
7ff5c64db000-7ff5c64dc000 r--p 00020000 fc:00 3150399                    /lib/x86_64-linux-gnu/liblzma.so.5.0.0
7ff5c64dc000-7ff5c64dd000 rw-p 00021000 fc:00 3150399                    /lib/x86_64-linux-gnu/liblzma.so.5.0.0
7ff5c64dd000-7ff5c665c000 r-xp 00000000 fc:00 795353                     /usr/lib/x86_64-linux-gnu/libicuuc.so.55.1
7ff5c665c000-7ff5c685c000 ---p 0017f000 fc:00 795353                     /usr/lib/x86_64-linux-gnu/libicuuc.so.55.1
7ff5c685c000-7ff5c686c000 r--p 0017f000 fc:00 795353                     /usr/lib/x86_64-linux-gnu/libicuuc.so.55.1
7ff5c686c000-7ff5c686d000 rw-p 0018f000 fc:00 795353                     /usr/lib/x86_64-linux-gnu/libicuuc.so.55.1
7ff5c686d000-7ff5c6871000 rw-p 00000000 00:00 0 
7ff5c6871000-7ff5c6874000 r-xp 00000000 fc:00 3150356                    /lib/x86_64-linux-gnu/libdl-2.23.so
7ff5c6874000-7ff5c6a73000 ---p 00003000 fc:00 3150356                    /lib/x86_64-linux-gnu/libdl-2.23.so
7ff5c6a73000-7ff5c6a74000 r--p 00002000 fc:00 3150356                    /lib/x86_64-linux-gnu/libdl-2.23.so
7ff5c6a74000-7ff5c6a75000 rw-p 00003000 fc:00 3150356                    /lib/x86_64-linux-gnu/libdl-2.23.so
7ff5c6a75000-7ff5c6a8b000 r-xp 00000000 fc:00 3150370                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7ff5c6a8b000-7ff5c6c8a000 ---p 00016000 fc:00 3150370                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7ff5c6c8a000-7ff5c6c8b000 rw-p 00015000 fc:00 3150370                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7ff5c6c8b000-7ff5c6dfd000 r-xp 00000000 fc:00 795799                     /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.21
7ff5c6dfd000-7ff5c6ffd000 ---p 00172000 fc:00 795799                     /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.21
7ff5c6ffd000-7ff5c7007000 r--p 00172000 fc:00 795799                     /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.21
7ff5c7007000-7ff5c7009000 rw-p 0017c000 fc:00 795799                     /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.21
7ff5c7009000-7ff5c700d000 rw-p 00000000 00:00 0 
7ff5c700d000-7ff5c703d000 r-xp 00000000 fc:00 795644                     /usr/lib/x86_64-linux-gnu/libprotobuf-lite.so.9.0.1
7ff5c703d000-7ff5c723c000 ---p 00030000 fc:00 795644                     /usr/lib/x86_64-linux-gnu/libprotobuf-lite.so.9.0.1
7ff5c723c000-7ff5c723d000 r--p 0002f000 fc:00 795644                     /usr/lib/x86_64-linux-gnu/libprotobuf-lite.so.9.0.1
7ff5c723d000-7ff5c723e000 rw-p 00030000 fc:00 795644                     /usr/lib/x86_64-linux-gnu/libprotobuf-lite.so.9.0.1
7ff5c723e000-7ff5c7432000 r-xp 00000000 fc:00 796004                     /usr/lib/x86_64-linux-gnu/libxapian.so.22.7.0
7ff5c7432000-7ff5c7632000 ---p 001f4000 fc:00 796004                     /usr/lib/x86_64-linux-gnu/libxapian.so.22.7.0
7ff5c7632000-7ff5c7639000 r--p 001f4000 fc:00 796004                     /usr/lib/x86_64-linux-gnu/libxapian.so.22.7.0
7ff5c7639000-7ff5c763a000 rw-p 001fb000 fc:00 796004                     /usr/lib/x86_64-linux-gnu/libxapian.so.22.7.0
7ff5c763a000-7ff5c7657000 r-xp 00000000 fc:00 796058                     /usr/lib/x86_64-linux-gnu/libyaml-0.so.2.0.4
7ff5c7657000-7ff5c7857000 ---p 0001d000 fc:00 796058                     /usr/lib/x86_64-linux-gnu/libyaml-0.so.2.0.4
7ff5c7857000-7ff5c7858000 r--p 0001d000 fc:00 796058                     /usr/lib/x86_64-linux-gnu/libyaml-0.so.2.0.4
7ff5c7858000-7ff5c7859000 rw-p 0001e000 fc:00 796058                     /usr/lib/x86_64-linux-gnu/libyaml-0.so.2.0.4
7ff5c7859000-7ff5c7a09000 r-xp 00000000 fc:00 796050                     /usr/lib/x86_64-linux-gnu/libxml2.so.2.9.3
7ff5c7a09000-7ff5c7c08000 ---p 001b0000 fc:00 796050                     /usr/lib/x86_64-linux-gnu/libxml2.so.2.9.3
7ff5c7c08000-7ff5c7c10000 r--p 001af000 fc:00 796050                     /usr/lib/x86_64-linux-gnu/libxml2.so.2.9.3
7ff5c7c10000-7ff5c7c12000 rw-p 001b7000 fc:00 796050                     /usr/lib/x86_64-linux-gnu/libxml2.so.2.9.3
7ff5c7c12000-7ff5c7c13000 rw-p 00000000 00:00 0 
7ff5c7c13000-7ff5c7c1a000 r-xp 00000000 fc:00 795044                     /usr/lib/x86_64-linux-gnu/libffi.so.6.0.4
7ff5c7c1a000-7ff5c7e19000 ---p 00007000 fc:00 795044                     /usr/lib/x86_64-linux-gnu/libffi.so.6.0.4
7ff5c7e19000-7ff5c7e1a000 r--p 00006000 fc:00 795044                     /usr/lib/x86_64-linux-gnu/libffi.so.6.0.4
7ff5c7e1a000-7ff5c7e1b000 rw-p 00007000 fc:00 795044                     /usr/lib/x86_64-linux-gnu/libffi.so.6.0.4
7ff5c7e1b000-7ff5c7e32000 r-xp 00000000 fc:00 3150484                    /lib/x86_64-linux-gnu/libresolv-2.23.so
7ff5c7e32000-7ff5c8032000 ---p 00017000 fc:00 3150484                    /lib/x86_64-linux-gnu/libresolv-2.23.so
7ff5c8032000-7ff5c8033000 r--p 00017000 fc:00 3150484                    /lib/x86_64-linux-gnu/libresolv-2.23.so
7ff5c8033000-7ff5c8034000 rw-p 00018000 fc:00 3150484                    /lib/x86_64-linux-gnu/libresolv-2.23.so
7ff5c8034000-7ff5c8036000 rw-p 00000000 00:00 0 
7ff5c8036000-7ff5c8055000 r-xp 00000000 fc:00 3150490                    /lib/x86_64-linux-gnu/libselinux.so.1
7ff5c8055000-7ff5c8254000 ---p 0001f000 fc:00 3150490                    /lib/x86_64-linux-gnu/libselinux.so.1
7ff5c8254000-7ff5c8255000 r--p 0001e000 fc:00 3150490                    /lib/x86_64-linux-gnu/libselinux.so.1
7ff5c8255000-7ff5c8256000 rw-p 0001f000 fc:00 3150490                    /lib/x86_64-linux-gnu/libselinux.so.1
7ff5c8256000-7ff5c8258000 rw-p 00000000 00:00 0 
7ff5c8258000-7ff5c8271000 r-xp 00000000 fc:00 3150523                    /lib/x86_64-linux-gnu/libz.so.1.2.8
7ff5c8271000-7ff5c8470000 ---p 00019000 fc:00 3150523                    /lib/x86_64-linux-gnu/libz.so.1.2.8
7ff5c8470000-7ff5c8471000 r--p 00018000 fc:00 3150523                    /lib/x86_64-linux-gnu/libz.so.1.2.8
7ff5c8471000-7ff5c8472000 rw-p 00019000 fc:00 3150523                    /lib/x86_64-linux-gnu/libz.so.1.2.8
7ff5c8472000-7ff5c8475000 r-xp 00000000 fc:00 795175                     /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.4800.0
7ff5c8475000-7ff5c8674000 ---p 00003000 fc:00 795175                     /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.4800.0
7ff5c8674000-7ff5c8675000 r--p 00002000 fc:00 795175                     /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.4800.0
7ff5c8675000-7ff5c8676000 rw-p 00003000 fc:00 795175                     /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.4800.0
7ff5c8676000-7ff5c868e000 r-xp 00000000 fc:00 3150478                    /lib/x86_64-linux-gnu/libpthread-2.23.so
7ff5c868e000-7ff5c888d000 ---p 00018000 fc:00 3150478                    /lib/x86_64-linux-gnu/libpthread-2.23.so
7ff5c888d000-7ff5c888e000 r--p 00017000 fc:00 3150478                    /lib/x86_64-linux-gnu/libpthread-2.23.so
7ff5c888e000-7ff5c888f000 rw-p 00018000 fc:00 3150478                    /lib/x86_64-linux-gnu/libpthread-2.23.so
7ff5c888f000-7ff5c8893000 rw-p 00000000 00:00 0 
7ff5c8893000-7ff5c8901000 r-xp 00000000 fc:00 3150461                    /lib/x86_64-linux-gnu/libpcre.so.3.13.2
7ff5c8901000-7ff5c8b01000 ---p 0006e000 fc:00 3150461                    /lib/x86_64-linux-gnu/libpcre.so.3.13.2
7ff5c8b01000-7ff5c8b02000 r--p 0006e000 fc:00 3150461                    /lib/x86_64-linux-gnu/libpcre.so.3.13.2
7ff5c8b02000-7ff5c8b03000 rw-p 0006f000 fc:00 3150461                    /lib/x86_64-linux-gnu/libpcre.so.3.13.2
7ff5c8b03000-7ff5c8cc3000 r-xp 00000000 fc:00 3150332                    /lib/x86_64-linux-gnu/libc-2.23.so
7ff5c8cc3000-7ff5c8ec2000 ---p 001c0000 fc:00 3150332                    /lib/x86_64-linux-gnu/libc-2.23.so
7ff5c8ec2000-7ff5c8ec6000 r--p 001bf000 fc:00 3150332                    /lib/x86_64-linux-gnu/libc-2.23.so
7ff5c8ec6000-7ff5c8ec8000 rw-p 001c3000 fc:00 3150332                    /lib/x86_64-linux-gnu/libc-2.23.so
7ff5c8ec8000-7ff5c8ecc000 rw-p 00000000 00:00 0 
7ff5c8ecc000-7ff5c8f17000 r-xp 00000000 fc:00 794737                     /usr/lib/x86_64-linux-gnu/libappstream.so.0.9.4
7ff5c8f17000-7ff5c9117000 ---p 0004b000 fc:00 794737                     /usr/lib/x86_64-linux-gnu/libappstream.so.0.9.4
7ff5c9117000-7ff5c9118000 r--p 0004b000 fc:00 794737                     /usr/lib/x86_64-linux-gnu/libappstream.so.0.9.4
7ff5c9118000-7ff5c9119000 rw-p 0004c000 fc:00 794737                     /usr/lib/x86_64-linux-gnu/libappstream.so.0.9.4
7ff5c9119000-7ff5c916b000 r-xp 00000000 fc:00 795199                     /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.4800.0
7ff5c916b000-7ff5c936a000 ---p 00052000 fc:00 795199                     /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.4800.0
7ff5c936a000-7ff5c936b000 r--p 00051000 fc:00 795199                     /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.4800.0
7ff5c936b000-7ff5c936c000 rw-p 00052000 fc:00 795199                     /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.4800.0
7ff5c936c000-7ff5c94ec000 r-xp 00000000 fc:00 795161                     /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0.4800.0
7ff5c94ec000-7ff5c96ec000 ---p 00180000 fc:00 795161                     /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0.4800.0
7ff5c96ec000-7ff5c96f0000 r--p 00180000 fc:00 795161                     /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0.4800.0
7ff5c96f0000-7ff5c96f2000 rw-p 00184000 fc:00 795161                     /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0.4800.0
7ff5c96f2000-7ff5c96f4000 rw-p 00000000 00:00 0 
7ff5c96f4000-7ff5c9802000 r-xp 00000000 fc:00 3150374                    /lib/x86_64-linux-gnu/libglib-2.0.so.0.4800.0
7ff5c9802000-7ff5c9a02000 ---p 0010e000 fc:00 3150374                    /lib/x86_64-linux-gnu/libglib-2.0.so.0.4800.0
7ff5c9a02000-7ff5c9a03000 r--p 0010e000 fc:00 3150374                    /lib/x86_64-linux-gnu/libglib-2.0.so.0.4800.0
7ff5c9a03000-7ff5c9a04000 rw-p 0010f000 fc:00 3150374                    /lib/x86_64-linux-gnu/libglib-2.0.so.0.4800.0
7ff5c9a04000-7ff5c9a05000 rw-p 00000000 00:00 0 
7ff5c9a05000-7ff5c9a2b000 r-xp 00000000 fc:00 3150304                    /lib/x86_64-linux-gnu/ld-2.23.so
7ff5c9be2000-7ff5c9c01000 r--s 00000000 fc:00 1317201                    /usr/share/mime/mime.cache
7ff5c9c01000-7ff5c9c0f000 rw-p 00000000 00:00 0 
7ff5c9c27000-7ff5c9c2a000 rw-p 00000000 00:00 0 
7ff5c9c2a000-7ff5c9c2b000 r--p 00025000 fc:00 3150304                    /lib/x86_64-linux-gnu/ld-2.23.so
7ff5c9c2b000-7ff5c9c2c000 rw-p 00026000 fc:00 3150304                    /lib/x86_64-linux-gnu/ld-2.23.so
7ff5c9c2c000-7ff5c9c2d000 rw-p 00000000 00:00 0 
7ffda159a000-7ffda15bb000 rw-p 00000000 00:00 0                          [stack]
7ffda15ec000-7ffda15ee000 r--p 00000000 00:00 0                          [vvar]
7ffda15ee000-7ffda15f0000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
Aborted (core dumped)
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/cache/app-info -a -e /usr/bin/appstreamcli; then appstreamcli refresh > /dev/null; fi'
E: Sub-process returned an error code
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
mal@Compaq:~$ 
```

It maybe that "APT" has been corrupted .



```
Computer   Hp Compaq dc7900
HDD          150Gb
RAM          2Gb
Processor   Intel Core 2 duo CPU E8400@ 3Ghz
O,S            Ubuntu 16.04
```

---

### Post by robelli on 2017-08-16
Well I don't know what has happend but I have just completed the update of Ubuntu 16.04 so seems like "APT" has fixed itself.
This thread can be considered closed thank you

---


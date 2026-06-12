---
title: "Problem with Mono"
date: 2007-03-19
forum: General Help
---

### Post by ebike on 2007-03-19
Hi All,

I have in the past used mono to run an xmltvnz.exe program to get TV guide data for my mythtv box. This has worked great on my gentoo box, but since moving to Ubuntu mono doesn't want to work.

The error follows, can anyone give some in-site into this problem, I don't know what this "assembly" the error is referring to ...

Thanks.

> 
bmentink@mythtv:~/xmlTVNZ$ /usr/bin/mono /home/bmentink/xmlTVNZ/xmlTVNZ.exe tv.xml -days 5 tv1 tv2 prime sky_tv3

** (/home/bmentink/xmlTVNZ/xmlTVNZ.exe:26219): WARNING **: The following assembly referenced from /home/bmentink/xmlTVNZ/xmlTVNZ.exe could not be loaded:
Assembly: System.Runtime.Serialization.Formatters.Soap (assemblyref_index=2)
Version: 1.0.5000.0
Public Key: b03f5f7f11d50a3a
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/bmentink/xmlTVNZ).


** (/home/bmentink/xmlTVNZ/xmlTVNZ.exe:26219): WARNING **: Could not load file or assembly 'System.Runtime.Serialization.Formatters.Soap, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies.
*** glibc detected *** /usr/bin/mono: free(): invalid pointer: 0x082474cc ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d498bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb7d49a44]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb7ea2b51]
/usr/bin/mono(mono_metadata_parse_mh_full+0x381)[0x80e7031]
/usr/bin/mono(mono_method_get_header+0x16b)[0x80e987b]
/usr/bin/mono[0x8123b46]
/usr/bin/mono[0x8138185]
/usr/bin/mono[0x8140f06]
/usr/bin/mono[0x8142791]
/usr/bin/mono(mono_magic_trampoline+0x1a)[0x807fdaa]
[0xb7bc3032]
[0xb744a7c3]
/usr/bin/mono(mono_runtime_exec_main+0x62)[0x80996b2]
/usr/bin/mono(mono_runtime_run_main+0x1b9)[0x8099999]
/usr/bin/mono(mono_main+0xe47)[0x805d477]
/usr/bin/mono[0x805c122]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7cf88cc]
/usr/bin/mono[0x805c071]
======= Memory map: ========
00001000-00082000 rw-p 00001000 00:00 0
08048000-081e7000 r-xp 00000000 03:01 114944 /usr/bin/mono
081e7000-081e9000 rw-p 0019f000 03:01 114944 /usr/bin/mono
081e9000-081fc000 rw-p 081e9000 00:00 0
081fc000-081fd000 rwxp 081fc000 00:00 0
081fd000-08294000 rw-p 081fd000 00:00 0
b6f00000-b6f21000 rw-p b6f00000 00:00 0
b6f21000-b7000000 ---p b6f21000 00:00 0
b7065000-b706f000 r-xp 00000000 03:01 481936 /lib/libgcc_s.so.1
b706f000-b7070000 rw-p 00009000 03:01 481936 /lib/libgcc_s.so.1
b707d000-b713e000 r-xp 00000000 03:01 260680 /usr/lib/mono/gac/System/1.0.5000.0__b77a5c561934e089/System.dll
b713e000-b713f000 ---p b713e000 00:00 0
b713f000-b723f000 rw-p b713f000 00:00 0
b723f000-b7348000 r-xp 00000000 03:01 260678 /usr/lib/mono/gac/System.Xml/1.0.5000.0__b77a5c561934e089/System.Xml.dll
b7348000-b7349000 ---p b7348000 00:00 0
b7349000-b7449000 rw-p b7349000 00:00 0
b7449000-b7459000 rwxp b7449000 00:00 0
b7459000-b77de000 rw-s 00000000 03:01 515633 /home/bmentink/.wapi/shared_fileshare-mythtv-Linux-i686-36-10-0
b77de000-b7913000 rw-s 00000000 03:01 514234 /home/bmentink/.wapi/shared_data-mythtv-Linux-i686-308-10-0
b7913000-b7980000 rw-p b7913000 00:00 0
b7980000-b7989000 r-xp 00000000 03:01 481953 /lib/tls/i686/cmov/libnss_files-2.4.so
b7989000-b798b000 rw-p 00008000 03:01 481953 /lib/tls/i686/cmov/libnss_files-2.4.so
b798b000-b7993000 r-xp 00000000 03:01 481955 /lib/tls/i686/cmov/libnss_nis-2.4.so
b7993000-b7995000 rw-p 00007000 03:01 481955 /lib/tls/i686/cmov/libnss_nis-2.4.so
b7995000-b799c000 r-xp 00000000 03:01 481951 /lib/tls/i686/cmov/libnss_compat-2.4.so
b799c000-b799e000 rw-p 00006000 03:01 481951 /lib/tls/i686/cmov/libnss_compat-2.4.so
b79a7000-b79a8000 ---p b79a7000 00:00 0
b79a8000-b79ab000 rw-p b79a8000 00:00 0
b79ab000-b7b91000 r-xp 00000000 03:01 260976 /usr/lib/mono/1.0/mscorlib.dll
b7b91000-b7bc3000 r-xp 00000000 03:01 515207 /home/bmentink/xmlTVNZ/xmlTVNZ.exe
b7bc3000-b7bd3000 rwxp b7bc3000 00:00 0
b7bd3000-b7c06000 r--p 00000000 03:01 146960 /usr/lib/locale/en_NZ.utf8/LC_CTYPE
b7c06000-b7c07000 r--p 00000000 03:01 146961 /usr/lib/locale/en_NZ.utf8/LC_NUMERIC
b7c07000-b7c08000 r--p 00000000 03:01 146962 /usr/lib/locale/en_NZ.utf8/LC_TIME
b7c08000-b7cdf000 r--p 00000000 03:01 146963 /usr/lib/locale/en_NZ.utf8/LC_COLLATE
b7cdf000-b7ce0000 r--p 00000000 03:01 146964 /usr/lib/locale/en_NZ.utf8/LC_MONETARY
b7ce0000-b7ce1000 r--p 00000000 03:01 146966 /usr/lib/locale/en_NZ.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7ce1000-b7ce3000 rw-p b7ce1000 00:00 0
b7ce3000-b7e10000 r-xp 00000000 03:01 481944 /lib/tls/i686/cmov/libc-2.4.so
b7e10000-b7e12000 r--p 0012c000 03:01 481944 /lib/tls/i686/cmov/libc-2.4.so
b7e12000-b7e14000 rw-p 0012e000 03:01 481944 /lib/tls/i686/cmov/libc-2.4.so
b7e14000-b7e17000 rw-p b7e14000 00:00 0
b7e17000-b7e3b000 r-xp 00000000 03:01 481948 /lib/tls/i686/cmov/libm-2.4.so
b7e3b000-b7e3d000 rw-p 00023000 03:01 481948 /lib/tls/i686/cmov/libm-2.4.so
b7e3d000-b7e4c000 r-xp 00000000 03:01 481958 /lib/tls/i686/cmov/libpthread-2.4.so
b7e4c000-b7e4e000 rw-p 0000f000 03:01 481958 /lib/tls/i686/cmov/libpthread-2.4.so
b7e4e000-b7e51000 rw-p b7e4e000 00:00 0
b7e51000-b7e63000 r-xp 00000000 03:01 481950 /lib/tls/i686/cmov/libnsl-2.4.so
b7e63000-b7e65000 rw-p 00011000 03:01 481950 /lib/tls/i686/cmov/libnsl-2.4.so
b7e65000-b7e67000 rw-p b7e65000 00:00 0
b7e67000-b7e6e000 r-xp 00000000 03:01 481960 /lib/tls/i686/cmov/librt-2.4.so
b7e6e000-b7e70000 rw-p 00006000 03:01 481960 /lib/tls/i686/cmov/librt-2.4.so
b7e70000-b7f01000 r-xp 00000000 03:01 118754 /usr/lib/libglib-2.0.so.0.1200.4
b7f01000-b7f02000 rw-p 00091000 03:01 118754 /usr/lib/libglib-2.0.so.0.1200.4
b7f02000-b7f04000 r-xp 00000000 03:01 481947 /lib/tls/i686/cmov/libdl-2.4.so
b7f04000-b7f06000 rw-p 00001000 03:01 481947 /lib/tls/i686/cmov/libdl-2.4.so
b7f06000-b7f09000 r-xp 00000000 03:01 118756 /usr/lib/libgmodule-2.0.so.0.1200.4
b7f09000-b7f0a000 rw-p 00002000 03:01 118756 /usr/lib/libgmodule-2.0.so.0.1200.4
b7f0a000-b7f0e000 r-xp 00000000 03:01 118757 /usr/lib/libgthread-2.0.so.0.1200.4
b7f0e000-b7f0f000 rw-p 00003000 03:01 118757 /usr/lib/libgthread-2.0.so.0.1200.4
b7f0f000-b7f10000 rw-p b7f0f000 00:00 0
b7f10000-b7f11000 r--p 00000000 03:01 146967 /usr/lib/locale/en_NZ.utf8/LC_PAPER
b7f11000-b7f12000 r--p 00000000 03:01 146968 /usr/lib/locale/en_NZ.utf8/LC_NAME
b7f12000-b7f13000 r--p 00000000 03:01 146969 /usr/lib/locale/en_NZ.utf8/LC_ADDRESS
b7f13000-b7f14000 r--p 00000000 03:01 146970 /usr/lib/locale/en_NZ.utf8/LC_TELEPHONE
b7f14000-b7f15000 r--p 00000000 03:01 146971 /usr/lib/locale/en_NZ.utf8/LC_MEASUREMENT
b7f15000-b7f1c000 r--s 00000000 03:01 113360 /usr/lib/gconv/gconv-modules.cache
b7f1c000-b7f1d000 r--p 00000000 03:01 146972 /usr/lib/locale/en_NZ.utf8/LC_IDENTIFICATION
b7f1d000-b7f1e000 rw-p b7f1d000 00:00 0
b7f1e000-b7f37000 r-xp 00000000 03:01 483794 /lib/ld-2.4.so
b7f37000-b7f39000 rw-p 00018000 03:01 483794 /lib/ld-2.4.so
bfc1e000-bfc34000 rw-p bfc1e000 00:00 0 [stack]
ffffe000-fffff000 ---p 00000000 00:00 0 [vdso]

================================================== ===============
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries
used by your application.
================================================== ===============

Stacktrace:

at xmlTVNZ.xmlTVNZ.Main (string[]) <0xffffffff>
at xmlTVNZ.xmlTVNZ.Main (string[]) <0x00089>
at (wrapper runtime-invoke) System.Object.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

/usr/bin/mono(mono_handle_native_sigsegv+0xde) [0x815644e]
[0xffffe440]
/lib/tls/i686/cmov/libc.so.6(abort+0x103) [0xb7d0def3]
/lib/tls/i686/cmov/libc.so.6 [0xb7d41d0b]
/lib/tls/i686/cmov/libc.so.6 [0xb7d498bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84) [0xb7d49a44]
/usr/lib/libglib-2.0.so.0(g_free+0x31) [0xb7ea2b51]
/usr/bin/mono(mono_metadata_parse_mh_full+0x381) [0x80e7031]
/usr/bin/mono(mono_method_get_header+0x16b) [0x80e987b]
/usr/bin/mono [0x8123b46]
/usr/bin/mono [0x8138185]
/usr/bin/mono [0x8140f06]
/usr/bin/mono [0x8142791]
/usr/bin/mono(mono_magic_trampoline+0x1a) [0x807fdaa]
[0xb7bc3032]
[0xb744a7c3]
/usr/bin/mono(mono_runtime_exec_main+0x62) [0x80996b2]
/usr/bin/mono(mono_runtime_run_main+0x1b9) [0x8099999]
/usr/bin/mono(mono_main+0xe47) [0x805d477]
/usr/bin/mono [0x805c122]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7cf88cc]
/usr/bin/mono [0x805c071]
Aborted (core dumped)

---

### Post by ebike on 2007-03-19
An update. It seems there is something wrong with the Ubuntu version of mono.

I compiled mono from source from the official website, and it now works.:popcorn:

---


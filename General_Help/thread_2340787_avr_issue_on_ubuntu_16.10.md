---
title: "avr issue on ubuntu 16.10"
date: 2016-10-22
forum: General Help
---

### Post by bibishte on 2016-10-22
[SIZE=3]Hello all,
I am trying to compile and upload a file into an Atmega8 controller, but the linker output gives me this error:
```
** buffer overflow detected ***: /usr/lib/gcc/avr/4.9.2/../../../avr/bin/ld terminated
====== Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x790cb)[0x7f29b6e720cb]
/lib/x86_64-linux-gnu/libc.so.6(__fortify_fail+0x54)[0x7f29b6f132c4]
/lib/x86_64-linux-gnu/libc.so.6(+0x118240)[0x7f29b6f11240]
/lib/x86_64-linux-gnu/libc.so.6(+0x1177f9)[0x7f29b6f107f9]
/lib/x86_64-linux-gnu/libc.so.6(_IO_default_xsputn+0xa9)[0x7f29b6e76a09]
/lib/x86_64-linux-gnu/libc.so.6(_IO_vfprintf+0x106)[0x7f29b6e469d6]
/lib/x86_64-linux-gnu/libc.so.6(__vsprintf_chk+0x84)[0x7f29b6f10884]
/lib/x86_64-linux-gnu/libc.so.6(__sprintf_chk+0x7d)[0x7f29b6f107dd]
/usr/lib/gcc/avr/4.9.2/../../../avr/bin/ld(+0x39eca)[0x55ce19723eca]
/usr/lib/gcc/avr/4.9.2/../../../avr/bin/ld(+0xadb6d)[0x55ce19797b6d]
/usr/lib/gcc/avr/4.9.2/../../../avr/bin/ld(+0x33f24)[0x55ce1971df24]
/usr/lib/gcc/avr/4.9.2/../../../avr/bin/ld(+0x34af5)[0x55ce1971eaf5]
/usr/lib/gcc/avr/4.9.2/../../../avr/bin/ld(+0x349e7)[0x55ce1971e9e7]
/usr/lib/gcc/avr/4.9.2/../../../avr/bin/ld(+0x36f4a)[0x55ce19720f4a]
/usr/lib/gcc/avr/4.9.2/../../../avr/bin/ld(+0x25bf9)[0x55ce1970fbf9]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf1)[0x7f29b6e193f1]
/usr/lib/gcc/avr/4.9.2/../../../avr/bin/ld(+0x262ba)[0x55ce197102ba]
======= Memory map: ========
55ce196ea000-55ce19819000 r-xp 00000000 08:02 36045483                   /usr/lib/avr/bin/ld
55ce19a18000-55ce19a28000 r--p 0012e000 08:02 36045483                   /usr/lib/avr/bin/ld
55ce19a28000-55ce19a2c000 rw-p 0013e000 08:02 36045483                   /usr/lib/avr/bin/ld
55ce19a2c000-55ce19a33000 rw-p 00000000 00:00 0 
55ce1a833000-55ce1a8bb000 rw-p 00000000 00:00 0                          [heap]
7f29b65c7000-7f29b65dd000 r-xp 00000000 08:02 1835071                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7f29b65dd000-7f29b67dc000 ---p 00016000 08:02 1835071                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7f29b67dc000-7f29b67dd000 r--p 00015000 08:02 1835071                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7f29b67dd000-7f29b67de000 rw-p 00016000 08:02 1835071                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7f29b67de000-7f29b67ee000 r-xp 00000000 08:02 30543174                   /usr/lib/gcc/avr/4.9.2/liblto_plugin.so.0.0.0
7f29b67ee000-7f29b69ee000 ---p 00010000 08:02 30543174                   /usr/lib/gcc/avr/4.9.2/liblto_plugin.so.0.0.0
7f29b69ee000-7f29b69ef000 r--p 00010000 08:02 30543174                   /usr/lib/gcc/avr/4.9.2/liblto_plugin.so.0.0.0
7f29b69ef000-7f29b69f0000 rw-p 00011000 08:02 30543174                   /usr/lib/gcc/avr/4.9.2/liblto_plugin.so.0.0.0
7f29b69f0000-7f29b6df9000 r--p 00000000 08:02 30410509                   /usr/lib/locale/locale-archive
7f29b6df9000-7f29b6fb6000 r-xp 00000000 08:02 1835314                    /lib/x86_64-linux-gnu/libc-2.24.so
7f29b6fb6000-7f29b71b6000 ---p 001bd000 08:02 1835314                    /lib/x86_64-linux-gnu/libc-2.24.so
7f29b71b6000-7f29b71ba000 r--p 001bd000 08:02 1835314                    /lib/x86_64-linux-gnu/libc-2.24.so
7f29b71ba000-7f29b71bc000 rw-p 001c1000 08:02 1835314                    /lib/x86_64-linux-gnu/libc-2.24.so
7f29b71bc000-7f29b71c0000 rw-p 00000000 00:00 0 
7f29b71c0000-7f29b71c3000 r-xp 00000000 08:02 1835416                    /lib/x86_64-linux-gnu/libdl-2.24.so
7f29b71c3000-7f29b73c2000 ---p 00003000 08:02 1835416                    /lib/x86_64-linux-gnu/libdl-2.24.so
7f29b73c2000-7f29b73c3000 r--p 00002000 08:02 1835416                    /lib/x86_64-linux-gnu/libdl-2.24.so
7f29b73c3000-7f29b73c4000 rw-p 00003000 08:02 1835416                    /lib/x86_64-linux-gnu/libdl-2.24.so
7f29b73c4000-7f29b73dd000 r-xp 00000000 08:02 1835876                    /lib/x86_64-linux-gnu/libz.so.1.2.8
7f29b73dd000-7f29b75dc000 ---p 00019000 08:02 1835876                    /lib/x86_64-linux-gnu/libz.so.1.2.8
7f29b75dc000-7f29b75dd000 r--p 00018000 08:02 1835876                    /lib/x86_64-linux-gnu/libz.so.1.2.8
7f29b75dd000-7f29b75de000 rw-p 00019000 08:02 1835876                    /lib/x86_64-linux-gnu/libz.so.1.2.8
7f29b75de000-7f29b7603000 r-xp 00000000 08:02 1835306                    /lib/x86_64-linux-gnu/ld-2.24.so
7f29b77d2000-7f29b77d4000 rw-p 00000000 00:00 0 
7f29b77e5000-7f29b77e6000 rw-p 00000000 00:00 0 
7f29b77e6000-7f29b77f8000 r--p 00000000 08:02 32390828                   /usr/share/locale-langpack/bg/LC_MESSAGES/ld.mo
7f29b77f8000-7f29b77ff000 r--s 00000000 08:02 30806974                   /usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache
7f29b77ff000-7f29b7802000 rw-p 00000000 00:00 0 
7f29b7802000-7f29b7803000 r--p 00024000 08:02 1835306                    /lib/x86_64-linux-gnu/ld-2.24.so
7f29b7803000-7f29b7804000 rw-p 00025000 08:02 1835306                    /lib/x86_64-linux-gnu/ld-2.24.so
7f29b7804000-7f29b7805000 rw-p 00000000 00:00 0 
7ffc9798c000-7ffc979ad000 rw-p 00000000 00:00 0                          [stack]
7ffc979c0000-7ffc979c2000 r--p 00000000 00:00 0                          [vvar]
7ffc979c2000-7ffc979c4000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
```
:(
These are my versions for gcc-avr, avr-libc, and binutils:
         [B][I]binutils - 2.26.20160125+Atmel3.5.3-1(yakkety)
         avr-libc - 1:1.8.0+Atmel3.5.0-1[SIZE=3](yakkety)[/SIZE]
         gcc-avr - 1:4.9.2+Atmel3.5.0-1[SIZE=3](yakkety)[/SIZE][/I][/B]

And I am using **_*Ubuntu 16.10*_**!

Also at another computer that is installed _***Gento***_ works. The versions of avr-libc, binutils and gcc-avr are these :
[B][SIZE=3]        [I] avr-libc - 1.8.1
[SIZE=3]         binutils - 2.24[/SIZE]
[/I][/SIZE]*[SIZE=3]         gcc-avr - 4.9.3[/SIZE]*[/B]

My thoughts are that the versions are not compatible, or perhaps there is an error in binutils.
:confused:
Thank you for the help in advance :D
[/SIZE]

---


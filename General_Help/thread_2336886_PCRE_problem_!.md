---
title: "PCRE problem ?!"
date: 2016-09-12
forum: General Help
---

### Post by fairbird on 2016-09-12
I've this problem in my ubuntu 14.04
```
NAME="Ubuntu"VERSION="14.04.5 LTS, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04.5 LTS"
VERSION_ID="14.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"

```


```
ERROR: Unable to spawn terminal auto: Execution of '/home/raed/openpli/openpli-oe-core/build/tmp/work/mips32el-nf-oe-linux/gstreamer1.0-plugins-bad/1.9.2.1+gitAUTOINC+c117165f7b-r1/temp/run.do_terminal.16544' failed with exit code -5:

(gnome-terminal:17134): GLib-GIO-ERROR **: No GSettings schemas are installed on the system


ERROR: 
ERROR: Function failed: patch_do_patch
ERROR: Logfile of failure stored in: /home/raed/openpli/openpli-oe-core/build/tmp/work/mips32el-nf-oe-linux/gstreamer1.0-plugins-bad/1.9.2.1+gitAUTOINC+c117165f7b-r1/temp/log.do_patch.16544
ERROR: Task 1151 (/home/raed/openpli/openpli-oe-core/meta-openpli/recipes-multimedia/gstreamer/gstreamer1.0-plugins-bad_git.bb, do_patch) failed with exit code '1'
ERROR: Function failed: do_configure (log file is located at /home/raed/openpli/openpli-oe-core/build/tmp/work/i686-linux/glib-2.0-native/1_2.46.2-r0/temp/log.do_configure.16302)
ERROR: Logfile of failure stored in: /home/raed/openpli/openpli-oe-core/build/tmp/work/i686-linux/glib-2.0-native/1_2.46.2-r0/temp/log.do_configure.16302



| checking for broken poll... no
| checking for PCRE... yes
| checking for Unicode support in PCRE... no
| configure: error: *** The system-supplied PCRE does not support Unicode properties or UTF-8.
| Configure failed. The contents of all config.log files follows to aid debugging
| ERROR: oe_runconf failed
| WARNING: /home/raed/openpli/openpli-oe-core/build/tmp/work/i686-linux/glib-2.0-native/1_2.46.2-r0/temp/run.do_configure.16302:1 exit 1 from
|   exit 1
| ERROR: Function failed: do_configure (log file is located at /home/raed/openpli/openpli-oe-core/build/tmp/work/i686-linux/glib-2.0-native/1_2.46.2-r0/temp/log.do_configure.16302)
ERROR: Task 2308 (virtual:native:/home/raed/openpli/openpli-oe-core/openembedded-core/meta/recipes-core/glib-2.0/glib-2.0_2.46.2.bb, do_configure) failed with exit code '1'
NOTE: Tasks Summary: Attempted 2844 tasks of which 2828 didn't need to be rerun and 2 failed.
Waiting for 0 running tasks to finish:


Summary: 2 tasks failed:
  /home/raed/openpli/openpli-oe-core/meta-openpli/recipes-multimedia/gstreamer/gstreamer1.0-plugins-bad_git.bb, do_patch
  virtual:native:/home/raed/openpli/openpli-oe-core/openembedded-core/meta/recipes-core/glib-2.0/glib-2.0_2.46.2.bb, do_configure
Summary: There were 4 ERROR messages shown, returning a non-zero exit code.
```

I've also [COLOR=#282828][FONT=helvetica]updated PCER to 8.35
[/FONT][/COLOR]```
raed@fairbird:~$ php -i | grep PCREPCRE (Perl Compatible Regular Expressions) Support => enabledPCRE Library Version => 8.35 2014-04-04




raed@fairbird:$ locate libpcre
/lib/i386-linux-gnu/libpcre.so.3
/lib/i386-linux-gnu/libpcre.so.3.13.1
/usr/lib/i386-linux-gnu/libpcre.a
/usr/lib/i386-linux-gnu/libpcre.so
/usr/lib/i386-linux-gnu/libpcrecpp.a
/usr/lib/i386-linux-gnu/libpcrecpp.so
/usr/lib/i386-linux-gnu/libpcrecpp.so.0
/usr/lib/i386-linux-gnu/libpcrecpp.so.0.0.0
/usr/lib/i386-linux-gnu/libpcreposix.a
/usr/lib/i386-linux-gnu/libpcreposix.so
/usr/lib/i386-linux-gnu/libpcreposix.so.3
/usr/lib/i386-linux-gnu/libpcreposix.so.3.13.1
/usr/lib/i386-linux-gnu/pkgconfig/libpcre.pc
/usr/lib/i386-linux-gnu/pkgconfig/libpcrecpp.pc
/usr/lib/i386-linux-gnu/pkgconfig/libpcreposix.pc
/usr/share/doc/libpcre3
/usr/share/doc/libpcre3-dev
/usr/share/doc/libpcrecpp0
/usr/share/doc/libpcre3/AUTHORS
/usr/share/doc/libpcre3/NEWS.gz
/usr/share/doc/libpcre3/README.Debian
/usr/share/doc/libpcre3/README.gz
/usr/share/doc/libpcre3/changelog.Debian.gz
/usr/share/doc/libpcre3/copyright
/usr/share/doc/libpcre3-dev/changelog.Debian.gz
/usr/share/doc/libpcre3-dev/copyright
/usr/share/doc/libpcre3-dev/examples
/usr/share/doc/libpcre3-dev/examples/pcredemo.c.gz
/usr/share/doc/libpcrecpp0/AUTHORS
/usr/share/doc/libpcrecpp0/NEWS.gz
/usr/share/doc/libpcrecpp0/README.gz
/usr/share/doc/libpcrecpp0/changelog.Debian.gz
/usr/share/doc/libpcrecpp0/copyright
/var/cache/apt/archives/libpcre3-dev_1%3a8.31-2ubuntu2.3_i386.deb
/var/cache/apt/archives/libpcrecpp0_1%3a8.31-2ubuntu2.3_i386.deb
/var/lib/dpkg/info/libpcre3-dev:i386.list
/var/lib/dpkg/info/libpcre3-dev:i386.md5sums
/var/lib/dpkg/info/libpcre3:i386.list
/var/lib/dpkg/info/libpcre3:i386.md5sums
/var/lib/dpkg/info/libpcre3:i386.postinst
/var/lib/dpkg/info/libpcre3:i386.postrm
/var/lib/dpkg/info/libpcre3:i386.shlibs
/var/lib/dpkg/info/libpcre3:i386.symbols
/var/lib/dpkg/info/libpcrecpp0:i386.list
/var/lib/dpkg/info/libpcrecpp0:i386.md5sums
/var/lib/dpkg/info/libpcrecpp0:i386.postinst
/var/lib/dpkg/info/libpcrecpp0:i386.postrm
/var/lib/dpkg/info/libpcrecpp0:i386.shlibs

/var/lib/dpkg/info/libpcrecpp0:i386.symbols
``` 

> [COLOR=#000000]raed@fairbird[/COLOR][COLOR=#666600]:~[/COLOR][COLOR=#000000]$ pcretest [/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]C
[/COLOR][COLOR=#000000]pcretest[/COLOR][COLOR=#666600]:[/COLOR][COLOR=#000000] command [/COLOR][COLOR=#000088]not[/COLOR][COLOR=#000000] found[/COLOR]

but I still got same error ..

Any idea please ?!

Thank you

---

### Post by fairbird on 2016-09-13
Any source can I add to install pcre2-utils ?!
Because I've add it manually but I got same command missing ?!

> [COLOR=#000000]raed@fairbird[/COLOR][COLOR=#666600]:~/[/COLOR][COLOR=#660066]Desktop$[/COLOR][COLOR=#000000] sudo dpkg [/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]i libpcre2[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]16[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]0_10.21[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]1[/COLOR][COLOR=#000000]_i386[/COLOR][COLOR=#666600].[/COLOR][COLOR=#000000]deb[/COLOR][COLOR=#660066]Selecting[/COLOR] previously unselected [COLOR=#000088]package[/COLOR] libpcre2[COLOR=#666600]-[/COLOR][COLOR=#006666]16[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]0[/COLOR][COLOR=#666600]:[/COLOR]i386[COLOR=#666600].[/COLOR]
[COLOR=#666600]([/COLOR][COLOR=#660066]Reading[/COLOR] database [COLOR=#666600]...[/COLOR] [COLOR=#006666]235412[/COLOR] files [COLOR=#000088]and[/COLOR] directories currently installed[COLOR=#666600].)[/COLOR]
[COLOR=#660066]Preparing[/COLOR] to unpack libpcre2[COLOR=#666600]-[/COLOR][COLOR=#006666]16[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]0_10.21[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]1[/COLOR]_i386[COLOR=#666600].[/COLOR]deb [COLOR=#666600]...[/COLOR]
[COLOR=#660066]Unpacking[/COLOR] libpcre2[COLOR=#666600]-[/COLOR][COLOR=#006666]16[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]0[/COLOR][COLOR=#666600]:[/COLOR]i386 [COLOR=#666600]([/COLOR][COLOR=#006666]10.21[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]1[/COLOR][COLOR=#666600])[/COLOR] [COLOR=#666600]...[/COLOR]
[COLOR=#660066]Setting[/COLOR] up libpcre2[COLOR=#666600]-[/COLOR][COLOR=#006666]16[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]0[/COLOR][COLOR=#666600]:[/COLOR]i386 [COLOR=#666600]([/COLOR][COLOR=#006666]10.21[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]1[/COLOR][COLOR=#666600])[/COLOR] [COLOR=#666600]...[/COLOR]
[COLOR=#660066]Processing[/COLOR] triggers [COLOR=#000088]for[/COLOR] libc[COLOR=#666600]-[/COLOR]bin [COLOR=#666600]([/COLOR][COLOR=#006666]2.19[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]0ubuntu6.9[/COLOR][COLOR=#666600])[/COLOR] [COLOR=#666600]...[/COLOR]
raed@fairbird[COLOR=#666600]:~/[/COLOR][COLOR=#660066]Desktop$[/COLOR] sudo dpkg [COLOR=#666600]-[/COLOR]i libpcre2[COLOR=#666600]-[/COLOR][COLOR=#006666]32[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]0_10.21[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]1[/COLOR]_i386[COLOR=#666600].[/COLOR]deb
[COLOR=#666600]([/COLOR][COLOR=#660066]Reading[/COLOR] database [COLOR=#666600]...[/COLOR] [COLOR=#006666]235417[/COLOR] files [COLOR=#000088]and[/COLOR] directories currently installed[COLOR=#666600].)[/COLOR]
[COLOR=#660066]Preparing[/COLOR] to unpack libpcre2[COLOR=#666600]-[/COLOR][COLOR=#006666]32[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]0_10.21[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]1[/COLOR]_i386[COLOR=#666600].[/COLOR]deb [COLOR=#666600]...[/COLOR]
[COLOR=#660066]Unpacking[/COLOR] libpcre2[COLOR=#666600]-[/COLOR][COLOR=#006666]32[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]0[/COLOR][COLOR=#666600]:[/COLOR]i386 [COLOR=#666600]([/COLOR][COLOR=#006666]10.21[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]1[/COLOR][COLOR=#666600])[/COLOR] over [COLOR=#666600]([/COLOR][COLOR=#006666]10.21[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]1[/COLOR][COLOR=#666600])[/COLOR] [COLOR=#666600]...[/COLOR]
[COLOR=#660066]Setting[/COLOR] up libpcre2[COLOR=#666600]-[/COLOR][COLOR=#006666]32[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]0[/COLOR][COLOR=#666600]:[/COLOR]i386 [COLOR=#666600]([/COLOR][COLOR=#006666]10.21[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]1[/COLOR][COLOR=#666600])[/COLOR] [COLOR=#666600]...[/COLOR]
[COLOR=#660066]Processing[/COLOR] triggers [COLOR=#000088]for[/COLOR] libc[COLOR=#666600]-[/COLOR]bin [COLOR=#666600]([/COLOR][COLOR=#006666]2.19[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]0ubuntu6.9[/COLOR][COLOR=#666600])[/COLOR] [COLOR=#666600]...[/COLOR]
raed@fairbird[COLOR=#666600]:~/[/COLOR][COLOR=#660066]Desktop$[/COLOR] sudo dpkg [COLOR=#666600]-[/COLOR]i libpcre2[COLOR=#666600]-[/COLOR][COLOR=#006666]8[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]0_10.21[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]1[/COLOR]_i386[COLOR=#666600].[/COLOR]deb
[COLOR=#666600]([/COLOR][COLOR=#660066]Reading[/COLOR] database [COLOR=#666600]...[/COLOR] [COLOR=#006666]235417[/COLOR] files [COLOR=#000088]and[/COLOR] directories currently installed[COLOR=#666600].)[/COLOR]
[COLOR=#660066]Preparing[/COLOR] to unpack libpcre2[COLOR=#666600]-[/COLOR][COLOR=#006666]8[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]0_10.21[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]1[/COLOR]_i386[COLOR=#666600].[/COLOR]deb [COLOR=#666600]...[/COLOR]
[COLOR=#660066]Unpacking[/COLOR] libpcre2[COLOR=#666600]-[/COLOR][COLOR=#006666]8[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]0[/COLOR][COLOR=#666600]:[/COLOR]i386 [COLOR=#666600]([/COLOR][COLOR=#006666]10.21[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]1[/COLOR][COLOR=#666600])[/COLOR] over [COLOR=#666600]([/COLOR][COLOR=#006666]10.21[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]1[/COLOR][COLOR=#666600])[/COLOR] [COLOR=#666600]...[/COLOR]
[COLOR=#660066]Setting[/COLOR] up libpcre2[COLOR=#666600]-[/COLOR][COLOR=#006666]8[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]0[/COLOR][COLOR=#666600]:[/COLOR]i386 [COLOR=#666600]([/COLOR][COLOR=#006666]10.21[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]1[/COLOR][COLOR=#666600])[/COLOR] [COLOR=#666600]...[/COLOR]
[COLOR=#660066]Processing[/COLOR] triggers [COLOR=#000088]for[/COLOR] libc[COLOR=#666600]-[/COLOR]bin [COLOR=#666600]([/COLOR][COLOR=#006666]2.19[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]0ubuntu6.9[/COLOR][COLOR=#666600])[/COLOR] [COLOR=#666600]...[/COLOR]
raed@fairbird[COLOR=#666600]:~/[/COLOR][COLOR=#660066]Desktop$[/COLOR] sudo dpkg [COLOR=#666600]-[/COLOR]i libpcre2[COLOR=#666600]-[/COLOR]posix0_10[COLOR=#666600].[/COLOR][COLOR=#006666]21[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]1[/COLOR]_i386[COLOR=#666600].[/COLOR]deb
[COLOR=#666600]([/COLOR][COLOR=#660066]Reading[/COLOR] database [COLOR=#666600]...[/COLOR] [COLOR=#006666]235417[/COLOR] files [COLOR=#000088]and[/COLOR] directories currently installed[COLOR=#666600].)[/COLOR]
[COLOR=#660066]Preparing[/COLOR] to unpack libpcre2[COLOR=#666600]-[/COLOR]posix0_10[COLOR=#666600].[/COLOR][COLOR=#006666]21[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]1[/COLOR]_i386[COLOR=#666600].[/COLOR]deb [COLOR=#666600]...[/COLOR]
[COLOR=#660066]Unpacking[/COLOR] libpcre2[COLOR=#666600]-[/COLOR]posix0[COLOR=#666600]:[/COLOR]i386 [COLOR=#666600]([/COLOR][COLOR=#006666]10.21[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]1[/COLOR][COLOR=#666600])[/COLOR] over [COLOR=#666600]([/COLOR][COLOR=#006666]10.21[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]1[/COLOR][COLOR=#666600])[/COLOR] [COLOR=#666600]...[/COLOR]
[COLOR=#660066]Setting[/COLOR] up libpcre2[COLOR=#666600]-[/COLOR]posix0[COLOR=#666600]:[/COLOR]i386 [COLOR=#666600]([/COLOR][COLOR=#006666]10.21[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]1[/COLOR][COLOR=#666600])[/COLOR] [COLOR=#666600]...[/COLOR]
[COLOR=#660066]Processing[/COLOR] triggers [COLOR=#000088]for[/COLOR] libc[COLOR=#666600]-[/COLOR]bin [COLOR=#666600]([/COLOR][COLOR=#006666]2.19[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]0ubuntu6.9[/COLOR][COLOR=#666600])[/COLOR] [COLOR=#666600]...[/COLOR]
raed@fairbird[COLOR=#666600]:~/[/COLOR][COLOR=#660066]Desktop$[/COLOR] sudo dpkg [COLOR=#666600]-[/COLOR]i pcre2[COLOR=#666600]-[/COLOR]utils_10[COLOR=#666600].[/COLOR][COLOR=#006666]21[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]1[/COLOR]_i386[COLOR=#666600].[/COLOR]deb
[COLOR=#666600]([/COLOR][COLOR=#660066]Reading[/COLOR] database [COLOR=#666600]...[/COLOR] [COLOR=#006666]235417[/COLOR] files [COLOR=#000088]and[/COLOR] directories currently installed[COLOR=#666600].)[/COLOR]
[COLOR=#660066]Preparing[/COLOR] to unpack pcre2[COLOR=#666600]-[/COLOR]utils_10[COLOR=#666600].[/COLOR][COLOR=#006666]21[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]1[/COLOR]_i386[COLOR=#666600].[/COLOR]deb [COLOR=#666600]...[/COLOR]
[COLOR=#660066]Unpacking[/COLOR] pcre2[COLOR=#666600]-[/COLOR]utils [COLOR=#666600]([/COLOR][COLOR=#006666]10.21[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]1[/COLOR][COLOR=#666600])[/COLOR] over [COLOR=#666600]([/COLOR][COLOR=#006666]10.21[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]1[/COLOR][COLOR=#666600])[/COLOR] [COLOR=#666600]...[/COLOR]
[COLOR=#660066]Setting[/COLOR] up pcre2[COLOR=#666600]-[/COLOR]utils [COLOR=#666600]([/COLOR][COLOR=#006666]10.21[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]1[/COLOR][COLOR=#666600])[/COLOR] [COLOR=#666600]...[/COLOR]
[COLOR=#660066]Processing[/COLOR] triggers [COLOR=#000088]for[/COLOR] man[COLOR=#666600]-[/COLOR]db [COLOR=#666600]([/COLOR][COLOR=#006666]2.6[/COLOR][COLOR=#666600].[/COLOR][COLOR=#006666]7.1[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]1ubuntu1[/COLOR][COLOR=#666600])[/COLOR] [COLOR=#666600]...[/COLOR]
raed@fairbird[COLOR=#666600]:~/[/COLOR][COLOR=#660066]Desktop$[/COLOR] pcretest [COLOR=#666600]-[/COLOR]C [COLOR=#000000]pcretest[/COLOR][COLOR=#666600]:[/COLOR][COLOR=#000000] command [/COLOR][COLOR=#000088]not[/COLOR][COLOR=#000000] found[/COLOR]

---

### Post by howefield on 2016-09-13
How feasible is an upgrade to 16.04.1 ?

Packages appear present in xenial.

---

### Post by fairbird on 2016-09-13
I'm compile and build dreambox images ...
I've tried 16.04 but I've got such of error with compile ..then I've returned back to 14.04 ..

So can I install xenial on 14.04 without problem ?! and How to install any source ?!

Thank you

---

### Post by fairbird on 2016-09-15
ok...

I have installed new ubuntu 16.04 ...

But still I have problem ....

I'm update moving from 14.04 to 16.04 because 14.04 doesn't supported ([COLOR=#282828][FONT=helvetica]pcre-tools [/FONT][/COLOR][COLOR=#282828][FONT=helvetica]package[/FONT][/COLOR])
And also 16.04 doesn't supported, just ([COLOR=#282828][FONT=helvetica]pcre2-utils package[/FONT][/COLOR]) ...

I've installed and I got only this code supported 
> raed@fairbird:~/openpli/openpli-oe-core/build$ pcre2test -C
PCRE2  version 10.21 2016-01-12
Compiled with
8-bit support
16-bit support
32-bit support
UTF and UCP support (Unicode version 8.0.0)
Just-in-time compiler support: x86 32bit (little endian + unaligned)
Newline sequence is LF
\R matches CR, LF, or CRLF only
\C is supported
Internal link size = 2
Parentheses nest limit = 250
Default match limit = 10000000
Default recursion depth limit = 10000000
Match recursion uses stack

It missing 
> [COLOR=#000000]UTF[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]8[/COLOR][COLOR=#000000] support[/COLOR] UTF[COLOR=#666600]-[/COLOR][COLOR=#006666]16[/COLOR] support
UTF[COLOR=#666600]-[/COLOR][COLOR=#006666]32[/COLOR] support [COLOR=#660066]Unicode[/COLOR][COLOR=#000000] properties support[/COLOR]
because ([COLOR=#282828][FONT=helvetica]pcre-tools [/FONT][/COLOR][COLOR=#282828][FONT=helvetica]package[/FONT][/COLOR]) have this 
> [COLOR=#666600][[/COLOR][COLOR=#000000]wanwizard@catwoman[/COLOR][COLOR=#666600]][/COLOR][COLOR=#000000] $ pcretest [/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]C
[/COLOR]PCRE version [COLOR=#006666]8.39[/COLOR] [COLOR=#006666]2016[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]06[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]14[/COLOR]
[COLOR=#660066]Compiled[/COLOR] [COLOR=#000088]with[/COLOR]
[COLOR=#006666]8[/COLOR][COLOR=#666600]-[/COLOR]bit support
UTF[COLOR=#666600]-[/COLOR][COLOR=#006666]8[/COLOR] support
[COLOR=#006666]16[/COLOR][COLOR=#666600]-[/COLOR]bit support
UTF[COLOR=#666600]-[/COLOR][COLOR=#006666]16[/COLOR] support
[COLOR=#006666]32[/COLOR][COLOR=#666600]-[/COLOR]bit support
UTF[COLOR=#666600]-[/COLOR][COLOR=#006666]32[/COLOR] support
[COLOR=#660066]Unicode[/COLOR] properties support
[COLOR=#660066]Just[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000088]in[/COLOR][COLOR=#666600]-[/COLOR]time compiler support[COLOR=#666600]:[/COLOR] x86 [COLOR=#006666]64bit[/COLOR] [COLOR=#666600]([/COLOR]little endian [COLOR=#666600]+[/COLOR] unaligned[COLOR=#666600])[/COLOR]
[COLOR=#660066]Newline[/COLOR] sequence [COLOR=#000088]is[/COLOR] LF
\R matches all [COLOR=#660066]Unicode[/COLOR] newlines
[COLOR=#660066]Internal[/COLOR] link size [COLOR=#666600]=[/COLOR] [COLOR=#006666]2[/COLOR]
POSIX malloc threshold [COLOR=#666600]=[/COLOR] [COLOR=#006666]10[/COLOR]
[COLOR=#660066]Parentheses[/COLOR] nest limit [COLOR=#666600]=[/COLOR] [COLOR=#006666]250[/COLOR]
[COLOR=#660066]Default[/COLOR] match limit [COLOR=#666600]=[/COLOR] [COLOR=#006666]10000000[/COLOR]
[COLOR=#660066]Default[/COLOR] recursion depth limit [COLOR=#666600]=[/COLOR] [COLOR=#006666]10000000[/COLOR] [COLOR=#660066]Match[/COLOR][COLOR=#000000] recursion uses stack[/COLOR]

I need 
> [COLOR=#000000]UTF[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]8[/COLOR][COLOR=#000000] support
[/COLOR]UTF[COLOR=#666600]-[/COLOR][COLOR=#006666]16[/COLOR] support
UTF[COLOR=#666600]-[/COLOR][COLOR=#006666]32[/COLOR] support 
[COLOR=#660066]Unicode[/COLOR][COLOR=#000000] properties support[/COLOR]

Because I got this error with my build image dreambox
> | configure: error: *** The system-supplied PCRE does not support Unicode properties or UTF-8.


So How can I get full support from [COLOR=#000000]pcre ?![/COLOR]

---

### Post by fairbird on 2016-09-15
I have install PCRE 8.39
but get some missing support ...how can I enable that missing ?!
> raed@fairbird:~/pcre-8.39$ pcretest -CPCRE version 8.39 2016-06-14
Compiled with
  8-bit support
  No UTF-8 support
  No Unicode properties support
  No just-in-time compiler support
  Newline sequence is LF
  \R matches all Unicode newlines
  Internal link size = 2
  POSIX malloc threshold = 10
  Parentheses nest limit = 250
  Default match limit = 10000000
  Default recursion depth limit = 10000000
  Match recursion uses stack
raed@fairbird:~/pcre-8.39$

---

### Post by fairbird on 2016-09-15
[COLOR=#282828][FONT=helvetica]I fixes by these command[/FONT][/COLOR]
[COLOR=#666600]./[/COLOR]configure [COLOR=#666600]--[/COLOR]enable[COLOR=#666600]-[/COLOR]pcre16 [COLOR=#666600]--[/COLOR]enable[COLOR=#666600]-[/COLOR]pcre32 [COLOR=#666600]--[/COLOR]enable[COLOR=#666600]-[/COLOR]utf [COLOR=#666600]--[/COLOR]enable[COLOR=#666600]-[/COLOR]unicode[COLOR=#666600]-[/COLOR]properties
sudo make
sudo make install[COLOR=#282828][FONT=helvetica]and I got[/FONT][/COLOR]
> raed@fairbird[COLOR=#666600]:~/[/COLOR]pcre[COLOR=#666600]-[/COLOR][COLOR=#006666]8.39[/COLOR]$ pcretest [COLOR=#666600]-[/COLOR]C
PCRE version [COLOR=#006666]8.39[/COLOR] [COLOR=#006666]2016[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]06[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]14[/COLOR]
[COLOR=#660066]Compiled[/COLOR] [COLOR=#000088]with[/COLOR]
[COLOR=#006666]8[/COLOR][COLOR=#666600]-[/COLOR]bit support
UTF[COLOR=#666600]-[/COLOR][COLOR=#006666]8[/COLOR] support
[COLOR=#006666]16[/COLOR][COLOR=#666600]-[/COLOR]bit support
UTF[COLOR=#666600]-[/COLOR][COLOR=#006666]16[/COLOR] support
[COLOR=#006666]32[/COLOR][COLOR=#666600]-[/COLOR]bit support
UTF[COLOR=#666600]-[/COLOR][COLOR=#006666]32[/COLOR] support
[COLOR=#660066]Unicode[/COLOR] properties support
[COLOR=#660066]No[/COLOR] just[COLOR=#666600]-[/COLOR][COLOR=#000088]in[/COLOR][COLOR=#666600]-[/COLOR]time compiler support
[COLOR=#660066]Newline[/COLOR] sequence [COLOR=#000088]is[/COLOR] LF
\R matches all [COLOR=#660066]Unicode[/COLOR] newlines
[COLOR=#660066]Internal[/COLOR] link size [COLOR=#666600]=[/COLOR] [COLOR=#006666]2[/COLOR]
POSIX malloc threshold [COLOR=#666600]=[/COLOR] [COLOR=#006666]10[/COLOR]
[COLOR=#660066]Parentheses[/COLOR] nest limit [COLOR=#666600]=[/COLOR] [COLOR=#006666]250[/COLOR]
[COLOR=#660066]Default[/COLOR] match limit [COLOR=#666600]=[/COLOR] [COLOR=#006666]10000000[/COLOR]
[COLOR=#660066]Default[/COLOR] recursion depth limit [COLOR=#666600]=[/COLOR] [COLOR=#006666]10000000[/COLOR]
[COLOR=#660066]Match[/COLOR] recursion uses stack

[COLOR=#282828][FONT=helvetica]but still I got error with comiple

> [COLOR=#000000][FONT=Verdana]ERROR[/FONT][/COLOR][COLOR=#666600][FONT=Verdana]:[/FONT][/COLOR][COLOR=#660066][FONT=Verdana]Unable[/FONT][/COLOR][COLOR=#000000][FONT=Verdana] to spawn terminal [/FONT][/COLOR][COLOR=#000088][FONT=Verdana]auto[/FONT][/COLOR][COLOR=#666600][FONT=Verdana]:[/FONT][/COLOR][COLOR=#660066][FONT=Verdana]Execution[/FONT][/COLOR][COLOR=#000000][FONT=Verdana] of [/FONT][/COLOR][COLOR=#008800][FONT=Verdana]'/home/raed/openpli/openpli-oe-core/build/tmp/work/mips32el-nf-oe-linux/gstreamer1.0-plugins-bad/1.9.2.1+gitAUTOINC+c117165f7b-r1/temp/run.do_terminal.8758'[/FONT][/COLOR][COLOR=#000000][FONT=Verdana] failed [/FONT][/COLOR][COLOR=#000088][FONT=Verdana]with[/FONT][/COLOR][COLOR=#000088][FONT=Verdana]exit[/FONT][/COLOR][COLOR=#000000][FONT=Verdana] code [/FONT][/COLOR][COLOR=#006666][FONT=Verdana]8[/FONT][/COLOR][COLOR=#666600][FONT=Verdana]:[/FONT][/COLOR][/FONT][/COLOR]
[COLOR=#660066]Non[/COLOR] UTF[COLOR=#666600]-[/COLOR][COLOR=#006666]8[/COLOR] locale [COLOR=#666600]([/COLOR]ANSI_X3[COLOR=#666600].[/COLOR][COLOR=#006666]4[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]1968[/COLOR][COLOR=#666600])[/COLOR] [COLOR=#000088]is[/COLOR] [COLOR=#000088]not[/COLOR] supported[COLOR=#666600]!

[/COLOR][COLOR=#282828][FONT=helvetica]| checking for Unicode support in PCRE... no[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]| configure: error: *** The system-supplied PCRE does not support Unicode properties or UTF-8.[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]| Configure failed. The contents of all config.log files follows to aid debugging[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]| ERROR: oe_runconf failed[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]| WARNING: /home/raed/openpli/openpli-oe-core/build/tmp/work/i686-linux/glib-2.0-native/1_2.46.2-r0/temp/run.do_configure.8558:1 exit 1 from[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]|   exit 1[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]| ERROR: Function failed: do_configure (log file is located at /home/raed/openpli/openpli-oe-core/build/tmp/work/i686-linux/glib-2.0-native/1_2.46.2-r0/temp/log.do_configure.8558)[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]ERROR: Task 2308 (virtual:native:/home/raed/openpli/openpli-oe-core/openembedded-core/meta/recipes-core/glib-2.0/glib-2.0_2.46.2.bb, do_configure) failed with exit code '1'[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]NOTE: Tasks Summary: Attempted 2826 tasks of which 2814 didn't need to be rerun and 2 failed.[/FONT][/COLOR][COLOR=#282828][FONT=helvetica]
[/FONT][/COLOR]

---


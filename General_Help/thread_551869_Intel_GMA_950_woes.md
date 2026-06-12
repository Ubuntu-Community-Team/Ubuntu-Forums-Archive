---
title: "Intel GMA 950 woes"
date: 2007-09-15
forum: General Help
---

### Post by yang on 2007-09-15
I just installed Ubuntu 7.04 onto my new Dell Inspiron 530 desktop. Thanks to noob12 I just fixed my problem with Intel's Ethernet controller. Now I'm trying to get the graphics to work (better).

Currently I have very poor resolution. I can only go up to 1024x768. ubuntuguide.org says that I can manually edit xorg.conf to add higher resolutions if I'm on a >20" monitor and I want 1920x1200, but I have a Dell 2005FPW (20") whose native res is 1600x1050, so I have no idea what magic numbers to put on the "Modeline" line.

Also, I tried installing the 915resolution package as suggested in other threads, but it complains that I have the wrong chipset.

Lastly, I installed beryl, but running beryl-manager makes my screen go black for a second, and then I get logged out!

Here is some potentially relevant info:

```

yang@yang-inspiron:/tmp$ uname -a 
Linux yang-inspiron 2.6.20-16-generic #2 SMP Thu Aug 30 23:16:15 UTC 2007 x86_64 GNU/Linux

yang@yang-inspiron:/tmp$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Unknown device [8086:29c0] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation Unknown device [8086:29c1] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Unknown device [8086:29c2] (rev 02)
00:19.0 Ethernet controller [0200]: Intel Corporation Unknown device [8086:10c0] (rev 02)
00:1a.0 USB Controller [0c03]: Intel Corporation Unknown device [8086:2937] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation Unknown device [8086:2938] (rev 02)
00:1a.2 USB Controller [0c03]: Intel Corporation Unknown device [8086:2939] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation Unknown device [8086:293c] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation Unknown device [8086:293e] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation Unknown device [8086:2934] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation Unknown device [8086:2935] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation Unknown device [8086:2936] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation Unknown device [8086:293a] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 92)
00:1f.0 ISA bridge [0601]: Intel Corporation Unknown device [8086:2916] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation Unknown device [8086:2920] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation Unknown device [8086:2930] (rev 02)
00:1f.5 IDE interface [0101]: Intel Corporation Unknown device [8086:2926] (rev 02)
02:00.0 Communication controller [0780]: Conexant HSF 56k Data/Fax Modem [14f1:2f20]

```

Thanks in advance for any help.

---

### Post by yang on 2007-09-16
*bump*

---

### Post by yang on 2007-09-17
Anybody? I'm dyin' here, on Vista. :)

---

### Post by yang on 2007-09-18
This is a pretty serious issue for me. I'd like to avoid settling into Windows with my dev environment, because once I do, i know I'm going to end up using it for the next 3 years. I actually took the time and effort to free myself from Windows recently, and bought this computer to run Linux, only now to find that I can't look at my screen for too long in Ubuntu.

I tried tweaking xorg.conf, adding lines like 

```
Modeline	"1600x1050" 162.0 1600 1664 1856 2160 1050 1052 1064 1082
```

and

```
	SubSection "Display"
		Depth		24
		Modes		"1600x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
```

but nothing works (I restart X with c-a-bkspc).

I also went to the [http://www.intellinuxgraphics.org/](http://www.intellinuxgraphics.org/) site and downloaded the xf86-video-intel package but running autogen.sh gave me the following errors:

```
configure.ac:214: installing `./config.guess'
src/Makefile.am:36: Libtool library used but `LIBTOOL' is undefined
src/Makefile.am:36:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/Makefile.am:36:   to `configure.ac' and run `aclocal' and `autoconf' again.
src/Makefile.am:36:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
src/Makefile.am:36:   its definition is in aclocal's search path.
src/Makefile.am: installing `./depcomp'
src/ch7017/Makefile.am:8: Libtool library used but `LIBTOOL' is undefined
src/ch7017/Makefile.am:8:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/ch7017/Makefile.am:8:   to `configure.ac' and run `aclocal' and `autoconf' again.
src/ch7017/Makefile.am:8:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
src/ch7017/Makefile.am:8:   its definition is in aclocal's search path.
src/ch7xxx/Makefile.am:8: Libtool library used but `LIBTOOL' is undefined
src/ch7xxx/Makefile.am:8:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/ch7xxx/Makefile.am:8:   to `configure.ac' and run `aclocal' and `autoconf' again.
src/ch7xxx/Makefile.am:8:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
src/ch7xxx/Makefile.am:8:   its definition is in aclocal's search path.
src/ivch/Makefile.am:8: Libtool library used but `LIBTOOL' is undefined
src/ivch/Makefile.am:8:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/ivch/Makefile.am:8:   to `configure.ac' and run `aclocal' and `autoconf' again.
src/ivch/Makefile.am:8:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
src/ivch/Makefile.am:8:   its definition is in aclocal's search path.
src/sil164/Makefile.am:8: Libtool library used but `LIBTOOL' is undefined
src/sil164/Makefile.am:8:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/sil164/Makefile.am:8:   to `configure.ac' and run `aclocal' and `autoconf' again.
src/sil164/Makefile.am:8:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
src/sil164/Makefile.am:8:   its definition is in aclocal's search path.
src/tfp410/Makefile.am:8: Libtool library used but `LIBTOOL' is undefined
src/tfp410/Makefile.am:8:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/tfp410/Makefile.am:8:   to `configure.ac' and run `aclocal' and `autoconf' again.
src/tfp410/Makefile.am:8:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
src/tfp410/Makefile.am:8:   its definition is in aclocal's search path.
src/xvmc/Makefile.am:2: Libtool library used but `LIBTOOL' is undefined
src/xvmc/Makefile.am:2:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/xvmc/Makefile.am:2:   to `configure.ac' and run `aclocal' and `autoconf' again.
src/xvmc/Makefile.am:2:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
src/xvmc/Makefile.am:2:   its definition is in aclocal's search path.
autoreconf2.50: automake failed with exit status: 1

```

Thanks for any help.

---


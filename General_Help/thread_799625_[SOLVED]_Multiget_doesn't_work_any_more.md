---
title: "[SOLVED] Multiget doesn't work any more"
date: 2008-05-19
forum: General Help
---

### Post by pt123 on 2008-05-19
It was running fine on a Hardy a few weeks back but when I tried to run it today, I get this error message
```

*** stack smashing detected ***: multiget terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb6e95138]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb6e950f0]
multiget[0x8088704]
[0x74732064]


```
Memory Map
```

======= Memory map: ========
08048000-08159000 r-xp 00000000 08:03 122129     /usr/bin/multiget
08159000-0816a000 rw-p 00110000 08:03 122129     /usr/bin/multiget
0816a000-08235000 rw-p 0816a000 00:00 0          [heap]
b6703000-b6763000 rw-s 00000000 00:09 1507370    /SYSV00000000 (deleted)
b6763000-b67c3000 rw-s 00000000 00:09 1474601    /SYSV00000000 (deleted)
b67c3000-b67c9000 r-xp 00000000 08:03 140150     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b67c9000-b67ca000 rw-p 00005000 08:03 140150     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b67ca000-b67f9000 r-xp 00000000 08:03 139129     /usr/lib/libgnomecanvas-2.so.0.2001.0
b67f9000-b67fa000 rw-p 0002f000 08:03 139129     /usr/lib/libgnomecanvas-2.so.0.2001.0
b67fa000-b6838000 r-xp 00000000 08:03 139689     /usr/lib/libgnomeprintui-2-2.so.0.1.0
b6838000-b683a000 rw-p 0003d000 08:03 139689     /usr/lib/libgnomeprintui-2-2.so.0.1.0
b683a000-b684f000 r-xp 00000000 08:03 139348     /usr/lib/libart_lgpl_2.so.2.3.20
b684f000-b6850000 rw-p 00014000 08:03 139348     /usr/lib/libart_lgpl_2.so.2.3.20
b6850000-b68b3000 r-xp 00000000 08:03 139607     /usr/lib/libgnomeprint-2-2.so.0.1.0
b68b3000-b68b5000 rw-p 00063000 08:03 139607     /usr/lib/libgnomeprint-2-2.so.0.1.0
b68b7000-b68ba000 rw-s 00000000 00:09 1540139    /SYSV00000000 (deleted)
b68ba000-b68c5000 r-xp 00000000 08:03 138452     /usr/lib/gtk-2.0/2.10.0/engines/libmist.so
b68c5000-b68c6000 rw-p 0000a000 08:03 138452     /usr/lib/gtk-2.0/2.10.0/engines/libmist.so
b68c6000-b68cf000 r-xp 00000000 08:03 447090     /lib/tls/i686/cmov/libnss_files-2.7.so
b68cf000-b68d1000 rw-p 00008000 08:03 447090     /lib/tls/i686/cmov/libnss_files-2.7.so
b68d1000-b68d9000 r-xp 00000000 08:03 447119     /lib/tls/i686/cmov/libnss_nis-2.7.so
b68d9000-b68db000 rw-p 00007000 08:03 447119     /lib/tls/i686/cmov/libnss_nis-2.7.so
b68db000-b68ef000 r-xp 00000000 08:03 447088     /lib/tls/i686/cmov/libnsl-2.7.so
b68ef000-b68f1000 rw-p 00013000 08:03 447088     /lib/tls/i686/cmov/libnsl-2.7.so
b68f1000-b68f3000 rw-p b68f1000 00:00 0 
b68f3000-b68fa000 r-xp 00000000 08:03 447109     /lib/tls/i686/cmov/libnss_compat-2.7.so
b68fa000-b68fc000 rw-p 00006000 08:03 447109     /lib/tls/i686/cmov/libnss_compat-2.7.so
b68fc000-b68fd000 r--p 00000000 08:03 246450     /usr/share/locale-langpack/en_AU/LC_MESSAGES/glib20.mo
b68fd000-b6904000 r-xp 00000000 08:03 140001     /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
b6904000-b6905000 rw-p 00007000 08:03 140001     /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
b6905000-b690b000 r-xp 00000000 08:03 139857     /usr/lib/libgailutil.so.18.0.1
b690b000-b690c000 rw-p 00006000 08:03 139857     /usr/lib/libgailutil.so.18.0.1
b690c000-b690d000 r--p 00000000 08:03 246452     /usr/share/locale-langpack/en_AU/LC_MESSAGES/gtk20-properties.mo
b690d000-b6912000 r--p 00000000 08:03 246451     /usr/share/locale-langpack/en_AU/LC_MESSAGES/gtk20.mo
b6912000-b6913000 r--p 00000000 08:03 195122     /usr/lib/locale/en_AU.utf8/LC_NUMERIC
b6913000-b6914000 r--p 00000000 08:03 195161     /usr/lib/locale/en_AU.utf8/LC_TIME
b6914000-b69f5000 r--p 00000000 08:03 195128     /usr/lib/locale/en_AU.utf8/LC_COLLATE
b69f5000-b69f6000 r--p 00000000 08:03 195159     /usr/lib/locale/en_AU.utf8/LC_MONETARY
b69f6000-b69f7000 r--p 00000000 08:03 195136     /usr/lib/locale/en_AU.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b69f7000-b6a36000 r--p 00000000 08:03 195126     /usr/lib/locale/en_AU.utf8/LC_CTYPE
b6a36000-b6a3a000 rw-p b6a36000 00:00 0 
b6a3a000-b6a3e000 r-xp 00000000 08:03 139410     /usr/lib/libXdmcp.so.6.0.0
b6a3e000-b6a3f000 rw-p 00003000 08:03 139410     /usr/lib/libXdmcp.so.6.0.0
b6a3f000-b6a54000 r-xp 00000000 08:03 138758     /usr/lib/libICE.so.6.3.0
b6a54000-b6a55000 rw-p 00014000 08:03 138758     /usr/lib/libICE.so.6.3.0
b6a55000-b6a57000 rw-p b6a55000 00:00 0 
b6a57000-b6a6e000 r-xp 00000000 08:03 139191     /usr/lib/libxcb.so.1.0.0
b6a6e000-b6a6f000 rw-p 00016000 08:03 139191     /usr/lib/libxcb.so.1.0.0
b6a6f000-b6a70000 r-xp 00000000 08:03 139598     /usr/lib/libxcb-xlib.so.0.0.0
b6a70000-b6a71000 rw-p 00000000 08:03 139598     /usr/lib/libxcb-xlib.so.0.0.0
b6a71000-b6a72000 rw-p b6a71000 00:00 0 
b6a72000-b6a74000 r-xp 00000000 08:03 139151     /usr/lib/libXau.so.6.0.0
b6a74000-b6a75000 rw-p 00001000 08:03 139151     /usr/lib/libXau.so.6.0.0
b6a75000-b6a94000 r-xp 00000000 08:03 139519     /usr/lib/libexpat.so.1.5.2
b6a94000-b6a96000 rw-p 0001e000 08:03 139519     /usr/lib/libexpat.so.1.5.2
b6a96000-b6a97000 rw-p b6a96000 00:00 0 
b6a97000-b6ae8000 r-xp 00000000 08:03 138797     /usr/lib/libtiff.so.4.2.1
b6ae8000-b6aea000 rw-p 00050000 08:03 138797     /usr/lib/libtiff.so.4.2.1
b6aea000-b6b09000 r-xp 00000000 08:03 139696     /usr/lib/libjpeg.so.62.0.0
b6b09000-b6b0a000 rw-p 0001e000 08:03 139696     /usr/lib/libjpeg.so.62.0.0
b6b0a000-b6b11000 r-xp 00000000 08:03 139484     /usr/lib/libSM.so.6.0.0
b6b11000-b6b12000 rw-p 00006000 08:03 139484     /usr/lib/libSM.so.6.0.0
b6b12000-b6b19000 r-xp 00000000 08:03 447120     /lib/tls/i686/cmov/librt-2.7.so
b6b19000-b6b1b000 rw-p 00006000 08:03 447120     /lib/tls/i686/cmov/librt-2.7.so
b6b1b000-b6b1f000 r-xp 00000000 08:03 139913     /usr/lib/libgthread-2.0.so.0.1600.3
b6b1f000-b6b20000 rw-p 00003000 08:03 139913     /usr/lib/libgthread-2.0.so.0.1600.3
b6b20000-b6b46000 r-xp 00000000 08:03 138771     /usr/lib/libpcre.so.3.12.1
b6b46000-b6b47000 rw-p 00026000 08:03 138771     /usr/lib/libpcre.so.3.12.1
b6b47000-b6b48000 rw-p b6b47000 00:00 0 
b6b48000-b6b5f000 r-xp 00000000 08:03 448439     /lib/libselinux.so.1
b6b5f000-b6b61000 rw-p 00016000 08:03 448439     /lib/libselinux.so.1
b6b61000-b6b89000 r-xp 00000000 08:03 139143     /usr/lib/libpixman-1.so.0.10.0
b6b89000-b6b8a000 rw-p 00027000 08:03 139143     /usr/lib/libpixman-1.so.0.10.0
b6b8a000-b6bac000 r-xp 00000000 08:03 139727     /usr/lib/libpng12.so.0.15.0
b6bac000-b6bad000 rw-p 00022000 08:03 139727     /usr/lib/libpng12.so.0.15.0
b6bad000-b6c19000 r-xp 00000000 08:03 139320     /usr/lib/libfreetype.so.6.3.16
b6c19000-b6c1d000 rw-p 0006b000 08:03 139320     /usr/lib/libfreetype.so.6.3.16
b6c1d000-b6c43000 r-xp 00000000 08:03 139160     /usr/lib/libpangoft2-1.0.so.0.2000.1
b6c43000-b6c44000 rw-p 00026000 08:03 139160     /usr/lib/libpangoft2-1.0.so.0.2000.1
b6c44000-b6c45000 rw-p b6c44000 00:00 0 
b6c45000-b6c59000 r-xp 00000000 08:03 139896     /usr/lib/libz.so.1.2.3.3
b6c59000-b6c5a000 rw-p 00013000 08:03 139896     /usr/lib/libz.so.1.2.3.3
b6c5a000-b6c5e000 r-xp 00000000 08:03 140084     /usr/lib/libXfixes.so.3.1.0
b6c5e000-b6c5f000 rw-p 00003000 08:03 140084     /usr/lib/libXfixes.so.3.1.0
b6c5f000-b6d43000 r-xp 00000000 08:03 139337     /usr/lib/libX11.so.6.2.0
b6d43000-b6d46000 rw-p 000e4000 08:03 139337     /usr/lib/libX11.so.6.2.0
b6d46000-b6d48000 r-xp 00000000 08:03 139057     /usr/lib/libXdamage.so.1.1.0
b6d48000-b6d49000 rw-p 00001000 08:03 139057     /usr/lib/libXdamage.so.1.1.0
b6d49000-b6d4b000 r-xp 00000000 08:03 139259     /usr/lib/libXcomposite.so.1.0.0
b6d4b000-b6d4c000 rw-p 00001000 08:03 139259     /usr/lib/libXcomposite.so.1.0.0
b6d4c000-b6d4d000 rw-p b6d4c000 00:00 0 
b6d4d000-b6d55000 r-xp 00000000 08:03 139145     /usr/lib/libXcursor.so.1.0.2
b6d55000-b6d56000 rw-p 00007000 08:03 139145     /usr/lib/libXcursor.so.1.0.2
b6d56000-b6d5b000 r-xp 00000000 08:03 139248     /usr/lib/libXrandr.so.2.1.0
b6d5b000-b6d5c000 rw-p 00005000 08:03 139248     /usr/lib/libXrandr.so.2.1.0
b6d5c000-b6d63000 r-xp 00000000 08:03 138827     /usr/lib/libXi.so.6.0.0
b6d63000-b6d64000 rw-p 00006000 08:03 138827     /usr/lib/libXi.so.6.0.0
b6d64000-b6d66000 r-xp 00000000 08:03 140202     /usr/lib/libXinerama.so.1.0.0
b6d66000-b6d67000 rw-p 00001000 08:03 140202     /usr/lib/libXinerama.so.1.0.0
b6d67000-b6d6e000 r-xp 00000000 08:03 139293     /usr/lib/libXrender.so.1.3.0
b6d6e000-b6d6f000 rw-p 00007000 08:03 139293     /usr/lib/libXrender.so.1.3.0
b6d6f000-b6d7c000 r-xp 00000000 08:03 139671     /usr/lib/libXext.so.6.4.0
b6d7c000-b6d7d000 rw-p 0000d000 08:03 139671     /usr/lib/libXext.so.6.4.0
b6d7d000-b6d7e000 rw-p b6d7d000 00:00 0 
b6d7e000-b6da7000 r-xp 00000000 08:03 139693     /usr/lib/libfontconfig.so.1.3Aborted


```


The DEB I am using is 
multiget_1.2.0-0~getdeb1_i386

from GetDeb.net

I had similar issues from 
PPA for LI Daobing
[https://launchpad.net/~lidaobing/+archive](https://launchpad.net/~lidaobing/+archive)

Anyone else having this problem

---

### Post by pt123 on 2008-05-23
There was a problem with the .Multiget folder. AS I had copied it from another installation of mine.
After deleting it everything works fine.

---


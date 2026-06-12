---
title: "New Gutsy Install, Open Office Word Processor doesn't work at all!"
date: 2007-11-02
forum: General Help
---

### Post by bg1256 on 2007-11-02
I just did a fresh install of Gutsy this week, and I have almost no functionality with Open Office Word Processor.

I can open documents just fine, but when I attempt to edit them in any way, the program crashes. I can type text, but if I save it, crash.  I can open a document, but if I try to print it, crash.

Is this a common problem, and is there a workaround?  

I know it is not an open office problem, because I'm using the same version in Vista with no problems. It is clearly a gutsy problem, and a hugely significant one at that.

Thanks!

---

### Post by Can+~ on 2007-11-02
Well... to produce a diagnostic, we need info, so let's start by opening a terminal window and using

> oowriter
And see if it causes any output when crashing

Otherwise, check if it leaves any log in /var/log.

---

### Post by bg1256 on 2007-11-02
Thanks for the reply.

After running oowriter in a terminal, OOwriter opened just fine. So, I went to tools -> options -> view and it froze up, which it has been doing every time.

It didn't leave anything in /var/log, at least that I can see.

Here is the output from the terminal, although I don't see an error message:

```

fwe680li.so
b2f32000-b32f7000 r-xp 00000000 08:03 1343144    /usr/lib/openoffice/program/libsfx680li.so
b32f7000-b3311000 rw-p 003c4000 08:03 1343144    /usr/lib/openoffice/program/libsfx680li.so
b3311000-b3312000 rw-p b3311000 00:00 0 
b3312000-b336c000 r-xp 00000000 08:03 1343176    /usr/lib/openoffice/program/libucpfile1.so
b336c000-b336f000 rw-p 00059000 08:03 1343176    /usr/lib/openoffice/program/libucpfile1.so
b336f000-b33a8000 r-xp 00000000 08:03 1343065    /usr/lib/openoffice/program/libfwi680li.so
b33a8000-b33aa000 rw-p 00039000 08:03 1343065    /usr/lib/openoffice/program/libfwi680li.so
b33aa000-b33cc000 r-xp 00000000 08:03 1343067    /usr/lib/openoffice/program/libfwl680li.so
b33cc000-b33cd000 rw-p 00021000 08:03 1343067    /usr/lib/openoffice/program/libfwl680li.so
b33cd000-b3403000 r-xp 00000000 08:03 1618973    /lib/libsepol.so.1
b3403000-b3404000 rw-p 00035000 08:03 1618973    /lib/libsepol.so.1
b3404000-b340e000 rw-p b3404000 00:00 0 
b340e000-b345d000 r-xp 00000000 08:03 1277304    /usr/lib/libgcrypt.so.11.2.3
b345d000-b345f000 rw-p 0004e000 08:03 1277304    /usr/lib/libgcrypt.so.11.2.3
b345f000-b3462000 r-xp 00000000 08:03 1277411    /usr/lib/libgpg-error.so.0.3.0
b3462000-b3463000 rw-p 00002000 08:03 1277411    /usr/lib/libgpg-error.so.0.3.0
b3463000-b3472000 r-xp 00000000 08:03 1277779    /usr/lib/libtasn1.so.3.0.9
b3472000-b3473000 rw-p 0000e000 08:03 1277779    /usr/lib/libtasn1.so.3.0.9
b3473000-b3475000 r-xp 00000000 08:03 1622309    /lib/tls/i686/cmov/libutil-2.6.1.so
b3475000-b3477000 rw-p 00001000 08:03 1622309    /lib/tls/i686/cmov/libutil-2.6.1.so
b3477000-b348b000 r-xp 00000000 08:03 1618972    /lib/libselinux.so.1
b348b000-b348d000 rw-p 00013000 08:03 1618972    /lib/libselinux.so.1
b348d000-b349c000 r-xp 00000000 08:03 1622303    /lib/tls/i686/cmov/libresolv-2.6.1.so
b349c000-b349e000 rw-p 0000f000 08:03 1622303    /lib/tls/i686/cmov/libresolv-2.6.1.so
b349e000-b34a0000 rw-p b349e000 00:00 0 
b34a0000-b34ae000 r-xp 00000000 08:03 1277144    /usr/lib/libavahi-client.so.3.2.2
b34ae000-b34af000 rw-p 0000e000 08:03 1277144    /usr/lib/libavahi-client.so.3.2.2
b34af000-b34b9000 r-xp 00000000 08:03 1277146    /usr/lib/libavahi-common.so.3.4.4
b34b9000-b34ba000 rw-p 00009000 08:03 1277146    /usr/lib/libavahi-common.so.3.4.4
b34ba000-b3524000 r-xp 00000000 08:03 1277407    /usr/lib/libgnutls.so.13.3.0
b3524000-b352a000 rw-p 0006a000 08:03 1277407    /usr/lib/libgnutls.so.13.3.0
b352a000-b355e000 r-xp 00000000 08:03 1277207    /usr/lib/libdbus-1.so.3.3.0
b355e000-b355f000 rw-p 00033000 08:03 1277207    /usr/lib/libdbus-1.so.3.3.0
b355f000-b3579000 r-xp 00000000 08:03 1277209    /usr/lib/libdbus-glib-1.so.2.1.0
b3579000-b357a000 rw-p 0001a000 08:03 1277209    /usr/lib/libdbus-glib-1.so.2.1.0
b357a000-b35d0000 r-xp 00000000 08:03 1277401    /usr/lib/libgnomevfs-2.so.0.2000.0
b35d0000-b35d3000 rw-p 00055000 08:03 1277401    /usr/lib/libgnomevfs-2.so.0.2000.0
b35d3000-b35da000 r-xp 00000000 08:03 1340941    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
b35da000-b35db000 rw-p 00007000 08:03 1340941    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
b35db000-b35e1000 r-xp 00000000 08:03 1343091    /usr/lib/openoffice/program/libj680li_g.so
b35e1000-b35e2000 rw-p 00006000 08:03 1343091    /usr/lib/openoffice/program/libj680li_g.so
b35e2000-b3608000 r-xp 00000000 08:03 1343288    /usr/lib/openoffice/program/ucpgvfs1.uno.so
b3608000-b360a000 rw-p 00025000 08:03 1343288    /usr/lib/openoffice/program/ucpgvfs1.uno.so
b360a000-b364a000 r-xp 00000000 08:03 1343172    /usr/lib/openoffice/program/libucb1.so
b364a000-b364d000 rw-p 0003f000 08:03 1343172    /usr/lib/openoffice/program/libucb1.so
b364d000-b3652000 r-xp 00000000 08:03 1343152    /usr/lib/openoffice/program/libspl_unx680li.so
b3652000-b3653000 rw-p 00004000 08:03 1343152    /usr/lib/openoffice/program/libspl_unx680li.so
b3653000-b3654000 ---p b3653000 00:00 0 
b3654000-b3e54000 rw-p b3654000 00:00 0 
b3e54000-b3e69000 r-xp 00000000 08:03 1343297    /usr/lib/openoffice/program/uriproc.uno.so
b3e69000-b3e6b000 rw-p 00015000 08:03 1343297    /usr/lib/openoffice/program/uriproc.uno.so
b3e6b000-b3e6c000 ---p b3e6b000 00:00 0 
b3e6c000-b466c000 rw-p b3e6c000 00:00 0 
b466c000-b4674000 r-xp 00000000 08:03 1343215    /usr/lib/openoffice/program/localebe1.uno.so
b4674000-b4675000 rw-p 00007000 08:03 1343215    /usr/lib/openoffice/program/localebe1.uno.so
b4675000-b4691000 r-xp 00000000 08:03 1343252    /usr/lib/openoffice/program/sax.uno.so
b4691000-b4692000 rw-p 0001c000 08:03 1343252    /usr/lib/openoffice/program/sax.uno.so
b4692000-b46db000 r-xp 00000000 08:03 1277047    /usr/lib/libORBit-2.so.0.1.0
b46db000-b46e4000 rw-p 00049000 08:03 1277047    /usr/lib/libORBit-2.so.0.1.0
b46e4000-b46e5000 rw-p b46e4000 00:00 0 
b46e5000-b4714000 r-xp 00000000 08:03 1277302    /usr/lib/libgconf-2.so.4.1.2
b4714000-b4717000 rw-p 0002e000 08:03 1277302    /usr/lib/libgconf-2.so.4.1.2
b4718000-b4719000 r--s 00000000 08:03 32777      /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b4719000-b471b000 r-xp 00000000 08:03 1277150    /usr/lib/libavahi-glib.so.1.0.1
b471b000-b471c000 rw-p 00001000 08:03 1277150    /usr/lib/libavahi-glib.so.1.0.1
b471c000-b4725000 r-xp 00000000 08:03 1342961    /usr/lib/openoffice/program/behelper.uno.so
b4725000-b4726000 rw-p 00009000 08:03 1342961    /usr/lib/openoffice/program/behelper.uno.so
b4726000-b4737000 r-xp 00000000 08:03 1342982    /usr/lib/openoffice/program/gconfbe1.uno.so
b4737000-b4738000 rw-p 00011000 08:03 1342982    /usr/lib/openoffice/program/gconfbe1.uno.so
b4738000-b4743000 r-xp 00000000 08:03 1343280    /usr/lib/openoffice/program/sysmgr1.uno.so
b4743000-b4744000 rw-p 0000b000 08:03 1343280    /usr/lib/openoffice/program/sysmgr1.uno.so
b4744000-b474c000 r-xp 00000000 08:03 1343284    /usr/lib/openoffice/program/typeconverter.uno.so
b474c000-b474d000 rw-p 00008000 08:03 1343284    /usr/lib/openoffice/program/typeconverter.uno.so
b474d000-b4961000 r-xp 00000000 08:03 1342970    /usr/lib/openoffice/program/configmgr2.uno.so
b4961000-b4974000 rw-p 00214000 08:03 1342970    /usr/lib/openoffice/program/configmgr2.uno.so
b4974000-b4975000 rw-p b4974000 00:00 0 
b4975000-b49ae000 r-xp 00000000 08:03 1343247    /usr/lib/openoffice/program/regtypeprov.uno.so
b49ae000-b49b2000 rw-p 00038000 08:03 1343247    /usr/lib/openoffice/program/regtypeprov.uno.so
b49b2000-b49c2000 rw-p b49b2000 00:00 0 
b49c2000-b49c8000 r-xp 00000000 08:03 1343182    /usr/lib/openoffice/program/libuno_purpenvhelpergcc3.so.3
b49c8000-b49c9000 rw-p 00005000 08:03 1343182    /usr/lib/openoffice/program/libuno_purpenvhelpergcc3.so.3
b49c9000-b49cb000 r-xp 00000000 08:03 1343186    /usr/lib/openoffice/program/libunsafe_uno_uno.so
b49cb000-b49cc000 rw-p 00001000 08:03 1343186    /usr/lib/openoffice/program/libunsafe_uno_uno.so
b49cc000-b4c1c000 r--s 00000000 08:03 1343260    /usr/lib/openoffice/program/services.rdb
b4c1c000-b4c1d000 r--s 00000000 08:04 4096392    /home/benjamin/.openoffice.org2/user/uno_packages/cache/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend/Linux_x86_.rdb
b4c1d000-b4c1e000 r--s 00000000 08:04 4096344    /home/benjamin/.openoffice.org2/user/uno_packages/cache/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend/common_.rdb
b4c1e000-b4fbe000 r--s 00000000 08:03 1343286    /usr/lib/openoffice/program/types.rdb
b4fbe000-b50de000 r--s 00000000 08:03 1343224    /usr/lib/openoffice/program/oovbaapi.rdb
b50de000-b50f9000 r-xp 00000000 08:03 1343257    /usr/lib/openoffice/program/security.uno.so
b50f9000-b50fb000 rw-p 0001a000 08:03 1343257    /usr/lib/openoffice/program/security.uno.so
b50fb000-b510e000 r-xp 00000000 08:03 1342990    /usr/lib/openoffice/program/implreg.uno.so
b510e000-b510f000 rw-p 00013000 08:03 1342990    /usr/lib/openoffice/program/implreg.uno.so
b510f000-b5137000 r-xp 00000000 08:03 1343285    /usr/lib/openoffice/program/typemgr.uno.so
b5137000-b5139000 rw-p 00027000 08:03 1343285    /usr/lib/openoffice/program/typemgr.uno.so
b5139000-b5148000 r-xp 00000000 08:03 1343220    /usr/lib/openoffice/program/nestedreg.uno.so
b5148000-b5149000 rw-p 0000f000 08:03 1343220    /usr/lib/openoffice/program/nestedreg.uno.so
b5149000-b5159000 r-xp 00000000 08:03 1343266    /usr/lib/openoffice/program/simplereg.uno.so
b5159000-b515a000 rw-p 00010000 08:03 1343266    /usr/lib/openoffice/program/simplereg.uno.so
b515a000-b5160000 r-xp 00000000 08:03 1343264    /usr/lib/openoffice/program/shlibloader.uno.so
b5160000-b5161000 rw-p 00005000 08:03 1343264    /usr/lib/openoffice/program/shlibloader.uno.so
b5161000-b5180000 r-xp 00000000 08:03 1343259    /usr/lib/openoffice/program/servicemgr.uno.so
b5180000-b5182000 rw-p 0001e000 08:03 1343259    /usr/lib/openoffice/program/servicemgr.uno.so
b5182000-b519e000 r-xp 00000000 08:03 1343155    /usr/lib/openoffice/program/libstore.so.3
b519e000-b519f000 rw-p 0001c000 08:03 1343155    /usr/lib/openoffice/program/libstore.so.3
b519f000-b51c0000 r-xp 00000000 08:03 1343127    /usr/lib/openoffice/program/libreg.so.3
b51c0000-b51c1000 rw-p 00020000 08:03 1343127    /usr/lib/openoffice/program/libreg.so.3
b51c1000-b51d3000 r-xp 00000000 08:03 1343056    /usr/lib/openoffice/program/libexlink680li.so
b51d3000-b51d4000 rw-p 00012000 08:03 1343056    /usr/lib/openoffice/program/libexlink680li.so
b51d4000-b5204000 rw-p b51d4000 00:00 0 
b5204000-b520d000 r-xp 00000000 08:03 1622292    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b520d000-b520f000 rw-p 00008000 08:03 1622292    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b520f000-b5217000 r-xp 00000000 08:03 1622296    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b5217000-b5219000 rw-p 00007000 08:03 1622296    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b5219000-b522d000 r-xp 00000000 08:03 1622286    /lib/tls/i686/cmov/libnsl-2.6.1.so
b522d000-b522f000 rw-p 00013000 08:03 1622286    /lib/tls/i686/cmov/libnsl-2.6.1.so
b522f000-b5231000 rw-p b522f000 00:00 0 
b5231000-b5238000 r-xp 00000000 08:03 1622288    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b5238000-b523a000 rw-p 00006000 08:03 1622288    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b523b000-b5248000 r-xp 00000000 08:03 1343069    /usr/lib/openoffice/program/libgcc3_uno.so
b5248000-b5249000 rw-p 0000d000 08:03 1343069    /usr/lib/openoffice/program/libgcc3_uno.so
b5249000-b5329000 r--p 00000000 08:03 1341778    /usr/lib/locale/en_US.utf8/LC_COLLATE
b5329000-b532d000 r-xp 00000000 08:03 1277640    /usr/lib/libogg.so.0.5.3
b532d000-b532e000 rw-p 00003000 08:03 1277640    /usr/lib/libogg.so.0.5.3
b532e000-b5375000 r-xp 00000000 08:03 1277024    /usr/lib/libFLAC.so.8.0.1
b5375000-b5376000 rw-p 00046000 08:03 1277024    /usr/lib/libFLAC.so.8.0.1
b5376000-b537e000 r-xp 00000000 08:03 1277771    /usr/lib/libstartup-notification-1.so.0.0.0
b537e000-b537f000 rw-p 00007000 08:03 1277771    /usr/lib/libstartup-notification-1.so.0.0.0
b537f000-b5385000 r-xp 00000000 08:03 1277697    /usr/lib/libportaudio.so.0.0.18
b5385000-b5386000 rw-p 00005000 08:03 1277697    /usr/lib/libportaudio.so.0.0.18
b5386000-b53dc000 r-xp 00000000 08:03 1277755    /usr/lib/libsndfile.so.1.0.17
b53dc000-b53dd000 rw-p 00056000 08:03 1277755    /usr/lib/libsndfile.so.1.0.17
b53dd000-b53e2000 rw-p b53dd000 00:00 0 
b53e2000-b5460000 r-xp 00000000 08:03 1343193    /usr/lib/openoffice/program/libvclplug_gen680li.so
b5460000-b5468000 rw-p 0007e000 08:03 1343193    /usr/lib/openoffice/program/libvclplug_gen680li.so
b5468000-b5469000 rw-p b5468000 00:00 0 
b5469000-b5470000 r-xp 00000000 08:03 1622305    /lib/tls/i686/cmov/librt-2.6.1.so
b5470000-b5472000 rw-p 00006000 08:03 1622305    /lib/tls/i686/cmov/librt-2.6.1.so
b5472000-b548b000 r-xp 00000000 08:03 1277138    /usr/lib/libatk-1.0.so.0.2009.1
b548b000-b548d000 rw-p 00018000 08:03 1277138    /usr/lib/libatk-1.0.so.0.2009.1
b548d000-b580a000 r-xp 00000000 08:03 1277474    /usr/lib/libgtk-x11-2.0.so.0.1200.0
b580a000-b5811000 rw-p 0037c000 08:03 1277474    /usr/lib/libgtk-x11-2.0.so.0.1200.0
b5811000-b5812000 rw-p b5811000 00:00 0 
b5812000-b5815000 r-xp 00000000 08:03 1342975    /usr/lib/openoffice/program/desktopbe1.uno.so
b5815000-b5816000 rw-p 00003000 08:03 1342975    /usr/lib/openoffice/program/desktopbe1.uno.so
b5816000-b5817000 r-xp 00000000 08:03 1279357    /usr/lib/gconv/ISO8859-1.so
b5817000-b5819000 rw-p 00000000 08:03 1279357    /usr/lib/gconv/ISO8859-1.so
b5819000-b581a000 r--p 00000000 08:03 1341782    /usr/lib/locale/en_US.utf8/LC_MONETARY
b581a000-b581b000 r--p 00000000 08:03 1341788    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b581b000-b581c000 r--p 00000000 08:03 1341785    /usr/lib/locale/en_US.utf8/LC_PAPER
b581c000-b581d000 r--p 00000000 08:03 1341783    /usr/lib/locale/en_US.utf8/LC_NAME
b581d000-b581e000 r--p 00000000 08:03 1341777    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b581e000-b581f000 r--p 00000000 08:03 1341786    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b581f000-b5820000 r--p 00000000 08:03 1341781    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b5820000-b5821000 r--p 00000000 08:03 1341780    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b5821000-b586c000 r-xp 00000000 08:03 1343194    /usr/lib/openoffice/program/libvclplug_gtk680li.so
b586c000-b5872000 rw-p 0004a000 08:03 1343194    /usr/lib/openoffice/program/libvclplug_gtk680li.so
b5872000-b58b1000 r--p 00000000 08:03 1341779    /usr/lib/locale/en_US.utf8/LC_CTYPE
b58b1000-b58b5000 rw-p b58b1000 00:00 0 
b58b5000-b58d7000 r-xp 00000000 08:03 1275762    /usr/lib/libpng12.so.0.15.0
b58d7000-b58d8000 rw-p 00021000 08:03 1275762    /usr/lib/libpng12.so.0.15.0
b58d8000-b5905000 r-xp 00000000 08:03 1277664    /usr/lib/libpangoft2-1.0.so.0.1800.2
b5905000-b5906000 rw-p 0002c000 08:03 1277664    /usr/lib/libpangoft2-1.0.so.0.1800.2
b5906000-b5a1e000 r-xp 00000000 08:03 1277837    /usr/lib/libxml2.so.2.6.30
b5a1e000-b5a23000 rw-p 00118000 08:03 1277837    /usr/lib/libxml2.so.2.6.30
b5a23000-b5a25000 rw-p b5a23000 00:00 0 
b5a25000-b5a43000 r-xp 00000000 08:03 1277267    /usr/lib/libexpat.so.1.0.0
b5a43000-b5a45000 rw-p 0001e000 08:03 1277267    /usr/lib/libexpat.so.1.0.0
b5a45000-b63f4000 r--p 00000000 08:03 1277524    /usr/lib/libicudata.so.36.0
b63f4000-b63f5000 rw-p 009ae000 08:03 1277524    /usr/lib/libicudata.so.36.0
b63f5000-b63f9000 r-xp 00000000 08:03 1277082    /usr/lib/libXfixes.so.3.1.0
b63f9000-b63fa000 rw-p 00003000 08:03 1277082    /usr/lib/libXfixes.so.3.1.0
b63fa000-b64b6000 r-xp 00000000 08:03 1277359    /usr/lib/libglib-2.0.so.0.1400.1
b64b6000-b64b7000 rw-p 000bc000 08:03 1277359    /usr/lib/libglib-2.0.so.0.1400.1
b64b7000-b64b8000 rw-p b64b7000 00:00 0 
b64b8000-b64bb000 r-xp 00000000 08:03 1277369    /usr/lib/libgmodule-2.0.so.0.1400.1
b64bb000-b64bc000 rw-p 00002000 08:03 1277369    /usr/lib/libgmodule-2.0.so.0.1400.1
b64bc000-b64f6000 r-xp 00000000 08:03 1277409    /usr/lib/libgobject-2.0.so.0.1400.1
b64f6000-b64f7000 rw-p 0003a000 08:03 1277409    /usr/lib/libgobject-2.0.so.0.1400.1
b64f7000-b656c000 r-xp 00000000 08:03 1277169    /usr/lib/libcairo.so.2.11.5
b656c000-b656e000 rw-p 00074000 08:03 1277169    /usr/lib/libcairo.so.2.11.5
b656e000-b65a9000 r-xp 00000000 08:03 1277660    /usr/lib/libpango-1.0.so.0.1800.2
b65a9000-b65ab000 rw-p 0003b000 08:03 1277660    /usr/lib/libpango-1.0.so.0.1800.2
b65ab000-b65ad000 r-xp 00000000 08:03 1277074    /usr/lib/libXdamage.so.1.1.0
b65ad000-b65ae000 rw-p 00001000 08:03 1277074    /usr/lib/libXdamage.so.1.1.0
b65ae000-b65b0000 r-xp 00000000 08:03 1277070    /usr/lib/libXcomposite.so.1.0.0
b65b0000-b65b1000 rw-p 00001000 08:03 1277070    /usr/lib/libXcomposite.so.1.0.0
b65b1000-b65b2000 rw-p b65b1000 00:00 0 
b65b2000-b65ba000 r-xp 00000000 08:03 1277072    /usr/lib/libXcursor.so.1.0.2
b65ba000-b65bb000 rw-p 00007000 08:03 1277072    /usr/lib/libXcursor.so.1.0.2
b65bb000-b65c0000 r-xp 00000000 08:03 1277100    /usr/lib/libXrandr.so.2.1.0
b65c0000-b65c1000 rw-p 00005000 08:03 1277100    /usr/lib/libXrandr.so.2.1.0
b65c1000-b65c8000 r-xp 00000000 08:03 1277088    /usr/lib/libXi.so.6.0.0
b65c8000-b65c9000 rw-p 00006000 08:03 1277088    /usr/lib/libXi.so.6.0.0
b65c9000-b65cb000 r-xp 00000000 08:03 1277090    /usr/lib/libXinerama.so.1.0.0
b65cb000-b65cc000 rw-p 00001000 08:03 1277090    /usr/lib/libXinerama.so.1.0.0
b65cc000-b65d3000 r-xp 00000000 08:03 1277102    /usr/lib/libXrender.so.1.3.0
b65d3000-b65d4000 rw-p 00006000 08:03 1277102    /usr/lib/libXrender.so.1.3.0
b65d4000-b65dc000 r-xp 00000000 08:03 1277662    /usr/lib/libpangocairo-1.0.so.0.1800.2
b65dc000-b65dd000 rw-p 00007000 08:03 1277662    /usr/lib/libpangocairo-1.0.so.0.1800.2
b65dd000-b65de000 rw-p b65dd000 00:00 0 
b65de000-b65f5000 r-xp 00000000 08:03 1277321    /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b65f5000-b65f6000 rw-p 00016000 08:03 1277321    /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b65f6000-b667a000 r-xp 00000000 08:03 1277319    /usr/lib/libgdk-x11-2.0.so.0.1200.0
b667a000-b667d000 rw-p 00084000 08:03 1277319    /usr/lib/libgdk-x11-2.0.so.0.1200.0
b667d000-b6681000 r-xp 00000000 08:03 1277076    /usr/lib/libXdmcp.so.6.0.0
b6681000-b6682000 rw-p 00003000 08:03 1277076    /usr/lib/libXdmcp.so.6.0.0
b6682000-b6684000 r-xp 00000000 08:03 1277065    /usr/lib/libXau.so.6.0.0
b6684000-b6685000 rw-p 00001000 08:03 1277065    /usr/lib/libXau.so.6.0.0
b6685000-b668a000 r-xp 00000000 08:03 1622279    /lib/tls/i686/cmov/libcrypt-2.6.1.so
b668a000-b668c000 rw-p 00004000 08:03 1622279    /lib/tls/i686/cmov/libcrypt-2.6.1.so
b668c000-b66b4000 rw-p b668c000 00:00 0 
b66b4000-b66bd000 r-xp 00000000 08:03 1618953    /lib/libpam.so.0.81.6
b66bd000-b66be000 rw-p 00008000 08:03 1618953    /lib/libpam.so.0.81.6
b66be000-b66c2000 r-xp 00000000 08:03 1343184    /usr/lib/openoffice/program/libuno_salhelpergcc3.so.3
b66c2000-b66c3000 rw-p 00003000 08:03 1343184    /usr/lib/openoffice/program/libuno_salhelpergcc3.so.3
b66c3000-b66e0000 r-xp 00000000 08:03 1343099    /usr/lib/openoffice/program/libjvmfwk.so.3
b66e0000-b66e1000 rw-p 0001c000 08:03 1343099    /usr/lib/openoffice/program/libjvmfwk.so.3
b66e1000-b6700000 r-xp 00000000 08:03 1277553    /usr/lib/libjpeg.so.62.0.0
b6700000-b6701000 rw-p 0001e000 08:03 1277553    /usr/lib/libjpeg.so.62.0.0
b6701000-b6702000 rw-p b6701000 00:00 0 
b6702000-b6725000 r-xp 00000000 08:03 1277273    /usr/lib/libfontconfig.so.1.2.0
b6725000-b672d000 rw-p 00023000 08:03 1277273    /usr/lib/libfontconfig.so.1.2.0
b672d000-b6741000 r-xp 00000000 08:03 1277843    /usr/lib/libz.so.1.2.3.3
b6741000-b6742000 rw-p 00013000 08:03 1277843    /usr/lib/libz.so.1.2.3.3
b6742000-b67ae000 r-xp 00000000 08:03 1277281    /usr/lib/libfreetype.so.6.3.16
b67ae000-b67b2000 rw-p 0006b000 08:03 1277281    /usr/lib/libfreetype.so.6.3.16
b67b2000-b67b8000 r-xp 00000000 08:03 1343098    /usr/lib/openoffice/program/libjvmaccessgcc3.so.3
b67b8000-b67b9000 rw-p 00006000 08:03 1343098    /usr/lib/openoffice/program/libjvmaccessgcc3.so.3
b67b9000-b67fa000 r-xp 00000000 08:03 1277530    /usr/lib/libicule.so.36.0
b67fa000-b67fc000 rw-p 00040000 08:03 1277530    /usr/lib/libicule.so.36.0
b67fc000-b67fd000 rw-p b67fc000 00:00 0 
b67fd000-b6918000 r-xp 00000000 08:03 1277536    /usr/lib/libicuuc.so.36.0
b6918000-b691f000 rw-p 0011b000 08:03 1277536    /usr/lib/libicuuc.so.36.0
b691f000-b6921000 rw-p b691f000 00:00 0 
b6921000-b6997000 r-xp 00000000 08:03 1343011    /usr/lib/openoffice/program/libbasegfx680li.so
b6997000-b6998000 rw-p 00076000 08:03 1343011    /usr/lib/openoffice/program/libbasegfx680li.so
b6998000-b69f3000 r-xp 00000000 08:03 1343148    /usr/lib/openoffice/program/libsot680li.so
b69f3000-b69f6000 rw-p 0005a000 08:03 1343148    /usr/lib/openoffice/program/libsot680li.so
b69f6000-b6a96000 r-xp 00000000 08:03 1343123    /usr/lib/openoffice/program/libpsp680li.so
b6a96000-b6adf000 rw-p 000a0000 08:03 1343123    /usr/lib/openoffice/program/libpsp680li.so
b6adf000-b6ae1000 rw-p b6adf000 00:00 0 
b6ae1000-b6c25000 r-xp 00000000 08:03 1622275    /lib/tls/i686/cmov/libc-2.6.1.so
b6c25000-b6c26000 r--p 00143000 08:03 1622275    /lib/tls/i686/cmov/libc-2.6.1.so
b6c26000-b6c28000 rw-p 00144000 08:03 1622275    /lib/tls/i686/cmov/libc-2.6.1.so
b6c28000-b6c2c000 rw-p b6c28000 00:00 0 
b6c2c000-b6c36000 r-xp 00000000 08:03 1618915    /lib/libgcc_s.so.1
b6c36000-b6c37000 rw-p 0000a000 08:03 1618915    /lib/libgcc_s.so.1
b6c37000-b6c5a000 r-xp 00000000 08:03 1622283    /lib/tls/i686/cmov/libm-2.6.1.so
b6c5a000-b6c5c000 rw-p 00023000 08:03 1622283    /lib/tls/i686/cmov/libm-2.6.1.so
b6c5c000-b6d44000 r-xp 00000000 08:03 1277773    /usr/lib/libstdc++.so.6.0.9
b6d44000-b6d47000 r--p 000e8000 08:03 1277773    /usr/lib/libstdc++.so.6.0.9
b6d47000-b6d49000 rw-p 000eb000 08:03 1277773    /usr/lib/libstdc++.so.6.0.9
b6d49000-b6d4f000 rw-p b6d49000 00:00 0 
b6d4f000-b6e21000 r-xp 00000000 08:03 1343154    /usr/lib/openoffice/program/libstlport_gcc.so
b6e21000-b6e25000 rw-p 000d2000 08:03 1343154    /usr/lib/openoffice/program/libstlport_gcc.so
b6e25000-b6e26000 rw-p b6e25000 00:00 0 
b6e26000-b6e3a000 r-xp 00000000 08:03 1622301    /lib/tls/i686/cmov/libpthread-2.6.1.so
b6e3a000-b6e3c000 rw-p 00013000 08:03 1622301    /lib/tls/i686/cmov/libpthread-2.6.1.so
b6e3c000-b6e3e000 rw-p b6e3c000 00:00 0 
b6e3e000-b6e40000 r-xp 00000000 08:03 1622281    /lib/tls/i686/cmov/libdl-2.6.1.so
b6e40000-b6e42000 rw-p 00001000 08:03 1622281    /lib/tls/i686/cmov/libdl-2.6.1.so
b6e42000-b6e43000 rw-p b6e42000 00:00 0 
b6e43000-b6f30000 r-xp 00000000 08:03 1277059    /usr/lib/libX11.so.6.2.0
b6f30000-b6f34000 rw-p 000ed000 08:03 1277059    /usr/lib/libX11.so.6.2.0
b6f34000-b6f49000 r-xp 00000000 08:03 1277037    /usr/lib/libICE.so.6.3.0
b6f49000-b6f4b000 rw-p 00014000 08:03 1277037    /usr/lib/libICE.so.6.3.0
b6f4b000-b6f4c000 rw-p b6f4b000 00:00 0 
b6f4c000-b6f53000 r-xp 00000000 08:03 1277055    /usr/lib/libSM.so.6.0.0
b6f53000-b6f54000 rw-p 00006000 08:03 1277055    /usr/lib/libSM.so.6.0.0
b6f54000-b6f61000 r-xp 00000000 08:03 1277080    /usr/lib/libXext.so.6.4.0
b6f61000-b6f62000 rw-p 0000d000 08:03 1277080    /usr/lib/libXext.so.6.4.0
b6f62000-b6f63000 rwxp b6f62000 00:00 0 
b6f63000-b6f64000 r--p 00000000 08:03 1341784    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b6f64000-b6f65000 r--p 00000000 08:03 1341787    /usr/lib/locale/en_US.utf8/LC_TIME
b6f65000-b6f69000 r-xp 00000000 08:03 1277471    /usr/lib/libgthread-2.0.so.0.1400.1
b6f69000-b6f6a000 rw-p 00003000 08:03 1277471    /usr/lib/libgthread-2.0.so.0.1400.1
b6f6a000-b6f71000 r--s 00000000 08:03 1279410    /usr/lib/gconv/gconv-modules.cache
b6f71000-b715d000 r-xp 00000000 08:03 1343169    /usr/lib/openoffice/program/libtk680li.so
b715d000-b7180000 rw-p 001eb000 08:03 1343169    /usr/lib/openoffice/program/libtk680li.so
b7180000-b7182000 rw-p b7180000 00:00 0 
b7182000-b7330000 r-xp 00000000 08:03 1343183    /usr/lib/openoffice/program/libuno_sal.so.3
b7330000-b7343000 rw-p 001ae000 08:03 1343183    /usr/lib/openoffice/program/libuno_sal.so.3
b7343000-b7346000 rw-p b7343000 00:00 0 
b7346000-b7375000 r-xp 00000000 08:03 1343180    /usr/lib/openoffice/program/libuno_cppu.so.3
b7375000-b7376000 rw-p 0002e000 08:03 1343180    /usr/lib/openoffice/program/libuno_cppu.so.3
b7376000-b7436000 r-xp 00000000 08:03 1343181    /usr/lib/openoffice/program/libuno_cppuhelpergcc3.so.3
b7436000-b743a000 rw-p 000bf000 08:03 1343181    /usr/lib/openoffice/program/libuno_cppuhelpergcc3.so.3
b743a000-b745f000 r-xp 00000000 08:03 1343195    /usr/lib/openoffice/program/libvos3gcc3.so
b745f000-b7461000 rw-p 00024000 08:03 1343195    /usr/lib/openoffice/program/libvos3gcc3.so
b7461000-b74d6000 r-xp 00000000 08:03 1343173    /usr/lib/openoffice/program/libucbhelper4gcc3.so
b74d6000-b74d9000 rw-p 00074000 08:03 1343173    /usr/lib/openoffice/program/libucbhelper4gcc3.so
b74d9000-b74da000 rw-p b74d9000 00:00 0 
b74da000-b75f8000 r-xp 00000000 08:03 1343021    /usr/lib/openoffice/program/libcomphelp4gcc3.so
b75f8000-b7601000 rw-p 0011d000 08:03 1343021    /usr/lib/openoffice/program/libcomphelp4gcc3.so
b7601000-b7603000 rw-p b7601000 00:00 0 
b7603000-b7608000 r-xp 00000000 08:03 1343075    /usr/lib/openoffice/program/libi18nisolang1gcc3.so
b7608000-b7609000 rw-p 00004000 08:03 1343075    /usr/lib/openoffice/program/libi18nisolang1gcc3.so
b7609000-b76a9000 r-xp 00000000 08:03 1343170    /usr/lib/openoffice/program/libtl680li.so
b76a9000-b76ac000 rw-p 000a0000 08:03 1343170    /usr/lib/openoffice/program/libtl680li.so
b76ac000-b773a000 r-xp 00000000 08:03 1343189    /usr/lib/openoffice/program/libutl680li.so
b773a000-b773f000 rw-p 0008d000 08:03 1343189    /usr/lib/openoffice/program/libutl680li.so
b773f000-b7afe000 r-xp 00000000 08:03 1343159    /usr/lib/openoffice/program/libsvt680li.so
b7afe000-b7b1e000 rw-p 003bf000 08:03 1343159    /usr/lib/openoffice/program/libsvt680li.so
b7b1e000-b7b1f000 rw-p b7b1e000 00:00 0 
b7b1f000-b7c34000 r-xp 00000000 08:03 1343158    /usr/lib/openoffice/program/libsvl680li.so
b7c34000-b7c3a000 rw-p 00115000 08:03 1343158    /usr/lib/openoffice/program/libsvl680li.so
b7c3a000-b7c3b000 rw-p b7c3a000 00:00 0 
b7c3b000-b7fbc000 r-xp 00000000 08:03 1343192    /usr/lib/openoffice/program/libvcl680li.so
b7fbc000-b7fd0000 rw-p 00380000 08:03 1343192    /usr/lib/openoffice/program/libvcl680li.so
b7fd0000-b7fd3000 rw-p b7fd0000 00:00 0 
b7fd3000-b7fed000 r-xp 00000000 08:03 1618868    /lib/ld-2.6.1.so
b7fed000-b7fef000 rw-p 00019000 08:03 1618868    /lib/ld-2.6.1.so
bfc46000-bfc8e000 rw-p bfc46000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]

```

---

### Post by bg1256 on 2007-11-03
Well, I completely uninstalled and removed everything related to Open Office, but it is still not functioning at all.  I don't understand...

---

### Post by kolinab on 2007-11-03
Have a look at this thread to see if it helps . . .

[http://ubuntuforums.org/showthread.php?t=584088](http://ubuntuforums.org/showthread.php?t=584088)

---

### Post by bg1256 on 2007-11-03
Thanks for the help.  It looks like the suspect package was:

openoffice.org-gtk


It's really unfortunate this bug slipped past the beta versions of Gutsy. I sincerely hope it is resolved soon.

thanks for the links.

---


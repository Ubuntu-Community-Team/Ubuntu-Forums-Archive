---
title: "Skype on XUbuntu crash, help"
date: 2006-12-10
forum: General Help
---

### Post by solotim on 2006-12-10
Hi,
my skype crashed recently, i don't know how to fix it. Reinstall make no sense here. please give a hand. 
thank you.

```
frank@frank-laptop:~$ skype
*** glibc detected *** skype: free(): invalid pointer: 0x08b891a8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb73d88bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb73d8a44]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb7197fc1]
/usr/lib/libstdc++.so.6(_ZNSs4_Rep10_M_destroyERKSaIcE+0x1d)[0xb7174d3d]
/usr/lib/libscim-1.0.so.8[0xb592b633]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x37)[0xb592c8c7]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x45)[0xb59270c5]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim23QScimInputContextGlobal10initializeEv+0x257)[0xb59c5cf7]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim17QScimInputContextC1Ev+0x31e)[0xb59c7ace]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN22ScimInputContextPlugin6createERK7QString+0x7e)[0xb59c0cae]
/usr/lib/libqt-mt.so.3(_ZN26QInputContextPluginPrivate6createERK7QString+0x25)[0xb7b8e01f]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0x94)[0xb7b8dbec]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext17changeInputMethodE7QString+0xc3)[0xb59d685b]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext5slaveEv+0x43)[0xb59d6a0f]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext15setHolderWidgetEP7QWidget+0x26)[0xb59d6c7e]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0xb8)[0xb7b8dc10]
/usr/lib/libqt-mt.so.3(_ZN7QWidget18createInputContextEv+0x8f)[0xb78e0a8d]
/usr/lib/libqt-mt.so.3(_ZN7QWidget17resetInputContextEv+0x1d)[0xb78e0d93]
/usr/lib/libqt-mt.so.3(_ZN9QLineEdit7setTextERK7QString+0x1d)[0xb7a6119d]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox11setLineEditEP9QLineEdit+0x82)[0xb7a2849e]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox13setUpLineEditEv+0x60)[0xb7a22d68]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox11setEditableEb+0x67)[0xb7a26021]
skype[0x81944a7]
skype[0x8078989]
skype[0x8075972]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb73878cc]
skype(_ZN6QFrame10paintEventEP11QPaintEvent+0x6d)[0x806f7b1]
======= Memory map: ========
08048000-08988000 rwxp 00000000 03:07 73673      /usr/bin/skype
08988000-08b9a000 rw-p 08988000 00:00 0          [heap]
b5700000-b5721000 rw-p b5700000 00:00 0 
b5721000-b5800000 ---p b5721000 00:00 0 
b5892000-b589d000 r-xp 00000000 03:07 113292     /usr/lib/qt3/plugins/inputmethods/libqxim.so
b589d000-b589e000 rw-p 0000a000 03:07 113292     /usr/lib/qt3/plugins/inputmethods/libqxim.so
b589e000-b58c2000 r-xp 00000000 03:07 113291     /usr/lib/qt3/plugins/inputmethods/libqsimple.so
b58c2000-b58c3000 rw-p 00024000 03:07 113291     /usr/lib/qt3/plugins/inputmethods/libqsimple.so
b58c3000-b5998000 r-xp 00000000 03:07 65388      /usr/lib/libscim-1.0.so.8.1.0
b5998000-b59a6000 rw-p 000d5000 03:07 65388      /usr/lib/libscim-1.0.so.8.1.0
b59a6000-b59a8000 r-xp 00000000 03:07 65392      /usr/lib/libscim-x11utils-1.0.so.8.1.0
b59a8000-b59a9000 rw-p 00001000 03:07 65392      /usr/lib/libscim-x11utils-1.0.so.8.1.0
b59b2000-b59d0000 r-xp 00000000 03:07 351431     /usr/lib/qt3/plugins/inputmethods/libqscim.so
b59d0000-b59d1000 rw-p 0001e000 03:07 351431     /usr/lib/qt3/plugins/inputmethods/libqscim.so
b59d1000-b59da000 r-xp 00000000 03:07 113289     /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
b59da000-b59db000 rw-p 00008000 03:07 113289     /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
b59db000-b5a4c000 r--p 00000000 03:07 196239     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b5a4c000-b5aa6000 rw-p b5a4c000 00:00 0 
b5aa6000-b6e78000 r--p 00000000 03:07 196128     /usr/share/fonts/truetype/arphic/uming.ttf
b6e78000-b6ea2000 r-xp 00000000 03:07 65273      /usr/lib/liblcms.so.1.0.15
b6ea2000-b6ea3000 rw-p 00029000 03:07 65273      /usr/lib/liblcms.so.1.0.15
b6ea3000-b6ea6000 rw-p b6ea3000 00:00 0 
b6ea6000-b6f11000 r-xp 00000000 03:07 65310      /usr/lib/libmng.so.1.1.0.9
b6f11000-b6f14000 rw-p 0006a000 03:07 65310      /usr/lib/libmng.so.1.1.0.9
b6f18000-b6f1c000 r-xp 00000000 03:07 113290     /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
b6f1c000-b6f1d000 rw-p 00003000 03:07 113290     /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
b6f1d000-b6f22000 r-xp 00000000 03:07 113287     /usr/lib/qt3/plugins/imageformats/libqmng.so
b6f22000-b6f23000 rw-p 00004000 03:07 113287     /usr/lib/qt3/plugins/imageformats/libqmng.so
b6f23000-b6f24000 ---p b6f23000 00:00 0 
b6f24000-b6fa4000 rw-p b6f24000 00:00 0 
b6fa4000-b6fa5000 r-xp 00000000 03:07 96021      /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b6fa5000-b6fa6000 rw-p 00000000 03:07 96021      /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b6fa6000-b6fda000 r--p 00000000 03:07 98750      /usr/lib/locale/zh_CN.utf8/LC_CTYPE
b6fda000-b6fdb000 r--p 00000000 03:07 97342      /usr/lib/locale/zh_CN.utf8/LC_NUMERIC
b6fdb000-b6fdc000 r--p 00000000 03:07 263676     /usr/lib/locale/zh_CN.utf8/LC_TIME
b6fdc000-b70b3000 r--p 00000000 03:07 97310      /usr/lib/locale/zh_CN.utf8/LC_COLLATE
b70b3000-b70b4000 r--p 00000000 03:07 263677     /usr/lib/locale/zh_CN.utf8/LC_MONETARY
b70b4000-b70b5000 r--p 00000000 03:07 144139     /usr/lib/locale/zh_CN.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b70b5000-b70b6000 r--p 00000000 03:07 97317      /usr/lib/locale/zh_CN.utf8/LC_PAPER
b70b6000-b70b7000 r--p 00000000 03:07 98754      /usr/lib/locale/zh_CN.utf8/LC_NAME
b70b7000-b70b8000 r--p 00000000 03:07 263678     /usr/lib/locale/zh_CN.utf8/LC_ADDRESS
b70b8000-b70b9000 r--p 00000000 03:07 263679     /usr/lib/locale/zh_CN.utf8/LC_TELEPHONE
b70b9000-b70bb000 rw-p b70b9000 00:00 0 
b70bb000-b70bf000 r-xp 00000000 03:07 64937      /usr/lib/libXfixes.so.3.1.0
b70bf000-b70c0000 rw-p 00003000 03:07 64937      /usr/lib/libXfixes.so.3.1.0
b70c0000-b70dc000 r-xp 00000000 03:07 65084      /usr/lib/libexpat.so.1.0.0
b70dc000-b70de000 rw-p 0001c000 03:07 65084      /usr/lib/libexpat.so.1.0.0
b70de000-b70df000 rw-p b70de000 00:00 0 
b70df000-b70e3000 r-xp 00000000 03:07 64931      /usr/lib/libXdmcp.so.6.0.0
b70e3000-b70e4000 rw-p 00003000 03:07 64931      /usr/lib/libXdmcp.so.6.0.0
b70e4000-b70e6000 r-xp 00000000 03:07 64920      /usr/lib/libXau.so.6.0.0
b70e6000-b70e7000 rw-p 00001000 03:07 64920      /usr/lib/libXau.so.6.0.0
b70e7000-b71bb000 r-xp 00000000 03:07 65419      /usr/lib/libstdc++.so.6.0.8
b71bb000-b71be000 r--p 000d4000 03:07 65419      /usr/lib/libstdc++.so.6.0.8
b71be000-b71c0000 rw-p 000d7000 03:07 65419      /usr/lib/libstdc++.so.6.0.8
b71c0000-b71c6000 rw-p b71c0000 00:00 0 
b71c6000-b71db000 r-xp 00000000 03:07 64904      /usr/lib/libICE.so.6.3.0
b71db000-b71dc000 rw-p 00014000 03:07 64904      /usr/lib/libICE.so.6.3.0
b71dc000-b71de000 rw-p b71dc000 00:00 0 
b71de000-b71e6000 r-xp 00000000 03:07 64914      /usr/lib/libSM.so.6.0.0
b71e6000-b71e7000 rw-p 00007000 03:07 64914      /usr/lib/libSM.so.6.0.0
b71e7000-b71e8000 rw-p b71e7000 00:00 0 
b71e8000-b724f000 r-xp 00000000 03:07 65100      /usr/lib/libfreetype.so.6.3.10
b724f000-b7252000 rw-p 00067000 03:07 65100      /usr/lib/libfreetype.so.6.3.10
b7252000-b7263000 r-xp 00000000 03:07 64941      /usr/lib/libXft.so.2.1.2
b7263000-b7264000 rw-p 00010000 03:07 64941      /usr/lib/libXft.so.2.1.2
b7264000-b7266000 r-xp 00000000 03:07 64945      /usr/lib/libXinerama.so.1.0.0
b7266000-b7267000 rw-p 00001000 03:07 64945      /usr/lib/libXinerama.so.1.0.0
b7267000-b726f000 r-xp 00000000 03:07 64927      /usr/lib/libXcursor.so.1.0.2
b726f000-b7270000 rw-p 00007000 03:07 64927      /usr/lib/libXcursor.so.1.0.2
b7270000-b7272000 r-xp 00000000 03:07 64955      /usr/lib/libXrandr.so.2.0.0
b7272000-b7273000 rw-p 00002000 03:07 64955      /usr/lib/libXrandr.so.2.0.0
b7273000-b727a000 r-xp 00000000 03:07 64957      /usr/lib/libXrender.so.1.3.0
b727a000-b727b000 rw-p 00006000 03:07 64957      /usr/lib/libXrender.so.1.3.0
b727b000-b727c000 rw-p b727b000 00:00 0 
b727c000-b7283000 r-xp 00000000 03:07 64943      /usr/lib/libXi.so.6.0.0
b7283000-b7284000 rw-p 00006000 03:07 64943      /usr/lib/libXi.so.6.0.0
b7284000-b7297000 r-xp 00000000 03:07 65489      /usr/lib/libz.so.1.2.3
b7297000-b7298000 rw-p 00012000 03:07 65489      /usr/lib/libz.so.1.2.3
b7298000-b72ba000 r-xp 00000000 03:07 65370      /usr/lib/libpng12.so.0.1.2.8
b72ba000-b72bb000 rw-p 00021000 03:07 65370      /usr/lib/libpng12.so.0.1.2.8
b72bb000-b72d9000 r-xp 00000000 03:07 65257      /usr/lib/libjpeg.so.62.0.0
b72d9000-b72da000 rw-p 0001d000 03:07 65257      /usr/lib/libjpeg.so.62.0.0
b72da000-b7324000 r-xp 00000000 03:07 64961      /usr/lib/libXt.so.6.0.0
b7324000-b7328000 rw-p 00049000 03:07 64961      /usr/lib/libXt.so.6.0.0
b7328000-b733d000 r-xp 00000000 03:07 73503      /usr/lib/libaudio.so.2.4
b733d000-b733e000 rw-p 00014000 03:07 73503      /usr/lib/libaudio.so.2.4
b733e000-b733f000 rw-p b733e000 00:00 0 
b733f000-b7368000 r-xp 00000000 03:07 65090      /usr/lib/libfontconfig.so.1.0.4
b7368000-b736d000 rw-p 00028000 03:07 65090      /usr/lib/libfontconfig.so.1.0.4
b736d000-b736e000 rw-p b736d000 00:00 0 
b736e000-b7370000 r-xp 00000000 03:07 144035     /lib/tls/i686/cmov/libdl-2.4.so
b7370000-b7372000 rw-p 00001000 03:07 144035     /lib/tls/i686/cmov/libdl-2.4.so
b7372000-b749f000 r-xp 00000000 03:07 144029     /lib/tls/i686/cmov/libc-2.4.so
b749f000-b74a1000 r--p 0012c000 03:07 144029     /lib/tls/i686/cmov/libc-2.4.so
b74a1000-b74a3000 rw-p 0012e000 03:07 144029     /lib/tls/i686/cmov/libc-2.4.so
b74a3000-b74a6000 rw-p b74a3000 00:00 0 
b74a6000-b74b0000 r-xp 00000000 03:07 111842     /lib/libgcc_s.so.1
b74b0000-b74b1000 rw-p 00009000 03:07 111842     /lib/libgcc_s.so.1
b74b1000-b74d5000 r-xp 00000000 03:07 144037     /lib/tls/i686/cmov/libm-2.4.so
b74d5000-b74d7000 rw-p 00023000 03:07 144037     /lib/tls/i686/cmov/libm-2.4.so
b74d7000-b7587000 r-xp 00000000 03:07 65417      /usr/lib/libstdc++.so.5.0.7
b7587000-b758c000 rw-p 000af000 03:07 65417      /usr/lib/libstdc++.so.5.0.7
b758c000-b7592000 rw-p b758c000 00:00 0 
b7592000-b75a1000 r-xp 00000000 03:07 144055     /lib/tls/i686/cmov/libpthread-2.4.so
b75a1000-b75a3000 rw-p 0000f000 03:07 144055     /lib/tls/i686/cmov/libpthread-2.4.so
b75a3000-b75a5000 rw-p b75a3000 00:00 0 
b75a5000-b766b000 r-xp 00000000 03:07 64916      /usr/lib/libX11.so.6.2.0
b766b000-b766e000 rw-p 000c5000 03:07 64916      /usr/lib/libX11.so.6.2.0
b766e000-b767a000 r-xp 00000000 03:07 64935      /usr/lib/libXext.so.6.4.0
b767a000-b767b000 rw-p 0000c000 03:07 64935      /usr/lib/libXext.so.6.4.0
b767b000-b7e10000 r-xp 00000000 03:07 64318      /usr/lib/libqt-mt.so.3.3.6
b7e10000-b7e57000 rw-p 00794000 03:07 64318      /usr/lib/libqt-mt.so.3.3.6
b7e57000-b7e5a000 rw-p b7e57000 00:00 0 
b7e5a000-b7f0d000 r-xp 00000000 03:07 64995      /usr/lib/libasound.so.2.0.0
b7f0d000-b7f12000 rw-p 000b2000 03:07 64995      /usr/lib/libasound.so.2.0.0
b7f12000-b7f19000 r-xp 00000000 03:07 144059     /lib/tls/i686/cmov/librt-2.4.so
b7f19000-b7f1b000 rw-p 00006000 03:07 144059     /lib/tls/i686/cmov/librt-2.4.so
b7f1b000-b7f1c000 rw-p b7f1b000 00:00 0 
b7f1c000-b7f1d000 r--p 00000000 03:07 97313      /usr/lib/locale/zh_CN.utf8/LC_MEASUREMENT
b7f1d000-b7f24000 r--s 00000000 03:07 80483      /usr/lib/gconv/gconv-modules.cache
b7f24000-b7f25000 r--p 00000000 03:07 263680     /usr/lib/locale/zh_CN.utf8/LC_IDENTIFICATION
b7f25000-b7f26000 rw-p b7f25000 00:00 0 
b7f26000-b7f3f000 r-xp 00000000 03:07 111797     /lib/ld-2.4.so
b7f3f000-b7f41000 rw-p 00018000 03:07 111797     /lib/ld-2.4.so
bfd5b000-bfd71000 rw-p bfd5b000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]
&#24573;&#30053;

```

---

### Post by solotim on 2006-12-12
Please Help~~~~

---

### Post by gaumann on 2006-12-17
I am getting a very similar crash. I am using Gnome Ubuntu Edgy. Skype was working fine for me a couple of weeks ago but now it just crashes. Can't think of any change to the system other than the regular updates. Interesting that I am also using scim. I am using Skype 1.3.0.53-0plf6.10 from the [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy-plf repository.

Here is my crash report: 
```
$ skype
*** glibc detected *** skype: munmap_chunk(): invalid pointer: 0x08a35d20 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x18a)[0xb7489b4a]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb7248fc1]
/usr/lib/libstdc++.so.6(_ZNSs4_Rep10_M_destroyERKSaIcE+0x1d)[0xb7225d3d]
/usr/lib/libscim-1.0.so.8[0xb6dba633]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x37)[0xb6dbb8c7]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x45)[0xb6db60c5]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim23QScimInputContextGlobal10initializeEv+0x257)[0xb6e58cf7]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim17QScimInputContextC1Ev+0x31e)[0xb6e5aace]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN22ScimInputContextPlugin6createERK7QString+0x7e)[0xb6e53cae]
/usr/lib/libqt-mt.so.3(_ZN26QInputContextPluginPrivate6createERK7QString+0x25)[0xb7c4001f]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0x94)[0xb7c3fbec]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext17changeInputMethodE7QString+0xc3)[0xb6fb185b]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext5slaveEv+0x43)[0xb6fb1a0f]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext15setHolderWidgetEP7QWidget+0x26)[0xb6fb1c7e]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0xb8)[0xb7c3fc10]
/usr/lib/libqt-mt.so.3(_ZN7QWidget18createInputContextEv+0x8f)[0xb7992a8d]
/usr/lib/libqt-mt.so.3(_ZN7QWidget17resetInputContextEv+0x1d)[0xb7992d93]
/usr/lib/libqt-mt.so.3(_ZN9QLineEdit7setTextERK7QString+0x1d)[0xb7b1319d]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox11setLineEditEP9QLineEdit+0x82)[0xb7ada49e]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox13setUpLineEditEv+0x60)[0xb7ad4d68]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox11setEditableEb+0x67)[0xb7ad8021]
skype[0x81944a7]
skype[0x8078989]
skype[0x8075972]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb74388cc]
skype(_ZN6QFrame10paintEventEP11QPaintEvent+0x6d)[0x806f7b1]
======= Memory map: ========
08048000-08988000 rwxp 00000000 03:07 2561806    /usr/bin/skype
08988000-08aa4000 rw-p 08988000 00:00 0          [heap]
b6d2d000-b6d51000 r-xp 00000000 03:07 2559081    /usr/lib/qt3/plugins/inputmethods/libqsimple.so
b6d51000-b6d52000 rw-p 00024000 03:07 2559081    /usr/lib/qt3/plugins/inputmethods/libqsimple.so
b6d52000-b6e27000 r-xp 00000000 03:07 2557800    /usr/lib/libscim-1.0.so.8.1.0
b6e27000-b6e35000 rw-p 000d5000 03:07 2557800    /usr/lib/libscim-1.0.so.8.1.0
b6e39000-b6e44000 r-xp 00000000 03:07 2559082    /usr/lib/qt3/plugins/inputmethods/libqxim.so
b6e44000-b6e45000 rw-p 0000a000 03:07 2559082    /usr/lib/qt3/plugins/inputmethods/libqxim.so
b6e45000-b6e63000 r-xp 00000000 03:07 2561004    /usr/lib/qt3/plugins/inputmethods/libqscim.so
b6e63000-b6e64000 rw-p 0001e000 03:07 2561004    /usr/lib/qt3/plugins/inputmethods/libqscim.so
b6e64000-b6ed5000 r--p 00000000 03:07 2801801    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6ed5000-b6eff000 r-xp 00000000 03:07 2557650    /usr/lib/liblcms.so.1.0.15
b6eff000-b6f00000 rw-p 00029000 03:07 2557650    /usr/lib/liblcms.so.1.0.15
b6f00000-b6f03000 rw-p b6f00000 00:00 0 
b6f03000-b6f6e000 r-xp 00000000 03:07 2557681    /usr/lib/libmng.so.1.1.0.9
b6f6e000-b6f71000 rw-p 0006a000 03:07 2557681    /usr/lib/libmng.so.1.1.0.9
b6f79000-b6f7b000 r-xp 00000000 03:07 2557804    /usr/lib/libscim-x11utils-1.0.so.8.1.0
b6f7b000-b6f7c000 rw-p 00001000 03:07 2557804    /usr/lib/libscim-x11utils-1.0.so.8.1.0
b6f7c000-b6f80000 r-xp 00000000 03:07 2559080    /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
b6f80000-b6f81000 rw-p 00003000 03:07 2559080    /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
b6f81000-b6fab000 r-xp 00000000 03:07 2559894    /usr/lib/libkdefx.so.4.2.0
b6fab000-b6fac000 rw-p 00029000 03:07 2559894    /usr/lib/libkdefx.so.4.2.0
b6fac000-b6fb5000 r-xp 00000000 03:07 2559079    /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
b6fb5000-b6fb6000 rw-p 00008000 03:07 2559079    /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
b6fb6000-b6fbb000 r-xp 00000000 03:07 2559077    /usr/lib/qt3/plugins/imageformats/libqmng.so
b6fbb000-b6fbc000 rw-p 00004000 03:07 2559077    /usr/lib/qt3/plugins/imageformats/libqmng.so
b6fbc000-b6fda000 r-xp 00000000 03:07 2559883    /usr/lib/kde3/plugins/styles/plastik.so
b6fda000-b6fdb000 rw-p 0001e000 03:07 2559883    /usr/lib/kde3/plugins/styles/plastik.so
b6fdb000-b6fdc000 ---p b6fdb000 00:00 0 
b6fdc000-b705c000 rw-p b6fdc000 00:00 0 
b705c000-b705d000 r-xp 00000000 03:07 2605198    /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b705d000-b705e000 rw-p 00000000 03:07 2605198    /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b705e000-b7091000 r--p 00000000 03:07 2622888    /usr/lib/locale/en_AU.utf8/LC_CTYPE
b7091000-b7092000 r--p 00000000 03:07 2622893    /usr/lib/locale/en_AU.utf8/LC_NUMERIC
b7092000-b7169000 r--p 00000000 03:07 2622887    /usr/lib/locale/en_AU.utf8/LC_COLLATE
b7169000-b716c000 rw-p b7169000 00:00 0 
b716c000-b7170000 r-xp 00000000 03:07 2557173    /usr/lib/libXfixes.so.3.1.0
b7170000-b7171000 rw-p 00003000 03:07 2557173    /usr/lib/libXfixes.so.3.1.0
b7171000-b718d000 r-xp 00000000 03:07 2557352    /usr/lib/libexpat.so.1.0.0
b718d000-b718f000 rw-p 0001c000 03:07 2557352    /usr/lib/libexpat.so.1.0.0
b718f000-b7193000 r-xp 00000000 03:07 2557167    /usr/lib/libXdmcp.so.6.0.0
b7193000-b7194000 rw-p 00003000 03:07 2557167    /usr/lib/libXdmcp.so.6.0.0
b7194000-b7196000 r-xp 00000000 03:07 2557158    /usr/lib/libXau.so.6.0.0
b7196000-b7197000 rw-p 00001000 03:07 2557158    /usr/lib/libXau.so.6.0.0
b7197000-b7198000 rw-p b7197000 00:00 0 
b7198000-b726c000 r-xp 00000000 03:07 2557841    /usr/lib/libstdc++.so.6.0.8
b726c000-b726f000 r--p 000d4000 03:07 2557841    /usr/lib/libstdc++.so.6.0.8
b726f000-b7271000 rw-p 000d7000 03:07 2557841    /usr/lib/libstdc++.so.6.0.8
b7271000-b7277000 rw-p b7271000 00:00 0 
b7277000-b728c000 r-xp 00000000 03:07 2557130    /usr/lib/libICE.so.6.3.0
b728c000-b728d000 rw-p 00014000 03:07 2557130    /usr/lib/libICE.so.6.3.0
b728d000-b728f000 rw-p b728d000 00:00 0 
b728f000-b7297000 r-xp 00000000 03:07 2557148    /usr/lib/libSM.so.6.0.0
b7297000-b7298000 rw-p 00007000 03:07 2557148    /usr/lib/libSM.so.6.0.0
b7298000-b72ff000 r-xp 00000000 03:07 2557368    /usr/lib/libfreetype.so.6.3.10
b72ff000-b7302000 rw-p 00067000 03:07 2557368    /usr/lib/libfreetype.so.6.3.10
b7302000-b7313000 r-xp 00000000 03:07 2557177    /usr/lib/libXft.so.2.1.2
b7313000-b7314000 rw-p 00010000 03:07 2557177    /usr/lib/libXft.so.2.1.2
b7314000-b7316000 r-xp 00000000 03:07 2557181    /usr/lib/libXinerama.so.1.0.0
b7316000-b7317000 rw-p 00001000 03:07 2557181    /usr/lib/libXinerama.so.1.0.0
b7317000-b7318000 rw-p b7317000 00:00 0 
b7318000-b7320000 r-xp 00000000 03:07 2557163    /usr/lib/libXcursor.so.1.0.2
b7320000-b7321000 rw-p 00007000 03:07 2557163    /usr/lib/libXcursor.so.1.0.2
b7321000-b7323000 r-xp 00000000 03:07 2557191    /usr/lib/libXrandr.so.2.0.0
b7323000-b7324000 rw-p 00002000 03:07 2557191    /usr/lib/libXrandr.so.2.0.0
b7324000-b732b000 r-xp 00000000 03:07 2557193    /usr/lib/libXrender.so.1.3.0
b732b000-b732c000 rw-p 00006000 03:07 2557193    /usr/lib/libXrender.so.1.3.0
b732c000-b7333000 r-xp 00000000 03:07 2557179    /usr/lib/libXi.so.6.0.0
b7333000-b7334000 rw-p 00006000 03:07 2557179    /usr/lib/libXi.so.6.0.0
b7334000-b7347000 r-xp 00000000 03:07 2557898    /usr/lib/libz.so.1.2.3
b7347000-b7348000 rw-p 00012000 03:07 2557898    /usr/lib/libz.so.1.2.3
b7348000-b736b000 r-xp 00000000 03:07 2561603    /usr/lib/libpng12.so.0.1.2.8
b736b000-b736c000 rw-p 00023000 03:07 2561603    /usr/lib/libpng12.so.0.1.2.8
b736c000-b736d000 rw-p b736c000 00:00 0 
b736d000-b738b000 r-xp 00000000 03:07 2557634    /usr/lib/libjpeg.so.62.0.0
b738b000-b738c000 rw-p 0001d000 03:07 2557634    /usr/lib/libjpeg.so.62.0.0
b738c000-b73d6000 r-xp 00000000 03:07 2557197    /usr/lib/libXt.so.6.0.0
b73d6000-b73da000 rw-p 00049000 03:07 2557197    /usr/lib/libXt.so.6.0.0
b73da000-b73ef000 r-xp 00000000 03:07 2557234    /usr/lib/libaudio.so.2.4
b73ef000-b73f0000 rw-p 00014000 03:07 2557234    /usr/lib/libaudio.so.2.4
b73f0000-b7419000 r-xp 00000000 03:07 2557358    /usr/lib/libfontconfig.so.1.0.4
b7419000-b741e000 rw-p 00028000 03:07 2557358    /usr/lib/libfontconfig.so.1.0.4
b741e000-b741f000 rw-p b741e000 00:00 0 
b741f000-b7421000 r-xp 00000000 03:07 1524352    /lib/tls/i686/cmov/libdl-2.4.so
b7421000-b7423000 rw-p 00001000 03:07 1524352    /lib/tls/i686/cmov/libdl-2.4.so
b7423000-b7550000 r-xp 00000000 03:07 1524346    /lib/tls/i686/cmov/libc-2.4.so
b7550000-b7552000 r--p 0012c000 03:07 1524346    /lib/tls/i686/cmov/libc-2.4.so
b7552000-b7554000 rw-p 0012e000 03:07 1524346    /lib/tls/i686/cmov/libc-2.4.so
b7554000-b7558000 rw-p b7554000 00:00 0 
b7558000-b7562000 r-xp 00000000 03:07 1491011    /lib/libgcc_s.so.1
b7562000-b7563000 rw-p 00009000 03:07 1491011    /lib/libgcc_s.so.1
b7563000-b7587000 r-xp 00000000 03:07 1524354    /lib/tls/i686/cmov/libm-2.4.so
b7587000-b7589000 rw-p 00023000 03:07 1524354    /lib/tls/i686/cmov/libm-2.4.so
b7589000-b7639000 r-xp 00000000 03:07 2557839    /usr/lib/libstdc++.so.5.0.7
b7639000-b763e000 rw-p 000af000 03:07 2557839    /usr/lib/libstdc++.so.5.0.7
b763e000-b7643000 rw-p b763e000 00:00 0 
b7643000-b7652000 r-xp 00000000 03:07 1524372    /lib/tls/i686/cmov/libpthread-2.4.so
b7652000-b7654000 rw-p 0000f000 03:07 1524372    /lib/tls/i686/cmov/libpthread-2.4.so
b7654000-b7656000 rw-p b7654000 00:00 0 
b7656000-b771c000 r-xp 00000000 03:07 2557152    /usr/lib/libX11.so.6.2.0
b771c000-b771f000 rw-p 000c5000 03:07 2557152    /usr/lib/libX11.so.6.2.0
b771f000-b772b000 r-xp 00000000 03:07 2557171    /usr/lib/libXext.so.6.4.0
b772b000-b772c000 rw-p 0000c000 03:07 2557171    /usr/lib/libXext.so.6.4.0
b772c000-b772d000 rw-p b772c000 00:00 0 
b772d000-b7ec2000 r-xp 00000000 03:07 2559072    /usr/lib/libqt-mt.so.3.3.6
b7ec2000-b7f09000 rw-p 00794000 03:07 2559072    /usr/lib/libqt-mt.so.3.3.6
b7f09000-b7f0c000 rw-p b7f09000 00:00 0 
b7f0c000-b7fbf000 r-xp 00000000 03:07 2557221    /usr/lib/libasound.so.2.0.0
b7fbf000-b7fc4000 rw-p 000b2000 03:07 2557221    /usr/lib/libasound.so.2.0.0
b7fc4000-b7fcb000 r-xp 00000000 03:07 1524376    /lib/tls/i686/cmov/librt-2.4.so
b7fcb000-b7fcd000 rw-p 00006000 03:07 1524376    /lib/tls/i686/cmov/librt-2.4.so
b7fcd000-b7fce000 r--p 00000000 03:07 2622896    /usr/lib/locale/en_AU.utf8/LC_TIME
b7fce000-b7fcf000 r--p 00000000 03:07 2622891    /usr/lib/locale/en_AU.utf8/LC_MONETARY
b7fcf000-b7fd0000 r--p 00000000 03:07 2637892    /usr/lib/locale/en_AU.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7fd0000-b7fd1000 r--p 00000000 03:07 2622894    /usr/lib/locale/en_AU.utf8/LC_PAPER
b7fd1000-b7fd2000 r--p 00000000 03:07 2622892    /usr/lib/locale/en_AU.utf8/LC_NAME
b7fd2000-b7fd3000 r--p 00000000 03:07 2622886    /usr/lib/locale/en_AU.utf8/LC_ADDRESS
b7fd3000-b7fd4000 r--p 00000000 03:07 2622895    /usr/lib/locale/en_AU.utf8/LC_TELEPHONE
b7fd4000-b7fd5000 r--p 00000000 03:07 2622890    /usr/lib/locale/en_AU.utf8/LC_MEASUREMENT
b7fd5000-b7fdc000 r--s 00000000 03:07 2589416    /usr/lib/gconv/gconv-modules.cache
b7fdc000-b7fdd000 r--p 00000000 03:07 2622889    /usr/lib/locale/en_AU.utf8/LC_IDENTIFICATION
b7fdd000-b7fdf000 rw-p b7fdd000 00:00 0 
b7fdf000-b7ff8000 r-xp 00000000 03:07 1490966    /lib/ld-2.4.so
b7ff8000-b7ffa000 rw-p 00018000 03:07 1490966    /lib/ld-2.4.so
bf94c000-bf961000 rw-p bf94c000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

---

### Post by gaumann on 2006-12-17
Found two helpful threads on the skype forums.

[http://forum.skype.com/index.php?showtopic=64211](http://forum.skype.com/index.php?showtopic=64211)

[http://forum.skype.com/index.php?showtopic=70843](http://forum.skype.com/index.php?showtopic=70843)

export LANG=C
export QT_IM_MODULE="xim skype"
skype

fixed the problem for me

---

### Post by solotim on 2006-12-22
it works great!, Thank you~ &#65306;D

---

### Post by sarc on 2006-12-22
How the heck did you get Skype 1.3 to work on Edgy?  Mine does not crash but it turns off microphone or audio at will - most posts indicate that Skype for Debian is pretty much useless.  How did you do it?

---

### Post by vochinch on 2006-12-22
Worked great for me too.  Many thanks!  I had also just installed scim for the Korean input.

---


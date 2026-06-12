---
title: "skype not working after installation of Asian languages"
date: 2007-05-13
forum: General Help
---

### Post by ndefontenay on 2007-05-13
Good evening,

I've installed packages to be able to write Japanese recently and since then skype fails with the following error:

```
MyName@Anthrax:~$ skype
*** glibc detected *** skype: free(): invalid pointer: 0x08a423d8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb73d17cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb73d4e30]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb7186d11]
/usr/lib/libstdc++.so.6(_ZNSs4_Rep10_M_destroyERKSaIcE+0x1d)[0xb7163a5d]
/usr/lib/libstdc++.so.6(_ZNSsD1Ev+0x57)[0xb71665e7]
/usr/lib/libscim-1.0.so.8[0xb6bfd08b]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKS
s+0x37)[0xb6bfdf77]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsS
aISsEE+0x45)[0xb6bf8f05]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim23QScimInputContextGlobal1
0initializeEv+0x257)[0xb6c9dcf7]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim17QScimInputContextC1Ev+0x
31e)[0xb6c9face]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN22ScimInputContextPlugin6create
ERK7QString+0x7e)[0xb6c98cae]
/usr/lib/libqt-mt.so.3(_ZN26QInputContextPluginPrivate6createERK7QString+0x25)[0
xb7bf2f67]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0x94
)[0xb7bf2b34]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext17cha
ngeInputMethodE7QString+0xc3)[0xb6cd3c9b]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext5slav
eEv+0x43)[0xb6cd3e4f]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext15set
HolderWidgetEP7QWidget+0x26)[0xb6cd40be]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0xb8
)[0xb7bf2b58]
/usr/lib/libqt-mt.so.3(_ZN7QWidget18createInputContextEv+0x8f)[0xb7945965]
/usr/lib/libqt-mt.so.3(_ZN7QWidget17resetInputContextEv+0x1d)[0xb7945c6b]
/usr/lib/libqt-mt.so.3(_ZN9QLineEdit7setTextERK7QString+0x1d)[0xb7ac60e5]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox11setLineEditEP9QLineEdit+0x82)[0xb7a8d3e6]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox13setUpLineEditEv+0x60)[0xb7a87cb0]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox11setEditableEb+0x67)[0xb7a8af69]
skype[0x81944a7]
skype[0x8078989]
skype[0x8075972]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb737febc]
skype(_ZN6QFrame10paintEventEP11QPaintEvent+0x6d)[0x806f7b1]
======= Memory map: ========
08048000-08988000 rwxp 00000000 08:01 10930224   /usr/bin/skype
08988000-08a4b000 rw-p 08988000 00:00 0          [heap]
b6a00000-b6a21000 rw-p b6a00000 00:00 0
b6a21000-b6b00000 ---p b6a21000 00:00 0
b6b95000-b6c69000 r-xp 00000000 08:01 10930681   /usr/lib/libscim-1.0.so.8.1.0
b6c69000-b6c77000 rw-p 000d4000 08:01 10930681   /usr/lib/libscim-1.0.so.8.1.0
b6c8a000-b6ca8000 r-xp 00000000 08:01 11060883   /usr/lib/qt3/plugins/inputmetho
ds/libqscim.so
b6ca8000-b6ca9000 rw-p 0001e000 08:01 11060883   /usr/lib/qt3/plugins/inputmetho
ds/libqscim.so
b6ca9000-b6ccd000 r-xp 00000000 08:01 11060884   /usr/lib/qt3/plugins/inputmetho
ds/libqsimple.so
b6ccd000-b6cce000 rw-p 00024000 08:01 11060884   /usr/lib/qt3/plugins/inputmetho
ds/libqsimple.so
b6cce000-b6cd7000 r-xp 00000000 08:01 11060880   /usr/lib/qt3/plugins/inputmetho
ds/libqimsw-multi.so
b6cd7000-b6cd8000 rw-p 00009000 08:01 11060880   /usr/lib/qt3/plugins/inputmetho
ds/libqimsw-multi.so
b6cd8000-b6d55000 r--p 00000000 08:01 11190422   /usr/share/fonts/truetype/ttf-d
ejavu/DejaVuSans.ttf
b6d55000-b6d7f000 r-xp 00000000 08:01 10930529   /usr/lib/liblcms.so.1.0.15
b6d7f000-b6d80000 rw-p 00029000 08:01 10930529   /usr/lib/liblcms.so.1.0.15
b6d80000-b6d83000 rw-p b6d80000 00:00 0
b6d83000-b6dee000 r-xp 00000000 08:01 10930559   /usr/lib/libmng.so.1.1.0.9
b6dee000-b6df1000 rw-p 0006a000 08:01 10930559   /usr/lib/libmng.so.1.1.0.9
b6df8000-b6e03000 r-xp 00000000 08:01 11060885   /usr/lib/qt3/plugins/inputmetho
ds/libqxim.so
b6e03000-b6e04000 rw-p 0000a000 08:01 11060885   /usr/lib/qt3/plugins/inputmetho
ds/libqxim.so
b6e04000-b6e2e000 r-xp 00000000 08:01 10930266   /usr/lib/libkdefx.so.4.2.0
b6e2e000-b6e2f000 rw-p 0002a000 08:01 10930266   /usr/lib/libkdefx.so.4.2.0
b6e34000-b6e36000 r-xp 00000000 08:01 10930685   /usr/lib/libscim-x11utils-1.0.s
o.8.1.0
b6e36000-b6e37000 rw-p 00001000 08:01 10930685   /usr/lib/libscim-x11utils-1.0.s
o.8.1.0
b6e37000-b6e3b000 r-xp 00000000 08:01 11060881   /usr/lib/qt3/plugins/inputmetho
ds/libqimsw-none.so
b6e3b000-b6e3c000 rw-p 00003000 08:01 11060881   /usr/lib/qt3/plugins/inputmetho
ds/libqimsw-none.so
b6e3c000-b6e41000 r-xp 00000000 08:01 11060879   /usr/lib/qt3/plugins/imageforma
ts/libqmng.so
b6e41000-b6e42000 rw-p 00004000 08:01 11060879   /usr/lib/qt3/plugins/imageforma
ts/libqmng.so
b6e42000-b6e6a000 r-xp 00000000 08:01 11010070   /usr/lib/kde3/plugins/styles/po
lyester.so
b6e6a000-b6e6b000 rw-p 00028000 08:01 11010070   /usr/lib/kde3/plugins/styles/po
lyester.so
b6e6b000-b6e6c000 ---p b6e6b000 00:00 0
b6e6c000-b6eec000 rw-p b6e6c000 00:00 0
b6eec000-b6ef2000 r--s 00000000 08:01 3113035    /var/cache/fontconfig/945677eb7
aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b6ef2000-b6ef3000 r--s 00000000 08:01 3113067    /var/cache/fontconfig/fd9505950
c048a77dc4b710eb6a628ed-x86.cache-2
b6ef3000-b6ef6000 r--s 00000000 08:01 3113053    /var/cache/fontconfig/ddc79d3ea
06a7c6ffa86ede85f3bb5df-x86.cache-2
b6ef6000-b6ef7000 r--s 00000000 08:01 3113060    /var/cache/fontconfig/e7071f4a2
9fa870f4323321c154eba04-x86.cache-2
b6ef7000-b6ef8000 r--s 00000000 08:01 3113038    /var/cache/fontconfig/a2ab74764
b07279e7c36ddb1d302cf26-x86.cache-2
b6ef8000-b6efc000 r--s 00000000 08:01 3113032    /var/cache/fontconfig/921a30a17
f0be15c70ac14043cb7a739-x86.cache-2
b6efc000-b6efd000 r--s 00000000 08:01 3113019    /var/cache/fontconfig/4c73fe0c4
7614734b17d736dbde7580a-x86.cache-2
b6efd000-b6eff000 r--s 00000000 08:01 3113025    /var/cache/fontconfig/646addb84
44faa74ee138aa00ab0b6a0-x86.cache-2
b6eff000-b6f01000 r--s 00000000 08:01 3113011    /var/cache/fontconfig/20bd79ad9
7094406f7d1b9654bfbd926-x86.cache-2
b6f01000-b6f02000 r--s 00000000 08:01 3113028    /var/cache/fontconfig/75a2cd575
a62c63e802c11411fb87c37-x86.cache-2
b6f02000-b6f04000 r--s 00000000 08:01 3113036    /var/cache/fontconfig/9c0624108
b9a2ae8552f664125be8356-x86.cache-2
b6f04000-b6f0a000 r--s 00000000 08:01 3113026    /var/cache/fontconfig/6d41288fd
70b0be22e8c3a91e032eec0-x86.cache-2
b6f0a000-b6f0c000 r--s 00000000 08:01 3113054    /var/cache/fontconfig/de156ccd2
eddbdc19d37a45b8b2aac9c-x86.cache-2
b6f0c000-b6f0e000 r--s 00000000 08:01 3113051    /var/cache/fontconfig/da1bd5ca8
443ffe22927a23ce431d198-x86.cache-2
b6f0e000-b6f16000 r--s 00000000 08:01 3113058    /var/cache/fontconfig/e3de0de47
9f42330eadf588a55fb5bf4-x86.cache-2
b6f16000-b6f1c000 r--s 00000000 08:01 3113005    /var/cache/fontconfig/0f34bcd4b
6ee430af32735b75db7f02b-x86.cache-2
b6f1c000-b6f1d000 r--s 00000000 08:01 3113017    /var/cache/fontconfig/4794a0821
666d79190d59a36cb4f44b5-x86.cache-2
b6f1d000-b6f34000 r--s 00000000 08:01 3115411    /var/cache/fontconfig/365b55f21
0c0a22e9a19e35191240f32-x86.cache-2
b6f34000-b6f36000 r--s 00000000 08:01 3113055    /var/cache/fontconfig/de9486f0b
47a4d768a594cb4198cb1c6-x86.cache-2
b6f36000-b6f3c000 r--s 00000000 08:01 3113049    /var/cache/fontconfig/d52a86440
73d54c13679302ca1180695-x86.cache-2
b6f3c000-b6f3f000 r--s 00000000 08:01 3113024    /var/cache/fontconfig/6386b8602
0ecc1ef9690bb720a13964f-x86.cache-2
b6f3f000-b6f43000 r--s 00000000 08:01 3113003    /var/cache/fontconfig/089dead88
2dea3570ffc31a9898cfb69-x86.cache-2
b6f43000-b6f4a000 r--s 00000000 08:01 3113982    /var/cache/fontconfig/e13b20fdb
08344e0e664864cc2ede53d-x86.cache-2
b6f4a000-b6f4b000 r--s 00000000 08:01 3113065    /var/cache/fontconfig/fcff1cd55
d48a2c86a175e9943c3506d-x86.cache-2
b6f4b000-b6f4c000 r--s 00000000 08:01 3113061    /var/cache/fontconfig/e9e445846
08a73233979f764b5f9dd81-x86.cache-2
b6f4c000-b6f4d000 r--s 00000000 08:01 3113043    /var/cache/fontconfig/b5a4f3f56
8a71026ccdc6a3a51afa9b4-x86.cache-2
b6f4d000-b6f4e000 r--s 00000000 08:01 3113013    /var/cache/fontconfig/256167957
6a9c7fd2ce41d281d4e00d1-x86.cache-2
b6f4e000-b6f4f000 r--s 00000000 08:01 3118224    /var/cache/fontconfig/b8613a33d
e00eecd32d5a94c3c617829-x86.cache-2
b6f4f000-b6f52000 r--s 00000000 08:01 3113040    /var/cache/fontconfig/b21a91cee
725896328b8cee8091cf747-x86.cache-2
b6f52000-b6f57000 r--s 00000000 08:01 3118223    /var/cache/fontconfig/fd9416c4b
92f07c6f59a3a8cf496e9dc-x86.cache-2
b6f57000-b6f59000 r--s 00000000 08:01 3113002    /var/cache/fontconfig/059138ec8
77db160474b4d5de1248d14-x86.cache-2
b6f59000-b6f5a000 r--s 00000000 08:01 3113063    /var/cache/fontconfig/f5a93ac94
3883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b6f5a000-b6f5c000 r--s 00000000 08:01 3113007    /var/cache/fontconfig/118d8d531
1348bbdf5fe3b106d7c13d4-x86.cache-2
b6f5c000-b6f5d000 r--s 00000000 08:01 3113037    /var/cache/fontconfig/a1131b7be
650f9abae4907495aa5815d-x86.cache-2
b6f5d000-b6f62000 r--s 00000000 08:01 3113031    /var/cache/fontconfig/8ab5f685c
d6d8ba67c37c908faf08172-x86.cache-2
b6f62000-b6f66000 r--s 00000000 08:01 3113004    /var/cache/fontconfig/0f32d3adc
6a232110812e17374eaa446-x86.cache-2
b6f66000-b6f68000 r--s 00000000 08:01 3113029    /var/cache/fontconfig/7b4a97c10
f6c0166998ddfa1cf7392fb-x86.cache-2
b6f68000-b6f6b000 r--s 00000000 08:01 3113021    /var/cache/fontconfig/61c830dfa
c3fd78a12654da5e9ba3f56-x86.cache-2
b6f6b000-b6f6c000 r--s 00000000 08:01 3113056    /var/cache/fontconfig/e0f9e9542
9e756d56293ed4d63866094-x86.cache-2
b6f6c000-b6f6e000 r--s 00000000 08:01 3113015    /var/cache/fontconfig/4123634e9
c08547d899d0aaff05ebe69-x86.cache-2
b6f6e000-b6f72000 r--s 00000000 08:01 3118221    /var/cache/fontconfig/142ecfc43
5bad6f1fbc2648c1119d5eb-x86.cache-2
b6f72000-b6f78000 r--s 00000000 08:01 3113006    /var/cache/fontconfig/102e5142c
2e9e50c5e8ece26694a2dad-x86.cache-2
b6f78000-b6f79000 r--s 00000000 08:01 3113033    /var/cache/fontconfig/92a571655
fb1c0ec1c4d6f496220600a-x86.cache-2
b6f79000-b6f81000 r--s 00000000 08:01 3113039    /var/cache/fontconfig/a960c40fc
9306f090224a04585f8a963-x86.cache-2
b6f81000-b6f83000 r--s 00000000 08:01 3118220    /var/cache/fontconfig/9404ff413
c67fc2a1526fd14eb4163a8-x86.cache-2
b6f83000-b6f86000 r--s 00000000 08:01 3113041    /var/cache/fontconfig/b3fedf7c4
09f006ca1a6fceffceb77cf-x86.cache-2
b6f86000-b6f88000 r--s 00000000 08:01 3118218    /var/cache/fontconfig/633032210
5e0c4105d7c7a6ea2974107-x86.cache-2
b6f88000-b6f8f000 r--s 00000000 08:01 3113981    /var/cache/fontconfig/beeeeb3df
e132a8a0633a017c99ce0c0-x86.cache-2
b6f8f000-b6fca000 r--p 00000000 08:01 11010436   /usr/lib/locale/en_US.utf8/LC_C
TYPE
b6fca000-b70a1000 r--p 00000000 08:01 11010435   /usr/lib/locale/en_US.utf8/LC_C
OLLATE
b70a1000-b70a4000 rw-p b70a1000 00:00 0
b70a4000-b70a8000 r-xp 00000000 08:01 10929825   /usr/lib/libXfixes.so.3.1.0
b70a8000-b70a9000 rw-p 00003000 08:01 10929825   /usr/lib/libXfixes.so.3.1.0
b70a9000-b70c7000 r-xp 00000000 08:01 10930001   /usr/lib/libexpat.so.1.0.0
b70c7000-b70c9000 rw-p 0001d000 08:01 10930001   /usr/lib/libexpat.so.1.0.0
b70c9000-b70cd000 r-xp 00000000 08:01 10929821   /usr/lib/libXdmcp.so.6.0.0
b70cd000-b70ce000 rw-p 00003000 08:01 10929821   /usr/lib/libXdmcp.so.6.0.0
b70ce000-b70d0000 r-xp 00000000 08:01 10929810   /usr/lib/libXau.so.6.0.0
b70d0000-b70d1000 rw-p 00001000 08:01 10929810   /usr/lib/libXau.so.6.0.0
b70d1000-b70d2000 rw-p b70d1000 00:00 0
b70d2000-b71b1000 r-xp 00000000 08:01 10930714   /usr/lib/libstdc++.so.6.0.8
b71b1000-b71b4000 r--p 000de000 08:01 10930714   /usr/lib/libstdc++.so.6.0.8
b71b4000-b71b6000 rw-p 000e1000 08:01 10930714   /usr/lib/libstdc++.so.6.0.8
b71b6000-b71bc000 rw-p b71b6000 00:00 0
b71bc000-b71d1000 r-xp 00000000 08:01 10929739   /usr/lib/libICE.so.6.3.0
b71d1000-b71d3000 rw-p 00014000 08:01 10929739   /usr/lib/libICE.so.6.3.0
b71d3000-b71d4000 rw-p b71d3000 00:00 0
b71d4000-b71dc000 r-xp 00000000 08:01 10929802   /usr/lib/libSM.so.6.0.0
b71dc000-b71dd000 rw-p 00007000 08:01 10929802   /usr/lib/libSM.so.6.0.0
b71dd000-b7245000 r-xp 00000000 08:01 10930025   /usr/lib/libfreetype.so.6.3.10
b7245000-b7248000 rw-p 00068000 08:01 10930025   /usr/lib/libfreetype.so.6.3.10
b7248000-b7259000 r-xp 00000000 08:01 10929829   /usr/lib/libXft.so.2.1.2
b7259000-b725a000 rw-p 00010000 08:01 10929829   /usr/lib/libXft.so.2.1.2
b725a000-b725c000 r-xp 00000000 08:01 10929833   /usr/lib/libXinerama.so.1.0.0
b725c000-b725d000 rw-p 00001000 08:01 10929833   /usr/lib/libXinerama.so.1.0.0
b725d000-b725e000 rw-p b725d000 00:00 0
b725e000-b7266000 r-xp 00000000 08:01 10929817   /usr/lib/libXcursor.so.1.0.2
b7266000-b7267000 rw-p 00007000 08:01 10929817   /usr/lib/libXcursor.so.1.0.2
b7267000-b726c000 r-xp 00000000 08:01 10929843   /usr/lib/libXrandr.so.2.1.0
b726c000-b726d000 rw-p 00005000 08:01 10929843   /usr/lib/libXrandr.so.2.1.0
b726d000-b7274000 r-xp 00000000 08:01 10929845   /usr/lib/libXrender.so.1.3.0
b7274000-b7275000 rw-p 00006000 08:01 10929845   /usr/lib/libXrender.so.1.3.0
b7275000-b727c000 r-xp 00000000 08:01 10929831   /usr/lib/libXi.so.6.0.0
b727c000-b727d000 rw-p 00006000 08:01 10929831   /usr/lib/libXi.so.6.0.0
b727d000-b7290000 r-xp 00000000 08:01 10930783   /usr/lib/libz.so.1.2.3
b7290000-b7291000 rw-p 00012000 08:01 10930783   /usr/lib/libz.so.1.2.3
b7291000-b72b3000 r-xp 00000000 08:01 10930633   /usr/lib/libpng12.so.0.15.0
b72b3000-b72b4000 rw-p 00021000 08:01 10930633   /usr/lib/libpng12.so.0.15.0
b72b4000-b72b5000 rw-p b72b4000 00:00 0
b72b5000-b72d3000 r-xp 00000000 08:01 10930183   /usr/lib/libjpeg.so.62.0.0
b72d3000-b72d4000 rw-p 0001d000 08:01 10930183   /usr/lib/libjpeg.so.62.0.0
b72d4000-b7321000 r-xp 00000000 08:01 10929849   /usr/lib/libXt.so.6.0.0
b7321000-b7325000 rw-p 0004c000 08:01 10929849   /usr/lib/libXt.so.6.0.0
b7325000-b733a000 r-xp 00000000 08:01 10929921   /usr/lib/libaudio.so.2.4
b733a000-b733b000 rw-p 00015000 08:01 10929921   /usr/lib/libaudio.so.2.4
b733b000-b735e000 r-xp 00000000 08:01 10930017   /usr/lib/libfontconfig.so.1.2.0
b735e000-b7366000 rw-p 00023000 08:01 10930017   /usr/lib/libfontconfig.so.1.2.0
b7366000-b7368000 r-xp 00000000 08:01 5033189    /lib/tls/i686/cmov/libdl-2.5.so
b7368000-b736a000 rw-p 00001000 08:01 5033189    /lib/tls/i686/cmov/libdl-2.5.so
b736a000-b74a5000 r-xp 00000000 08:01 5033183    /lib/tls/i686/cmov/libc-2.5.so
b74a5000-b74a6000 r--p 0013b000 08:01 5033183    /lib/tls/i686/cmov/libc-2.5.so
b74a6000-b74a8000 rw-p 0013c000 08:01 5033183    /lib/tls/i686/cmov/libc-2.5.so
b74a8000-b74ac000 rw-p b74a8000 00:00 0
b74ac000-b74b7000 r-xp 00000000 08:01 5029950    /lib/libgcc_s.so.1
b74b7000-b74b8000 rw-p 0000a000 08:01 5029950    /lib/libgcc_s.so.1
b74b8000-b74dd000 r-xp 00000000 08:01 5033191    /lib/tls/i686/cmov/libm-2.5.so
b74dd000-b74df000 rw-p 00024000 08:01 5033191    /lib/tls/i686/cmov/libm-2.5.so
b74df000-b758f000 r-xp 00000000 08:01 10934269   /usr/lib/libstdc++.so.5.0.7
b758f000-b7594000 rw-p 000af000 08:01 10934269   /usr/lib/libstdc++.so.5.0.7
b7594000-b7599000 rw-p b7594000 00:00 0
b7599000-b75ac000 r-xp 00000000 08:01 5033209    /lib/tls/i686/cmov/libpthread-2
.5.so
b75ac000-b75ae000 rw-p 00013000 08:01 5033209    /lib/tls/i686/cmov/libpthread-2
.5.so
b75ae000-b75b0000 rw-p b75ae000 00:00 0
b75b0000-b769d000 r-xp 00000000 08:01 10929806   /usr/lib/libX11.so.6.2.0
b769d000-b76a1000 rw-p 000ed000 08:01 10929806   /usr/lib/libX11.so.6.2.0
b76a1000-b76ae000 r-xp 00000000 08:01 10929823   /usr/lib/libXext.so.6.4.0
b76ae000-b76af000 rw-p 0000d000 08:01 10929823   /usr/lib/libXext.so.6.4.0
b76af000-b7e75000 r-xp 00000000 08:01 10930659   /usr/lib/libqt-mt.so.3.3.7
b7e75000-b7ebb000 rw-p 007c5000 08:01 10930659   /usr/lib/libqt-mt.so.3.3.7
b7ebb000-b7ec0000 rw-p b7ebb000 00:00 0
b7ec0000-b7f80000 r-xp 00000000 08:01 10929913   /usr/lib/libasound.so.2.0.0
b7f80000-b7f85000 rw-p 000bf000 08:01 10929913   /usr/lib/libasound.so.2.0.0
b7f85000-b7f8c000 r-xp 00000000 08:01 5033213    /lib/tls/i686/cmov/librt-2.5.so
b7f8c000-b7f8e000 rw-p 00006000 08:01 5033213    /lib/tls/i686/cmov/librt-2.5.so
b7f90000-b7f91000 r--p 00000000 08:01 11010441   /usr/lib/locale/en_US.utf8/LC_N
UMERIC
b7f91000-b7f92000 r--p 00000000 08:01 11010444   /usr/lib/locale/en_US.utf8/LC_T
IME
b7f92000-b7f93000 r--p 00000000 08:01 11010439   /usr/lib/locale/en_US.utf8/LC_M
ONETARY
b7f93000-b7f94000 r--p 00000000 08:01 11010445   /usr/lib/locale/en_US.utf8/LC_M              ESSAGES/SYS_LC_MESSAGES
b7f94000-b7f95000 r--p 00000000 08:01 11010442   /usr/lib/locale/en_US.utf8/LC_P              APER
b7f95000-b7f96000 r--p 00000000 08:01 11010440   /usr/lib/locale/en_US.utf8/LC_N              AME
b7f96000-b7f97000 r--p 00000000 08:01 11010434   /usr/lib/locale/en_US.utf8/LC_A              DDRESS
b7f97000-b7f98000 r--p 00000000 08:01 11010443   /usr/lib/locale/en_US.utf8/LC_T              ELEPHONE
b7f98000-b7f99000 r--p 00000000 08:01 11010438   /usr/lib/locale/en_US.utf8/LC_M              EASUREMENT
b7f99000-b7fa0000 r--s 00000000 08:01 10931543   /usr/lib/gconv/gconv-modules.ca              che
b7fa0000-b7fa1000 r--p 00000000 08:01 11010437   /usr/lib/locale/en_US.utf8/LC_I              DENTIFICATION
b7fa1000-b7fa3000 rw-p b7fa1000 00:00 0
b7fa3000-b7fbc000 r-xp 00000000 08:01 5029909    /lib/ld-2.5.so
b7fbc000-b7fbe000 rw-p 00019000 08:01 5029909    /lib/ld-2.5.so
bfd47000-bfd5c000 rw-p bfd47000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

It seems to be due to the languages I've installed. Is there a way to fix it?

Thanks in advance.

---

### Post by seshomaru samma on 2007-05-13
I had a similar problem before
It seems that in Ubuntu scim clashes with several programmes ( vmware ,skype and maybe others)
The only solutions I can offer are:
try to upgrade or downgrade skype
use a different kernel 
use a different input system

---

### Post by ndefontenay on 2007-05-13
Thanks for the advice.

I will remove it and try skim instead.

---

### Post by ndefontenay on 2007-05-14
I've removed the scim libraries and skype is working fine again...

I still don't have my Japanese language though :(

---

### Post by faust99 on 2007-05-20
You can get Skype to start by using this command in the terminal:

> XMODIFIERS=@im=none QT_IM_MODULE=xim skype

and then you won't need to mess with scim.

---


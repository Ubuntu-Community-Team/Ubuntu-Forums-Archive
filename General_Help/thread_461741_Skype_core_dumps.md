---
title: "Skype core dumps"
date: 2007-06-02
forum: General Help
---

### Post by cisforcojo on 2007-06-02
Anyone know how to solve skype core dumping?

```
cojones@tipping-point:~$ skype
*** glibc detected *** skype: free(): invalid pointer: 0x08a3a268 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb73ba7cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb73bde30]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb716cd11]
/usr/lib/libstdc++.so.6(_ZNSs4_Rep10_M_destroyERKSaIcE+0x1d)[0xb7149a5d]
/usr/lib/libstdc++.so.6(_ZNSsD1Ev+0x57)[0xb714c5e7]
/usr/lib/libscim-1.0.so.8[0xb6bac08b]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x37)[0xb6bacf77]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x45)[0xb6ba7f05]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim23QScimInputContextGlobal10initializeEv+0x257)[0xb6c4dcf7]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim17QScimInputContextC1Ev+0x31e)[0xb6c4face]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN22ScimInputContextPlugin6createERK7QString+0x7e)[0xb6c48cae]
/usr/lib/libqt-mt.so.3(_ZN26QInputContextPluginPrivate6createERK7QString+0x25)[0xb7bdbf67]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0x94)[0xb7bdbb34]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext17changeInputMethodE7QString+0xc3)[0xb6dd9c9b]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext5slaveEv+0x43)[0xb6dd9e4f]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext15setHolderWidgetEP7QWidget+0x26)[0xb6dda0be]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0xb8)[0xb7bdbb58]
/usr/lib/libqt-mt.so.3(_ZN7QWidget18createInputContextEv+0x8f)[0xb792e965]
/usr/lib/libqt-mt.so.3(_ZN7QWidget17resetInputContextEv+0x1d)[0xb792ec6b]
/usr/lib/libqt-mt.so.3(_ZN9QLineEdit7setTextERK7QString+0x1d)[0xb7aaf0e5]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox11setLineEditEP9QLineEdit+0x82)[0xb7a763e6]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox13setUpLineEditEv+0x60)[0xb7a70cb0]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox11setEditableEb+0x67)[0xb7a73f69]
skype[0x81944a7]
skype[0x8078989]
skype[0x8075972]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7368ebc]
skype(_ZN6QFrame10paintEventEP11QPaintEvent+0x6d)[0x806f7b1]
======= Memory map: ========
08048000-08988000 rwxp 00000000 03:02 1771021    /usr/bin/skype
08988000-08a49000 rw-p 08988000 00:00 0          [heap]
b6a00000-b6a21000 rw-p b6a00000 00:00 0 
b6a21000-b6b00000 ---p b6a21000 00:00 0 
b6b44000-b6c18000 r-xp 00000000 03:02 1771394    /usr/lib/libscim-1.0.so.8.1.0
b6c18000-b6c26000 rw-p 000d4000 03:02 1771394    /usr/lib/libscim-1.0.so.8.1.0
b6c26000-b6c28000 r-xp 00000000 03:02 1771398    /usr/lib/libscim-x11utils-1.0.so.8.1.0
b6c28000-b6c29000 rw-p 00001000 03:02 1771398    /usr/lib/libscim-x11utils-1.0.so.8.1.0
b6c3a000-b6c58000 r-xp 00000000 03:02 1130497    /usr/lib/qt3/plugins/inputmethods/libqscim.so
b6c58000-b6c59000 rw-p 0001e000 03:02 1130497    /usr/lib/qt3/plugins/inputmethods/libqscim.so
b6c59000-b6c7d000 r-xp 00000000 03:02 2263043    /usr/lib/qt3/plugins/inputmethods/libqsimple.so
b6c7d000-b6c7e000 rw-p 00024000 03:02 2263043    /usr/lib/qt3/plugins/inputmethods/libqsimple.so
b6c7e000-b6cfb000 r--p 00000000 03:02 1968084    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6cfb000-b6d25000 r-xp 00000000 03:02 1771240    /usr/lib/liblcms.so.1.0.15
b6d25000-b6d26000 rw-p 00029000 03:02 1771240    /usr/lib/liblcms.so.1.0.15
b6d26000-b6d29000 rw-p b6d26000 00:00 0 
b6d29000-b6d94000 r-xp 00000000 03:02 1771269    /usr/lib/libmng.so.1.1.0.9
b6d94000-b6d97000 rw-p 0006a000 03:02 1771269    /usr/lib/libmng.so.1.1.0.9
b6d97000-b6da2000 r-xp 00000000 03:02 2263044    /usr/lib/qt3/plugins/inputmethods/libqxim.so
b6da2000-b6da3000 rw-p 0000a000 03:02 2263044    /usr/lib/qt3/plugins/inputmethods/libqxim.so
b6da3000-b6da7000 r-xp 00000000 03:02 2263042    /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
b6da7000-b6da8000 rw-p 00003000 03:02 2263042    /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
b6da8000-b6dd2000 r-xp 00000000 03:02 1772012    /usr/lib/libkdefx.so.4.2.0
b6dd2000-b6dd3000 rw-p 0002a000 03:02 1772012    /usr/lib/libkdefx.so.4.2.0
b6dd4000-b6ddd000 r-xp 00000000 03:02 2263041    /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
b6ddd000-b6dde000 rw-p 00009000 03:02 2263041    /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
b6dde000-b6de3000 r-xp 00000000 03:02 2263039    /usr/lib/qt3/plugins/imageformats/libqmng.so
b6de3000-b6de4000 rw-p 00004000 03:02 2263039    /usr/lib/qt3/plugins/imageformats/libqmng.so
b6de4000-b6e03000 r-xp 00000000 03:02 2280100    /usr/lib/kde3/plugins/styles/plastik.so
b6e03000-b6e04000 rw-p 0001e000 03:02 2280100    /usr/lib/kde3/plugins/styles/plastik.so
b6e04000-b6e05000 ---p b6e04000 00:00 0 
b6e05000-b6e85000 rw-p b6e05000 00:00 0 
b6e85000-b6e8b000 r--s 00000000 03:02 557414     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b6e8b000-b6e8c000 r--s 00000000 03:02 557412     /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b6e8c000-b6e8f000 r--s 00000000 03:02 557411     /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b6e8f000-b6e90000 r--s 00000000 03:02 557410     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b6e90000-b6e91000 r--s 00000000 03:02 557409     /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b6e91000-b6e95000 r--s 00000000 03:02 557408     /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b6e95000-b6e96000 r--s 00000000 03:02 557406     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b6e96000-b6e98000 r--s 00000000 03:02 557405     /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b6e98000-b6e9a000 r--s 00000000 03:02 557404     /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b6e9a000-b6e9b000 r--s 00000000 03:02 557403     /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b6e9b000-b6e9d000 r--s 00000000 03:02 557402     /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b6e9d000-b6ea3000 r--s 00000000 03:02 557401     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b6ea3000-b6ea5000 r--s 00000000 03:02 557400     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b6ea5000-b6ea7000 r--s 00000000 03:02 557399     /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b6ea7000-b6eaf000 r--s 00000000 03:02 557398     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b6eaf000-b6eb5000 r--s 00000000 03:02 557397     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b6eb5000-b6eb6000 r--s 00000000 03:02 557396     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b6eb6000-b6ecd000 r--s 00000000 03:02 557395     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b6ecd000-b6ecf000 r--s 00000000 03:02 557394     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b6ecf000-b6ed5000 r--s 00000000 03:02 557393     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b6ed5000-b6ed7000 r--s 00000000 03:02 557387     /var/cache/fontconfig/b9ff51d8e180009819346aa132be1b02-x86.cache-2
b6ed7000-b6eda000 r--s 00000000 03:02 557386     /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b6eda000-b6ee1000 r--s 00000000 03:02 557165     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b6ee1000-b6ee3000 r--s 00000000 03:02 557382     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b6ee3000-b6ee4000 r--s 00000000 03:02 557378     /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b6ee4000-b6ee5000 r--s 00000000 03:02 557377     /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b6ee5000-b6ee6000 r--s 00000000 03:02 557376     /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b6ee6000-b6ee7000 r--s 00000000 03:02 557375     /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b6ee7000-b6ee9000 r--s 00000000 03:02 557374     /var/cache/fontconfig/0f004ce578a5ca7ae310546afb5e47d3-x86.cache-2
b6ee9000-b6eea000 r--s 00000000 03:02 557373     /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
b6eea000-b6eed000 r--s 00000000 03:02 557372     /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b6eed000-b6ef0000 r--s 00000000 03:02 557371     /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b6ef0000-b6ef9000 r--s 00000000 03:02 557370     /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b6ef9000-b6efc000 r--s 00000000 03:02 557369     /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b6efc000-b6efd000 r--s 00000000 03:02 557368     /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b6efd000-b6eff000 r--s 00000000 03:02 557367     /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b6eff000-b6f00000 r--s 00000000 03:02 557366     /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b6f00000-b6f05000 r--s 00000000 03:02 557359     /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b6f05000-b6f09000 r--s 00000000 03:02 557330     /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b6f09000-b6f0b000 r--s 00000000 03:02 557164     /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b6f0b000-b6f0e000 r--s 00000000 03:02 557162     /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b6f0e000-b6f0f000 r--s 00000000 03:02 557160     /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b6f0f000-b6f10000 r--s 00000000 03:02 557159     /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86.cache-2
b6f10000-b6f12000 r--s 00000000 03:02 557158     /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b6f12000-b6f19000 r--s 00000000 03:02 557156     /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b6f19000-b6f1f000 r--s 00000000 03:02 557153     /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b6f1f000-b6f20000 r--s 00000000 03:02 557152     /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b6f20000-b6f28000 r--s 00000000 03:02 557150     /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b6f28000-b6f2d000 r--s 00000000 03:02 557148     /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b6f2d000-b6f32000 r--s 00000000 03:02 557140     /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b6f32000-b6f37000 r--s 00000000 03:02 557144     /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b6f37000-b6f39000 r--s 00000000 03:02 557417     /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
b6f39000-b6f57000 r--s 00000000 03:02 558376     /var/cache/fontconfig/ce4a2257fa4c69f1309743ed0f77519f-x86.cache-2
b6f57000-b6f75000 r--s 00000000 03:02 1430779    /home/cojones/.fontconfig/c7dc40cce47ff3c3465a119b0b69418e-x86.cache-2
b6f75000-b6fb0000 r--p 00000000 03:02 1819989    /usr/lib/locale/en_US.utf8/LC_CTYPE
b6fb0000-b7087000 r--p 00000000 03:02 1819988    /usr/lib/locale/en_US.utf8/LC_COLLATE
b7087000-b708a000 rw-p b7087000 00:00 0 
b708a000-b708e000 r-xp 00000000 03:02 1770763    /usr/lib/libXfixes.so.3.1.0
b708e000-b708f000 rw-p 00003000 03:02 1770763    /usr/lib/libXfixes.so.3.1.0
b708f000-b70ad000 r-xp 00000000 03:02 1770942    /usr/lib/libexpat.so.1.0.0
b70ad000-b70af000 rw-p 0001d000 03:02 1770942    /usr/lib/libexpat.so.1.0.0
b70af000-b70b3000 r-xp 00000000 03:02 1770757    /usr/lib/libXdmcp.so.6.0.0
b70b3000-b70b4000 rw-p 00003000 03:02 1770757    /usr/lib/libXdmcp.so.6.0.0
b70b4000-b70b6000 r-xp 00000000 03:02 1770746    /usr/lib/libXau.so.6.0.0
b70b6000-b70b7000 rw-p 00001000 03:02 1770746    /usr/lib/libXau.so.6.0.0
b70b7000-b70b8000 rw-p b70b7000 00:00 0 
b70b8000-b7197000 r-xp 00000000 03:02 1771437    /usr/lib/libstdc++.so.6.0.8
b7197000-b719a000 r--p 000de000 03:02 1771437    /usr/lib/libstdc++.so.6.0.8
b719a000-b719c000 rw-p 000e1000 03:02 1771437    /usr/lib/libstdc++.so.6.0.8
b719c000-b71a2000 rw-p b719c000 00:00 0 
b71a2000-b71b7000 r-xp 00000000 03:02 1770718    /usr/lib/libICE.so.6.3.0
b71b7000-b71b9000 rw-p 00014000 03:02 1770718    /usr/lib/libICE.so.6.3.0
b71b9000-b71ba000 rw-p b71b9000 00:00 0 
b71ba000-b71c2000 r-xp 00000000 03:02 1770736    /usr/lib/libSM.so.6.0.0
b71c2000-b71c3000 rw-p 00007000 03:02 1770736    /usr/lib/libSM.so.6.0.0
b71c3000-b722d000 r-xp 00000000 03:02 1771066    /usr/lib/libfreetype.so.6.3.15
b722d000-b7231000 rw-p 00069000 03:02 1771066    /usr/lib/libfreetype.so.6.3.15
b7231000-b7242000 r-xp 00000000 03:02 442383     /usr/lib/libXft.so.2.1.2
b7242000-b7243000 rw-p 00010000 03:02 442383     /usr/lib/libXft.so.2.1.2
b7243000-b7245000 r-xp 00000000 03:02 1770771    /usr/lib/libXinerama.so.1.0.0
b7245000-b7246000 rw-p 00001000 03:02 1770771    /usr/lib/libXinerama.so.1.0.0
b7246000-b7247000 rw-p b7246000 00:00 0 
b7247000-b724f000 r-xp 00000000 03:02 1770753    /usr/lib/libXcursor.so.1.0.2
b724f000-b7250000 rw-p 00007000 03:02 1770753    /usr/lib/libXcursor.so.1.0.2
b7250000-b7255000 r-xp 00000000 03:02 1770781    /usr/lib/libXrandr.so.2.1.0
b7255000-b7256000 rw-p 00005000 03:02 1770781    /usr/lib/libXrandr.so.2.1.0
b7256000-b725d000 r-xp 00000000 03:02 1770783    /usr/lib/libXrender.so.1.3.0
b725d000-b725e000 rw-p 00006000 03:02 1770783    /usr/lib/libXrender.so.1.3.0
b725e000-b7265000 r-xp 00000000 03:02 1770769    /usr/lib/libXi.so.6.0.0
b7265000-b7266000 rw-p 00006000 03:02 1770769    /usr/lib/libXi.so.6.0.0
b7266000-b7279000 r-xp 00000000 03:02 1771501    /usr/lib/libz.so.1.2.3
b7279000-b727a000 rw-p 00012000 03:02 1771501    /usr/lib/libz.so.1.2.3
b727a000-b729c000 r-xp 00000000 03:02 1771355    /usr/lib/libpng12.so.0.15.0
b729c000-b729d000 rw-p 00021000 03:02 1771355    /usr/lib/libpng12.so.0.15.0
b729d000-b729e000 rw-p b729d000 00:00 0 
b729e000-b72bc000 r-xp 00000000 03:02 1771224    /usr/lib/libjpeg.so.62.0.0
b72bc000-b72bd000 rw-p 0001d000 03:02 1771224    /usr/lib/libjpeg.so.62.0.0
b72bd000-b730a000 r-xp 00000000 03:02 1770787    /usr/lib/libXt.so.6.0.0
b730a000-b730e000 rw-p 0004c000 03:02 1770787    /usr/lib/libXt.so.6.0.0
b730e000-b7323000 r-xp 00000000 03:02 1770821    /usr/lib/libaudio.so.2.4
b7323000-b7324000 rw-p 00015000 03:02 1770821    /usr/lib/libaudio.so.2.4
b7324000-b7347000 r-xp 00000000 03:02 1770948    /usr/lib/libfontconfig.so.1.2.0
b7347000-b734f000 rw-p 00023000 03:02 1770948    /usr/lib/libfontconfig.so.1.2.0
b734f000-b7351000 r-xp 00000000 03:02 1590534    /lib/tls/i686/cmov/libdl-2.5.so
b7351000-b7353000 rw-p 00001000 03:02 1590534    /lib/tls/i686/cmov/libdl-2.5.so
b7353000-b748e000 r-xp 00000000 03:02 1590528    /lib/tls/i686/cmov/libc-2.5.so
b748e000-b748f000 r--p 0013b000 03:02 1590528    /lib/tls/i686/cmov/libc-2.5.so
b748f000-b7491000 rw-p 0013c000 03:02 1590528    /lib/tls/i686/cmov/libc-2.5.so
b7491000-b7495000 rw-p b7491000 00:00 0 
b7495000-b74a0000 r-xp 00000000 03:02 1556544    /lib/libgcc_s.so.1
b74a0000-b74a1000 rw-p 0000a000 03:02 1556544    /lib/libgcc_s.so.1
b74a1000-b74c6000 r-xp 00000000 03:02 1590536    /lib/tls/i686/cmov/libm-2.5.so
b74c6000-b74c8000 rw-p 00024000 03:02 1590536    /lib/tls/i686/cmov/libm-2.5.so
b74c8000-b7578000 r-xp 00000000 03:02 1771435    /usr/lib/libstdc++.so.5.0.7
b7578000-b757d000 rw-p 000af000 03:02 1771435    /usr/lib/libstdc++.so.5.0.7
b757d000-b7582000 rw-p b757d000 00:00 0 
b7582000-b7595000 r-xp 00000000 03:02 1590554    /lib/tls/i686/cmov/libpthread-2.5.so
b7595000-b7597000 rw-p 00013000 03:02 1590554    /lib/tls/i686/cmov/libpthread-2.5.so
b7597000-b7599000 rw-p b7597000 00:00 0 
b7599000-b7686000 r-xp 00000000 03:02 1770740    /usr/lib/libX11.so.6.2.0
b7686000-b768a000 rw-p 000ed000 03:02 1770740    /usr/lib/libX11.so.6.2.0
b768a000-b7697000 r-xp 00000000 03:02 1770761    /usr/lib/libXext.so.6.4.0
b7697000-b7698000 rw-p 0000d000 03:02 1770761    /usr/lib/libXext.so.6.4.0
b7698000-b7e5e000 r-xp 00000000 03:02 1771879    /usr/lib/libqt-mt.so.3.3.7
b7e5e000-b7ea4000 rw-p 007c5000 03:02 1771879    /usr/lib/libqt-mt.so.3.3.7
b7ea4000-b7ea9000 rw-p b7ea4000 00:00 0 
b7ea9000-b7f69000 r-xp 00000000 03:02 1770811    /usr/lib/libasound.so.2.0.0
b7f69000-b7f6e000 rw-p 000bf000 03:02 1770811    /usr/lib/libasound.so.2.0.0
b7f6e000-b7f75000 r-xp 00000000 03:02 1590558    /lib/tls/i686/cmov/librt-2.5.so
b7f75000-b7f77000 rw-p 00006000 03:02 1590558    /lib/tls/i686/cmov/librt-2.5.so
b7f77000-b7f78000 r--p 00000000 03:02 1819994    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7f78000-b7f79000 r--p 00000000 03:02 1819997    /usr/lib/locale/en_US.utf8/LC_TIME
b7f79000-b7f7a000 r--p 00000000 03:02 1819992    /usr/lib/locale/en_US.utf8/LC_MONETARY
b7f7a000-b7f7b000 r--p 00000000 03:02 1835060    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f7b000-b7f7c000 r--p 00000000 03:02 1819995    /usr/lib/locale/en_US.utf8/LC_PAPER
b7f7c000-b7f7d000 r--p 00000000 03:02 1819993    /usr/lib/locale/en_US.utf8/LC_NAME
b7f7d000-b7f7e000 r--p 00000000 03:02 1819987    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7f7e000-b7f7f000 r--p 00000000 03:02 1819996    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7f7f000-b7f80000 r--p 00000000 03:02 1819991    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f80000-b7f87000 r--s 00000000 03:02 2572523    /usr/lib/gconv/gconv-modules.cache
b7f87000-b7f88000 r--p 00000000 03:02 1819990    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f88000-b7f8a000 rw-p b7f88000 00:00 0 
b7f8a000-b7fa3000 r-xp 00000000 03:02 1556501    /lib/ld-2.5.so
b7fa3000-b7fa5000 rw-p 00019000 03:02 1556501    /lib/ld-2.5.so
bffc6000-bffdc000 rw-p bffc6000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

---

### Post by justanick on 2008-01-07
For me (Kubuntu Gutsy + Mediubuntu) renaming the Skype setting directories did the trick. I.e rename /home/[your username]/.Skype to /home/[your username]/.Skype_old and try running Skype again. It seems to get stuck and crash on a dialog for accepting a "Skype end user license" if you have had Skype installed before.

---


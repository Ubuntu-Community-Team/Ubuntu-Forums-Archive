---
title: "firefox crashes"
date: 2007-11-10
forum: General Help
---

### Post by eappleton on 2007-11-10
Hi everyone,

I recently installed Ubuntu 7.10 and everything is running pretty well, but I'm having problems with Firefox. It hangs after a couple minutes on any web site. I've been using Epiphany without any problems, but I would rather use Firefox. I'm using version 2.0.0.8. Any ideas?

Thanks for the help.
Eric

---

### Post by taurus on 2007-11-10
What sites did firefox crash on?  Try running firefox from a terminal to see exactly what's the error message is.

```
firefox
```

---

### Post by eappleton on 2007-11-11
It crashes on all sites. I just ran it from a terminal and it crashed almost immediately. What am I looking for in the terminal?

---

### Post by taurus on 2007-11-11
The error message while it crashes.

---

### Post by eappleton on 2007-11-11
It dumped a few pages. This is what was left in the terminal:


b4751000-b4754000 r--s 00000000 03:01 424894     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b4754000-b4756000 r--s 00000000 03:01 424914     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b4756000-b475e000 r--s 00000000 03:01 424918     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b475e000-b4764000 r--s 00000000 03:01 424882     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b4764000-b4765000 r--s 00000000 03:01 424888     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b4765000-b4767000 r--s 00000000 03:01 424915     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b4767000-b476d000 r--s 00000000 03:01 424912     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b476d000-b4771000 r--s 00000000 03:01 424880     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b4771000-b4773000 r--s 00000000 03:01 426957     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b4773000-b4774000 r--s 00000000 03:01 424922     /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b4774000-b4775000 r--s 00000000 03:01 424919     /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b4775000-b4776000 r--s 00000000 03:01 424909     /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b4776000-b4779000 r--s 00000000 03:01 424907     /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b4779000-b477c000 r--s 00000000 03:01 424923     /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b477c000-b477e000 r--s 00000000 03:01 424879     /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b477e000-b477f000 r--s 00000000 03:01 424920     /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b477f000-b4780000 r--s 00000000 03:01 424884     /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b4780000-b4781000 r--s 00000000 03:01 424904     /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b4781000-b4786000 r--s 00000000 03:01 424899     /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b4786000-b478b000 r--s 00000000 03:01 424881     /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b478b000-b478d000 r--s 00000000 03:01 424897     /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b478d000-b4790000 r--s 00000000 03:01 424891     /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b4790000-b4793000 r--s 00000000 03:01 424885     /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b4793000-b4799000 r--s 00000000 03:01 424883     /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b4799000-b479d000 r--s 00000000 03:01 424906     /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b479d000-b479f000 r--s 00000000 03:01 424902     /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b479f000-b47a3000 r--s 00000000 03:01 424908     /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b47a3000-b47fc000 r-xp 00000000 03:01 114952     /usr/lib/firefox/components/libhtmlpars.so
b47fc000-b4804000 rw-p 00058000 03:01 114952     /usr/lib/firefox/components/libhtmlpars.so
b4804000-b48c1000 r-xp 00000000 03:01 114910     /usr/lib/firefox/components/libuconv.so
b48c1000-b48c7000 rw-p 000bc000 03:01 114910     /usr/lib/firefox/components/libuconv.so
b48c7000-b48d1000 rw-p b48c7000 00:00 0 
b48d1000-b48e7000 r-xp 00000000 03:01 65434      /usr/lib/firefox/libjsj.so
b48e7000-b48e8000 rw-p 00016000 03:01 65434      /usr/lib/firefox/libjsj.so
b48e8000-b48fc000 r-xp 00000000 03:01 115021     /usr/lib/firefox/components/liboji.so
b48fc000-b48fd000 rw-p 00014000 03:01 115021     /usr/lib/firefox/components/liboji.so
b48fd000-b4904000 r-xp 00000000 03:01 115072     /usr/lib/firefox/components/libpipboot.so
b4904000-b4905000 rw-p 00006000 03:01 115072     /usr/lib/firefox/components/libpipboot.so
b4905000-b4906000 ---p b4905000 00:00 0 
b4906000-b5106000 rw-p b4906000 00:00 0 
b5106000-b510e000 r-xp 00000000 03:01 115077     /usr/lib/firefox/components/libcookie.so
b510e000-b510f000 rw-p 00007000 03:01 115077     /usr/lib/firefox/components/libcookie.so
b510f000-b5120000 r-xp 00000000 03:01 115010     /usr/lib/firefox/components/libwebbrwsr.so
b5120000-b5122000 rw-p 00010000 03:01 115010     /usr/lib/firefox/components/libwebbrwsr.so
b5122000-b5158000 r-xp 00000000 03:01 81565      /lib/libsepol.so.1
b5158000-b5159000 rw-p 00035000 03:01 81565      /lib/libsepol.so.1
b5159000-b5163000 rw-p b5159000 00:00 0 
b5163000-b51b2000 r-xp 00000000 03:01 846981     /usr/lib/libgcrypt.so.11.2.3
b51b2000-b51b4000 rw-p 0004e000 03:01 846981     /usr/lib/libgcrypt.so.11.2.3
b51b4000-b51c3000 r-xp 00000000 03:01 847456     /usr/lib/libtasn1.so.3.0.9
b51c3000-b51c4000 rw-p 0000e000 03:01 847456     /usr/lib/libtasn1.so.3.0.9
b51c4000-b5285000 r-xp 00000000 03:01 50254      /usr/lib/libasound.so.2.0.0
b5285000-b528a000 rw-p 000c0000 03:01 50254      /usr/lib/libasound.so.2.0.0
b528a000-b528e000 r-xp 00000000 03:01 50173      /usr/lib/libORBitCosNaming-2.so.0.1.0
b528e000-b528f000 rw-p 00003000 03:01 50173      /usr/lib/libORBitCosNaming-2.so.0.1.0
b528f000-b52a3000 r-xp 00000000 03:01 81564      /lib/libselinux.so.1
b52a3000-b52a5000 rw-p 00013000 03:01 81564      /lib/libselinux.so.1
b52a5000-b52b3000 r-xp 00000000 03:01 50266      /usr/lib/libavahi-client.so.3.2.2
b52b3000-b52b4000 rw-p 0000e000 03:01 50266      /usr/lib/libavahi-client.so.3.2.2
b52b4000-b52be000 r-xp 00000000 03:01 50268      /usr/lib/libavahi-common.so.3.4.4
b52be000-b52bf000 rw-p 00009000 03:01 50268      /usr/lib/libavahi-common.so.3.4.4
b52bf000-b5329000 r-xp 00000000 03:01 847084     /usr/lib/libgnutls.so.13.3.0
b5329000-b532f000 rw-p 0006a000 03:01 847084     /usr/lib/libgnutls.so.13.3.0
b532f000-b5363000 r-xp 00000000 03:01 50329      /usr/lib/libdbus-1.so.3.3.0
b5363000-b5364000 rw-p 00033000 03:01 50329      /usr/lib/libdbus-1.so.3.3.0
b5364000-b537e000 r-xp 00000000 03:01 50331      /usr/lib/libdbus-glib-1.so.2.1.0
b537e000-b537f000 rw-p 0001a000 03:01 50331      /usr/lib/libdbus-glib-1.so.2.1.0
b537f000-b5497000 r-xp 00000000 03:01 847514     /usr/lib/libxml2.so.2.6.30
b5497000-b549c000 rw-p 00118000 03:01 847514     /usr/lib/libxml2.so.2.6.30
b549c000-b549d000 rw-p b549c000 00:00 0 
b549d000-b54a4000 r-xp 00000000 03:01 81554      /lib/libpopt.so.0.0.0
b54a4000-b54a5000 rw-p 00006000 03:01 81554      /lib/libpopt.so.0.0.0
b54a5000-b54c5000 r-xp 00000000 03:01 50264      /usr/lib/libaudiofile.so.0.0.2
b54c5000-b54c7000 rw-p 00020000 03:01 50264      /usr/lib/libaudiofile.so.0.0.2
b54c7000-b54d0000 r-xp 00000000 03:01 50380      /usr/lib/libesd.so.0.2.38
b54d0000-b54d1000 rw-p 00009000 03:01 50380      /usr/lib/libesd.so.0.2.38
b54d1000-b54e4000 r-xp 00000000 03:01 50285      /usr/lib/libbonobo-activation.so.4.0.0
b54e4000-b54e6000 rw-p 00013000 03:01 50285      /usr/lib/libbonobo-activation.so.4.0.0
b54e6000-b5538000 r-xp 00000000 03:01 50283      /usr/lib/libbonobo-2.so.0.0.0
b5538000-b5542000 rw-p 00051000 03:01 50283      /usr/lib/libbonobo-2.so.0.0.0
b5542000-b5598000 r-xp 00000000 03:01 847078     /usr/lib/libgnomevfs-2.so.0.2000.0
b5598000-b559b000 rw-p 00055000 03:01 847078     /usr/lib/libgnomevfs-2.so.0.2000.0
b559b000-b55af000 r-xp 00000000 03:01 847048     /usr/lib/libgnome-2.so.0.2000.0
b55af000-b55b0000 rw-p 00014000 03:01 847048     /usr/lib/libgnome-2.so.0.2000.0
b55b0000-b55b3000 r--s 00000000 03:01 424892     /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b55b3000-b55b6000 r-xp 00000000 03:01 115038     /usr/lib/firefox/components/libremoteservice.so
b55b6000-b55b7000 rw-p 00002000 03:01 115038     /usr/lib/firefox/components/libremoteservice.so
b55b7000-b55ba000 r-xp 00000000 03:01 115093     /usr/lib/firefox/components/libpermissions.so
b55ba000-b55bb000 rw-p 00002000 03:01 115093     /usr/lib/firefox/components/libpermissions.so
b55bb000-b561b000 rw-s 00000000 00:09 8126480    /SYSV00000000 (deleted)
b561b000-b562c000 r-xp 00000000 03:01 50208      /usr/lib/libXft.so.2.1.2
b562c000-b562d000 rw-p 00010000 03:01 50208      /usr/lib/libXft.so.2.1.2
b562d000-b5633000 r-xp 00000000 03:01 847347     /usr/lib/libpangoxft-1.0.so.0.1800.2
b5633000-b5634000 rw-p 00005000 03:01 847347     /usr/lib/libpangoxft-1.0.so.0.1800.2
b5634000-b5637000 r-xp 00000000 03:01 847088     /usr/lib/libgpg-error.so.0.3.0
b5637000-b5638000 rw-p 00002000 03:01 847088     /usr/lib/libgpg-error.so.0.3.0
b5638000-b563e000 r-xp 00000000 03:01 130834     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b563e000-b563f000 rw-p 00005000 03:01 130834     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b563f000-b5677000 r-xp 00000000 03:01 114955     /usr/lib/firefox/components/libgfx_gtk.so
b5677000-b567a000 rw-p 00038000 03:01 114955     /usr/lib/firefox/components/libgfx_gtk.so
b567a000-b5699000 r-xp 00000000 03:01 847230     /usr/lib/libjpeg.so.62.0.0
b5699000-b569a000 rw-p 0001e000 03:01 847230     /usr/lib/libjpeg.so.62.0.0
b569a000-b56be000 r-xp 00000000 03:01 114957     /usr/lib/firefox/components/libimglib2.so
b56be000-b56c0000 rw-p 00023000 03:01 114957     /usr/lib/firefox/components/libimglib2.so
b56c0000-b5be3000 r-xp 00000000 03:01 114994     /usr/lib/firefox/components/libgklayout.so
b5be3000-b5c42000 rw-p 00522000 03:01 114994     /usr/lib/firefox/components/libgklayout.so
b5c42000-b5c49000 rw-p b5c42000 00:00 0 
b5c49000-b5c92000 r-xp 00000000 03:01 50169      /usr/lib/libORBit-2.so.0.1.0
b5c92000-b5c9b000 rw-p 00049000 03:01 50169      /usr/lib/libORBit-2.so.0.1.0
b5c9b000-b5c9c000 rw-p b5c9b000 00:00 0 
b5c9c000-b5ccb000 r-xp 00000000 03:01 846979     /usr/lib/libgconf-2.so.4.1.2
b5ccb000-b5cce000 rw-p 0002e000 03:01 846979     /usr/lib/libgconf-2.so.4.1.2
b5cd0000-b5cd2000 r-xp 00000000 03:01 115150     /lib/tls/i686/cmov/libutil-2.6.1.so
b5cd2000-b5cd4000 rw-p 00001000 03:01 115150     /lib/tls/i686/cmov/libutil-2.6.1.so
b5cd4000-b5cd8000 r-xp 00000000 03:01 115057     /usr/lib/firefox/components/libcommandlines.so
b5cd8000-b5cd9000 rw-p 00004000 03:01 115057     /usr/lib/firefox/components/libcommandlines.so
b5cd9000-b5cef000 r-xp 00000000 03:01 115019     /usr/lib/firefox/components/libnsappshell.so
b5cef000-b5cf1000 rw-p 00015000 03:01 115019     /usr/lib/firefox/components/libnsappshell.so
b5cf1000-b5d05000 r-xp 00000000 03:01 115034     /usr/lib/firefox/components/libappcomps.so
b5d05000-b5d06000 rw-p 00014000 03:01 115034     /usr/lib/firefox/components/libappcomps.so
b5d06000-b5d53000 r-xp 00000000 03:01 114997     /usr/lib/firefox/components/libdocshell.so
b5d53000-b5d57000 rw-p 0004d000 03:01 114997     /usr/lib/firefox/components/libdocshell.so
b5d57000-b5d7e000 r-xp 00000000 03:01 114949     /usr/lib/firefox/components/librdf.so
b5d7e000-b5d80000 rw-p 00026000 03:01 114949     /usr/lib/firefox/components/librdf.so
b5d80000-b5d81000 ---p b5d80000 00:00 0 
b5d81000-b6581000 rw-p b5d81000 00:00 0 
b6581000-b6594000 r-xp 00000000 03:01 114947     /usr/lib/firefox/components/libcaps.so
b6594000-b6595000 rw-p 00013000 03:01 114947     /usr/lib/firefox/components/libcaps.so
b6595000-b65bf000 r-xp 00000000 03:01 115008     /usr/lib/firefox/components/libembedcomponents.so
b65bf000-b65c1000 rw-p 0002a000 03:01 115008     /usr/lib/firefox/components/libembedcomponents.so
b65c1000-b6606000 r-xp 00000000 03:01 115060     /usr/lib/firefox/components/libtoolkitcomps.so
b6606000-b6609000 rw-p 00045000 03:01 115060     /usr/lib/firefox/components/libtoolkitcomps.so
b6609000-b661b000 r-xp 00000000 03:01 130801     /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b661b000-b661c000 rw-p 00011000 03:01 130801     /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b661c000-b6631000 r-xp 00000000 03:01 50159      /usr/lib/libICE.so.6.3.0
b6631000-b6633000 rw-p 00014000 03:01 50159      /usr/lib/libICE.so.6.3.0
b6633000-b6634000 rw-p b6633000 00:00 0 
b6634000-b663b000 r-xp 00000000 03:01 50177      /usr/lib/libSM.so.6.0.0
b663b000-b663c000 rw-p 00006000 03:01 50177      /usr/lib/libSM.so.6.0.0
b663c000-b6689000 r-xp 00000000 03:01 50228      /usr/lib/libXt.so.6.0.0
b6689000-b668d000 rw-p 0004c000 03:01 50228      /usr/lib/libXt.so.6.0.0
b668e000-b668f000 rw-p b668e000 00:00 0 
b668f000-b6691000 r-xp 00000000 03:01 50272      /usr/lib/libavahi-glib.so.1.0.1
b6691000-b6692000 rw-p 00001000 03:01 50272      /usr/lib/libavahi-glib.so.1.0.1
b6692000-b6697000 r-xp 00000000 03:01 115085     /usr/lib/firefox/components/libsystem-pref.so
b6697000-b6698000 rw-p 00004000 03:01 115085     /usr/lib/firefox/components/libsystem-pref.so
b6698000-b669b000 r-xp 00000000 03:01 65401      /usr/lib/firefox/libgtkxtbin.so
b669b000-b669c000 rw-p 00003000 03:01 65401      /usr/lib/firefox/libgtkxtbin.so
b669c000-b66c7000 r-xp 00000000 03:01 114979     /usr/lib/firefox/components/libwidget_gtk2.so
b66c7000-b66cb000 rw-p 0002b000 03:01 114979     /usr/lib/firefox/components/libwidget_gtk2.so
b66cb000-b66dc000 r-xp 00000000 03:01 114939     /usr/lib/firefox/components/libjar50.so
b66dc000-b66dd000 rw-p 00011000 03:01 114939     /usr/lib/firefox/components/libjar50.so
b66dd000-b6728000 r-xp 00000000 03:01 114907     /usr/lib/firefox/components/libxpconnect.so
b6728000-b672c000 rw-p 0004b000 03:01 114907     /usr/lib/firefox/components/libxpconnect.so
b672c000-b672d000 ---p b672c000 00:00 0 
b672d000-b6f2d000 rw-p b672d000 00:00 0 
b6f2d000-b6f46000 r-xp 00000000 03:01 66492      /usr/lib/firefox/libxpcom_compat.so
b6f46000-b6f47000 rw-p 00018000 03:01 66492      /usr/lib/firefox/libxpcom_compat.so
b6f47000-b6f48000 rw-p b6f47000 00:00 0 
b6f48000-b6f65000 r-xp 00000000 03:01 65381      /usr/lib/firefox/libgkgfx.so
b6f65000-b6f67000 rw-p 0001c000 03:01 65381      /usr/lib/firefox/libgkgfx.so
b6f67000-b6fa0000 r-xp 00000000 03:01 115119     /usr/lib/firefox/components/libbrowsercomps.so
b6fa0000-b6fa3000 rw-p 00038000 03:01 115119     /usr/lib/firefox/components/libbrowsercomps.so
b6fa3000-b6fd9000 r-xp 00000000 03:01 114916     /usr/lib/firefox/components/libi18n.so
b6fd9000-b6fdc000 rw-p 00035000 03:01 114916     /usr/lib/firefox/components/libi18n.so
b6fdc000-b709c000 r-xp 00000000 03:01 114937     /usr/lib/firefox/components/libnecko.so
b709c000-b70a4000 rw-p 000c0000 03:01 114937     /usr/lib/firefox/components/libnecko.so
b70a4000-b70b2000 r-xp 00000000 03:01 114945     /usr/lib/firefox/components/libpref.so
b70b2000-b70b3000 rw-p 0000e000 03:01 114945     /usr/lib/firefox/components/libpref.so
b70b3000-b70c2000 r-xp 00000000 03:01 115026     /usr/lib/firefox/components/libchrome.so
b70c2000-b70c3000 rw-p 0000f000 03:01 115026     /usr/lib/firefox/components/libchrome.so
b70c3000-b70f9000 r-xp 00000000 03:01 847199     /usr/lib/libhunspell-1.1.so.0.0.0
b70f9000-b70fd000 rw-p 00036000 03:01 847199     /usr/lib/libhunspell-1.1.so.0.0.0
b70fd000-b70ff000 r-xp 00000000 03:01 65307      /usr/lib/firefox/libgfxpsshar.so
b70ff000-b7100000 rw-p 00001000 03:01 65307      /usr/lib/firefox/libgfxpsshar.so
b7100000-b7107000 r-xp 00000000 03:01 115084     /usr/lib/firefox/components/libautoconfig.so
b7107000-b7108000 rw-p 00006000 03:01 115084     /usr/lib/firefox/components/libautoconfig.so
b7108000-b710a000 r-xp 00000000 03:01 81533      /lib/libnss_mdns4.so.2
b710a000-b710b000 rw-p 00001000 03:01 81533      /lib/libnss_mdns4.so.2
b710b000-b711a000 r-xp 00000000 03:01 115146     /lib/tls/i686/cmov/libresolv-2.6.1.so
b711a000-b711c000 rw-p 0000f000 03:01 115146     /lib/tls/i686/cmov/libresolv-2.6.1.so
b711c000-b711e000 rw-p b711c000 00:00 0 
b711e000-b7122000 r-xp 00000000 03:01 115139     /lib/tls/i686/cmov/libnss_dns-2.6.1.so
b7122000-b7124000 rw-p 00003000 03:01 115139     /lib/tls/i686/cmov/libnss_dns-2.6.1.so
b7124000-b7125000 r--s 00000000 03:01 424916     /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b7125000-b7126000 r--s 00000000 03:01 424887     /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b7126000-b712a000 r-xp 00000000 03:01 115096     /usr/lib/firefox/components/libmyspell.so
b712a000-b712b000 rw-p 00004000 03:01 115096     /usr/lib/firefox/components/libmyspell.so
b712b000-b712e000 r-xp 00000000 03:01 115099     /usr/lib/firefox/components/libbrowserdirprovider.so
b712e000-b712f000 rw-p 00002000 03:01 115099     /usr/lib/firefox/components/libbrowserdirprovider.so
b712f000-b7138000 r-xp 00000000 03:01 115140     /lib/tls/i686/cmov/libnss_files-2.6.1.so
b7138000-b713a000 rw-p 00008000 03:01 115140     /lib/tls/i686/cmov/libnss_files-2.6.1.so
b713a000-b7142000 r-xp 00000000 03:01 115142     /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b7142000-b7144000 rw-p 00007000 03:01 115142     /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b7144000-b7158000 r-xp 00000000 03:01 115137     /lib/tls/i686/cmov/libnsl-2.6.1.so
b7158000-b715a000 rw-p 00013000 03:01 115137     /lib/tls/i686/cmov/libnsl-2.6.1.so
b715a000-b715c000 rw-p b715a000 00:00 0 
b715c000-b7163000 r-xp 00000000 03:01 115138     /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b7163000-b7165000 rw-p 00006000 03:01 115138     /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b7165000-b7166000 r--s 00000000 03:01 424901     /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b7166000-b7168000 r-xp 00000000 03:01 81534      /lib/libnss_mdns4_minimal.so.2
b7168000-b7169000 rw-p 00001000 03:01 81534      /lib/libnss_mdns4_minimal.so.2
b7169000-b716b000 r-xp 00000000 03:01 201911     /usr/lib/gconv/UTF-16.so
b716b000-b716d000 rw-p 00001000 03:01 201911     /usr/lib/gconv/UTF-16.so
b716d000-b716e000 r-xp 00000000 03:01 201857     /usr/lib/gconv/ISO8859-1.so
b716e000-b7170000 rw-p 00000000 03:01 201857     /usr/lib/gconv/ISO8859-1.so
b7170000-b71af000 r--p 00000000 03:01 131594     /usr/lib/locale/en_US.utf8/LC_CTYPE
b71af000-b71b0000 r--p 00000000 03:01 131599     /usr/lib/locale/en_US.utf8/LC_NUMERIC
b71b0000-b71b1000 r--p 00000000 03:01 131602     /usr/lib/locale/en_US.utf8/LC_TIME
b71b1000-b7291000 r--p 00000000 03:01 131593     /usr/lib/locale/en_US.utf8/LC_COLLATE
b7291000-b7292000 r--p 00000000 03:01 131597     /usr/lib/locale/en_US.utf8/LC_MONETARY
b7292000-b7293000 r--p 00000000 03:01 146632     /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7293000-b7294000 r--p 00000000 03:01 131600     /usr/lib/locale/en_US.utf8/LC_PAPER
b7294000-b7295000 r--p 00000000 03:01 131598     /usr/lib/locale/en_US.utf8/LC_NAME
b7295000-b7298000 rw-p b7295000 00:00 0 
b7298000-b72b6000 r-xp 00000000 03:01 50389      /usr/lib/libexpat.so.1.0.0
b72b6000-b72b8000 rw-p 0001e000 03:01 50389      /usr/lib/libexpat.so.1.0.0
b72b8000-b72da000 r-xp 00000000 03:01 49173      /usr/lib/libpng12.so.0.15.0
b72da000-b72db000 rw-p 00021000 03:01 49173      /usr/lib/libpng12.so.0.15.0
b72db000-b72ef000 r-xp 00000000 03:01 847520     /usr/lib/libz.so.1.2.3.3
b72ef000-b72f0000 rw-p 00013000 03:01 847520     /usr/lib/libz.so.1.2.3.3
b72f0000-b72f1000 rw-p b72f0000 00:00 0 
b72f1000-b735d000 r-xp 00000000 03:01 50403      /usr/lib/libfreetype.so.6.3.16
b735d000-b7361000 rw-p 0006b000 03:01 50403      /usr/lib/libfreetype.so.6.3.16
b7361000-b738e000 r-xp 00000000 03:01 847341     /usr/lib/libpangoft2-1.0.so.0.1800.2
b738e000-b738f000 rw-p 0002c000 03:01 847341     /usr/lib/libpangoft2-1.0.so.0.1800.2
b738f000-b7396000 r-xp 00000000 03:01 115147     /lib/tls/i686/cmov/librt-2.6.1.so
b7396000-b7398000 rw-p 00006000 03:01 115147     /lib/tls/i686/cmov/librt-2.6.1.so
b7398000-b739c000 r-xp 00000000 03:01 50198      /usr/lib/libXdmcp.so.6.0.0
b739c000-b739d000 rw-p 00003000 03:01 50198      /usr/lib/libXdmcp.so.6.0.0
b739d000-b739f000 r-xp 00000000 03:01 50187      /usr/lib/libXau.so.6.0.0
b739f000-b73a0000 rw-p 00001000 03:01 50187      /usr/lib/libXau.so.6.0.0
b73a0000-b73a1000 rw-p b73a0000 00:00 0 
b73a1000-b73a9000 r-xp 00000000 03:01 50194      /usr/lib/libXcursor.so.1.0.2
b73a9000-b73aa000 rw-p 00007000 03:01 50194      /usr/lib/libXcursor.so.1.0.2
b73aa000-b73af000 r-xp 00000000 03:01 50222      /usr/lib/libXrandr.so.2.1.0
b73af000-b73b0000 rw-p 00005000 03:01 50222      /usr/lib/libXrandr.so.2.1.0
b73b0000-b73b7000 r-xp 00000000 03:01 50210      /usr/lib/libXi.so.6.0.0
b73b7000-b73b8000 rw-p 00006000 03:01 50210      /usr/lib/libXi.so.6.0.0
b73b8000-b73ba000 r-xp 00000000 03:01 50212      /usr/lib/libXinerama.so.1.0.0
b73ba000-b73bb000 rw-p 00001000 03:01 50212      /usr/lib/libXinerama.so.1.0.0
b73bb000-b73c2000 r-xp 00000000 03:01 50224      /usr/lib/libXrender.so.1.3.0
b73c2000-b73c3000 rw-p 00006000 03:01 50224      /usr/lib/libXrender.so.1.3.0
b73c3000-b73d0000 r-xp 00000000 03:01 50202      /usr/lib/libXext.so.6.4.0
b73d0000-b73d1000 rw-p 0000d000 03:01 50202      /usr/lib/libXext.so.6.4.0
b73d1000-b73d2000 rw-p b73d1000 00:00 0 
b73d2000-b73f5000 r-xp 00000000 03:01 50395      /usr/lib/libfontconfig.so.1.2.0
b73f5000-b73fd000 rw-p 00023000 03:01 50395      /usr/lib/libfontconfig.so.1.2.0
b73fd000-b7472000 r-xp 00000000 03:01 50291      /usr/lib/libcairo.so.2.11.5
b7472000-b7474000 rw-p 00074000 03:01 50291      /usr/lib/libcairo.so.2.11.5
b7474000-b7530000 r-xp 00000000 03:01 847036     /usr/lib/libglib-2.0.so.0.1400.1
b7530000-b7531000 rw-p 000bc000 03:01 847036     /usr/lib/libglib-2.0.so.0.1400.1
b7531000-b7534000 r-xp 00000000 03:01 847046     /usr/lib/libgmodule-2.0.so.0.1400.1
b7534000-b7535000 rw-p 00002000 03:01 847046     /usr/lib/libgmodule-2.0.so.0.1400.1
b7535000-b756f000 r-xp 00000000 03:01 847086     /usr/lib/libgobject-2.0.so.0.1400.1
b756f000-b7570000 rw-p 0003a000 03:01 847086     /usr/lib/libgobject-2.0.so.0.1400.1
b7570000-b7571000 rw-p b7570000 00:00 0 
b7571000-b758a000 r-xp 00000000 03:01 50260      /usr/lib/libatk-1.0.so.0.2009.1
b758a000-b758c000 rw-p 00018000 03:01 50260      /usr/lib/libatk-1.0.so.0.2009.1
b758c000-b7590000 r-xp 00000000 03:01 50204      /usr/lib/libXfixes.so.3.1.0
b7590000-b7591000 rw-p 00003000 03:01 50204      /usr/lib/libXfixes.so.3.1.0
b7591000-b7593000 r-xp 00000000 03:01 50196      /usr/lib/libXdamage.so.1.1.0
b7593000-b7594000 rw-p 00001000 03:01 50196      /usr/lib/libXdamage.so.1.1.0
b7594000-b7596000 r-xp 00000000 03:01 50192      /usr/lib/libXcomposite.so.1.0.0
b7596000-b7597000 rw-p 00001000 03:01 50192      /usr/lib/libXcomposite.so.1.0.0
b7597000-b75d2000 r-xp 00000000 03:01 847337     /usr/lib/libpango-1.0.so.0.1800.2
b75d2000-b75d4000 rw-p 0003b000 03:01 847337     /usr/lib/libpango-1.0.so.0.1800.2
b75d4000-b75dc000 r-xp 00000000 03:01 847339     /usr/lib/libpangocairo-1.0.so.0.1800.2
b75dc000-b75dd000 rw-p 00007000 03:01 847339     /usr/lib/libpangocairo-1.0.so.0.1800.2
b75dd000-b75de000 rw-p b75dd000 00:00 0 
b75de000-b75f5000 r-xp 00000000 03:01 846998     /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b75f5000-b75f6000 rw-p 00016000 03:01 846998     /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b75f6000-b7600000 r-xp 00000000 03:01 81507      /lib/libgcc_s.so.1
b7600000-b7601000 rw-p 0000a000 03:01 81507      /lib/libgcc_s.so.1
b7601000-b7603000 r-xp 00000000 03:01 847366     /usr/lib/libplds4.so.0d
b7603000-b7604000 rw-p 00001000 03:01 847366     /usr/lib/libplds4.so.0d
b7604000-b7606000 r-xp 00000000 03:01 115134     /lib/tls/i686/cmov/libdl-2.6.1.so
b7606000-b7608000 rw-p 00001000 03:01 115134     /lib/tls/i686/cmov/libdl-2.6.1.so
b7608000-b762b000 r-xp 00000000 03:01 115135     /lib/tls/i686/cmov/libm-2.6.1.so
b762b000-b762d000 rw-p 00023000 03:01 115135     /lib/tls/i686/cmov/libm-2.6.1.so
b762d000-b762e000 rw-p b762d000 00:00 0 
b762e000-b7772000 r-xp 00000000 03:01 115131     /lib/tls/i686/cmov/libc-2.6.1.so
b7772000-b7773000 r--p 00143000 03:01 115131     /lib/tls/i686/cmov/libc-2.6.1.so
b7773000-b7775000 rw-p 00144000 03:01 115131     /lib/tls/i686/cmov/libc-2.6.1.so
b7775000-b7778000 rw-p b7775000 00:00 0 
b7778000-b7860000 r-xp 00000000 03:01 847450     /usr/lib/libstdc++.so.6.0.9
b7860000-b7863000 r--p 000e8000 03:01 847450     /usr/lib/libstdc++.so.6.0.9
b7863000-b7865000 rw-p 000eb000 03:01 847450     /usr/lib/libstdc++.so.6.0.9
b7865000-b786b000 rw-p b7865000 00:00 0 
b786b000-b786f000 r-xp 00000000 03:01 847148     /usr/lib/libgthread-2.0.so.0.1400.1
b786f000-b7870000 rw-p 00003000 03:01 847148     /usr/lib/libgthread-2.0.so.0.1400.1
b7870000-b795d000 r-xp 00000000 03:01 50181      /usr/lib/libX11.so.6.2.0
b795d000-b7961000 rw-p 000ed000 03:01 50181      /usr/lib/libX11.so.6.2.0
b7961000-b79e5000 r-xp 00000000 03:01 846996     /usr/lib/libgdk-x11-2.0.so.0.1200.0
b79e5000-b79e8000 rw-p 00084000 03:01 846996     /usr/lib/libgdk-x11-2.0.so.0.1200.0
b79e8000-b7d65000 r-xp 00000000 03:01 847151     /usr/lib/libgtk-x11-2.0.so.0.1200.0
b7d65000-b7d6c000 rw-p 0037c000 03:01 847151     /usr/lib/libgtk-x11-2.0.so.0.1200.0
b7d6c000-b7d6e000 rw-p b7d6c000 00:00 0 
b7d6e000-b7d82000 r-xp 00000000 03:01 115145     /lib/tls/i686/cmov/libpthread-2.6.1.so
b7d82000-b7d84000 rw-p 00013000 03:01 115145     /lib/tls/i686/cmov/libpthread-2.6.1.so
b7d84000-b7d86000 rw-p b7d84000 00:00 0 
b7d86000-b7db4000 r-xp 00000000 03:01 847312     /usr/lib/libnspr4.so.0d
b7db4000-b7db5000 rw-p 0002e000 03:01 847312     /usr/lib/libnspr4.so.0d
b7db5000-b7db7000 rw-p b7db5000 00:00 0 
b7db7000-b7dbb000 r-xp 00000000 03:01 847365     /usr/lib/libplc4.so.0d
b7dbb000-b7dbc000 rw-p 00003000 03:01 847365     /usr/lib/libplc4.so.0d
b7dbc000-b7dbd000 r--p 00000000 03:01 131592     /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7dbd000-b7dbe000 r--p 00000000 03:01 131601     /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7dbe000-b7dbf000 r--p 00000000 03:01 131596     /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7dbf000-b7dc6000 r--s 00000000 03:01 65857      /usr/lib/gconv/gconv-modules.cache
b7dc6000-b7dc7000 r--p 00000000 03:01 131595     /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7dc7000-b7e69000 r-xp 00000000 03:01 66493      /usr/lib/firefox/libxpcom_core.so
b7e69000-b7e71000 rw-p 000a1000 03:01 66493      /usr/lib/firefox/libxpcom_core.so
b7e71000-b7e73000 r-xp 00000000 03:01 66491      /usr/lib/firefox/libxpcom.so
b7e73000-b7e74000 rw-p 00002000 03:01 66491      /usr/lib/firefox/libxpcom.so
b7e74000-b7f1b000 r-xp 00000000 03:01 65839      /usr/lib/firefox/libmozjs.so
b7f1b000-b7f20000 rw-p 000a7000 03:01 65839      /usr/lib/firefox/libmozjs.so
b7f20000-b7f22000 rw-p b7f20000 00:00 0 
b7f22000-b7f3c000 r-xp 00000000 03:01 81453      /lib/ld-2.6.1.so
b7f3c000-b7f3e000 rw-p 00019000 03:01 81453      /lib/ld-2.6.1.so
bf846000-bf85b000 rw-p bf846000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]

---


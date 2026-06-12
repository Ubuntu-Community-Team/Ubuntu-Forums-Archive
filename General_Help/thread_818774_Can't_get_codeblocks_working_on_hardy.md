---
title: "Can't get code::blocks working on hardy?"
date: 2008-06-04
forum: General Help
---

### Post by zorocke on 2008-06-04
I have followed this tutorial on getting code::blocks installed. [http://lgp203.free.fr/spip/spip.php?article1](http://lgp203.free.fr/spip/spip.php?article1)
But, i seem to have a problem. When I run code::blocks it shows the splash screen then disappears. 

If i execute codeblocks from the console i see:
```
Initialize EditColourSet .....
Initialize EditColourSet: done.
Loading toolbar...
*** glibc detected *** codeblocks: double free or corruption (out): 0x08960450 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb68f5a85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb68f94f0]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb78388b1]
/usr/local/lib/libwx_gtk2u_core-2.8.so.0(_ZN8wxWindow9DoSetSizeEiiiii+0x5db)[0xb6e02ddb]
/usr/local/lib/libwx_gtk2u_core-2.8.so.0(_ZN14wxBitmapButton10SetDefaultEv+0x7d)[0xb6e3f0dd]
codeblocks[0x80b13d4]
codeblocks[0x80a8370]
codeblocks[0x80a8fba]
codeblocks[0x806e255]
codeblocks[0x806f061]
codeblocks(_ZN12wxAppConsole10CallOnInitEv+0x11)[0x8070131]
/usr/local/lib/libwx_baseu-2.8.so.0(_Z7wxEntryRiPPw+0x40)[0xb6ba0f70]
/usr/local/lib/libwx_baseu-2.8.so.0(_Z7wxEntryRiPPc+0x37)[0xb6ba1047]
codeblocks[0x806b1c0]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb68a0450]
codeblocks(_ZN9wxAppBase8MainLoopEv+0x4d)[0x806aee1]
======= Memory map: ========
08048000-080d7000 r-xp 00000000 08:03 1444290    /usr/bin/codeblocks
080d7000-080dd000 rw-p 0008e000 08:03 1444290    /usr/bin/codeblocks
080dd000-08b93000 rw-p 080dd000 00:00 0          [heap]
b3f00000-b3f21000 rw-p b3f00000 00:00 0 
b3f21000-b4000000 ---p b3f21000 00:00 0 
b404c000-b404d000 ---p b404c000 00:00 0 
b404d000-b484d000 rw-p b404d000 00:00 0 
b484d000-b484e000 ---p b484d000 00:00 0 
b484e000-b504e000 rw-p b484e000 00:00 0 
b504e000-b504f000 ---p b504e000 00:00 0 
b504f000-b584f000 rw-p b504f000 00:00 0 
b584f000-b5850000 ---p b584f000 00:00 0 
b5850000-b6050000 rw-p b5850000 00:00 0 
b6050000-b605f000 r-xp 00000000 08:03 1761318    /lib/libbz2.so.1.0.4
b605f000-b6060000 rw-p 0000f000 08:03 1761318    /lib/libbz2.so.1.0.4
b6060000-b60bf000 r-xp 00000000 08:03 1442111    /usr/lib/libgio-2.0.so.0.0.0
b60bf000-b60c1000 rw-p 0005e000 08:03 1442111    /usr/lib/libgio-2.0.so.0.0.0
b60c1000-b61da000 r-xp 00000000 08:03 1443967    /usr/lib/libxml2.so.2.6.31
b61da000-b61df000 rw-p 00119000 08:03 1443967    /usr/lib/libxml2.so.2.6.31
b61df000-b61e0000 rw-p b61df000 00:00 0 
b61e0000-b6212000 r-xp 00000000 08:03 1443267    /usr/lib/libcroco-0.6.so.3.0.1
b6212000-b6215000 rw-p 00031000 08:03 1443267    /usr/lib/libcroco-0.6.so.3.0.1
b6215000-b6245000 r-xp 00000000 08:03 1443521    /usr/lib/libgsf-1.so.114.0.7
b6245000-b6248000 rw-p 0002f000 08:03 1443521    /usr/lib/libgsf-1.so.114.0.7
b6248000-b6249000 rw-p b6248000 00:00 0 
b6249000-b6279000 r-xp 00000000 08:03 1443844    /usr/lib/librsvg-2.so.2.22.2
b6279000-b627a000 rw-p 00030000 08:03 1443844    /usr/lib/librsvg-2.so.2.22.2
b627a000-b627b000 r-xp 00000000 08:03 1474993    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b627b000-b627c000 rw-p 00000000 08:03 1474993    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b627c000-b6327000 r--p 00000000 08:03 1673633    /usr/share/icons/Tangerine/icon-theme.cache
b6327000-b63b8000 r--p 00000000 08:03 1582563    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b63b8000-b6418000 rw-s 00000000 00:09 3276814    /SYSV00000000 (deleted)
b6418000-b649f000 r--p 00000000 08:03 1582562    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b649f000-b64a1000 r-xp 00000000 08:03 1483184    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b64a1000-b64a2000 rw-p 00001000 08:03 1483184    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b64a2000-b6502000 rw-s 00000000 00:09 3211276    /SYSV00000000 (deleted)
b6502000-b6508000 r--s 00000000 08:03 2367552    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b6508000-b650b000 r--s 00000000 08:03 2367562    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b650b000-b650c000 r--s 00000000 08:03 2367554    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b650c000-b650d000 r--s 00000000 08:03 2367547    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b650d000-b6510000 r--s 00000000 08:03 2367553    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b6510000-b6513000 r--s 00000000 08:03 2367549    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b6513000-b6516000 r--s 00000000 08:03 2367559    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b6516000-b651e000 r--s 00000000 08:03 2367563    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b651e000-b6526000 r--s 00000000 08:03 2367542    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b6526000-b6527000 r--s 00000000 08:03 2367545    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b6527000-b6549000 r--s 00000000 08:03 2371001    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b6549000-b6573000 rw-p b6549000 00:00 0 
b6581000-b6585000 r-xp 00000000 08:03 1475213    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6585000-b6586000 rw-p 00003000 08:03 1475213    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6587000-b6588000 rw-p b6587000 00:00 0 
b6588000-b658b000 rw-s 00000000 00:09 3244045    /SYSV00000000 (deleted)
b658b000-b658e000 r--s 00000000 08:03 2367560    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b658e000-b6595000 r--s 00000000 08:03 2367557    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b6595000-b659b000 r--s 00000000 08:03 2367541    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b659b000-b659d000 r--s 00000000 08:03 2369273    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b659d000-b65a6000 r-xp 00000000 08:03 1779090    /lib/tls/i686/cmov/libnss_files-2.7.so
b65a6000-b65a8000 rw-p 00008000 08:03 1779090    /lib/tls/i686/cmov/libnss_files-2.7.so
b65a8000-b65b0000 r-xp 00000000 08:03 1779094    /lib/tls/i686/cmov/libnss_nis-2.7.so
b65b0000-b65b2000 rw-p 00007000 08:03 1779094    /lib/tls/i686/cmov/libnss_nis-2.7.so
b65b2000-b65c6000 r-xp 00000000 08:03 1779084    /lib/tls/i686/cmov/libnsl-2.7.so
b65c6000-b65c8000 rw-p 00013000 08:03 1779084    /lib/tls/i686/cmov/libnsl-2.7.so
b65c8000-b65ca000 rw-p b65c8000 00:00 0 
b65ca000-b65d1000 r-xp 00000000 08:03 1779086    /lib/tls/i686/cmov/libnss_compat-2.7.so
b65d1000-b65d3000 rw-p 00006000 08:03 1779086    /lib/tls/i686/cmov/libnss_compat-2.7.so
b65d3000-b65e4000 r-xp 00000000 08:03 1474956    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b65e4000-b65e5000 rw-p 00011000 08:03 1474956    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b65e5000-b65e6000 r--p 00000000 08:03 1475455    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b65e6000-b65e7000 r--p 00000000 08:03 1475458    /usr/lib/locale/en_US.utf8/LC_TIME
b65e7000-b66c8000 r--p 00000000 08:03 1475449    /usr/lib/locale/en_US.utf8/LC_COLLATE
b66c8000-b66c9000 r--p 00000000 08:03 1475453    /usr/lib/locale/en_US.utf8/LC_MONETARY
b66c9000-b6708000 r--p 00000000 08:03 1475450    /usr/lib/locale/en_US.utf8/LC_CTYPE
b6708000-b670c000 rw-p b6708000 00:00 0 
b670c000-b6721000 r-xp 00000000 08:03 1443084    /usr/lib/libICE.so.6.3.0
b6721000-b6722000 rw-p 00014000 08:03 1443084    /usr/lib/libICE.so.6.3.0
b6722000-b6724000 rw-p b6722000 00:00 0 
b6724000-b6728000 r-xp 00000000 08:03 1443131    /usr/lib/libXdmcp.so.6.0.0
b6728000-b6729000 rw-p 00003000 08:03 1443131    /usr/lib/libXdmcp.so.6.0.0
b6729000-b672a000 rw-p b6729000 00:00 0 
b672a000-b677b000 r-xp 00000000 08:03 1443908    /usr/lib/libtiff.so.4.2.1
b677b000-b677d000 rw-p 00050000 08:03 1443908    /usr/lib/libtiff.so.4.2.1
b677d000-b679c000 r-xp 00000000 08:03 1443650    /usr/lib/libjpeg.so.62.0.0
b679c000-b679d000 rw-p 0001e000 08:03 1443650    /usr/lib/libjpeg.so.62.0.0
b679d000-b67a4000 r-xp 00000000 08:03 1443108    /usr/lib/libSM.so.6.0.0
b67a4000-b67a5000 rw-p 00006000 08:03 1443108    /usr/lib/libSM.so.6.0.0
b67a5000-b67ac000 r-xp 00000000 08:03 1779103    /lib/tls/i686/cmov/librt-2.7.so
b67ac000-b67ae000 rw-p 00006000 08:03 1779103    /lib/tls/i686/cmov/librt-2.7.so
b67ae000-b67af000 rw-p b67ae000 00:00 0 
b67af000-b67b3000 r-xp 00000000 08:03 1442357    /usr/lib/libgthread-2.0.so.0.1600.3
b67b3000-b67b4000 rw-p 00003000 08:03 1442357    /usr/lib/libgthread-2.0.so.0.1600.3
b67b4000-b67da000 r-xp 00000000 08:03 1443779    /usr/lib/libpcre.so.3.12.1
b67da000-b67db000 rw-p 00026000 08:03 1443779    /usr/lib/libpcre.so.3.12.1
b67db000-b67f2000 r-xp 00000000 08:03 1761405    /lib/libselinux.so.1
b67f2000-b67f4000 rw-p 00016000 08:03 1761405    /lib/libselinux.so.1
b67f4000-b680b000 r-xp 00000000 08:03 1443961    /usr/lib/libxcb.so.1.0.0
b680b000-b680c000 rw-p 00016000 08:03 1443961    /usr/lib/libxcb.so.1.0.0
b680c000-b680d000 r-xp 00000000 08:03 1443959    /usr/lib/libxcb-xlib.so.0.0.0
b680d000-b680e000 rw-p 00000000 08:03 1443959    /usr/lib/libxcb-xlib.so.0.0.0
b680e000-b680f000 rw-p b680e000 00:00 0 
b680f000-b682e000 r-xp 00000000 08:03 1443357    /usr/lib/libexpat.so.1.5.2
b682e000-b6830000 rw-p 0001e000 08:03 1443357    /usr/lib/libexpat.so.1.5.2
b6830000-b6858000 r-xp 00000000 08:03 1443789    /usr/lib/libpixman-1.so.0.10.0
b6858000-b6859000 rw-p 00027000 08:03 1443789    /usr/lib/libpixman-1.so.0.10.0
b6859000-b685b000 r-xp 00000000 08:03 1443120   Aborted
```

Any one have any ideas? I am quite stuck on this problem, and don't have a clue what to do now.

---

### Post by ibuclaw on 2008-06-04
What is wrong with just installing it the standard way?

[Grab the Ubuntu deb.tar.gz package from the main site here.]("http://www.codeblocks.org/downloads/5") Extract the tarball, and open up a terminal to the location and type in
```
sudo dpkg -i *.deb
```

Works just fine for me.

Regards
Iain

---

### Post by zorocke on 2008-06-04
Nope, sorry.
I uninstalled and tried it your way, but still the same result..

---

### Post by ibuclaw on 2008-06-04
OK then. Lets walk through the standards packages for compiling.
Do you have build-essential installed?

Also, the last package on your list is in the repos, might as well check that too.
```
sudo apt-get install build-essential libpixman-1-dev
```

[EDIT]
And check apt for any lingering dependancies that need installing
```
sudo apt-get install -f
```

Regards
Iain

---

### Post by zorocke on 2008-06-04
Nope, both commands returned saying everything is all ready up to date.

---

### Post by ibuclaw on 2008-06-04
Hmmm...

Ok, this is getting curious.
> 
*** glibc detected *** codeblocks: double free or corruption (out): 0x08960450 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb68f5a85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb68f94f0]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb78388b1]
/usr/local/lib/libwx_gtk2u_core-2.8.so.0 (_ZN8wxWindow9DoSetSizeEiiiii+0x5db)[0xb6e02ddb]
/usr/local/lib/libwx_gtk2u_core-2.8.so.0(_ZN14wxBitmapButton10SetDefaultEv+0x7d)[0xb6e3f0dd]
codeblocks[0x80b13d4]
codeblocks[0x80a8370]
codeblocks[0x80a8fba]
codeblocks[0x806e255]
codeblocks[0x806f061]
codeblocks(_ZN12wxAppConsole10CallOnInitEv+0x11)[0x8070131]
/usr/local/lib/libwx_baseu-2.8.so.0(_Z7wxEntryRiPPw+0x40)[0xb6ba0f70]
/usr/local/lib/libwx_baseu-2.8.so.0(_Z7wxEntryRiPPc+0x37)[0xb6ba1047]
codeblocks[0x806b1c0]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb68a0450]
codeblocks(_ZN9wxAppBase8MainLoopEv+0x4d)[0x806aee1]

Just running through the backtrace log, seeing what I can link to my system.

Hmm... Seems odd that you have your "libwx_baseu-2.8.so.0" and "libwx_gtk2u_core-2.8.so.0" in your local lib folders. Did you compile them from source yourself?

Anyhow, try this:
```
sudo apt-get install libwxgtk2.8-0-dev libwxbase2.8-0-dev libc6-dev libglib2.0-0-dev
```
and reboot your system, just incase.

Regards
Iain

---

### Post by zorocke on 2008-06-05
Fixed.

Thanks for all the help on this, but it turned out that I had tried to compile wxwidgets from source a while back, which seemed to have been messing it up because i uninstalled that compile. Everything works good now. :)

---

### Post by zorocke on 2008-06-06
Never mind, the problem seems to be back for some very odd reason. I did an update this morning with the update manager, but I did not look at all was being updates so the problem might light there? I've tried rebooting, and that provided no luck either. 

Any one have any ideas?

Also is there I can like remove absolutely everything dealing with Code::Blocks or WxWidgets, and try starting over? Like because in the past i have compiled from source, and used deb. So it might be possible that some things are duplicates and what not. This might even be causing the problem, but i don't know.

---

### Post by pedro_orange on 2008-06-06
sudo apt-get remove package-name

Or you can use Synaptic.

---

### Post by zorocke on 2008-06-06
I've been using that. I have been trying to remove wx files with commands like: 
```
sudo apt-get remove wx2.*
```
Which gives me information like:
```
Note, selecting wx2.6-doc for regex 'wx2.*'
Note, selecting wx2.8-examples for regex 'wx2.*'
Note, selecting wx2.6-common for regex 'wx2.*'
Note, selecting wx2.6-headers for regex 'wx2.*'
Note, selecting wx2.5-i18n for regex 'wx2.*'
Note, selecting wx2.6-examples for regex 'wx2.*'
Note, selecting wx2.4-headers for regex 'wx2.*'
Note, selecting wx2.4-doc for regex 'wx2.*'
Note, selecting wx2.8-doc for regex 'wx2.*'
Note, selecting wx2.4-examples for regex 'wx2.*'
Note, selecting wx2.8-i18n for regex 'wx2.*'
Note, selecting wx2.6-i18n for regex 'wx2.*'
Note, selecting wx2.4-i18n for regex 'wx2.*'

```

But then only says 
```

The following packages will be REMOVED:
  wx2.8-headers

``` But are the 2.6 versions not being removed?

---

### Post by pedro_orange on 2008-06-06
I'm not 100% sure mate.

I'd feel safer deleting from the GUI like synaptic or add/remove or apt-get remove.

I don't want to tell you to rm stuff incase I send you in the wrong direction.
I would try removing the 2.8 and then seeing if 2.6 was still hanging around or not. (I would imagine 2.6 would have been removed when you installed 2.8 )

Also make sure you're only removing what you want to. Wildcards can be dangerous!

---


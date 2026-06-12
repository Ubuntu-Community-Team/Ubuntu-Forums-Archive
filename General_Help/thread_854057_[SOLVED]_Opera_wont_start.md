---
title: "[SOLVED] Opera wont start"
date: 2008-07-09
forum: General Help
---

### Post by The Midnight Coder on 2008-07-09
Opera was working until a while back and I dont know whay it wont open again. I tried to start it from the terminal and this is the output I got:

> 
fabian23@fabian23-desktop:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
*** glibc detected *** /usr/lib/opera/9.50/opera: double free or corruption (!prev): 0x0909c6c8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb73efa85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb73f34f0]
/usr/lib/opera/9.50/opera[0x8808037]
/usr/lib/opera/9.50/opera[0x8808ac5]
/usr/lib/opera/9.50/opera[0x88239bc]
/usr/lib/opera/9.50/opera[0x881f7a6]
/usr/lib/opera/9.50/opera[0x8819f9b]
/usr/lib/opera/9.50/opera[0x84ad2fd]
/usr/lib/opera/9.50/opera[0x82ee828]
/usr/lib/opera/9.50/opera[0x82eea52]
/usr/lib/opera/9.50/opera[0x81b35ff]
/usr/lib/opera/9.50/opera[0x8062e7d]
/usr/lib/opera/9.50/opera(_ZN7QWidget10setEnabledEb+0x20f)[0x805e587]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb739a450]
/usr/lib/opera/9.50/opera(_ZN7QWidget25setPaletteBackgroundColorERK6QColor+0xc9)[0x805e471]
======= Memory map: ========
08048000-08ac5000 r-xp 00000000 08:05 209683     /usr/lib/opera/9.50/opera
08ac5000-08b18000 rw-p 00a7d000 08:05 209683     /usr/lib/opera/9.50/opera
08b18000-090e3000 rw-p 08b18000 00:00 0          [heap]
b6f00000-b6f21000 rw-p b6f00000 00:00 0 
b6f21000-b7000000 ---p b6f21000 00:00 0 
b7043000-b704a000 rw-p b7043000 00:00 0 
b704a000-b705b000 r--p 00000000 08:05 261216     /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf
b705b000-b705c000 r-xp 00000000 08:05 209681     /usr/lib/opera/9.50/missingsyms.so
b705c000-b705d000 rw-p 00000000 08:05 209681     /usr/lib/opera/9.50/missingsyms.so
b705d000-b7064000 r--s 00000000 08:05 147594     /usr/lib/gconv/gconv-modules.cache
b7064000-b706a000 r--s 00000000 08:05 199422     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b706a000-b706d000 r--s 00000000 08:05 199432     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b706d000-b706e000 r--s 00000000 08:05 199424     /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b706e000-b706f000 r--s 00000000 08:05 199417     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b706f000-b7072000 r--s 00000000 08:05 199423     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b7072000-b7079000 r--s 00000000 08:05 199419     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b7079000-b707c000 r--s 00000000 08:05 199429     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b707c000-b7084000 r--s 00000000 08:05 199433     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b7084000-b708c000 r--s 00000000 08:05 199413     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b708c000-b708f000 r--s 00000000 08:05 199430     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b708f000-b7096000 r--s 00000000 08:05 199427     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b7096000-b709c000 r--s 00000000 08:05 199412     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b709c000-b709e000 r--s 00000000 08:05 192265     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b709e000-b70dd000 r--p 00000000 08:05 192327     /usr/lib/locale/en_IN/LC_CTYPE
b70dd000-b71be000 r--p 00000000 08:05 192326     /usr/lib/locale/en_IN/LC_COLLATE
b71be000-b71c0000 rw-p b71be000 00:00 0 
b71c0000-b71c4000 r-xp 00000000 08:05 145488     /usr/lib/libXdmcp.so.6.0.0
b71c4000-b71c5000 rw-p 00003000 08:05 145488     /usr/lib/libXdmcp.so.6.0.0
b71c5000-b71c9000 r-xp 00000000 08:05 145494     /usr/lib/libXfixes.so.3.1.0
b71c9000-b71ca000 rw-p 00003000 08:05 145494     /usr/lib/libXfixes.so.3.1.0
b71ca000-b71cb000 rw-p b71ca000 00:00 0 
b71cb000-b71ea000 r-xp 00000000 08:05 145680     /usr/lib/libexpat.so.1.5.2
b71ea000-b71ec000 rw-p 0001e000 08:05 145680     /usr/lib/libexpat.so.1.5.2
b71ec000-b71ee000 r-xp 00000000 08:05 145477     /usr/lib/libXau.so.6.0.0
b71ee000-b71ef000 rw-p 00001000 08:05 145477     /usr/lib/libXau.so.6.0.0
b71ef000-b7206000 r-xp 00000000 08:05 146221     /usr/lib/libxcb.so.1.0.0
b7206000-b7207000 rw-p 00016000 08:05 146221     /usr/lib/libxcb.so.1.0.0
b7207000-b7208000 r-xp 00000000 08:05 146219     /usr/lib/libxcb-xlib.so.0.0.0
b7208000-b7209000 rw-pAborted
fabian23@fabian23-desktop:~$ 


Any ideas? I am currently posting this from Firefox

---

### Post by The Midnight Coder on 2008-07-10
Doesn't anybody have a solution? :(

---

### Post by zvacet on 2008-07-10
I know this is not answer to your question,but it is a solution.Export your bookmarks and contacts (to your home directory for example),delete Opera from synaptic and delete .opera folder.Install Opera 9.51.Other solution is to ask on [Opera forums.]("http://my.opera.com/community/forums/forum.dml?id=3")

---

### Post by The Midnight Coder on 2008-07-10
I had tried that but hadnt deleted .opera from my home directory. After I deleted it and reinstalled it, it works.

Also I did not need to backup anything as I use the Opera link to backup everything.

---


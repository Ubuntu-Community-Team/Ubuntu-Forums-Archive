---
title: "can you take a look at this code?"
date: 2007-09-22
forum: General Help
---

### Post by nerojrnde on 2007-09-22
i downloaded regnum tday..

like most files, i cant open this one. when i try to run the rolauncher executable i get this in the 

```

jonathan@jonathan-laptop:~$ cd /home/jonathan/Desktop
jonathan@jonathan-laptop:~/Desktop$ ./rolauncher

(rolauncher:9955): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libthinice.so: wrong ELF class: ELFCLASS64
Fontconfig warning: "/etc/fonts/conf.d/53-monospace-lcd-filter.conf", line 17: invalid constant used : legacy
*** glibc detected *** ./rolauncher: free(): invalid pointer: 0x08660460 ***
======= Backtrace: =========
/lib32/libc.so.6[0xf77858e5]
/lib32/libc.so.6(cfree+0x90)[0xf7789380]
/usr/lib32/libglib-2.0.so.0(g_free+0x31)[0xf76948c1]
./rolauncher[0x817613d]
./rolauncher[0x8070b53]
./rolauncher[0x8065a7a]
./rolauncher[0x8067ed1]
./rolauncher[0x810074e]
./rolauncher[0x805c55e]
/lib32/libc.so.6(__libc_start_main+0xe0)[0xf7731050]
./rolauncher(__gxx_personality_v0+0x3d5)[0x805c391]
======= Memory map: ========
08048000-0840e000 r-xp 00000000 08:01 12157018                           /home/jonathan/Desktop/rolauncher
0840e000-0844b000 rw-p 003c6000 08:01 12157018                           /home/jonathan/Desktop/rolauncher
0844b000-0866f000 rw-p 0844b000 00:00 0                                  [heap]
f5c00000-f5c21000 rw-p f5c00000 00:00 0 
f5c21000-f5d00000 ---p f5c21000 00:00 0 
f5df7000-f5e83000 r--p 00000000 08:01 1639542                            /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
f5e83000-f5e85000 r-xp 00000000 08:01 1902365                            /usr/lib32/pango/1.6.0/modules/pango-basic-fc.so
f5e85000-f5e86000 rw-p 00001000 08:01 1902365                            /usr/lib32/pango/1.6.0/modules/pango-basic-fc.so
f5e86000-f5e8c000 r--s 00000000 08:01 11993612                           /home/jonathan/.fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
f5e8c000-f5e8f000 r--s 00000000 08:01 11993331                           /home/jonathan/.fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
f5e8f000-f5e90000 r--s 00000000 08:01 11993330                           /home/jonathan/.fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
f5e90000-f5e92000 r--s 00000000 08:01 11993329                           /home/jonathan/.fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
f5e92000-f5e93000 r--s 00000000 08:01 11993328                           /home/jonathan/.fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
f5e93000-f5e94000 r--s 00000000 08:01 11993326                           /home/jonathan/.fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
f5e94000-f5e98000 r--s 00000000 08:01 11993327                           /home/jonathan/.fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
f5e98000-f5e99000 r--s 00000000 08:01 11993324                           /home/jonathan/.fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
f5e99000-f5e9a000 r--s 00000000 08:01 11993325                           /home/jonathan/.fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
f5e9a000-f5e9c000 r--s 00000000 08:01 11993444                           /home/jonathan/.fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
f5e9c000-f5e9f000 r--s 00000000 08:01 11993323                           /home/jonathan/.fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
f5e9f000-f5ea1000 r--s 00000000 08:01 11993321                           /home/jonathan/.fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
f5ea1000-f5ea2000 r--s 00000000 08:01 11993322                           /home/jonathan/.fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
f5ea2000-f5ea4000 r--s 00000000 08:01 11993320                           /home/jonathan/.fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
f5ea4000-f5eaa000 r--s 00000000 08:01 11993318                           /home/jonathan/.fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
f5eaa000-f5eac000 r--s 00000000 08:01 11993319                           /home/jonathan/.fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
f5eac000-f5eae000 r--s 00000000 08:01 11993317                           /home/jonathan/.fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
f5eae000-f5eb6000 r--s 00000000 08:01 11993316                           /home/jonathan/.fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
f5eb6000-f5ebc000 r--s 00000000 08:01 11993315                           /home/jonathan/.fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
f5ebc000-f5ebd000 r--s 00000000 08:01 11993313                           /home/jonathan/.fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
f5ebd000-f5ed4000 r--s 00000000 08:01 11993665                           /home/jonathan/.fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
f5ed4000-f5ed6000 r--s 00000000 08:01 11993314                           /home/jonathan/.fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
f5ed6000-f5edc000 r--s 00000000 08:01 11993311                           /home/jonathan/.fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
f5edc000-f5edf000 r--s 00000000 08:01 11993312                           /home/jonathan/.fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
f5edf000-f5ee3000 r--s 00000000 08:01 11993308                           /home/jonathan/.fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
f5ee3000-f5eea000 r--s 00000000 08:01 11993307                           /home/jonathan/.fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
f5eea000-f5eeb000 r--s 00000000 08:01 11993302                           /home/jonathan/.fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
f5eeb000-f5eec000 r--s 00000000 08:01 11993301                           /home/jonathan/.fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
f5eec000-f5eed000 r--s 00000000 08:01 11993299                           /home/jonathan/.fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
f5eed000-f5eef000 r--s 00000000 08:01 11993297                           /home/jonathan/.fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
f5eef000-f5ef2000 r--s 00000000 08:01 11993298                           /home/jonathan/.fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
f5ef2000-f5efb000 r--s 00000000 08:01 11993663                           /home/jonathan/.fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
f5efb000-f5efe000 r--s 00000000 08:01 11993296                           /home/jonathan/.fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
f5efe000-f5eff000 r--s 00000000 08:01 11993295                           /home/jonathan/.fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
f5eff000-f5f01000 r--s 00000000 08:01 11993294                           /home/jonathan/.fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
f5f01000-f5f02000 r--s 00000000 08:01 11993292                           /home/jonathan/.fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
f5f02000-f5f07000 r--s 00000000 08:01 11993289                           /home/jonathan/.fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
f5f07000-f5f0b000 r--s 00000000 08:01 11993287                           /home/jonathan/.fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
f5f0b000-f5f0d000 r--s 00000000 08:01 11993285                           /home/jonathan/.fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
f5f0d000-f5f10000 r--s 00000000 08:01 11993283                           /home/jonathan/.fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
f5f10000-f5f11000 r--s 00000000 08:01 11993280                           /home/jonathan/.fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
f5f11000-f5f12000 r--s 00000000 08:01 11993274                           /home/jonathan/.fontconfig/892f88ea27b235637f494d515247eddd-x86.cache-2
f5f12000-f5f14000 r--s 00000000 08:01 11993277                           /home/jonathan/.fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
f5f14000-f5f1a000 r--s 00000000 08:01 11993265                           /home/jonathan/.fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
f5f1a000-f5f20000 r--s 00000000 08:01 11993268                           /home/jonathan/.fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
f5f20000-f5f21000 r--s 00000000 08:01 11993267                           /home/jonathan/.fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
f5f21000-f5f29000 r--s 00000000 08:01 11993266                           /home/jonathan/.fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
f5f29000-f5f2e000 r--s 00000000 08:01 11993256                           /home/jonathan/.fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
f5f2e000-f5f32000 r--s 00000000 08:01 11993264                           /home/jonathan/.fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
f5f32000-f5f38000 r--s 00000000 08:01 11993429                           /home/jonathan/.fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
f5f38000-f5f39000 ---p f5f38000 00:00 0 
f5f39000-f6739000 rwxp f5f39000 00:00 0 
f6739000-f675a000 rw-p f6739000 00:00 0 
f675a000-f6763000 r-xp 00000000 08:01 11010126                           /lib32/libnss_files-2.6.1.so
f6763000-f6765000 rw-p 00008000 08:01 11010126                           /lib32/libnss_files-2.6.1.so
f6765000-f6779000 r-xp 00000000 08:01 11010123                           /lib32/libnsl-2.6.1.so
f6779000-f677b000 rw-p 00013000 08:01 11010123                           /lib32/libnsl-2.6.1.so
f677b000-f677d000 rw-p f677b000 00:00 0 
f677d000-f6784000 r-xp 00000000 08:01 11010124                           /lib32/libnss_compat-2.6.1.so
f6784000-f6786000 rw-p 00006000 08:01 11010124                           /lib32/libnss_compat-2.6.1.so
f6799000-f679a000 r-xp 00000000 08:01 1787567                            /usr/lib32/gconv/ISO8859-1.so
f679a000-f679c000 rw-p 00000000 08:01 1787567                            /usr/lib32/gconv/ISO8859-1.so
f679c000-f687c000 r--p 00000000 08:01 1229100                            /usr/lib/locale/en_US.utf8/LC_COLLATE
f687c000-f687e000 r-xp 00000000 08:01 1787622                            /usr/lib32/gconv/UTF-32.so
f687e000-f6880000 rw-p 00001000 08:01 1787622                            /usr/lib32/gconv/UTF-32.so
f6880000-f68bf000 r--p 00000000 08:01 1229099                            /usr/lib/locale/en_US.utf8/LC_CTYPE
f68bf000-f691d000 rw-p f68bf000 00:00 0 
f691d000-f693f000 r-xp 00000000 08:01 1165037                            /usr/lib32/libpng12.so.0.15.0
f693f000-f6940000 rw-p 00021000 08:01 1165037                            /usr/lib32/libpng12.so.0.15.0
f6940000-f69ab000 r-xp 00000000 08:01 1164647                            /usr/lib32/libfreetype.so.6.3.16
f69ab000-f69af000 rw-p 0006a000 08:01 1164647                            /usr/lib32/libfreetype.so.6.3.16
f69af000-f69dc000 r-xp 00000000 08:01 1164979                            /usr/lib32/libpangoft2-1.0.so.0.1800.1
f69dc000-f69dd000 rw-p 0002c000 08:01 1164979                            /usr/lib32/libpangoft2-1.0.so.0.1800.1
f69dd000-f69de000 rw-p f69dd000 00:00 0 
f69de000-f69e2000 r-xp 00000000 08:01 1165352                            /usr/lib32/libXdmcp.so.6.0.0
f69e2000-f69e3000 rw-p 00003000 08:01 1165352                            /usr/lib32/libXdmcp.so.6.0.0
f69e3000-f69f8000 r-xp 00000000 08:01 1164890                            /usr/lib32/libICE.so.6.3.0
f69f8000-f69fa000 rw-p 00014000 08:01 1164890                            /usr/lib32/libICE.so.6.3.0
f69fa000-f69fb000 rw-p f69fa000 00:00 0 
f69fb000-f69fd000 r-xp 00000000 08:01 1165188                            /usr/lib32/libXau.so.6.0.0
f69fd000-f69fe000 rw-p 00001000 08:01 1165188                            /usr/lib32/libXau.so.6.0.0
f69fe000-f69ff000 r-xp 00000000 08:01 1278393                            /usr/lib32/tls/libnvidia-tls.so.100.14.19
f69ff000-f6a00000 rw-p 00000000 08:01 1278393                            /usr/lib32/tls/libnvidia-tls.so.100.14.19
f6a00000-f735c000 r-xp 00000000 08:01 1165950                            /usr/lib32/libGLcore.so.100.14.19
f735c000-f7394000 rwxp 0095c000 08:01 1165950                            /usr/lib32/libGLcore.so.100.14.19
f7394000-f7398000 rwxp f7394000 00:00 0 
f7398000-f7399000 rw-p f7398000 00:00 0 
f7399000-f73a1000 r-xp 00000000 08:01 1165262                            /usr/lib32/libXcursor.so.1.0.2
f73a1000-f73a2000 rw-p 00007000 08:01 1165262                            /usr/lib32/libXcursor.so.1.0.2
f73a2000-f73a7000 r-xp 00000000 08:01 1165464                            /usr/lib32/libXrandr.so.2.1.0
f73a7000-f73a8000 rw-p 00005000 08:01 1165464                            /usr/lib32/libXrandr.so.2.1.0
f73a8000-f73af000 r-xp 00000000 08:01 1165395                            /usr/lib32/libXi.so.6.0.0
f73af000-f73b0000 rw-p 00006000 08:01 1165395                            /usr/lib32/libXi.so.6.0.0
f73b0000-f73b7000 r-xp 00000000 08:01 1165471                            /usr/lib32/libXrender.so.1.3.0
f73b7000-f73b8000 rw-p 00006000 08:01 1165471                            /usr/lib32/libXrender.so.1.3.0
f73b8000-f73db000 r-xp 00000000 08:01 1164646                            /usr/lib32/libfontconfig.so.1.2.0
f73db000-f73e3000 rw-p 00023000 08:01 1164646                            /usr/lib32/libfontconfig.so.1.2.0
f73e3000-f73e4000 rw-p f73e3000 00:00 0 
f73e4000-f7458000 r-xp 00000000 08:01 1164485                            /usr/lib32/libcairo.so.2.11.5
f7458000-f745a000 rw-p 00074000 08:01 1164485                            /usr/lib32/libcairo.so.2.11.5
f745a000-f745d000 r-xp 00000000 08:01 1164695                            /usr/lib32/libgmodule-2.0.so.0.1400.0
f745d000-f745e000 rw-p 00002000 08:01 1164695                            /usr/lib32/libgmodule-2.0.so.0.1400.0
f745e000-f7477000 r-xp 00000000 08:01 1164476                            /usr/lib32/libatk-1.0.so.0.1915.1
f7477000-f7479000 rw-p 00018000 08:01 1164476                            /usr/lib32/libatk-1.0.so.0.1915.1
f7479000-f747d000 r-xp 00000000 08:01 1165378                            /usr/lib32/libXfixes.so.3.1.0
f747d000-f747e000 rw-p 00003000 08:01 1165378                            /usr/lib32/libXfixes.so.3.1.0
f747e000-f7480000 r-xp 00000000 08:01 1165337                            /usr/lib32/libXdamage.so.1.1.0
f7480000-f7481000 rw-p 00001000 08:01 1165337                            /usr/lib32/libXdamage.so.1.1.0
f7481000-f7482000 rw-p f7481000 00:00 0 
f7482000-f7484000 r-xp 00000000 08:01 1165224                            /usr/lib32/libXcomposite.so.1.0.0
f7484000-f7485000 rw-p 00001000 08:01 1165224                            /usr/lib32/libXcomposite.so.1.0.0
f7485000-f748d000 r-xp 00000000 08:01 1164974                            /usr/lib32/libpangocairo-1.0.so.0.1800.1
f748d000-f748e000 rw-p 00007000 08:01 1164974                            /usr/lib32/libpangocairo-1.0.so.0.1800.1
f748e000-f7495000 r-xp 00000000 08:01 11010133                           /lib32/librt-2.6.1.so
f7495000-f7497000 rw-p 00006000 08:01 11010133                           /lib32/librt-2.6.1.so
f7497000-f74b5000 r-xp 00000000 08:01 1164645                            /usr/lib32/libexpat.so.1.0.0
f74b5000-f74b7000 rw-p 0001e000 08:01 1164645                            /usr/lib32/libexpat.so.1.0.0
f74b7000-f74cb000 r-xp 00000000 08:01 1163756                            /usr/lib32/libz.so.1.2.3.3
f74cb000-f74cc000 rw-p 00013000 08:01 1163756                            /usr/lib32/libz.so.1.2.3.3
f74cc000-f74cd000 rw-p f74cc000 00:00 0 
f74cd000-f74d4000 r-xp 00000000 08:01 1165128                            /usr/lib32/libSM.so.6.0.0
f74d4000-f74d5000 rw-p 00006000 08:01 1165128                            /usr/lib32/libSM.so.6.0.0
f74d5000-f74d7000 r-xp 00000000 08:01 1165396                            /usr/lib32/libXinerama.so.1.0.0
f74d7000-f74d8000 rw-p 00001000 08:01 1165396                            /usr/lib32/libXinerama.so.1.0.0
f74d8000-f74da000 r-xp 00000000 08:01 11010120                           /lib32/libdl-2.6.1.so
f74da000-f74dc000 rw-p 00001000 08:01 11010120                           /lib32/libdl-2.6.1.so
f74dc000-f7516000 r-xp 00000000 08:01 1164697                            /usr/lib32/libgobject-2.0.so.0.1400.0
f7516000-f7517000 rw-p 0003a000 08:01 1164697                            /usr/lib32/libgobject-2.0.so.0.1400.0
f7517000-f7604000 r-xp 00000000 08:01 1165187                            /usr/lib32/libX11.so.6.2.0
f7604000-f7608000 rw-p 000ed000 08:01 1165187                            /usr/lib32/libX11.so.6.2.0
f7608000-f7643000 r-xp 00000000 08:01 1164973                            /usr/lib32/libpango-1.0.so.0.1800.1
f7643000-f7645000 rw-p 0003b000 08:01 1164973                            /usr/lib32/libpango-1.0.so.0.1800.1
f7645000-f7646000 rw-p f7645000 00:00 0 
f7646000-f765d000 r-xp 00000000 08:01 1164887                            /usr/lib32/libgdk_pixbuf-2.0.so.0.1106.0
f765d000-f765e000 rw-p 00016000 08:01 1164887                            /usr/lib32/libgdk_pixbuf-2.0.so.0.1106.0
f765e000-f771a000 r-xp 00000000 08:01 1164694                            /usr/lib32/libglib-2.0.so.0.1400.0
f771a000-f771b000 rw-p 000bc000 08:01 1164694                            /usr/lib32/libglib-2.0.so.0.1400.0
f771b000-f785f000 r-xp 00000000 08:01 11010117                           /lib32/libc-2.6.1.so
f785f000-f7860000 r--p 00143000 08:01 11010117                           /lib32/libc-2.6.1.so
f7860000-f7862000 rw-p 00144000 08:01 11010117                           /lib32/libc-2.6.1.so
f7862000-f7865000 rw-p f7862000 00:00 0 
f7865000-f786f000 r-xp 00000000 08:01 1164451                            /usr/lib32/libgcc_s.so.1
f786f000-f7870000 rw-p 0000a000 08:01 1164451                            /usr/lib32/libgcc_s.so.1
f7870000-f7893000 r-xp 00000000 08:01 11010121                           /lib32/libm-2.6.1.so
f7893000-f7895000 rw-p 00023000 08:01 11010121                           /lib32/libm-2.6.1.so
f7895000-f797d000 r-xp 00000000 08:01 1163977                            /usr/lib32/libstdc++.so.6.0.9
f797d000-f7980000 r--p 000e8000 08:01 1163977                            /usr/lib32/libstdc++.so.6.0.9
f7980000-f7982000 rw-p 000eb000 08:01 1163977                            /usr/lib32/libstdc++.so.6.0.9
f7982000-f7989000 rw-p f7982000 00:00 0 
f7989000-f79d6000 r-xp 00000000 08:01 1165480                            /usr/lib32/libXt.so.6.0.0
f79d6000-f79da000 rw-p 0004c000 08:01 1165480                            /usr/lib32/libXt.so.6.0.0
f79da000-f79e7000 r-xp 00000000 08:01 1165366                            /usr/lib32/libXext.so.6.4.0
f79e7000-f79e8000 rw-p 0000d000 08:01 1165366                            /usr/lib32/libXext.so.6.4.0
f79e8000-f79ec000 r-xp 00000000 08:01 1165868                            /usr/lib32/libXxf86vm.so.1.0.0
f79ec000-f79ed000 rw-p 00003000 08:01 1165868                            /usr/lib32/libXxf86vm.so.1.0.0
f79ed000-f7a67000 r-xp 00000000 08:01 1165942                            /usr/lib32/libGL.so.100.14.19
f7a67000-f7a82000 rwxp 00079000 08:01 1165942                            /usr/lib32/libGL.so.100.14.19
f7a82000-f7a83000 rwxp f7a82000 00:00 0 
f7a83000-f7b10000 r-xp 00000000 08:01 1164867                            /usr/lib32/libgdk-x11-2.0.so.0.1106.0
f7b10000-f7b13000 rw-p 0008c000 08:01 1164867                            /usr/lib32/libgdk-x11-2.0.so.0.1106.0
f7b13000-f7ec5000 r-xp 00000000 08:01 1164889                            /usr/lib32/libgtk-x11-2.0.so.0.1106.0
f7ec5000-f7ecb000 rw-p 003b1000 08:01 1164889                            /usr/lib32/libgtk-x11-2.0.so.0.1106.0
f7ecb000-f7ecd000 rw-p f7ecb000 00:00 0 
f7ecd000-f7ed1000 r-xp 00000000 08:01 1164717                            /usr/lib32/libgthread-2.0.so.0.1400.0
f7ed1000-f7ed2000 rw-p 00003000 08:01 1164717                            /usr/lib32/libgthread-2.0.so.0.1400.0
f7ed2000-f7ee6000 r-xp 00000000 08:01 11010131                           /lib32/libpthread-2.6.1.so
f7ee6000-f7ee8000 rw-p 00013000 08:01 11010131                           /lib32/libpthread-2.6.1.so
f7ee8000-f7eea000 rw-p f7ee8000 00:00 0 
f7eea000-f7ef2000 r-xp 00000000 08:01 11010128                           /lib32/libnss_nis-2.6.1.so
f7ef2000-f7ef4000 rw-p 00007000 08:01 11010128                           /lib32/libnss_nis-2.6.1.so
f7ef4000-f7ef5000 r--p 00000000 08:01 1229859                            /usr/lib/locale/en_US.utf8/LC_NUMERIC
f7ef5000-f7ef6000 r--p 00000000 08:01 1229154                            /usr/lib/locale/en_US.utf8/LC_TIME
f7ef6000-f7ef7000 r--p 00000000 08:01 1229155                            /usr/lib/locale/en_US.utf8/LC_MONETARY
f7ef7000-f7ef8000 r--p 00000000 08:01 1245204                            /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
f7ef8000-f7ef9000 r--p 00000000 08:01 1229915                            /usr/lib/locale/en_US.utf8/LC_PAPER
f7ef9000-f7efa000 r--p 00000000 08:01 1229913                            /usr/lib/locale/en_US.utf8/LC_NAME
f7efa000-f7efb000 r--p 00000000 08:01 1229156                            /usr/lib/locale/en_US.utf8/LC_ADDRESS
f7efb000-f7efc000 r--p 00000000 08:01 1229157                            /usr/lib/locale/en_US.utf8/LC_TELEPHONE
f7efc000-f7efd000 r--p 00000000 08:01 1229159                            /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
f7efd000-f7efe000 r--p 00000000 08:01 1229160                            /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
f7efe000-f7f00000 rwxp 00000000 00:0e 2823                               /dev/zero
f7f00000-f7f02000 rw-p f7f00000 00:00 0 
f7f02000-f7f1e000 r-xp 00000000 08:01 11010114                           /lib32/ld-2.6.1.so
f7f1e000-f7f20000 rw-p 0001b000 08:01 11010114                           /lib32/ld-2.6.1.so
fffa9000-fffb1000 rwxp fffa9000 00:00 0                                  [stack]
ffffe000-fffff000 r-xp ffffe000 00:00 0                                  [vdso]
Aborted (core dumped)
jonathan@jonathan-laptop:~/Desktop$ 


```

sorry i know its long. thanks!

---

### Post by Maestro23 on 2007-09-23
Is this it?: [http://www.regnumonline.com.ar/index.php?l=1&sec=6](http://www.regnumonline.com.ar/index.php?l=1&sec=6)

If so, you d/l the linux file to your desktop.  Right-click on it to extract it.  Then double left-click it.  Should open right up.

---

### Post by _francis on 2007-09-25
after updating to gutsy tribe 5 i encountered the same error like yours

try running the game with  MALLOC_CHECK_=0 ./rolauncher
it worked for me

my GPU
geforce 7800 gs

---


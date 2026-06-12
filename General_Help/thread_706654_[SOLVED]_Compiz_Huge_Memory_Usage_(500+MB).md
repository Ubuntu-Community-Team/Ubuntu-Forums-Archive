---
title: "[SOLVED] Compiz Huge Memory Usage (500+MB)"
date: 2008-02-24
forum: General Help
---

### Post by phibit on 2008-02-24
I run Ubuntu Gutsy x86_64 on my HP laptop with the following specs:

AMD Turion X2 64 bit
1 GB RAM
Nvidia Geforce 6150 (128 MB shared mem)

Generally, Compiz runs fine, but when I have many apps open (about 6 or 7), the memory usage of compiz shoots up to 600+ MB of my RAM!!

Obviously, this leads to extremely sluggish response, and I'm forced to revert to metacity, but I lose all the functionality of Compiz Window Management.

Does anybody else have this problem, or know a solution?!

---

### Post by Joeb454 on 2008-02-24
you could try running ```
killall compiz.real
``` from a terminal (I think that's the name of the compiz process)

But you would need to know how to start it again from the terminal

---

### Post by phibit on 2008-02-25
Oh yeah that absolutely fixes the problem, but once again that's not really what I'm looking for. I know I could just turn off compiz and use metacity, but I really like the window management functionality that compiz provides (desktop wall, scale windows, application switcher etc..).

So I'm trying to find a way to keep using Compiz, just cut down on its memory usage... My settings for compiz are pretty minimal, just a few plugins are enabled (the main ones to manage windows). Still, I can catch it sucking back over 67% of my 1GB ram.

Any suggestions? Perhaps some settings tweaks?

---

### Post by jonny84 on 2008-02-25
I have your same problem with a GeForce Go 6200 256 MB Turbo Cache.

Someone nows how to resolve?

---

### Post by phibit on 2008-03-02
Alright I found that using minimalist compiz settings helped alleviate this problem, so I cut down to only the basics, and removed all mipmap drawing... Less pretty but also less memory. :(
Just using: Move, resize, scale windows, desktop plane, expo and a few others..

---

### Post by phibit on 2008-03-05
Okay it may be moot to post this, but I feel the need to PROVE how ridiculous this compiz memory problem is.

So, attached is a screenshot of compiz occupying the most part of my RAM. Be amazed:)

---

### Post by SloYerRoll on 2008-03-05
As the saying goes. You can never be too skinny, too rich or have enough RAM. 

Time to raid the piggy bank and get some more! Memory in general is at an all time low. There's not many excuses to not upgrade IMHO. 

I'm a recent windows convert, so my stance on RAM may be a bit extreme to yours. But when I run Photoshop, Illustrator and other RAM intensive apps. The 4GB I have can get up to the 90% range. My machine would die if it only ran 1GB.

It also depends on the speed of your RAM as well. 1GB of fast RAM is as good as 2GB of off the shelf RAM.

---

### Post by phibit on 2008-03-05
Well said. I do agree that RAM is cheap as ever. I do have a cool 2 GB of overclocked RAM on my desktop PC, but this problem is with my HP Laptop.

It's just a bit more inconvenient to upgrade the RAM on this machine, and more expensive also.

And while it's all well and good to say "buy more powerful equipment", that doesn't seem to be "the linux way". Linux users tend to be cheap (conservative with their cash, I might say).

My initial question was if there were some settings tweaks I could change in the compiz-config-settings-manager or elsewhere that would reduce the memory footprint.
Upon some research it appears that Compiz has significant memory leaks, and restarting compiz using
```
compiz --replace
```
every so often can temporarily alleviate the problem.

Still, this solution isn't as elegant as I would like, but it will have to do.


Cheers,
phibit.


PS: many people appreciate the fact that Linux can often run faster and better on systems with less RAM and CPU power, and I've witnessed compiz running on machines only 64 MB of RAM (practicially no RAM at all by today's standards).

---

### Post by SloYerRoll on 2008-03-05
> **phibit said:**
> 
PS: many people appreciate the fact that Linux can often run faster and better on systems with less RAM and CPU power, and I've witnessed compiz running on machines only 64 MB of RAM (practicially no RAM at all by today's standards).That's why I made my windows disclaimer. I figured I get flamed if I didn't and was saying you needed tons of RAM..:)

---

### Post by Zwack on 2008-03-05
> **SloYerRoll said:**
> That's why I made my windows disclaimer. I figured I get flamed if I didn't and was saying you needed tons of RAM..:)

You young whippersnappers...   :-)

I remember running Linux on a dual boot system with a 40Mb hard drive and a whole 2Mb of RAM.  

Of course it was text only, and a kernel compile took several hours, but... :-D

z.

---

### Post by Crafty Kisses on 2008-03-05
> **Zwack said:**
> You young whippersnappers...   :-)

I remember running Linux on a dual boot system with a 40Mb hard drive and a whole 2Mb of RAM.  

Of course it was text only, and a kernel compile took several hours, but... :-D

z.

:lolflag:

---

### Post by chrisccoulson on 2008-03-05
Are you using the nvidia-glx-new drivers from the repository? There is a known memory leak with these drivers. See [bug 151168]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/151168")

When compiz.real is running at several hunder MBs, what is the output of:
```
cat /proc/`pidof compiz.real`/maps
```

---

### Post by phibit on 2008-03-06
This is my output for
```
cat /proc/`pidof compiz.real`/maps
```
with compiz using 450+ MB of RAM:
```
00400000-0043b000 r-xp 00000000 08:04 948800                             /usr/bin/compiz.real
0063a000-0063c000 rw-p 0003a000 08:04 948800                             /usr/bin/compiz.real
0063c000-05855000 rw-p 0063c000 00:00 0                                  [heap]
40002000-40004000 rwxp 00000000 00:0e 2986                               /dev/zero
40004000-40078000 rw-p 00000000 00:0e 2986                               /dev/zero
2aaaaaaab000-2aaaaab1f000 rw-p 2aaaaaaab000 00:00 0 
2aaaaab1f000-2aaaaab3d000 rw-s 00000000 00:09 0                          /SYSV00000000 (deleted)
2aaaaab3d000-2aaaaaf25000 rw-s d0000000 00:0e 20800                      /dev/nvidia0
2aaaaaf25000-2aaaaaf26000 rw-s c2001000 00:0e 20800                      /dev/nvidia0
2aaaaaf26000-2aaaaaf67000 rw-p 2aaaaaf26000 00:00 0 
2aaaaaf67000-2aaaab0a9000 rw-s 22238000 00:0e 20800                      /dev/nvidia0
2aaaab0a9000-2aaaab0aa000 rw-s c2c02000 00:0e 20800                      /dev/nvidia0
2aaaab0aa000-2aaaab0ab000 rw-s 2237e000 00:0e 20800                      /dev/nvidia0
2aaaab0ab000-2aaaab0ac000 rw-s 2237f000 00:0e 20800                      /dev/nvidia0
2aaaab0ac000-2aaaab0ad000 rw-s d3b07000 00:0e 20800                      /dev/nvidia0
2aaaab0ad000-2aaaab0b1000 rw-s 22383000 00:0e 20800                      /dev/nvidia0
2aaaab0b1000-2aaaab1b1000 rw-s 2221f000 00:0e 20800                      /dev/nvidia0
2aaaab1b1000-2aaaab1f1000 rw-s d3ac6000 00:0e 20800                      /dev/nvidia0
2aaaab1f1000-2aaaab1f2000 rw-s 00000000 00:09 229377                     /SYSV00000000 (deleted)
2aaaab1f2000-2aaaab1f3000 rw-s 00000000 00:09 262146                     /SYSV00000000 (deleted)
2aaaab1f3000-2aaaab1f6000 r-xp 00000000 08:04 963234                     /usr/lib/compiz/libccp.so
2aaaab1f6000-2aaaab3f5000 ---p 00003000 08:04 963234                     /usr/lib/compiz/libccp.so
2aaaab3f5000-2aaaab3f6000 rw-p 00002000 08:04 963234                     /usr/lib/compiz/libccp.so
2aaaab3f6000-2aaaab3f7000 rw-s 00000000 00:09 1212444                    /SYSV00000000 (deleted)
2aaaab3f7000-2aaaab3f8000 rw-s 00000000 00:09 1179677                    /SYSV00000000 (deleted)
2aaaab3f8000-2aaaab3f9000 rw-s 00000000 00:09 1245214                    /SYSV00000000 (deleted)
2aaaab3f9000-2aaaab3fa000 rw-s 00000000 00:09 1277983                    /SYSV00000000 (deleted)
2aaaab3fa000-2aaaab3fb000 rw-s 00000000 00:09 1540119                    /SYSV00000000 (deleted)
2aaaab3ff000-2aaaab400000 rw-s 00000000 00:09 1703974                    /SYSV00000000 (deleted)
2aaaab400000-2aaaab407000 r--s 00000000 08:04 963221                     /usr/lib/gconv/gconv-modules.cache
2aaaab407000-2aaaab40a000 r--s 00000000 08:04 1387680                    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86-64.cache-2
2aaaab40a000-2aaaab40b000 rw-s 00000000 00:09 6389794                    /SYSV00000000 (deleted)
2aaaab40b000-2aaaab422000 r-xp 00000000 08:04 947392                     /usr/lib/libcompizconfig.so.0.0.0
2aaaab422000-2aaaab622000 ---p 00017000 08:04 947392                     /usr/lib/libcompizconfig.so.0.0.0
2aaaab622000-2aaaab623000 rw-p 00017000 08:04 947392                     /usr/lib/libcompizconfig.so.0.0.0
2aaaab623000-2aaaab624000 rw-p 2aaaab623000 00:00 0 
2aaaab624000-2aaaab62f000 r-xp 00000000 08:04 1306308                    /usr/lib/compizconfig/backends/libgconf.so
2aaaab62f000-2aaaab82f000 ---p 0000b000 08:04 1306308                    /usr/lib/compizconfig/backends/libgconf.so
2aaaab82f000-2aaaab831000 rw-p 0000b000 08:04 1306308                    /usr/lib/compizconfig/backends/libgconf.so
2aaaab831000-2aaaab832000 rw-s 00000000 00:09 458760                     /SYSV00000000 (deleted)
2aaaab832000-2aaaab833000 rw-s 00000000 00:09 491529                     /SYSV00000000 (deleted)
2aaaab833000-2aaaab834000 rw-s 00000000 00:09 524298                     /SYSV00000000 (deleted)
2aaaab834000-2aaaab835000 rw-s 00000000 00:09 557067                     /SYSV00000000 (deleted)
2aaaab835000-2aaaab836000 rw-s 00000000 00:09 589836                     /SYSV00000000 (deleted)
2aaaab836000-2aaaab837000 rw-s 00000000 00:09 622605                     /SYSV00000000 (deleted)
2aaaab838000-2aaaab839000 rw-s 00000000 00:09 688143                     /SYSV00000000 (deleted)
2aaaab839000-2aaaab83e000 r--s 00000000 08:04 1387681                    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86-64.cache-2
2aaaab83e000-2aaaab840000 r--s 00000000 08:04 1387682                    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86-64.cache-2
2aaaab840000-2aaaab841000 rw-s 00000000 00:09 6455338                    /SYSV00000000 (deleted)
2aaaab841000-2aaaab842000 rw-s 00000000 00:09 5832774                    /SYSV00000000 (deleted)
2aaaab843000-2aaaab844000 rw-s 00000000 00:09 3211327                    /SYSV00000000 (deleted)
2aaaab844000-2aaaab845000 rw-s 00000000 00:09 5898314                    /SYSV00000000 (deleted)
2aaaab845000-2aaaab846000 rw-s 00000000 00:09 6520886                    /SYSV00000000 (deleted)
2aaaab846000-2aaaab87f000 r-xp 00000000 08:04 946907                     /usr/lib/libgconf-2.so.4.1.2
2aaaab87f000-2aaaaba7f000 ---p 00039000 08:04 946907                     /usr/lib/libgconf-2.so.4.1.2
2aaaaba7f000-2aaaaba84000 rw-p 00039000 08:04 946907                     /usr/lib/libgconf-2.so.4.1.2
2aaaaba84000-2aaaabae2000 r-xp 00000000 08:04 948532                     /usr/lib/libORBit-2.so.0.1.0
2aaaabae2000-2aaaabce1000 ---p 0005e000 08:04 948532                     /usr/lib/libORBit-2.so.0.1.0
2aaaabce1000-2aaaabcf4000 rw-p 0005d000 08:04 948532                     /usr/lib/libORBit-2.so.0.1.0
2aaaabcf4000-2aaaabcf8000 r-xp 00000000 08:04 947971                     /usr/lib/libgthread-2.0.so.0.1400.1
2aaaabcf8000-2aaaabef7000 ---p 00004000 08:04 947971                     /usr/lib/libgthread-2.0.so.0.1400.1
2aaaabef7000-2aaaabef8000 rw-p 00003000 08:04 947971                     /usr/lib/libgthread-2.0.so.0.1400.1
2aaaabef8000-2aaaabf00000 r-xp 00000000 08:04 2105466                    /lib/librt-2.6.1.so
2aaaabf00000-2aaaac0ff000 ---p 00008000 08:04 2105466                    /lib/librt-2.6.1.so
2aaaac0ff000-2aaaac101000 rw-p 00007000 08:04 2105466                    /lib/librt-2.6.1.so
2aaaac101000-2aaaac143000 r-xp 00000000 08:04 947958                     /usr/lib/libgobject-2.0.so.0.1400.1
2aaaac143000-2aaaac343000 ---p 00042000 08:04 947958                     /usr/lib/libgobject-2.0.so.0.1400.1
2aaaac343000-2aaaac345000 rw-p 00042000 08:04 947958                     /usr/lib/libgobject-2.0.so.0.1400.1
2aaaac345000-2aaaac411000 r-xp 00000000 08:04 947901                     /usr/lib/libglib-2.0.so.0.1400.1
2aaaac411000-2aaaac610000 ---p 000cc000 08:04 947901                     /usr/lib/libglib-2.0.so.0.1400.1
2aaaac610000-2aaaac611000 rw-p 000cb000 08:04 947901                     /usr/lib/libglib-2.0.so.0.1400.1
2aaaac611000-2aaaac612000 rw-p 2aaaac611000 00:00 0 
2aaaac612000-2aaaac628000 r-xp 00000000 08:04 2105459                    /lib/libpthread-2.6.1.so
2aaaac628000-2aaaac827000 ---p 00016000 08:04 2105459                    /lib/libpthread-2.6.1.so
2aaaac827000-2aaaac829000 rw-p 00015000 08:04 2105459                    /lib/libpthread-2.6.1.so
2aaaac829000-2aaaac82d000 rw-p 2aaaac829000 00:00 0 
2aaaac82d000-2aaaac830000 r-xp 00000000 08:04 947934                     /usr/lib/libgmodule-2.0.so.0.1400.1
2aaaac830000-2aaaaca2f000 ---p 00003000 08:04 947934                     /usr/lib/libgmodule-2.0.so.0.1400.1
2aaaaca2f000-2aaaaca30000 rw-p 00002000 08:04 947934                     /usr/lib/libgmodule-2.0.so.0.1400.1
2aaaaca30000-2aaaaca38000 r-xp 00000000 08:04 2105445                    /lib/libnss_compat-2.6.1.so
2aaaaca38000-2aaaacc37000 ---p 00008000 08:04 2105445                    /lib/libnss_compat-2.6.1.so
2aaaacc37000-2aaaacc39000 rw-p 00007000 08:04 2105445                    /lib/libnss_compat-2.6.1.so
2aaaacc39000-2aaaacc4f000 r-xp 00000000 08:04 2105444                    /lib/libnsl-2.6.1.so
2aaaacc4f000-2aaaace4e000 ---p 00016000 08:04 2105444                    /lib/libnsl-2.6.1.so
2aaaace4e000-2aaaace50000 rw-p 00015000 08:04 2105444                    /lib/libnsl-2.6.1.so
2aaaace50000-2aaaace52000 rw-p 2aaaace50000 00:00 0 
2aaaace52000-2aaaace5c000 r-xp 00000000 08:04 2105449                    /lib/libnss_nis-2.6.1.so
2aaaace5c000-2aaaad05b000 ---p 0000a000 08:04 2105449                    /lib/libnss_nis-2.6.1.so
2aaaad05b000-2aaaad05d000 rw-p 00009000 08:04 2105449                    /lib/libnss_nis-2.6.1.so
2aaaad05d000-2aaaad067000 r-xp 00000000 08:04 2105447                    /lib/libnss_files-2.6.1.so
2aaaad067000-2aaaad266000 ---p 0000a000 08:04 2105447                    /lib/libnss_files-2.6.1.so
2aaaad266000-2aaaad268000 rw-p 00009000 08:04 2105447                    /lib/libnss_files-2.6.1.so
2aaaad268000-2aaaad26c000 r-xp 00000000 08:04 620174                     /usr/lib/compiz/libmove.so
2aaaad26c000-2aaaad46b000 ---p 00004000 08:04 620174                     /usr/lib/compiz/libmove.so
2aaaad46b000-2aaaad46c000 rw-p 00003000 08:04 620174                     /usr/lib/compiz/libmove.so
2aaaad46c000-2aaaad472000 r-xp 00000000 08:04 963577                     /usr/lib/compiz/libshelf.so
2aaaad472000-2aaaad671000 ---p 00006000 08:04 963577                     /usr/lib/compiz/libshelf.so
2aaaad671000-2aaaad672000 rw-p 00005000 08:04 963577                     /usr/lib/compiz/libshelf.so
2aaaad672000-2aaaad677000 r-xp 00000000 08:04 963558                     /usr/lib/compiz/libbench.so
2aaaad677000-2aaaad877000 ---p 00005000 08:04 963558                     /usr/lib/compiz/libbench.so
2aaaad877000-2aaaad8fd000 rw-p 00005000 08:04 963558                     /usr/lib/compiz/libbench.so
2aaaad8fd000-2aaaad901000 r-xp 00000000 08:04 620183                     /usr/lib/compiz/libplace.so
2aaaad901000-2aaaadb00000 ---p 00004000 08:04 620183                     /usr/lib/compiz/libplace.so
2aaaadb00000-2aaaadb01000 rw-p 00003000 08:04 620183                     /usr/lib/compiz/libplace.so
2aaaadb01000-2aaaadb09000 r-xp 00000000 08:04 620181                     /usr/lib/compiz/libdbus.so
2aaaadb09000-2aaaadd08000 ---p 00008000 08:04 620181                     /usr/lib/compiz/libdbus.so
2aaaadd08000-2aaaadd09000 rw-p 00007000 08:04 620181                     /usr/lib/compiz/libdbus.so
2aaaadd09000-2aaaadd14000 r--s 00000000 08:04 1387706                    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86-64.cache-2
2aaaadd14000-2aaaadd15000 r--s 00000000 08:04 1387708                    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86-64.cache-2
2aaaadd15000-2aaaadd1d000 r--s 00000000 08:04 1387709                    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86-64.cache-2
2aaaadd1e000-2aaaadd59000 r-xp 00000000 08:04 948325                     /usr/lib/libdbus-1.so.3.3.0
2aaaadd59000-2aaaadf58000 ---p 0003b000 08:04 948325                     /usr/lib/libdbus-1.so.3.3.0
2aaaadf58000-2aaaadf5a000 rw-p 0003a000 08:04 948325                     /usr/lib/libdbus-1.so.3.3.0
2aaaadf5a000-2aaaadf5f000 r-xp 00000000 08:04 620176                     /usr/lib/compiz/libresize.so
2aaaadf5f000-2aaaae15f000 ---p 00005000 08:04 620176                     /usr/lib/compiz/libresize.so
2aaaae15f000-2aaaae160000 rw-p 00005000 08:04 620176                     /usr/lib/compiz/libresize.so
2aaaae160000-2aaaae163000 r-xp 00000000 08:04 620191                     /usr/lib/compiz/libpng.so
2aaaae163000-2aaaae362000 ---p 00003000 08:04 620191                     /usr/lib/compiz/libpng.so
2aaaae362000-2aaaae363000 rw-p 00002000 08:04 620191                     /usr/lib/compiz/libpng.so
2aaaae363000-2aaaae368000 r--s 00000000 08:04 1387735                    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86-64.cache-2
2aaaae368000-2aaaae36a000 r--s 00000000 08:04 1387740                    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86-64.cache-2
2aaaae36a000-2aaaae36b000 r--s 00000000 08:04 1387744                    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86-64.cache-2
2aaaae36b000-2aaaae36f000 r--s 00000000 08:04 1387747                    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86-64.cache-2
2aaaae36f000-2aaaae372000 r--s 00000000 08:04 1387748                    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86-64.cache-2
2aaaae372000-2aaaae378000 r--s 00000000 08:04 1387752                    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86-64.cache-2
2aaaae378000-2aaaae39c000 r-xp 00000000 08:04 947524                     /usr/lib/libpng12.so.0.15.0
2aaaae39c000-2aaaae59c000 ---p 00024000 08:04 947524                     /usr/lib/libpng12.so.0.15.0
2aaaae59c000-2aaaae59d000 rw-p 00024000 08:04 947524                     /usr/lib/libpng12.so.0.15.0
2aaaae59d000-2aaaae5a2000 r-xp 00000000 08:04 620192                     /usr/lib/compiz/libdecoration.so
2aaaae5a2000-2aaaae7a2000 ---p 00005000 08:04 620192                     /usr/lib/compiz/libdecoration.so
2aaaae7a2000-2aaaae7a3000 rw-p 00005000 08:04 620192                     /usr/lib/compiz/libdecoration.so
2aaaae7a3000-2aaaae7a4000 rw-s 00000000 00:09 753681                     /SYSV00000000 (deleted)
2aaaae7a4000-2aaaae7a5000 rw-s 00000000 00:09 786450                     /SYSV00000000 (deleted)
2aaaae7a5000-2aaaae7a6000 rw-s 00000000 00:09 819219                     /SYSV00000000 (deleted)
2aaaae7a6000-2aaaae7ad000 r--s 00000000 08:04 1387754                    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86-64.cache-2
2aaaae7ad000-2aaaae7ae000 r--s 00000000 08:04 1387755                    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86-64.cache-2
2aaaae7ae000-2aaaae7b1000 r--s 00000000 08:04 1387756                    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86-64.cache-2
2aaaae7b1000-2aaaae7b2000 r--s 00000000 08:04 1387758                    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86-64.cache-2
2aaaae7b2000-2aaaae7b5000 r--s 00000000 08:04 1387759                    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86-64.cache-2
2aaaae7b5000-2aaaae7b6000 rw-s 00000000 00:09 3440705                    /SYSV00000000 (deleted)
2aaaae7b6000-2aaaae7b7000 rw-s 00000000 00:09 5767234                    /SYSV00000000 (deleted)
2aaaae7b7000-2aaaae7b8000 rw-s 00000000 00:09 5603386                    /SYSV00000000 (deleted)
2aaaae7b8000-2aaaae7bf000 r-xp 00000000 08:04 948773                     /usr/lib/libdecoration.so.0.0.0
2aaaae7bf000-2aaaae9bf000 ---p 00007000 08:04 948773                     /usr/lib/libdecoration.so.0.0.0
2aaaae9bf000-2aaaae9c0000 rw-p 00007000 08:04 948773                     /usr/lib/libdecoration.so.0.0.0
2aaaae9c0000-2aaaae9c5000 r-xp 00000000 08:04 587540                     /usr/lib/compiz/libneg.so
2aaaae9c5000-2aaaaebc4000 ---p 00005000 08:04 587540                     /usr/lib/compiz/libneg.so
2aaaaebc4000-2aaaaebc5000 rw-p 00004000 08:04 587540                     /usr/lib/compiz/libneg.so
2aaaaebc5000-2aaaaebc9000 r-xp 00000000 08:04 587534                     /usr/lib/compiz/libtext.so
2aaaaebc9000-2aaaaedc8000 ---p 00004000 08:04 587534                     /usr/lib/compiz/libtext.so
2aaaaedc8000-2aaaaedc9000 rw-p 00003000 08:04 587534                     /usr/lib/compiz/libtext.so
2aaaaedc9000-2aaaaedd0000 r--s 00000000 08:04 1387760                    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86-64.cache-2
2aaaaedd0000-2aaaaedd4000 r--s 00000000 08:04 1387762                    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86-64.cache-2
2aaaaedd4000-2aaaaedd5000 r--s 00000000 08:04 1387729                    /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86-64.cache-2
2aaaaedd5000-2aaaaedd6000 r--s 00000000 08:04 1387769                    /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86-64.cache-2
2aaaaedd6000-2aaaaedd7000 r--s 00000000 08:04 1387770                    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86-64.cache-2
2aaaaedd7000-2aaaaedd8000 rw-s 00000000 00:09 5472327                    /SYSV00000000 (deleted)
2aaaaedd9000-2aaaaedda000 rw-s 00000000 00:09 6684733                    /SYSV00000000 (deleted)
2aaaaedda000-2aaaaeddb000 rw-s 00000000 00:09 4030526                    /SYSV00000000 (deleted)
2aaaaeddb000-2aaaaeddc000 rw-s 00000000 00:09 3506243                    /SYSV00000000 (deleted)
2aaaaedde000-2aaaaede8000 r-xp 00000000 08:04 947752                     /usr/lib/libpangocairo-1.0.so.0.1800.3
2aaaaede8000-2aaaaefe7000 ---p 0000a000 08:04 947752                     /usr/lib/libpangocairo-1.0.so.0.1800.3
2aaaaefe7000-2aaaaefe8000 rw-p 00009000 08:04 947752                     /usr/lib/libpangocairo-1.0.so.0.1800.3
2aaaaefe8000-2aaaaf02b000 r-xp 00000000 08:04 946834                     /usr/lib/libpango-1.0.so.0.1800.3
2aaaaf02b000-2aaaaf22b000 ---p 00043000 08:04 946834                     /usr/lib/libpango-1.0.so.0.1800.3
2aaaaf22b000-2aaaaf22e000 rw-p 00043000 08:04 946834                     /usr/lib/libpango-1.0.so.0.1800.3
2aaaaf22e000-2aaaaf2ac000 r-xp 00000000 08:04 946821                     /usr/lib/libcairo.so.2.11.5
2aaaaf2ac000-2aaaaf4ab000 ---p 0007e000 08:04 946821                     /usr/lib/libcairo.so.2.11.5
2aaaaf4ab000-2aaaaf4ae000 rw-p 0007d000 08:04 946821                     /usr/lib/libcairo.so.2.11.5
2aaaaf4ae000-2aaaaf4df000 r-xp 00000000 08:04 947800                     /usr/lib/libpangoft2-1.0.so.0.1800.3
2aaaaf4df000-2aaaaf6df000 ---p 00031000 08:04 947800                     /usr/lib/libpangoft2-1.0.so.0.1800.3
2aaaaf6df000-2aaaaf6e0000 rw-p 00031000 08:04 947800                     /usr/lib/libpangoft2-1.0.so.0.1800.3
2aaaaf6e0000-2aaaaf70b000 r-xp 00000000 08:04 946761                     /usr/lib/libfontconfig.so.1.2.0
2aaaaf70b000-2aaaaf90a000 ---p 0002b000 08:04 946761                     /usr/lib/libfontconfig.so.1.2.0
2aaaaf90a000-2aaaaf915000 rw-p 0002a000 08:04 946761                     /usr/lib/libfontconfig.so.1.2.0
2aaaaf915000-2aaaaf98f000 r-xp 00000000 08:04 948617                     /usr/lib/libfreetype.so.6.3.16
2aaaaf98f000-2aaaafb8f000 ---p 0007a000 08:04 948617                     /usr/lib/libfreetype.so.6.3.16
2aaaafb8f000-2aaaafb94000 rw-p 0007a000 08:04 948617                     /usr/lib/libfreetype.so.6.3.16
2aaaafb94000-2aaaafbb5000 r-xp 00000000 08:04 948611                     /usr/lib/libexpat.so.1.0.0
2aaaafbb5000-2aaaafdb4000 ---p 00021000 08:04 948611                     /usr/lib/libexpat.so.1.0.0
2aaaafdb4000-2aaaafdb7000 rw-p 00020000 08:04 948611                     /usr/lib/libexpat.so.1.0.0
2aaaafdb7000-2aaaafdbe000 r-xp 00000000 08:04 620193                     /usr/lib/compiz/libwobbly.so
2aaaafdbe000-2aaaaffbe000 ---p 00007000 08:04 620193                     /usr/lib/compiz/libwobbly.so
2aaaaffbe000-2aaaaffbf000 rw-p 00007000 08:04 620193                     /usr/lib/compiz/libwobbly.so
2aaaaffbf000-2aaaaffc0000 rw-p 2aaaaffbf000 00:00 0 
2aaaaffc0000-2aaaaffca000 r-xp 00000000 08:04 587536                     /usr/lib/compiz/libexpo.so
2aaaaffca000-2aaab01ca000 ---p 0000a000 08:04 587536                     /usr/lib/compiz/libexpo.so
2aaab01ca000-2aaab01cb000 rw-p 0000a000 08:04 587536                     /usr/lib/compiz/libexpo.so
2aaab01cb000-2aaab01d5000 r--s 00000000 08:04 1387481                    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86-64.cache-2
2aaab01d5000-2aaab01da000 r--s 00000000 08:04 1387501                    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86-64.cache-2
2aaab01da000-2aaab01de000 r--s 00000000 08:04 1387503                    /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86-64.cache-2
2aaab01e0000-2aaab0263000 r-xp 00000000 08:04 947457                     /usr/lib/libGLU.so.1.3.070001
2aaab0263000-2aaab0462000 ---p 00083000 08:04 947457                     /usr/lib/libGLU.so.1.3.070001
2aaab0462000-2aaab0464000 rw-p 00082000 08:04 947457                     /usr/lib/libGLU.so.1.3.070001
2aaab0464000-2aaab0554000 r-xp 00000000 08:04 948422                     /usr/lib/libstdc++.so.6.0.9
2aaab0554000-2aaab0753000 ---p 000f0000 08:04 948422                     /usr/lib/libstdc++.so.6.0.9
2aaab0753000-2aaab0759000 r--p 000ef000 08:04 948422                     /usr/lib/libstdc++.so.6.0.9
2aaab0759000-2aaab075c000 rw-p 000f5000 08:04 948422                     /usr/lib/libstdc++.so.6.0.9
2aaab075c000-2aaab076f000 rw-p 2aaab075c000 00:00 0 
2aaab076f000-2aaab077c000 r-xp 00000000 08:04 2105301                    /lib/libgcc_s.so.1
2aaab077c000-2aaab097c000 ---p 0000d000 08:04 2105301                    /lib/libgcc_s.so.1
2aaab097c000-2aaab097d000 rw-p 0000d000 08:04 2105301                    /lib/libgcc_s.so.1
2aaab097d000-2aaab0985000 r-xp 00000000 08:04 963576                     /usr/lib/compiz/libfirepaint.so
2aaab0985000-2aaab0b84000 ---p 00008000 08:04 963576                     /usr/lib/compiz/libfirepaint.so
2aaab0b84000-2aaab0b85000 rw-p 00007000 08:04 963576                     /usr/lib/compiz/libfirepaint.so
2aaab0b85000-2aaab0b8a000 r-xp 00000000 08:04 587539                     /usr/lib/compiz/libworkarounds.so
2aaab0b8a000-2aaab0d8a000 ---p 00005000 08:04 587539                     /usr/lib/compiz/libworkarounds.so
2aaab0d8a000-2aaab0d8b000 rw-p 00005000 08:04 587539                     /usr/lib/compiz/libworkarounds.so
2aaab0d8b000-2aaab0d8f000 r-xp 00000000 08:04 620173                     /usr/lib/compiz/libsvg.so
2aaab0d8f000-2aaab0f8f000 ---p 00004000 08:04 620173                     /usr/lib/compiz/libsvg.so
2aaab0f8f000-2aaab0f90000 rw-p 00004000 08:04 620173                     /usr/lib/compiz/libsvg.so
2aaab0f90000-2aaab0f97000 r--s 00000000 08:04 1387506                    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86-64.cache-2
2aaab0f97000-2aaab0f9a000 r--s 00000000 08:04 1387516                    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86-64.cache-2
2aaab0f9a000-2aaab0f9b000 r--s 00000000 08:04 1387517                    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86-64.cache-2
2aaab0f9b000-2aaab0fa3000 r--s 00000000 08:04 1387520                    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86-64.cache-2
2aaab0fa5000-2aaab0fd9000 r-xp 00000000 08:04 948199                     /usr/lib/librsvg-2.so.2.18.2
2aaab0fd9000-2aaab11d9000 ---p 00034000 08:04 948199                     /usr/lib/librsvg-2.so.2.18.2
2aaab11d9000-2aaab11db000 rw-p 00034000 08:04 948199                     /usr/lib/librsvg-2.so.2.18.2
2aaab11db000-2aaab11f4000 r-xp 00000000 08:04 277954                     /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
2aaab11f4000-2aaab13f4000 ---p 00019000 08:04 277954                     /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
2aaab13f4000-2aaab13f5000 rw-p 00019000 08:04 277954                     /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
2aaab13f5000-2aaab142c000 r-xp 00000000 08:04 946726                     /usr/lib/libgsf-1.so.114.0.7
2aaab142c000-2aaab162b000 ---p 00037000 08:04 946726                     /usr/lib/libgsf-1.so.114.0.7
2aaab162b000-2aaab162f000 rw-p 00036000 08:04 946726                     /usr/lib/libgsf-1.so.114.0.7
2aaab162f000-2aaab1630000 rw-p 2aaab162f000 00:00 0 
2aaab1630000-2aaab1668000 r-xp 00000000 08:04 948363                     /usr/lib/libcroco-0.6.so.3.0.1
2aaab1668000-2aaab1867000 ---p 00038000 08:04 948363                     /usr/lib/libcroco-0.6.so.3.0.1
2aaab1867000-2aaab186b000 rw-p 00037000 08:04 948363                     /usr/lib/libcroco-0.6.so.3.0.1
2aaab186b000-2aaab187a000 r-xp 00000000 08:04 2105353                    /lib/libbz2.so.1.0.4
2aaab187a000-2aaab1a79000 ---p 0000f000 08:04 2105353                    /lib/libbz2.so.1.0.4
2aaab1a79000-2aaab1a7b000 rw-p 0000e000 08:04 2105353                    /lib/libbz2.so.1.0.4
2aaab1a7b000-2aaab1a80000 r-xp 00000000 08:04 963564                     /usr/lib/compiz/libsplash.so
2aaab1a80000-2aaab1c80000 ---p 00005000 08:04 963564                     /usr/lib/compiz/libsplash.so
2aaab1c80000-2aaab1c81000 rw-p 00005000 08:04 963564                     /usr/lib/compiz/libsplash.so
2aaab1c81000-2aaab1c89000 r-xp 00000000 08:04 587530                     /usr/lib/compiz/libthumbnail.so
2aaab1c89000-2aaab1e89000 ---p 00008000 08:04 587530                     /usr/lib/compiz/libthumbnail.so
2aaab1e89000-2aaab1e8c000 rw-p 00008000 08:04 587530                     /usr/lib/compiz/libthumbnail.so
2aaab1e8c000-2aaab1e8f000 r-xp 00000000 08:04 963566                     /usr/lib/compiz/libcrashhandler.so
2aaab1e8f000-2aaab208e000 ---p 00003000 08:04 963566                     /usr/lib/compiz/libcrashhandler.so
2aaab208e000-2aaab208f000 rw-p 00002000 08:04 963566                     /usr/lib/compiz/libcrashhandler.so
2aaab208f000-2aaab2091000 r-xp 00000000 08:04 587544                     /usr/lib/compiz/libmousepoll.so
2aaab2091000-2aaab2290000 ---p 00002000 08:04 587544                     /usr/lib/compiz/libmousepoll.so
2aaab2290000-2aaab2291000 rw-p 00001000 08:04 587544                     /usr/lib/compiz/libmousepoll.so
2aaab2291000-2aaab2294000 r-xp 00000000 08:04 587527                     /usr/lib/compiz/libimgjpeg.so
2aaab2294000-2aaab2494000 ---p 00003000 08:04 587527                     /usr/lib/compiz/libimgjpeg.so
2aaab2494000-2aaab2495000 rw-p 00003000 08:04 587527                     /usr/lib/compiz/libimgjpeg.so
2aaab2495000-2aaab24a0000 r--s 00000000 08:04 1387522                    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86-64.cache-2
2aaab24a0000-2aaab24a2000 r--s 00000000 08:04 1387523                    /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86-64.cache-2
2aaab24a2000-2aaab24a5000 r--s 00000000 08:04 1387525                    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86-64.cache-2
2aaab24aa000-2aaab24cc000 r-xp 00000000 08:04 277609                     /usr/lib/libjpeg.so.62.0.0
2aaab24cc000-2aaab26cc000 ---p 00022000 08:04 277609                     /usr/lib/libjpeg.so.62.0.0
2aaab26cc000-2aaab26cd000 rw-p 00022000 08:04 277609                     /usr/lib/libjpeg.so.62.0.0
2aaab26cd000-2aaab26cf000 r-xp 00000000 08:04 620180                     /usr/lib/compiz/libregex.so
2aaab26cf000-2aaab28cf000 ---p 00002000 08:04 620180                     /usr/lib/compiz/libregex.so
2aaab28cf000-2aaab28d0000 rw-p 00002000 08:04 620180                     /usr/lib/compiz/libregex.so
2aaab28d0000-2aaab28d3000 r-xp 00000000 08:04 620169                     /usr/lib/compiz/libclone.so
2aaab28d3000-2aaab2ad3000 ---p 00003000 08:04 620169                     /usr/lib/compiz/libclone.so
2aaab2ad3000-2aaab2ad4000 rw-p 00003000 08:04 620169                     /usr/lib/compiz/libclone.so
2aaab2ad4000-2aaab2af8000 r-xp 00000000 08:04 587535                     /usr/lib/compiz/libanimation.so
2aaab2af8000-2aaab2cf7000 ---p 00024000 08:04 587535                     /usr/lib/compiz/libanimation.so
2aaab2cf7000-2aaab2cfa000 rw-p 00023000 08:04 587535                     /usr/lib/compiz/libanimation.so
2aaab2cfa000-2aaab2d02000 r-xp 00000000 08:04 587529                     /usr/lib/compiz/libezoom.so
2aaab2d02000-2aaab2f01000 ---p 00008000 08:04 587529                     /usr/lib/compiz/libezoom.so
2aaab2f01000-2aaab2f02000 rw-p 00007000 08:04 587529                     /usr/lib/compiz/libezoom.so
2aaab2f02000-2aaab2f0b000 r-xp 00000000 08:04 587542                     /usr/lib/compiz/libmag.so
2aaab2f0b000-2aaab310b000 ---p 00009000 08:04 587542                     /usr/lib/compiz/libmag.so
2aaab310b000-2aaab310c000 rw-p 00009000 08:04 587542                     /usr/lib/compiz/libmag.so
2aaab310c000-2aaab3113000 r-xp 00000000 08:04 587521                     /usr/lib/compiz/libswitcher.so
2aaab3113000-2aaab3313000 ---p 00007000 08:04 587521                     /usr/lib/compiz/libswitcher.so
2aaab3313000-2aaab3314000 rw-p 00007000 08:04 587521                     /usr/lib/compiz/libswitcher.so
2aaab3314000-2aaab3317000 r-xp 00000000 08:04 620178                     /usr/lib/compiz/libfade.so
2aaab3317000-2aaab3517000 ---p 00003000 08:04 620178                     /usr/lib/compiz/libfade.so
2aaab3517000-2aaab3518000 rw-p 00003000 08:04 620178                     /usr/lib/compiz/libfade.so
2aaab3518000-2aaab3520000 r-xp 00000000 08:04 620189                     /usr/lib/compiz/libscale.so
2aaab3520000-2aaab371f000 ---p 00008000 08:04 620189                     /usr/lib/compiz/libscale.so
2aaab371f000-2aaab3720000 rw-p 00007000 08:04 620189                     /usr/lib/compiz/libscale.so
2aaab3720000-2aaab3721000 rw-s 00000000 00:09 950286                     /SYSV00000000 (deleted)
2aaab3721000-2aaab3729000 r--s 00000000 08:04 1387530                    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86-64.cache-2
2aaab3729000-2aaab372c000 r--s 00000000 08:04 1387532                    /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86-64.cache-2
2aaab372c000-2aaab372e000 r--s 00000000 08:04 1387594                    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86-64.cache-2
2aaab372e000-2aaab3730000 r--s 00000000 08:04 1387595                    /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86-64.cache-2
2aaab3730000-2aaab3734000 r--s 00000000 08:04 1387611                    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86-64.cache-2
2aaab3734000-2aaab3736000 r--s 00000000 08:04 1387612                    /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86-64.cache-2
2aaab3736000-2aaab3737000 r--s 00000000 08:04 1387614                    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86-64.cache-2
2aaab3737000-2aaab3738000 r--s 00000000 08:04 1387619                    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86-64.cache-2
2aaab3738000-2aaab373d000 r--s 00000000 08:04 1387620                    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86-64.cache-2
2aaab373d000-2aaab373e000 r--s 00000000 08:04 1387629                    /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86-64.cache-2
2aaab373e000-2aaab373f000 r--s 00000000 08:04 1387650                    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86-64.cache-2
2aaab373f000-2aaab3742000 r--s 00000000 08:04 1387671                    /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86-64.cache-2
2aaab3742000-2aaab3743000 r--s 00000000 08:04 1387672                    /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86-64.cache-2
2aaab3743000-2aaab3746000 r--s 00000000 08:04 1387674                    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86-64.cache-2
2aaab3746000-2aaab374e000 r--s 00000000 08:04 1387677                    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86-64.cache-2
2aaab374e000-2aaab37ce000 rw-s 100a5000 00:0e 20800                      /dev/nvidia0
2aaab3846000-2aaab3d2a000 rw-p 2aaab3846000 00:00 0 
2aaab3d2b000-2aaab3d2c000 rw-s 00000000 00:09 1015832                    /SYSV00000000 (deleted)
2aaab3d2c000-2aaab40d7000 rw-p 2aaab3d2c000 00:00 0 
2aaab40d8000-2aaab40d9000 rw-s 00000000 00:09 1769507                    /SYSV00000000 (deleted)
2aaab40d9000-2aaab40db000 r-xp 00000000 08:04 1062232                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
2aaab40db000-2aaab42da000 ---p 00002000 08:04 1062232                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
2aaab42da000-2aaab42db000 rw-p 00001000 08:04 1062232                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
2aaab42db000-2aaab435f000 r--p 00000000 08:04 1161726                    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
2aaab4363000-2aaab4364000 rw-s 00000000 00:09 2261038                    /SYSV00000000 (deleted)
2aaab4365000-2aaab4366000 rw-s 00000000 00:09 2654248                    /SYSV00000000 (deleted)
2aaab4366000-2aaab4367000 rw-s 00000000 00:09 2326577                    /SYSV00000000 (deleted)
2aaab4367000-2aaab4370000 r-xp 00000000 08:04 620190                     /usr/lib/compiz/libcube.so
2aaab4370000-2aaab4570000 ---p 00009000 08:04 620190                     /usr/lib/compiz/libcube.so
2aaab4570000-2aaab4571000 rw-p 00009000 08:04 620190                     /usr/lib/compiz/libcube.so
2aaab4571000-2aaab4578000 r-xp 00000000 08:04 963571                     /usr/lib/compiz/lib3d.so
2aaab4578000-2aaab4778000 ---p 00007000 08:04 963571                     /usr/lib/compiz/lib3d.so
2aaab4778000-2aaab4779000 rw-p 00007000 08:04 963571                     /usr/lib/compiz/lib3d.so
2aaab4779000-2aaab477e000 r-xp 00000000 08:04 963575                     /usr/lib/compiz/libcubereflex.so
2aaab477e000-2aaab497e000 ---p 00005000 08:04 963575                     /usr/lib/compiz/libcubereflex.so
2aaab497e000-2aaab497f000 rw-p 00005000 08:04 963575                     /usr/lib/compiz/libcubereflex.so
2aaab497f000-2aaab4987000 r-xp 00000000 08:04 963563                     /usr/lib/compiz/libcubecaps.so
2aaab4987000-2aaab4b87000 ---p 00008000 08:04 963563                     /usr/lib/compiz/libcubecaps.so
2aaab4b87000-2aaab4b88000 rw-p 00008000 08:04 963563                     /usr/lib/compiz/libcubecaps.so
2aaab4b88000-2aaab4b8f000 r-xp 00000000 08:04 620182                     /usr/lib/compiz/librotate.so
2aaab4b8f000-2aaab4d8f000 ---p 00007000 08:04 620182                     /usr/lib/compiz/librotate.so
2aaab4d8f000-2aaab4d90000 rw-p 00007000 08:04 620182                     /usr/lib/compiz/librotate.so
2aaab4d90000-2aaab4d91000 rw-s 00000000 00:09 2555951                    /SYSV00000000 (deleted)
2aaab4d91000-2aaab4d92000 rw-s 00000000 00:09 2392105                    /SYSV00000000 (deleted)
2aaab4d93000-2aaab4d94000 rw-s 00000000 00:09 2490411                    /SYSV00000000 (deleted)
2aaab4d95000-2aaab4d96000 rw-s 00000000 00:09 2621490                    /SYSV00000000 (deleted)
2aaab4d96000-2aaab551a000 rw-s 04244000 00:0e 20800                      /dev/nvidia0
2aaab551d000-2aaab5ca1000 rw-s 03ac5000 00:0e 20800                      /dev/nvidia0
2aaab5ca1000-2aaab5ed6000 rw-s 2801e000 00:0e 20800                      /dev/nvidia0
2aaab5ed8000-2aaab613e000 rw-s 3a9da000 00:0e 20800                      /dev/nvidia0
2aaab613e000-2aaab613f000 rw-s 00000000 00:09 3571780                    /SYSV00000000 (deleted)
2aaab613f000-2aaab6140000 rw-s 00000000 00:09 6553636                    /SYSV00000000 (deleted)
2aaab6144000-2aaab6917000 rw-s 14b54000 00:0e 20800                      /dev/nvidia0
2aaab691a000-2aaab691b000 rw-s 00000000 00:09 3965006                    /SYSV00000000 (deleted)
2aaab691b000-2aaab709f000 rw-s 35920000 00:0e 20800                      /dev/nvidia0
2aaab709f000-2aaab72d4000 rw-s 0b688000 00:0e 20800                      /dev/nvidia0
2aaab72d5000-2aaab72d6000 rw-s 00000000 00:09 4194384                    /SYSV00000000 (deleted)
2aaab72d6000-2aaab73fe000 rw-s 384cd000 00:0e 20800                      /dev/nvidia0
2aaab73fe000-2aaab74a6000 rw-s 1ca62000 00:0e 20800                      /dev/nvidia0
2aaab74a6000-2aaab75ce000 rw-s 340f9000 00:0e 20800                      /dev/nvidia0
2aaab75ce000-2aaab76f6000 rw-s 1f459000 00:0e 20800                      /dev/nvidia0
2aaab76f6000-2aaab7e28000 rw-s 1d4fb000 00:0e 20800                      /dev/nvidia0
2aaab7e2a000-2aaab805f000 rw-s 2a007000 00:0e 20800                      /dev/nvidia0
2aaab8061000-2aaab8189000 rw-s 29eb5000 00:0e 20800                      /dev/nvidia0
2aaab8189000-2aaab83be000 rw-s 13e0b000 00:0e 20800                      /dev/nvidia0
2aaab83be000-2aaab84e6000 rw-s 18c28000 00:0e 20800                      /dev/nvidia0
2aaab84e6000-2aaab860e000 rw-s 14571000 00:0e 20800                      /dev/nvidia0
2aaab8610000-2aaab8925000 rw-s 2fc19000 00:0e 20800                      /dev/nvidia0
2aaab8926000-2aaab8a4e000 rw-s 38bdf000 00:0e 20800                      /dev/nvidia0
2aaab8a4f000-2aaab8b77000 rw-s 2f821000 00:0e 20800                      /dev/nvidia0
2aaab8b77000-2aaab8c9f000 rw-s 120c7000 00:0e 20800                      /dev/nvidia0
2aaab8c9f000-2aaab8f4c000 rw-s 264d3000 00:0e 20800                      /dev/nvidia0
2aaab8f4f000-2aaab937b000 rw-s 316e2000 00:0e 20800                      /dev/nvidia0
2aaab937b000-2aaab97a7000 rw-s 02fbe000 00:0e 20800                      /dev/nvidia0
2aaab97a9000-2aaab9f2d000 rw-s 36013000 00:0e 20800                      /dev/nvidia0
2aaab9f2d000-2aaaba1a2000 rw-s 02529000 00:0e 20800                      /dev/nvidia0
2aaaba1a5000-2aaaba224000 rw-s 01958000 00:0e 20800                      /dev/nvidia0
2aaaba228000-2aaaba2a7000 rw-s 1dd77000 00:0e 20800                      /dev/nvidia0
2aaaba2a7000-2aaaba3cf000 rw-s 019ea000 00:0e 20800                      /dev/nvidia0
2aaaba3cf000-2aaaba4f7000 rw-s 1117c000 00:0e 20800                      /dev/nvidia0
2aaaba4f7000-2aaaba61f000 rw-s 36250000 00:0e 20800                      /dev/nvidia0
2aaaba620000-2aaaba748000 rw-s 1c68e000 00:0e 20800                      /dev/nvidia0
2aaaba749000-2aaababcf000 rw-s 02623000 00:0e 20800                      /dev/nvidia0
2aaababcf000-2aaabb055000 rw-s 10ab1000 00:0e 20800                      /dev/nvidia0
2aaabb055000-2aaabb4db000 rw-s 38e86000 00:0e 20800                      /dev/nvidia0
2aaabb4db000-2aaabb961000 rw-s 36323000 00:0e 20800                      /dev/nvidia0
2aaabb961000-2aaabbda7000 rw-s 2d764000 00:0e 20800                      /dev/nvidia0
2aaabbda8000-2aaabc1ee000 rw-s 00d7b000 00:0e 20800                      /dev/nvidia0
2aaabc1ee000-2aaabc674000 rw-s 20aba000 00:0e 20800                      /dev/nvidia0
2aaabc674000-2aaabc9d9000 rw-s 22b4d000 00:0e 20800                      /dev/nvidia0
2aaabc9d9000-2aaabcd6d000 rw-s 1f4eb000 00:0e 20800                      /dev/nvidia0
2aaabcd72000-2aaabce9a000 rw-s 331b9000 00:0e 20800                      /dev/nvidia0
2aaabce9a000-2aaabcfc2000 rw-s 2d2c3000 00:0e 20800                      /dev/nvidia0
2aaabcfc2000-2aaabd3ee000 rw-s 218c0000 00:0e 20800                      /dev/nvidia0
2aaabd3f0000-2aaabd518000 rw-s 0e568000 00:0e 20800                      /dev/nvidia0
2aaabd519000-2aaabd641000 rw-s 34309000 00:0e 20800                      /dev/nvidia0
2aaabd641000-2aaabd769000 rw-s 33abd000 00:0e 20800                      /dev/nvidia0
2aaabd769000-2aaabd891000 rw-s 174aa000 00:0e 20800                      /dev/nvidia0
2aaabd891000-2aaabd9b9000 rw-s 10f72000 00:0e 20800                      /dev/nvidia0
2aaabd9b9000-2aaabdae1000 rw-s 3776c000 00:0e 20800                      /dev/nvidia0
2aaabdae1000-2aaabdc09000 rw-s 33413000 00:0e 20800                      /dev/nvidia0
2aaabdc09000-2aaabdc0a000 rw-s 00000000 00:09 5701688                    /SYSV00000000 (deleted)
2aaabdc0a000-2aaabe38e000 rw-s 1a0a9000 00:0e 20800                      /dev/nvidia0
2aaabe390000-2aaabe4b8000 rw-s 2cb61000 00:0e 20800                      /dev/nvidia0
2aaabe4b9000-2aaabe5e1000 rw-s 2fb8d000 00:0e 20800                      /dev/nvidia0
2aaabe5e1000-2aaabea67000 rw-s 28055000 00:0e 20800                      /dev/nvidia0
2aaabea67000-2aaabebaf000 rw-s 3360d000 00:0e 20800                      /dev/nvidia0
2aaabebaf000-2aaabf333000 rw-s 37434000 00:0e 20800                      /dev/nvidia0
2aaabf335000-2aaabf761000 rw-s 10ee5000 00:0e 20800                      /dev/nvidia0
2aaabf765000-2aaabf7e4000 rw-s 26949000 00:0e 20800                      /dev/nvidia0
2aaabf7e4000-2aaabf7e5000 rw-s 00000000 00:09 6258772                    /SYSV00000000 (deleted)
2aaabf7e5000-2aaabf8ae000 rw-s 36ad8000 00:0e 20800                      /dev/nvidia0
2aaabf8ae000-2aaabfca2000 rw-s 02152000 00:0e 20800                      /dev/nvidia0
2aaabfca2000-2aaabfdca000 rw-s 30bc1000 00:0e 20800                      /dev/nvidia0
2aaabfdca000-2aaabfef2000 rw-s 3041c000 00:0e 20800                      /dev/nvidia0
2aaabfef2000-2aaac00f2000 rw-s 2b063000 00:0e 20800                      /dev/nvidia0
2b5f160df000-2b5f160fc000 r-xp 00000000 08:04 2105434                    /lib/ld-2.6.1.so
2b5f160fc000-2b5f160ff000 rw-p 2b5f160fc000 00:00 0 
2b5f162fb000-2b5f162fd000 rw-p 0001c000 08:04 2105434                    /lib/ld-2.6.1.so
2b5f162fd000-2b5f162ff000 r-xp 00000000 08:04 277571                     /usr/lib/libXcomposite.so.1.0.0
2b5f162ff000-2b5f164fe000 ---p 00002000 08:04 277571                     /usr/lib/libXcomposite.so.1.0.0
2b5f164fe000-2b5f164ff000 rw-p 00001000 08:04 277571                     /usr/lib/libXcomposite.so.1.0.0
2b5f164ff000-2b5f16501000 r-xp 00000000 08:04 277579                     /usr/lib/libXdamage.so.1.1.0
2b5f16501000-2b5f16700000 ---p 00002000 08:04 277579                     /usr/lib/libXdamage.so.1.1.0
2b5f16700000-2b5f16701000 rw-p 00001000 08:04 277579                     /usr/lib/libXdamage.so.1.1.0
2b5f16701000-2b5f16706000 r-xp 00000000 08:04 277474                     /usr/lib/libXfixes.so.3.1.0
2b5f16706000-2b5f16905000 ---p 00005000 08:04 277474                     /usr/lib/libXfixes.so.3.1.0
2b5f16905000-2b5f16906000 rw-p 00004000 08:04 277474                     /usr/lib/libXfixes.so.3.1.0
2b5f16906000-2b5f1690d000 r-xp 00000000 08:04 277603                     /usr/lib/libXrandr.so.2.1.0
2b5f1690d000-2b5f16b0c000 ---p 00007000 08:04 277603                     /usr/lib/libXrandr.so.2.1.0
2b5f16b0c000-2b5f16b0d000 rw-p 00006000 08:04 277603                     /usr/lib/libXrandr.so.2.1.0
2b5f16b0d000-2b5f16b0e000 rw-p 2b5f16b0d000 00:00 0 
2b5f16b0e000-2b5f16b10000 r-xp 00000000 08:04 277585                     /usr/lib/libXinerama.so.1.0.0
2b5f16b10000-2b5f16d0f000 ---p 00002000 08:04 277585                     /usr/lib/libXinerama.so.1.0.0
2b5f16d0f000-2b5f16d10000 rw-p 00001000 08:04 277585                     /usr/lib/libXinerama.so.1.0.0
2b5f16d10000-2b5f16d18000 r-xp 00000000 08:04 947587                     /usr/lib/libSM.so.6.0.0
2b5f16d18000-2b5f16f17000 ---p 00008000 08:04 947587                     /usr/lib/libSM.so.6.0.0
2b5f16f17000-2b5f16f18000 rw-p 00007000 08:04 947587                     /usr/lib/libSM.so.6.0.0
2b5f16f18000-2b5f16f2f000 r-xp 00000000 08:04 947577                     /usr/lib/libICE.so.6.3.0
2b5f16f2f000-2b5f1712f000 ---p 00017000 08:04 947577                     /usr/lib/libICE.so.6.3.0
2b5f1712f000-2b5f17130000 rw-p 00017000 08:04 947577                     /usr/lib/libICE.so.6.3.0
2b5f17130000-2b5f17135000 rw-p 2b5f17130000 00:00 0 
2b5f17135000-2b5f1716c000 r-xp 00000000 08:04 947887                     /usr/lib/libxslt.so.1.1.21
2b5f1716c000-2b5f1736b000 ---p 00037000 08:04 947887                     /usr/lib/libxslt.so.1.1.21
2b5f1736b000-2b5f1736d000 rw-p 00036000 08:04 947887                     /usr/lib/libxslt.so.1.1.21
2b5f1736d000-2b5f174a9000 r-xp 00000000 08:04 947387                     /usr/lib/libxml2.so.2.6.30
2b5f174a9000-2b5f176a8000 ---p 0013c000 08:04 947387                     /usr/lib/libxml2.so.2.6.30
2b5f176a8000-2b5f176b2000 rw-p 0013b000 08:04 947387                     /usr/lib/libxml2.so.2.6.30
2b5f176b2000-2b5f176b3000 rw-p 2b5f176b2000 00:00 0 
2b5f176b3000-2b5f176bc000 r-xp 00000000 08:04 948514                     /usr/lib/libstartup-notification-1.so.0.0.0
2b5f176bc000-2b5f178bb000 ---p 00009000 08:04 948514                     /usr/lib/libstartup-notification-1.so.0.0.0
2b5f178bb000-2b5f178bc000 rw-p 00008000 08:04 948514                     /usr/lib/libstartup-notification-1.so.0.0.0
2b5f178bc000-2b5f178bd000 rw-p 2b5f178bc000 00:00 0 
2b5f178bd000-2b5f17951000 r-xp 00000000 08:04 947776                     /usr/lib/libGL.so.100.14.19
2b5f17951000-2b5f17a51000 ---p 00094000 08:04 947776                     /usr/lib/libGL.so.100.14.19
2b5f17a51000-2b5f17a85000 rwxp 00094000 08:04 947776                     /usr/lib/libGL.so.100.14.19
2b5f17a85000-2b5f17a87000 rwxp 2b5f17a85000 00:00 0 
2b5f17a87000-2b5f17b07000 r-xp 00000000 08:04 2105441                    /lib/libm-2.6.1.so
2b5f17b07000-2b5f17d06000 ---p 00080000 08:04 2105441                    /lib/libm-2.6.1.so
2b5f17d06000-2b5f17d08000 rw-p 0007f000 08:04 2105441                    /lib/libm-2.6.1.so
2b5f17d08000-2b5f17d12000 r-xp 00000000 08:04 277575                     /usr/lib/libXcursor.so.1.0.2
2b5f17d12000-2b5f17f11000 ---p 0000a000 08:04 277575                     /usr/lib/libXcursor.so.1.0.2
2b5f17f11000-2b5f17f12000 rw-p 00009000 08:04 277575                     /usr/lib/libXcursor.so.1.0.2
2b5f17f12000-2b5f17f13000 rw-p 2b5f17f12000 00:00 0 
2b5f17f13000-2b5f18065000 r-xp 00000000 08:04 2105437                    /lib/libc-2.6.1.so
2b5f18065000-2b5f18264000 ---p 00152000 08:04 2105437                    /lib/libc-2.6.1.so
2b5f18264000-2b5f18267000 r--p 00151000 08:04 2105437                    /lib/libc-2.6.1.so
2b5f18267000-2b5f18269000 rw-p 00154000 08:04 2105437                    /lib/libc-2.6.1.so
2b5f18269000-2b5f1826e000 rw-p 2b5f18269000 00:00 0 
2b5f1826e000-2b5f18378000 r-xp 00000000 08:04 947496                     /usr/lib/libX11.so.6.2.0
2b5f18378000-2b5f18578000 ---p 0010a000 08:04 947496                     /usr/lib/libX11.so.6.2.0
2b5f18578000-2b5f1857f000 rw-p 0010a000 08:04 947496                     /usr/lib/libX11.so.6.2.0
2b5f1857f000-2b5f18590000 r-xp 00000000 08:04 277569                     /usr/lib/libXext.so.6.4.0
2b5f18590000-2b5f1878f000 ---p 00011000 08:04 277569                     /usr/lib/libXext.so.6.4.0
2b5f1878f000-2b5f18790000 rw-p 00010000 08:04 277569                     /usr/lib/libXext.so.6.4.0
2b5f18790000-2b5f18791000 rw-p 2b5f18790000 00:00 0 
2b5f18791000-2b5f18793000 r-xp 00000000 08:04 2105440                    /lib/libdl-2.6.1.so
2b5f18793000-2b5f18993000 ---p 00002000 08:04 2105440                    /lib/libdl-2.6.1.so
2b5f18993000-2b5f18995000 rw-p 00002000 08:04 2105440                    /lib/libdl-2.6.1.so
2b5f18995000-2b5f1899e000 r-xp 00000000 08:04 947500                     /usr/lib/libXrender.so.1.3.0
2b5f1899e000-2b5f18b9d000 ---p 00009000 08:04 947500                     /usr/lib/libXrender.so.1.3.0
2b5f18b9d000-2b5f18b9e000 rw-p 00008000 08:04 947500                     /usr/lib/libXrender.so.1.3.0
2b5f18b9e000-2b5f18b9f000 rw-p 2b5f18b9e000 00:00 0 
2b5f18b9f000-2b5f18bb5000 r-xp 00000000 08:04 948595                     /usr/lib/libz.so.1.2.3.3
2b5f18bb5000-2b5f18db5000 ---p 00016000 08:04 948595                     /usr/lib/libz.so.1.2.3.3
2b5f18db5000-2b5f18db6000 rw-p 00016000 08:04 948595                     /usr/lib/libz.so.1.2.3.3
2b5f18db6000-2b5f19595000 r-xp 00000000 08:04 947777                     /usr/lib/libGLcore.so.100.14.19
2b5f19595000-2b5f19694000 ---p 007df000 08:04 947777                     /usr/lib/libGLcore.so.100.14.19
2b5f19694000-2b5f19807000 rwxp 007de000 08:04 947777                     /usr/lib/libGLcore.so.100.14.19
2b5f19807000-2b5f1980d000 rwxp 2b5f19807000 00:00 0 
2b5f1980d000-2b5f1980e000 r-xp 00000000 08:04 1256804                    /usr/lib/tls/libnvidia-tls.so.100.14.19
2b5f1980e000-2b5f1990d000 ---p 00001000 08:04 1256804                    /usr/lib/tls/libnvidia-tls.so.100.14.19
2b5f1990d000-2b5f1990e000 rw-p 00000000 08:04 1256804                    /usr/lib/tls/libnvidia-tls.so.100.14.19
2b5f1990e000-2b5f1990f000 rw-p 2b5f1990e000 00:00 0 
2b5f1990f000-2b5f19911000 r-xp 00000000 08:04 947398                     /usr/lib/libXau.so.6.0.0
2b5f19911000-2b5f19b10000 ---p 00002000 08:04 947398                     /usr/lib/libXau.so.6.0.0
2b5f19b10000-2b5f19b11000 rw-p 00001000 08:04 947398                     /usr/lib/libXau.so.6.0.0
2b5f19b11000-2b5f19b16000 r-xp 00000000 08:04 947478                     /usr/lib/libXdmcp.so.6.0.0
2b5f19b16000-2b5f19d15000 ---p 00005000 08:04 947478                     /usr/lib/libXdmcp.so.6.0.0
2b5f19d15000-2b5f19d16000 rw-p 00004000 08:04 947478                     /usr/lib/libXdmcp.so.6.0.0
2b5f19d16000-2b5f19d18000 rw-p 2b5f19d16000 00:00 0 
7fff94995000-7fff949c9000 rwxp 7fff94995000 00:00 0                      [stack]
7fff949c9000-7fff949cb000 rw-p 7fff949c9000 00:00 0 
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vdso]
```

Unfortunately I have no idea what the significance of that output is... But i seem to remember that I AM indeed using nvidia-glx-new drivers. My card is the GeForce 6150 Mobile with 128 MB shared memory!

Thanks.

---

### Post by chrisccoulson on 2008-03-06
Check out: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/151168/comments/42]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/151168/comments/42")

Your post also suggests your leak is related to the NVIDIA restricted driver

---

### Post by phibit on 2008-03-06
Ah okay so basically there is nothing I can do? Maybe try to revert back to the old nvidia drivers or something? Or am I just screwed?

---

### Post by chrisccoulson on 2008-03-06
You could try disabling some Compiz plugins to see if the behaviour goes away. I do apologise, but I can't help much more as I'm fortunate enough to not suffer this memory leak, and I never have with nvidia-glx-new on Gutsy

You could try running the latest Nvidia drivers using [Envy]("http://albertomilone.com/nvidia_scripts1.html"). I can't remember off the top of my head whether the memory leak was fixed in a later driver. I am running 169.12 using Envy, which I believe is the latest.

---

### Post by SloYerRoll on 2008-03-06
Quick Envy question.  (new user here)
If I already have everything installed and running fine, but jsut want to make sure my drivers are up to date...

Can I just install Envy per the directions on the website and that's that? I've finally got things dialed in to the way I like them (except one thing..) and don't want to install this if it's a headache..

Thanks.

---

### Post by chrisccoulson on 2008-03-06
Once you've installed Envy, you will need to launch it from either the icon in the Applications -> System Tools menu, or from the command line:
```
envy -g
```

Then select the option to install latest Nvidia driver. It will take care of removing the old driver etc. If you are already running the nvidia-glx-new driver successfully, you may not want Envy to update your xorg.conf.

---

### Post by SloYerRoll on 2008-03-06
> **chrisccoulson said:**
> Once you've installed Envy, you will need to launch it from either the icon in the Applications -> System Tools menu, or from the command line:
```
envy -g
```

Then select the option to install latest Nvidia driver. It will take care of removing the old driver etc. If you are already running the nvidia-glx-new driver successfully, you may not want Envy to update your xorg.conf.How can I tell which driver I'm 
using? On the restricted driver window, it only tells me I'm using the driver (it doesn't tell me the version)>

---

### Post by chrisccoulson on 2008-03-06
Open up nvidia-settngs from the terminal. If you're using nvidia-glx-new from the repository, then you're using 100.14.19.

---

### Post by phibit on 2008-03-06
Okay I updated to 169.12 using envy as suggested.. Now I'm going to test out if I have the same problem. Thanks for the help :)

---

### Post by SloYerRoll on 2008-03-06
> **chrisccoulson said:**
> Open up nvidia-settngs from the terminal. If you're using nvidia-glx-new from the repository, then you're using 100.14.19.
I am. Thanks!

---

### Post by phibit on 2008-03-10
Alright it's been a few days and I've been straining Compiz but this driver update seems to have worked!!! AMAZING! You have no idea how happy I am. Thanks.

As a recap, the problem was with a memory leak in the nvidia-glx-new drivers that come in the gutsy repos, and the solution was to use envy to install the latest nvidia drviers.

I am marking this thread as solved. Once again, thanks guys.

---


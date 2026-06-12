---
title: "need help compiling tcpdump for mips"
date: 2016-03-26
forum: General Help
---

### Post by petermg on 2016-03-26
In the past I've compiled some apps and even posted them for download.  However that was years ago and I don't do it often and I am pretty lost right now.  I'm trying to crosscompile tcpdump for my Netgear WNDR4500v1 router.  The cpu is MIPS 74K V4.9 and the lib folder contains
```
ld-uClibc.so.0                libpthread.so.0
libc.so.0                     librt.so.0
libcrypt.so.0                 libstdc++.so
libdl.so.0                    libstdc++.so.6
libgcc_s.so.1                 libutil.so.0
libm.so.0                     modules
libnsl.so.0                   openvpn_plugin_auth_nvram.so
```

I have looked at tutorials from different sites and they leave me very confused.  I suspect they are assuming certain understandings that I do not currently posses.  Here are some of the sites I've looked at

[http://www.androidtcpdump.com/android-tcpdump/compile](http://www.androidtcpdump.com/android-tcpdump/compile)
[http://www.evolware.org/?p=145](http://www.evolware.org/?p=145)
[https://wiki.openwrt.org/doc/devel/crosscompile](https://wiki.openwrt.org/doc/devel/crosscompile)

If anyone can please help me, maybe even just point me to a tutorial that is Ninja Warrior level 0 ;) thanks!!! :D

---

### Post by elroto07 on 2016-08-27
HI petermg,

I want to do the same like you. I would like to have the tcpdump binary for Huawei HG556a and/or Alcatel Lucent I240G-T. The first one has a BCM6358 V1.0 cpu and the second one has a MIPS 74Kc V4.12 cpu. 

I have compiled libpcap and tcpdump with CodeSourcery like this:

Download and decompress libpcap
 export CFLAGS="-muclibc -static"
 CC=mips-linux-gnu-gcc ac_cv_linux_vers=2 ./configure --host=mips-linux-gnu --with-pcap=linux
 make

Download and decompress tcpdump
 CC=mips-linux-gnu-gcc ac_cv_linux_vers=2 ./configure --host=mips-linux-gnu --includedir=/to/the/path/libpcap --disable-ipv6
 make
Although I have managed to compile, it isn't work in the routers.

Any idea?

Thanks, best regards.

---


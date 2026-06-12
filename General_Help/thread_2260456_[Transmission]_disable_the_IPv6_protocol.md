---
title: "[Transmission] disable the IPv6 protocol"
date: 2015-01-12
forum: General Help
---

### Post by balubeto on 2015-01-12
Hi

In Transmission 2.84-b23 for Lubuntu, how do I completely disable the IPv6 protocol?

Thanks

Bye

---

### Post by kerry_s on 2015-01-12
just turn it off in you connection

---

### Post by rottenkittie on 2015-01-20
No, it's not a solution but poor's man workaround.


The problem with transmission and IPv6 is that transmission developers are...well, not the nicest, to say the least: [https://trac.transmissionbt.com/ticket/4197](https://trac.transmissionbt.com/ticket/4197)

So the user who need to (a) use IPv6 but (b) NOT use IPv6 with transmission is left alone.

Fortunately number of solutions or workarounds appeared.


1. What works for me - disable IPv6 detection and recompile the transmission:
Please note, this is for 2.61 but should work on 2.8x, too.
##[FONT=courier new]# transmission_2.6{0,1}_noIPv6.patch
--- libtransmission/net.orig    2015-01-20 12:38:50.467348076 +0000
+++ libtransmission/net.c       2015-01-20 12:56:26.243717573 +0000
@@ -576,7 +576,7 @@
     {
              int addrlen = 16;
                const int rc = tr_globalAddress( AF_INET6,
ipv6, &addrlen );
-        have_ipv6 = ( rc >= 0 ) && ( addrlen == 16 );
+        have_ipv6 = 0;  /** NO, we do not have IPv6 **/
         last_time = now;
     }[/FONT]

Now compile and prepare dpkg:

[FONT=courier new]mkdir $HOME/transmission_build/
export PKG_CONFIG_PATH="$HOME/transmission_build/libevent/lib/pkgconfig"
cd $HOME/transmission-2.60 && \
./configure && make && \
   checkinstall --pakdir "$HOME/transmission_build" --backup=no \
   --deldoc=yes --fstrans=no --deldesc=yes --delspec=yes --default \
   --pkgversion "2.84-b23-p1v6" --maintainer you@localhost && \
   make clean[/FONT]

Then install your transmission*.dpkg from [FONT=courier new]$HOME/transmission_build[/FONT]

Remember to set [FONT=courier new]bind-address-ipv6 [/FONT]to "fe80::" or "::1" in settings.json

2. disabling via curl (as, supposedly, transmission uses libcurl to contact trackers):
[FONT=courier new]https://gitorious.org/wive-rtnl-ralink-rt305x-routers-firmware/wive-rtnl-ralink-rt305x-routers-firmware/commit/9af44cf3ddc67a295a6764b775c0487934dd3881[/FONT]

3. setting the CURLOPTS to ignore IPv6 before you start transmission shoud help, too.


Please contact me on PM if you can't compile it on your own - I may provide you with the dpkg of the version 2.61 with that patch AND the noupload patch I made for myself - however I would prefer if you would try to compile it on your own - due to clarity of the actual changes to the source code (so there are no doubts about the binary, since I do not wish to spend even a single second on explaining that those are only chances to the original code)

---


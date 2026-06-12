---
title: "Pidgin Problem"
date: 2008-05-23
forum: General Help
---

### Post by Dr Zolygon on 2008-05-23
Pidgin closes immediately after opening. I ran it in terminal and it returned the following

```

paul@Nigbuntu:~$ pidgin
Segmentation fault
paul@Nigbuntu:~$ pidgin
*** glibc detected *** pidgin: double free or corruption (fasttop): 0x085f9808 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7650a85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb76544f0]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb77b18b1]
/usr/lib/libpurple.so.0(purple_dnsquery_destroy+0x90)[0xb78dcd57]
/usr/lib/libpurple.so.0[0xb78db9cb]
/usr/lib/libpurple.so.0[0xb78dc9f5]
pidgin[0x80abca3]
/usr/lib/libglib-2.0.so.0[0xb77ddc5d]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x178)[0xb77a9bf8]
/usr/lib/libglib-2.0.so.0[0xb77ace5e]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1e7)[0xb77ad1e7]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7c6b264]
pidgin(main+0xbbc)[0x80c70d5]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb75fb450]
pidgin[0x806c821]
======= Memory map: ========
08048000-08115000 r-xp 00000000 08:01 2343701    /usr/bin/pidgin
08115000-08118000 rw-p 000cc000 08:01 2343701    /usr/bin/pidgin
08118000-08616000 rw-p 08118000 00:00 0          [heap]
b4f00000-b4f21000 rw-p b4f00000 00:00 0
b4f21000-b5000000 ---p b4f21000 00:00 0
b50ce000-b512e000 rw-s 00000000 00:09 8912907    /SYSV00000000 (deleted)
b512e000-b5232000 rw-p b512e000 00:00 0
b5232000-b52b9000 r--p 00000000 08:01 2491927    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b52b9000-b52d0000 r--s 00000000 08:01 3498301    /var/lib/aspell/en_US-wo_accents-only.rws
b52d0000-b5558000 r--s 00000000 08:01 3498289    /var/lib/aspell/en-common.rws
b555a000-b565e000 rw-p b555a000 00:00 0
b565e000-b5660000 r-xp 00000000 08:01 2418683    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5660000-b5661000 rw-p 00001000 08:01 2418683    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5661000-b56f2000 r--p 00000000 08:01 2491928    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b56f2000-b56f8000 r--s 00000000 08:01 3498048    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b56f8000-b56fb000 r--s 00000000 08:01 3498058    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b56fb000-b56fc000 r--s 00000000 08:01 3498050    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b56fc000-b56fd000 r--s 00000000 08:01 3498043    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b56fd000-b5700000 r--s 00000000 08:01 3498049    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b5700000-b5703000 r--s 00000000 08:01 3498045    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b5703000-b5706000 r--s 00000000 08:01 3498055    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b5706000-b570e000 r--s 00000000 08:01 3498059    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b570e000-b5716000 r--s 00000000 08:01 3498038    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b5716000-b5719000 r--s 00000000 08:01 3498056    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b5719000-b5720000 r--s 00000000 08:01 3498053    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b5720000-b5726000 r--s 00000000 08:01 3498037    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b5726000-b57d1000 r--p 00000000 08:01 2574507    /usr/share/icons/Tangerine/icon-theme.cache
b57d1000-b57d5000 r-xp 00000000 08:01 2368557    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b57d5000-b57d6000 rw-p 00003000 08:01 2368557    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b57d6000-b57e8000 r-xp 00000000 08:01 2369015    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b57e8000-b57e9000 rw-p 00012000 08:01 2369015    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b57e9000-b582a000 r-xp 00000000 08:01 2346360    /usr/lib/nss/libnssckbi.so
b582a000-b5834000 rw-p 00041000 08:01 2346360    /usr/lib/nss/libnssckbi.so
b5834000-b586e000 r-xp 00000000 08:01 2346359    /usr/lib/nss/libfreebl3.so
b586e000-b586f000 rw-p 0003a000 08:01 2346359    /usr/lib/nss/libfreebl3.so
b586f000-b589f000 r-xp 00000000 08:01 2346363    /usr/lib/nss/libsoftokn3.so
b589f000-b58a0000 rw-p 00030000 08:01 2346363    /usr/lib/nss/libsoftokn3.so
b58a0000-b58a1000 ---p b58a0000 00:00 0
b58a1000-b60a1000 rw-p b58a1000 00:00 0
b60a1000-b61bc000 r-xp 00000000 08:01 2345184    /usr/lib/libperl.so.5.8.8
b61bc000-b61c1000 rw-p 0011a000 08:01 2345184    /usr/lib/libperl.so.5.8.8
b61c1000-b61c3000 rw-p b61c1000 00:00 0
b61c5000-b61c7000 r--s 00000000 08:01 3499768    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b61c7000-b61c8000 r-xp 00000000 08:01 2346458    /usr/lib/purple-2/libaim.so
b61c8000-b61c9000 rw-p 00001000 08:01 2346458    /usr/lib/purple-2/libaim.so
b61c9000-b61cb000 r-xp 00000000 08:01 2346486    /usr/lib/purple-2/statenotify.so
b61cb000-b61cc000 rw-p 00001000 08:01 2346486    /usr/lib/purple-2/statenotify.so
b61cc000-b61ce000 r-xp 00000000 08:01 2346457    /usr/lib/purple-2/joinpart.so
b61ce000-b61cf000 rw-p 00001000 08:01 2346457    /usr/lib/purple-2/joinpart.so
b61cf000-b61da000 r-xp 00000000 08:01 2346481    /usr/lib/purple-2/perl.so
b61da000-b61db000 rw-p 0000b000 08:01 2346481    /usr/lib/purple-2/perl.so
b61db000-b61dc000 r-xp 00000000 08:01 2346483    /usr/lib/purple-2/ssl-gnutls.so
b61dc000-b61dd000 rw-p 00000000 08:01 2346483    /usr/lib/purple-2/ssl-gnutls.so
b61dd000-b61f4000 r-xp 00000000 08:01 2346467    /usr/lib/purple-2/libmyspace.so
b61f4000-b61f6000 rw-p 00016000 08:01 2346467    /usr/lib/purple-2/libmyspace.so
b61f6000-b623c000 r-xp 00000000 08:01 2346471    /usr/lib/purple-2/liboscar.so.0.0.0
b623c000-b623e000 rw-p 00045000 08:01 2346471    /usr/lib/purple-2/liboscar.so.0.0.0
b623e000-b623f000 r-xp 00000000 08:01 2346461    /usr/lib/purple-2/libicq.so
b623f000-b6240000 rw-p 00001000 08:01 2346461    /usr/lib/purple-2/libicq.so
b6240000-b6250000 r-xp 00000000 08:01 2346459    /usr/lib/purple-2/libbonjour.so
b6250000-b6251000 rw-p 00010000 08:01 2346459    /usr/lib/purple-2/libbonjour.so
b6251000-b6252000 rw-p b6251000 00:00 0
b6252000-b6281000 r-xp 00000000 08:01 2346472    /usr/lib/purple-2/libqq.so
b6281000-b6282000 rw-p 0002f000 08:01 2346472    /usr/lib/purple-2/libqq.so
b6282000-b6284000 r-xp 00000000 08:01 2346480    /usr/lib/purple-2/offlinemsg.so
b6284000-b6285000 rw-p 00001000 08:01 2346480    /usr/lib/purple-2/offlinemsg.so
b6285000-b6297000 r-xp 00000000 08:01 2346462    /usr/lib/purple-2/libirc.so
b6297000-b6298000 rw-p 00012000 08:01 2346462    /usr/lib/purple-2/libirc.so
b6298000-b62a3000 r-xp 00000000 08:01 2346474    /usr/lib/purple-2/libsimple.so
b62a3000-b62a4000 rw-p 0000a000 08:01 2346474    /usr/lib/purple-2/libsimple.so
b62a4000-b62b4000 rw-p b62a4000 00:00 0
b62b4000-b62b8000 r-xp 00000000 08:01 2346484    /usr/lib/purple-2/ssl-nss.so
b62b8000-b62b9000 rw-p 00003000 08:01 2346484    /usr/lib/purple-2/ssl-nss.so
b62b9000-b62c3000 r-xp 00000000 08:01 2347111    /usr/lib/sasl2/libdigestmd5.so.2.0.22
b62c3000-b62c4000 rw-p 0000a000 08:01 2347111    /usr/lib/sasl2/libdigestmd5.so.2.0.22
b62c4000-b63ee000 r-xp 00000000 08:01 2375809    /usr/lib/i686/cmov/libcrypto.so.0.9.8
b63ee000-b6403000 rw-p 00129000 08:01 2375809    /usr/lib/i686/cmov/libcrypto.so.0.9.8
b6403000-b6406000 rw-p b6403000 00:00 0
b6406000-b6408000 r-xp 00000000 08:01 2346482    /usr/lib/purple-2/psychic.so
b6408000-b6409000 rw-p 00001000 08:01 2346482    /usr/lib/purple-2/psychic.so
b6409000-b640c000 r-xp 00000000 08:01 2347101    /usr/lib/sasl2/libanonymous.so.2.0.22
b640c000-b640d000 rw-p 00002000 08:01 2347101    /usr/lib/sasl2/libanonymous.so.2.0.22
b640d000-b6411000 r-xp 00000000 08:01 2347106    /usr/lib/sasl2/libcrammd5.so.2.0.22
b6411000-b6412000 rw-p 00003000 08:01 2347106    /usr/lib/sasl2/libcrammd5.so.2.0.22
b6412000-b6419000 r-xp 00000000 08:01 2347121    /usr/lib/sasl2/libntlm.so.2.0.22
b6419000-b641a000 rw-p 00006000 08:01 2347121    /usr/lib/sasl2/libntlm.so.2.0.22
b641a000-b6423000 r-xp 00000000 08:01 1353022    /lib/tls/i686/cmov/libcrypt-2.7.so
b6423000-b6425000 rw-p 00008000 08:01 1353022    /lib/tls/i686/cmov/libcrypt-2.7.so
b6425000-b644c000 rw-p b6425000 00:00 0
b644c000-b6462000 r-xp 00000000 08:01 2345252    /usr/lib/libsasl2.so.2.0.22
b6462000-b6463000 rw-p 00015000 08:01 2345252    /usr/lib/libsasl2.so.2.0.22
b6463000-b6464000 r-xp 00000000 08:01 2346479    /usr/lib/purple-2/newline.so
b6464000-b6465000 rw-p 00000000 08:01 2346479    /usr/lib/purple-2/newline.so
b6465000-b6468000 r-xp 00000000 08:01 2347116    /usr/lib/sasl2/liblogin.so.2.0.22
b6468000-b6469000 rw-p 00002000 08:01 2347116    /usr/lib/sasl2/liblogin.so.2.0.22
b6469000-b646e000 r-xp 00000000 08:01 2347131    /usr/lib/sasl2/libsasldb.so.2.0.22
b646e000-b646f000 rw-p 00004000 08:01 2347131    /usr/lib/sasl2/libsasldb.so.2.0.22
b646f000-b64a7000 r-xp 00000000 08:01 2346465    /usr/lib/purple-2/libjabber.so.0.0.0
b64a7000-b64a8000 rw-p 00038000 08:01 2346465    /usr/lib/purple-2/libjabber.so.0.0.0
b64a8000-b64ab000 rw-p b64a8000 00:00Aborted
paul@Nigbuntu:~$

```

:guitar:

---


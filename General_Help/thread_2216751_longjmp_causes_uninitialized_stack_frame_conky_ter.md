---
title: "longjmp causes uninitialized stack frame: conky terminated - BUT using conky"
date: 2014-04-13
forum: General Help
---

### Post by s-p-constantine on 2014-04-13
I've searched and found quite a few threads, but all seem to suggest upgrading from conky 1.8.x (standard with LTS12.04) to 1.9.

This I did, but still get the error.

Anyone seen this and fixed it?

(My conky crashes after 5 mins!)

```
*** longjmp causes uninitialized stack frame ***: conky terminated======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(__fortify_fail+0x37)[0x7f498c466f47]
/lib/x86_64-linux-gnu/libc.so.6(+0x10aebd)[0x7f498c466ebd]
/lib/x86_64-linux-gnu/libc.so.6(__longjmp_chk+0x33)[0x7f498c466e23]
/usr/lib/x86_64-linux-gnu/libcurl-gnutls.so.4(+0xca45)[0x7f498cc8ca45]
/lib/x86_64-linux-gnu/libpthread.so.0(+0xfcb0)[0x7f498e949cb0]
/lib/x86_64-linux-gnu/libc.so.6(__select+0x33)[0x7f498c449763]
conky[0x430076]
conky[0x408c53]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed)[0x7f498c37d76d]
conky[0x408c89]
======= Memory map: ========
00400000-00462000 r-xp 00000000 08:07 943                                /usr/bin/conky
00661000-00662000 r--p 00061000 08:07 943                                /usr/bin/conky
00662000-00664000 rw-p 00062000 08:07 943                                /usr/bin/conky
00664000-00688000 rw-p 00000000 00:00 0 
01986000-01b2a000 rw-p 00000000 00:00 0                                  [heap]
7f4954000000-7f495402a000 rw-p 00000000 00:00 0 
7f495402a000-7f4958000000 ---p 00000000 00:00 0 
7f4958000000-7f495802a000 rw-p 00000000 00:00 0 
7f495802a000-7f495c000000 ---p 00000000 00:00 0 
7f495c000000-7f495c021000 rw-p 00000000 00:00 0 
7f495c021000-7f4960000000 ---p 00000000 00:00 0 
7f4960000000-7f4960029000 rw-p 00000000 00:00 0 
7f4960029000-7f4964000000 ---p 00000000 00:00 0 
7f4964000000-7f4964021000 rw-p 00000000 00:00 0 
7f4964021000-7f4968000000 ---p 00000000 00:00 0 
7f496c000000-7f496c021000 rw-p 00000000 00:00 0 
7f496c021000-7f4970000000 ---p 00000000 00:00 0 
7f4974000000-7f4974021000 rw-p 00000000 00:00 0 
7f4974021000-7f4978000000 ---p 00000000 00:00 0 
7f497ade8000-7f497adfd000 r-xp 00000000 08:07 527944                     /lib/x86_64-linux-gnu/libgcc_s.so.1
7f497adfd000-7f497affc000 ---p 00015000 08:07 527944                     /lib/x86_64-linux-gnu/libgcc_s.so.1
7f497affc000-7f497affd000 r--p 00014000 08:07 527944                     /lib/x86_64-linux-gnu/libgcc_s.so.1
7f497affd000-7f497affe000 rw-p 00015000 08:07 527944                     /lib/x86_64-linux-gnu/libgcc_s.so.1
7f497affe000-7f497afff000 ---p 00000000 00:00 0 
7f497afff000-7f497b7ff000 rw-p 00000000 00:00 0 
7f497b7ff000-7f497b800000 ---p 00000000 00:00 0 
7f497b800000-7f497c000000 rw-p 00000000 00:00 0 
7f497c000000-7f497c021000 rw-p 00000000 00:00 0 
7f497c021000-7f4980000000 ---p 00000000 00:00 0 
7f4980081000-7f4980088000 r-xp 00000000 08:07 527972                     /lib/x86_64-linux-gnu/libnss_dns-2.15.so
7f4980088000-7f4980287000 ---p 00007000 08:07 527972                     /lib/x86_64-linux-gnu/libnss_dns-2.15.so
7f4980287000-7f4980288000 r--p 00006000 08:07 527972                     /lib/x86_64-linux-gnu/libnss_dns-2.15.so
7f4980288000-7f4980289000 rw-p 00007000 08:07 527972                     /lib/x86_64-linux-gnu/libnss_dns-2.15.so
7f4980289000-7f498028b000 r-xp 00000000 08:07 523498                     /lib/libnss_mdns4_minimal.so.2
7f498028b000-7f498048a000 ---p 00002000 08:07 523498                     /lib/libnss_mdns4_minimal.so.2
7f498048a000-7f498048b000 r--p 00001000 08:07 523498                     /lib/libnss_mdns4_minimal.so.2
7f498048b000-7f498048c000 rw-p 00002000 08:07 523498                     /lib/libnss_mdns4_minimal.so.2
7f498048c000-7f4980498000 r-xp 00000000 08:07 527974                     /lib/x86_64-linux-gnu/libnss_files-2.15.so
7f4980498000-7f4980697000 ---p 0000c000 08:07 527974                     /lib/x86_64-linux-gnu/libnss_files-2.15.so
7f4980697000-7f4980698000 r--p 0000b000 08:07 527974                     /lib/x86_64-linux-gnu/libnss_files-2.15.so
7f4980698000-7f4980699000 rw-p 0000c000 08:07 527974                     /lib/x86_64-linux-gnu/libnss_files-2.15.so
7f4980699000-7f49806a3000 r-xp 00000000 08:07 527978                     /lib/x86_64-linux-gnu/libnss_nis-2.15.so
7f49806a3000-7f49808a3000 ---p 0000a000 08:07 527978                     /lib/x86_64-linux-gnu/libnss_nis-2.15.so
7f49808a3000-7f49808a4000 r--p 0000a000 08:07 527978                     /lib/x86_64-linux-gnu/libnss_nis-2.15.so
7f49808a4000-7f49808a5000 rw-p 0000b000 08:07 527978                     /lib/x86_64-linux-gnu/libnss_nis-2.15.so
7f49808a5000-7f49808bc000 r-xp 00000000 08:07 527968                     /lib/x86_64-linux-gnu/libnsl-2.15.so
7f49808bc000-7f4980abb000 ---p 00017000 08:07 527968                     /lib/x86_64-linux-gnu/libnsl-2.15.so
7f4980abb000-7f4980abc000 r--p 00016000 08:07 527968                     /lib/x86_64-linux-gnu/libnsl-2.15.so
7f4980abc000-7f4980abd000 rw-p 00017000 08:07 527968                     /lib/x86_64-linux-gnu/libnsl-2.15.so
7f4980abd000-7f4980abf000 rw-p 00000000 00:00 0 
7f4980abf000-7f4980ac7000 r-xp 00000000 08:07 527970                     /lib/x86_64-linux-gnu/libnss_compat-2.15.so
7f4980ac7000-7f4980cc6000 ---p 00008000 08:07 527970                     /lib/x86_64-linux-gnu/libnss_compat-2.15.so
7f4980cc6000-7f4980cc7000 r--p 00007000 08:07 527970                     /lib/x86_64-linux-gnu/libnss_compat-2.15.so
7f4980cc7000-7f4980cc8000 rw-p 00008000 08:07 527970                     /lib/x86_64-linux-gnu/libnss_compat-2.15.so
7f4980cc8000-7f4980cc9000 ---p 00000000 00:00 0 
7f4980cc9000-7f49814c9000 rw-p 00000000 00:00 0 
7f49814c9000-7f49814ca000 ---p 00000000 00:00 0 
7f49814ca000-7f4981cca000 rw-p 00000000 00:00 0 
7f4981cca000-7f4981ccb000 ---p 00000000 00:00 0 
7f4981ccb000-7f49824cb000 rw-p 00000000 00:00 0 
7f49824cb000-7f49824cc000 ---p 00000000 00:00 0 
7f49824cc000-7f4982ccc000 rw-p 00000000 00:00 0 
7f4982ccc000-7f4982ccd000 ---p 00000000 00:00 0 
7f4982ccd000-7f49834cd000 rw-p 00000000 00:00 0 
7f49834cd000-7f49834ce000 ---p 00000000 00:00 0 
7f49834ce000-7f4983cce000 rw-p 00000000 00:00 0 
7f4983cce000-7f4983ccf000 ---p 00000000 00:00 0 
7f4983ccf000-7f49844cf000 rw-p 00000000 00:00 0 
7f49844cf000-7f49844d0000 ---p 00000000 00:00 0 
7f49844d0000-7f4984cd0000 rw-p 00000000 00:00 0 
7f4984cd0000-7f4984cd8000 r-xp 00000000 08:07 9245                       /usr/lib/x86_64-linux-gnu/libxcb-render.so.0.0.0
7f4984cd8000-7f4984ed8000 ---p 00008000 08:07 9245                       /usr/lib/x86_64-linux-gnu/libxcb-render.so.0.0.0
7f4984ed8000-7f4984ed9000 r--p 00008000 08:07 9245                       /usr/lib/x86_64-linux-gnu/libxcb-render.so.0.0.0
7f4984ed9000-7f4984eda000 rw-p 00009000 08:07 9245                       /usr/lib/x86_64-linux-gnu/libxcb-render.so.0.0.0
7f4984eda000-7f4984edc000 r-xp 00000000 08:07 9249                       /usr/lib/x86_64-linux-gnu/libxcb-shm.so.0.0.0
7f4984edc000-7f49850db000 ---p 00002000 08:07 9249                       /usr/lib/x86_64-linux-gnu/libxcb-shm.so.0.0.0
7f49850db000-7f49850dc000 r--p 00001000 08:07 9249                       /usr/lib/x86_64-linux-gnu/libxcb-shm.so.0.0.0
7f49850dc000-7f49850dd000 rw-p 00002000 08:07 9249                       /usr/lib/x86_64-linux-gnu/libxcb-shm.so.0.0.0
7f49850dd000-7f4985103000 r-xp 00000000 08:07 528000                     /lib/x86_64-linux-gnu/libpng12.so.0.46.0
7f4985103000-7f4985303000 ---p 00026000 08:07 528000                     /lib/x86_64-linux-gnu/libpng12.so.0.46.0
7f4985303000-7f4985304000 r--p 00026000 08:07 528000                     /lib/x86_64-linux-gnu/libpng12.so.0.46.0
7f4985304000-7f4985305000 rw-p 00027000 08:07 528000                     /lib/x86_64-linux-gnu/libpng12.so.0.46.0
7f4985305000-7f4985395000 r-xp 00000000 08:07 9098                       /usr/lib/x86_64-linux-gnu/libpixman-1.so.0.30.2
7f4985395000-7f4985594000 ---p 00090000 08:07 9098                       /usr/lib/x86_64-linux-gnu/libpixman-1.so.0.30.2
7f4985594000-7f498559b000 r--p 0008f000 08:07 9098                       /usr/lib/x86_64-linux-gnu/libpixman-1.so.0.30.2
7f498559b000-7f498559c000 rw-p 00096000 08:07 9098                       /usr/lib/x86_64-linux-gnu/libpixman-1.so.0.30.2
7f498559c000-7f4985655000 r-xp 00000000 08:07 8762                       /usr/lib/x86_64-linux-gnu/libcairo.so.2.11000.2
7f4985655000-7f4985854000 ---p 000b9000 08:07 8762                       /usr/lib/x86_64-linux-gnu/libcairo.so.2.11000.2
7f4985854000-7f4985856000 r--p 000b8000 08:07 8762                       /usr/lib/x86_64-linux-gnu/libcairo.so.2.11000.2
7f4985856000-7f4985857000 rw-p 000ba000 08:07 8762                       /usr/lib/x86_64-linux-gnu/libcairo.so.2.11000.2
7f4985857000-7f498585a000 rw-p 00000000 00:00 0 
7f498585a000-7f4985882000 r-xp 00000000 08:07 414286                     /usr/lib/conky/libcairo.so.0.0.0
7f4985882000-7f4985a81000 ---p 00028000 08:07 414286                     /usr/lib/conky/libcairo.so.0.0.0
7f4985a81000-7f4985a82000 r--p 00027000 08:07 414286                     /usr/lib/conky/libcairo.so.0.0.0
7f4985a82000-7f4985a83000 rw-p 00028000 08:07 414286                     /usr/lib/conky/libcairo.so.0.0.0
7f4985a83000-7f498616d000 r--p 00000000 08:07 5009                       /usr/lib/locale/locale-archive
7f498616d000-7f498617f000 r-xp 00000000 08:07 135503                     /usr/lib/x86_64-linux-gnu/pkcs11/gnome-keyring-pkcs11.so
7f498617f000-7f498637e000 ---p 00012000 08:07 135503                     /usr/lib/x86_64-linux-gnu/pkcs11/gnome-keyring-pkcs11.so
7f498637e000-7f4986380000 r--p 00011000 08:07 135503                     /usr/lib/x86_64-linux-gnu/pkcs11/gnome-keyring-pkcs11.so
7f4986380000-7f4986381000 rw-p 00013000 08:07 135503                     /usr/lib/x86_64-linux-gnu/pkcs11/gnome-keyring-pkcs11.so
7f4986381000-7f498638a000 r-xp 00000000 08:07 527931                     /lib/x86_64-linux-gnu/libcrypt-2.15.so
7f498638a000-7f498658a000 ---p 00009000 08:07 527931                     /lib/x86_64-linux-gnu/libcrypt-2.15.so
7f498658a000-7f498658b000 r--p 00009000 08:07 527931                     /lib/x86_64-linux-gnu/libcrypt-2.15.so
7f498658b000-7f498658c000 rw-p 0000a000 08:07 527931                     /lib/x86_64-linux-gnu/libcrypt-2.15.so
7f498658c000-7f49865ba000 rw-p 00000000 00:00 0 
7f49865ba000-7f4986658000 r-xp 00000000 08:07 9171                       /usr/lib/x86_64-linux-gnu/libsqlite3.so.0.8.6
7f4986658000-7f4986858000 ---p 0009e000 08:07 9171                       /usr/lib/x86_64-linux-gnu/libsqlite3.so.0.8.6
7f4986858000-7f498685a000 r--p 0009e000 08:07 9171                       /usr/lib/x86_64-linux-gnu/libsqlite3.so.0.8.6
7f498685a000-7f498685c000 rw-p 000a0000 08:07 9171                       /usr/lib/x86_64-linux-gnu/libsqlite3.so.0.8.6
7f498685c000-7f498685d000 rw-p 00000000 00:00 0 
7f498685d000-7f49868a2000 r-xp 00000000 08:07 8981                       /usr/lib/x86_64-linux-gnu/libhx509.so.5.0.0
7f49868a2000-7f4986aa2000 ---p 00045000 08:07 8981                       /usr/lib/x86_64-linux-gnu/libhx509.so.5.0.0
7f4986aa2000-7f4986aa4000 r--p 00045000 08:07 8981                       /usr/lib/x86_64-linux-gnu/libhx509.so.5.0.0
7f4986aa4000-7f4986aa6000 rw-p 00047000 08:07 8981                       /usr/lib/x86_64-linux-gnu/libhx509.so.5.0.0
7f4986aa6000-7f4986aa7000 rw-p 00000000 00:00 0 
7f4986aa7000-7f4986ab5000 r-xp 00000000 08:07 8975                       /usr/lib/x86_64-linux-gnu/libheimbase.so.1.0.0
7f4986ab5000-7f4986cb4000 ---p 0000e000 08:07 8975                       /usr/lib/x86_64-linux-gnu/libheimbase.so.1.0.0
7f4986cb4000-7f4986cb5000 r--p 0000d000 08:07 8975                       /usr/lib/x86_64-linux-gnu/libheimbase.so.1.0.0
7f4986cb5000-7f4986cb6000 rw-p 0000e000 08:07 8975                       /usr/lib/x86_64-linux-gnu/libheimbase.so.1.0.0
7f4986cb6000-7f4986cde000 r-xp 00000000 08:07 9231                       /usr/lib/x86_64-linux-gnu/libwind.so.0.0.0
7f4986cde000-7f4986edd000 ---p 00028000 08:07 9231                       /usr/lib/x86_64-linux-gnu/libwind.so.0.0.0
7f4986edd000-7f4986ede000 r--p 00027000 08:07 9231                       /usr/lib/x86_64-linux-gnu/libwind.so.0.0.0
7f4986ede000-7f4986edf000 rw-p 00028000 08:07 9231                       /usr/lib/x86_64-linux-gnu/libwind.so.0.0.0
7f4986edf000-7f4986ee2000 r-xp 00000000 08:07 527954                     /lib/x86_64-linux-gnu/libkeyutils.so.1.4
7f4986ee2000-7f49870e1000 ---p 00003000 08:07 527954                     /lib/x86_64-linux-gnu/libkeyutils.so.1.4
7f49870e1000-7f49870e2000 r--p 00002000 08:07 527954                     /lib/x86_64-linux-gnu/libkeyutils.so.1.4
7f49870e2000-7f49870e3000 rw-p 00003000 08:07 527954                     /lib/x86_64-linux-gnu/libkeyutils.so.1.4
7f49870e3000-7f49870f7000 r-xp 00000000 08:07 9133                       /usr/lib/x86_64-linux-gnu/libroken.so.18.1.0
7f49870f7000-7f49872f6000 ---p 00014000 08:07 9133                       /usr/lib/x86_64-linux-gnu/libroken.so.18.1.0
7f49872f6000-7f49872f7000 r--p 00013000 08:07 9133                       /usr/lib/x86_64-linux-gnu/libroken.so.18.1.0
7f49872f7000-7f49872f8000 rw-p 00014000 08:07 9133                       /usr/lib/x86_64-linux-gnu/libroken.so.18.1.0
7f49872f8000-7f4987329000 r-xp 00000000 08:07 8973                       /usr/lib/x86_64-linux-gnu/libhcrypto.so.4.1.0
7f4987329000-7f4987529000 ---p 00031000 08:07 8973                       /usr/lib/x86_64-linux-gnu/libhcrypto.so.4.1.0
7f4987529000-7f498752a000 r--p 00031000 08:07 8973                       /usr/lib/x86_64-linux-gnu/libhcrypto.so.4.1.0
7f498752a000-7f498752b000 rw-p 00032000 08:07 8973                       /usr/lib/x86_64-linux-gnu/libhcrypto.so.4.1.0
7f498752b000-7f498752c000 rw-p 00000000 00:00 0 
7f498752c000-7f49875c7000 r-xp 00000000 08:07 8728                       /usr/lib/x86_64-linux-gnu/libasn1.so.8.0.0
7f49875c7000-7f49877c6000 ---p 0009b000 08:07 8728                       /usr/lib/x86_64-linux-gnu/libasn1.so.8.0.0
7f49877c6000-7f49877c8000 r--p 0009a000 08:07 8728                       /usr/lib/x86_64-linux-gnu/libasn1.so.8.0.0
7f49877c8000-7f49877cc000 rw-p 0009c000 08:07 8728                       /usr/lib/x86_64-linux-gnu/libasn1.so.8.0.0
7f49877cc000-7f498784c000 r-xp 00000000 08:07 9006                       /usr/lib/x86_64-linux-gnu/libkrb5.so.26.0.0
7f498784c000-7f4987a4c000 ---p 00080000 08:07 9006                       /usr/lib/x86_64-linux-gnu/libkrb5.so.26.0.0
7f4987a4c000-7f4987a4e000 r--p 00080000 08:07 9006                       /usr/lib/x86_64-linux-gnu/libkrb5.so.26.0.0
7f4987a4e000-7f4987a52000 rw-p 00082000 08:07 9006                       /usr/lib/x86_64-linux-gnu/libkrb5.so.26.0.0
7f4987a52000-7f4987a58000 r-xp 00000000 08:07 8977                       /usr/lib/x86_64-linux-gnu/libheimntlm.so.0.1.0
7f4987a58000-7f4987c57000 ---p 00006000 08:07 8977                       /usr/lib/x86_64-linux-gnu/libheimntlm.so.0.1.0
7f4987c57000-7f4987c58000 r--p 00005000 08:07 8977                       /usr/lib/x86_64-linux-gnu/libheimntlm.so.0.1.0
7f4987c58000-7f4987c59000 rw-p 00006000 08:07 8977                       /usr/lib/x86_64-linux-gnu/libheimntlm.so.0.1.0



```

---

### Post by s-p-constantine on 2014-05-02
This is fixed with 14.04...

---


---
title: "Error while compiling driver"
date: 2008-05-31
forum: General Help
---

### Post by luigibanzato on 2008-05-31
Hello,

Trying to compile a wireless card driver, getting the following error:

```
$./makedrv 
./ieee80211/
./ieee80211/ieee80211_module.c
./ieee80211/ieee80211_rx.c
./ieee80211/tags
./ieee80211/Makefile
./ieee80211/ieee80211_crypt_tkip.c
./ieee80211/ieee80211_softmac.c
./ieee80211/readme
./ieee80211/ieee80211_crypt_ccmp.c
./ieee80211/ieee80211.h
./ieee80211/ieee80211_tx.c
./ieee80211/ieee80211_softmac_wx.c
./ieee80211/ieee80211_crypt.h
./ieee80211/ieee80211_wx.c
./ieee80211/license
./ieee80211/ieee80211_crypt_wep.c
./ieee80211/ieee80211_crypt.c
rtl8185/
rtl8185/README.adhoc
rtl8185/r8180_sa2400.h
rtl8185/Makefile
rtl8185/copying
rtl8185/README.master
rtl8185/r8180.h
rtl8185/install
rtl8185/r8180_max2820.h
rtl8185/r8180_max2820.c
rtl8185/r8180_rtl8225.h
rtl8185/r8180_wx.h
rtl8185/authors
rtl8185/tags
rtl8185/r8180_pm.c
rtl8185/r8180_hw.h
rtl8185/r8180_gct.c
rtl8185/r8180_gct.h
rtl8185/r8180_rtl8225.c
rtl8185/readme
rtl8185/r8180_93cx6.h
rtl8185/ieee80211.h
rtl8185/license
rtl8185/r8180_pm.h
rtl8185/changes
rtl8185/r8180_rtl8225z2.c
rtl8185/r8180_wx.c
rtl8185/r8180_rtl8255.c
rtl8185/r8180_93cx6.c
rtl8185/r8180_sa2400.c
rtl8185/r8180_core.c
rtl8185/r8180_rtl8255.h
rtl8185/ieee80211_crypt.h
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/tmp
make -C /lib/modules/2.6.24-17-generic/build M=/home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'
  CC [M]  /home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.o
/home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_init’:
/home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2236: warning: assignment from incompatible pointer type
/home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2237: warning: assignment from incompatible pointer type
/home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2238: warning: assignment from incompatible pointer type
/home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2239: warning: assignment from incompatible pointer type
/home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2240: warning: assignment from incompatible pointer type
/home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2241: warning: assignment from incompatible pointer type
  CC [M]  /home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_rx.o
  CC [M]  /home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_tx.o
  CC [M]  /home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_wx.o
  CC [M]  /home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_module.o
  CC [M]  /home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt.o
  CC [M]  /home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.o
/home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_aes_encrypt’:
/home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:88: warning: passing argument 1 of ‘crypto_cipher_encrypt_one’ from incompatible pointer type
/home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_init’:
/home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:110: warning: assignment from incompatible pointer type
/home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:127: warning: passing argument 1 of ‘crypto_free_cipher’ from incompatible pointer type
/home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_deinit’:
/home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:144: warning: passing argument 1 of ‘crypto_free_cipher’ from incompatible pointer type
/home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_set_key’:
/home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:422: warning: passing argument 1 of ‘crypto_cipher_setkey’ from incompatible pointer type
  CC [M]  /home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.o
/home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c: In function ‘ieee80211_tkip_encrypt’:
/home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c:417: error: ‘struct scatterlist’ has no member named ‘page’
/home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c: In function ‘ieee80211_tkip_decrypt’:
/home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c:511: error: ‘struct scatterlist’ has no member named ‘page’
/home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c: In function ‘michael_mic’:
/home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c:613: error: ‘struct scatterlist’ has no member named ‘page’
/home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c:617: error: ‘struct scatterlist’ has no member named ‘page’
make[2]: *** [/home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.o] Error 1
make[1]: *** [_module_/home/luigi/rtl8185_linux_26.1027.0823.2007/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'
make: *** [modules] Error 2
rm -f *.mod.c *.mod *.o .*.cmd *.ko *~
rm -rf /home/luigi/rtl8185_linux_26.1027.0823.2007/rtl8185/tmp
make -C /lib/modules/2.6.24-17-generic/build M=/home/luigi/rtl8185_linux_26.1027.0823.2007/rtl8185 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'
  CC [M]  /home/luigi/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.o
/home/luigi/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c: In function ‘rtl8180_proc_module_init’:
/home/luigi/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:588: error: ‘proc_net’ undeclared (first use in this function)
/home/luigi/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:588: error: (Each undeclared identifier is reported only once
/home/luigi/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:588: error: for each function it appears in.)
/home/luigi/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c: In function ‘rtl8180_proc_module_remove’:
/home/luigi/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:594: error: ‘proc_net’ undeclared (first use in this function)
/home/luigi/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c: In function ‘rtl8180_init’:
/home/luigi/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:3159: warning: assignment from incompatible pointer type
/home/luigi/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:3522: error: ‘SA_SHIRQ’ undeclared (first use in this function)
/home/luigi/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:3522: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/luigi/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c: In function ‘rtl8180_pci_probe’:
/home/luigi/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:4213: error: implicit declaration of function ‘SET_MODULE_OWNER’
make[2]: *** [/home/luigi/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.o] Error 1
make[1]: *** [_module_/home/luigi/rtl8185_linux_26.1027.0823.2007/rtl8185] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'
make: *** [modules] Error 2

```

Anyone got a clue of what should I do?

Thanks in advance.

---

### Post by luigibanzato on 2008-05-31
Nevermind. Solved using another driver instead.

---

### Post by Gasoile on 2008-06-07
```
root@gasoileasus:/home/gasoile/Desktop/Wirless/ieee80211-1.2.18# make
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.24-18-generic for ieee80211 components...
make -C /lib/modules/2.6.24-18-generic/build M=/home/gasoile/Desktop/Wirless/ieee80211-1.2.18 modules
make[1]: Entrando no diretório `/usr/src/linux-headers-2.6.24-18-generic'
/home/gasoile/Desktop/Wirless/ieee80211-1.2.18/Makefile:17: 
/home/gasoile/Desktop/Wirless/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/gasoile/Desktop/Wirless/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/gasoile/Desktop/Wirless/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/gasoile/Desktop/Wirless/ieee80211-1.2.18/Makefile:21: 
  CC [M]  /home/gasoile/Desktop/Wirless/ieee80211-1.2.18/ieee80211_module.o
/home/gasoile/Desktop/Wirless/ieee80211-1.2.18/ieee80211_module.c: Na função &#8216;ieee80211_init&#8217;:
/home/gasoile/Desktop/Wirless/ieee80211-1.2.18/ieee80211_module.c:268: erro: &#8216;proc_net&#8217; undeclared (first use in this function)
/home/gasoile/Desktop/Wirless/ieee80211-1.2.18/ieee80211_module.c:268: erro: (Each undeclared identifier is reported only once
/home/gasoile/Desktop/Wirless/ieee80211-1.2.18/ieee80211_module.c:268: erro: for each function it appears in.)
/home/gasoile/Desktop/Wirless/ieee80211-1.2.18/ieee80211_module.c: Na função &#8216;ieee80211_exit&#8217;:
/home/gasoile/Desktop/Wirless/ieee80211-1.2.18/ieee80211_module.c:297: erro: &#8216;proc_net&#8217; undeclared (first use in this function)
make[2]: ** [/home/gasoile/Desktop/Wirless/ieee80211-1.2.18/ieee80211_module.o] Erro 1
make[1]: ** [_module_/home/gasoile/Desktop/Wirless/ieee80211-1.2.18] Erro 2
make[1]: Saindo do diretório `/usr/src/linux-headers-2.6.24-18-generic'
make: ** [modules] Erro 2
```

> **luigibanzato said:**
> Nevermind. Solved using another driver instead.

It seems that I'm with the same problem!
What driver did you use???

Thanks

---

### Post by selepo on 2009-06-28
Have a look at this post. I think you need to modify some of the files...

http://ubuntuforums.org/showpost.php?p=6688433&postcount=2]this%20post[/URL].%20Now,%20if%20you%20want%20to%20enable%20injection,%20you%27ll%20need%20to%20follow[URL=%22http://ubuntuforums.org/showpost.php?p=6934824&postcount=34

It doesn't seem to solve all issues with the complie though :(

---


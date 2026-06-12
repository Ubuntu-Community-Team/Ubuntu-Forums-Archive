---
title: "Lots of compiling warnings and errors wen compiling ipw2200 drivers!"
date: 2008-06-11
forum: General Help
---

### Post by Gasoile on 2008-06-11
Hi

I tried to compile the ieee80211 on Ubuntu 8.04 kernel version 2.6.24-18, and i got this...

```
# sudo make
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
/home/gasoile/Desktop/Wirless/ieee80211-1.2.18/ieee80211_module.c: Na função ‘ieee80211_init’:
/home/gasoile/Desktop/Wirless/ieee80211-1.2.18/ieee80211_module.c:268: erro: ‘proc_net’ undeclared (first use in this function)
/home/gasoile/Desktop/Wirless/ieee80211-1.2.18/ieee80211_module.c:268: erro: (Each undeclared identifier is reported only once
/home/gasoile/Desktop/Wirless/ieee80211-1.2.18/ieee80211_module.c:268: erro: for each function it appears in.)
/home/gasoile/Desktop/Wirless/ieee80211-1.2.18/ieee80211_module.c: Na função ‘ieee80211_exit’:
/home/gasoile/Desktop/Wirless/ieee80211-1.2.18/ieee80211_module.c:297: erro: ‘proc_net’ undeclared (first use in this function)
make[2]: ** [/home/gasoile/Desktop/Wirless/ieee80211-1.2.18/ieee80211_module.o] Erro 1
make[1]: ** [_module_/home/gasoile/Desktop/Wirless/ieee80211-1.2.18] Erro 2
make[1]: Saindo do diretório `/usr/src/linux-headers-2.6.24-18-generic'
make: ** [modules] Erro 2
```

Someone tels me that my kernel version already have the ieee80211 and i tried to compile the ipw2200 patched drivers pointing to my ieee80211 directory, and i get this...

```
# sudo make IEEE80211_INC=/lib/modules/2.6.24-18-generic/build/include/
mkdir -p /home/gasoile/Wirless/ipw2200-1.2.1/tmp/.tmp_versions
make -C /lib/modules/2.6.24-18-generic/build M=/home/gasoile/Wirless/ipw2200-1.2.1 MODVERDIR=/home/gasoile/Wirless/ipw2200-1.2.1/tmp/.tmp_versions modules
make[1]: Entrando no diretório `/usr/src/linux-headers-2.6.24-18-generic'
  CC [M]  /home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.o
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c: In function ‘ipw_send_adapter_address’:
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:2388: error: implicit declaration of function ‘MAC_ARG’
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:2388: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c: In function ‘ipw_add_station’:
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:3965: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c: In function ‘ipw_send_disassociate’:
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:4004: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c: In function ‘ipw_rx_notification’:
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:4529: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:4611: warning: format ‘%02x’ expects type ‘unsigned int’, but argument 7 has type ‘const char *’
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:4611: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:4636: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:4665: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:4705: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:4723: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c: In function ‘ipw_find_adhoc_network’:
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5564: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5574: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5587: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5606: warning: format ‘%02x’ expects type ‘unsigned int’, but argument 6 has type ‘const char *’
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5606: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5635: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5646: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5657: warning: format ‘%02x’ expects type ‘unsigned int’, but argument 6 has type ‘char * const’
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5657: warning: format ‘%02x’ expects type ‘unsigned int’, but argument 7 has type ‘char * const’
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5657: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5670: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5680: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5691: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5700: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5714: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c: In function ‘ipw_best_network’:
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5783: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5793: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5806: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5824: warning: format ‘%02x’ expects type ‘unsigned int’, but argument 6 has type ‘const char *’
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5824: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5840: warning: format ‘%02x’ expects type ‘unsigned int’, but argument 6 has type ‘const char *’
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5840: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5853: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5866: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5877: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5888: warning: format ‘%02x’ expects type ‘unsigned int’, but argument 6 has type ‘char * const’
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5888: warning: format ‘%02x’ expects type ‘unsigned int’, but argument 7 has type ‘char * const’
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5888: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5901: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5910: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5920: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5930: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5939: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:5954: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c: In function ‘ipw_debug_config’:
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:6216: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c: In function ‘ipw_associate_network’:
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:7602: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c: In function ‘ipw_handle_mgmt_packet’:
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:8406: error: ‘struct sk_buff’ has no member named ‘mac’
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c: In function ‘ipw_rx’:
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:8553: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c: In function ‘ipw_wx_set_wap’:
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:9127: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c: In function ‘ipw_wx_get_wap’:
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:9156: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c: In function ‘ipw_tx_skb’:
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:10382: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c: In function ‘ipw_net_set_mac_address’:
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:10706: warning: too few arguments for format
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c: In function ‘ipw_pci_probe’:
/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.c:11945: error: implicit declaration of function ‘SET_MODULE_OWNER’
make[2]: ** [/home/gasoile/Wirless/ipw2200-1.2.1/ipw2200.o] error 1
make[1]: ** [_module_/home/gasoile/Wirless/ipw2200-1.2.1] error 2
make[1]: Saindo do diretório `/usr/src/linux-headers-2.6.24-18-generic'
make: ** [modules] error 2
```

Anyone can help me???

---


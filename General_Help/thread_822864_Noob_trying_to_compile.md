---
title: "Noob trying to compile"
date: 2008-06-08
forum: General Help
---

### Post by spliffeh on 2008-06-08
I have these files:

> 
aircrack-ptw.c      aircrack-ptw-lib.h  Makefile
aircrack-ptw-lib.c  attacksim.c         README


I've never compiled before, so I did

> 
sudo apt-get install build-essential
sudo apt-get install automake


That seemed to go okay. So now when I type ./configure I get:

> 
bash: ./configure: No such file or directory


and when I go in the directory and type "make" I get:

> 
gcc -o aircrack-ptw -Wall -fomit-frame-pointer -O3 -lpcap aircrack-ptw.c aircrack-ptw-lib.c
aircrack-ptw.c:5:18: error: pcap.h: No such file or directory
aircrack-ptw.c: In function ‘main’:
aircrack-ptw.c:33: error: ‘PCAP_ERRBUF_SIZE’ undeclared (first use in this function)
aircrack-ptw.c:33: error: (Each undeclared identifier is reported only once
aircrack-ptw.c:33: error: for each function it appears in.)
aircrack-ptw.c:34: error: ‘pcap_t’ undeclared (first use in this function)
aircrack-ptw.c:34: error: ‘descr’ undeclared (first use in this function)
aircrack-ptw.c:55: warning: implicit declaration of function ‘pcap_open_offline’
aircrack-ptw.c:60: warning: implicit declaration of function ‘pcap_datalink’
aircrack-ptw.c:60: error: ‘DLT_IEEE802_11’ undeclared (first use in this function)
aircrack-ptw.c:64: warning: implicit declaration of function ‘pcap_next_ex’
aircrack-ptw.c:65: error: dereferencing pointer to incomplete type
aircrack-ptw.c:65: error: dereferencing pointer to incomplete type
aircrack-ptw.c:33: warning: unused variable ‘errbuf’
make: *** [aircrack-ptw] Error 1



.....what am I doing wrong here?

---

### Post by adam_89 on 2008-06-08
try this:
```

sudo apt-get install libpcap0.8 libpcap0.8-dev 

```

---

### Post by Crafty Kisses on 2008-06-08
> **adam_89 said:**
> try this:
```

sudo apt-get install libpcap0.8 libpcap0.8-dev 

```

Yes, you need that package, I had the same problem when I was trying to compile RainbowCrack.

---


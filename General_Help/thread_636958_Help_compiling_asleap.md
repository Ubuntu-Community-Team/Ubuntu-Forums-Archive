---
title: "Help compiling asleap"
date: 2007-12-10
forum: General Help
---

### Post by cwisham on 2007-12-10
Hi All,
I am trying to compile asleap-1.4 and receiving the below errors. I am running  2.6.22-14-generic #1 SMP 

Please help if you can.

Thank you
Chris

cc -pipe -Wall -D_LINUX -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE  -O4 -D_OPENSSL_MD4 -g3 -ggdb ajinject.c -c
ajinject.c:28:22: error: pcap-bpf.h: No such file or directory
In file included from ajinject.c:35:
/usr/include/linux/wireless.h:886: error: ‘IFNAMSIZ’ undeclared here (not in a function)
ajinject.c: In function ‘aj_setmonitor’:
ajinject.c:104: error: storage size of ‘req’ isn’t known
ajinject.c:104: warning: unused variable ‘req’
ajinject.c: In function ‘aj_setmode’:
ajinject.c:138: error: storage size of ‘req’ isn’t known
ajinject.c:138: warning: unused variable ‘req’
ajinject.c: In function ‘aj_setchannel’:
ajinject.c:172: error: storage size of ‘req’ isn’t known
ajinject.c:172: warning: unused variable ‘req’
ajinject.c: In function ‘aj_setessid’:
ajinject.c:206: error: storage size of ‘req’ isn’t known
ajinject.c:224: warning: pointer targets in passing argument 1 of ‘__builtin_strncpy’ differ in signedness
ajinject.c:206: warning: unused variable ‘req’
ajinject.c: In function ‘aj_setmac’:
ajinject.c:240: error: storage size of ‘req’ isn’t known
ajinject.c:240: warning: unused variable ‘req’
ajinject.c: In function ‘aj_ifupdown’:
ajinject.c:366: error: storage size of ‘ifr’ isn’t known
ajinject.c:388: error: ‘IFF_UP’ undeclared (first use in this function)
ajinject.c:388: error: (Each undeclared identifier is reported only once
ajinject.c:388: error: for each function it appears in.)
ajinject.c:366: warning: unused variable ‘ifr’
ajinject.c: In function ‘aj_getsocket’:
ajinject.c:410: error: storage size of ‘req’ isn’t known
ajinject.c:421: error: invalid application of ‘sizeof’ to incomplete type ‘struct ifreq’ 
ajinject.c:410: warning: unused variable ‘req’
make: *** [ajinject.o] Error 1

---

### Post by Dryw Paulic on 2007-12-11
Hi Chris,

Looks like your missing the pcap development libraries: 

```
sudo apt-get install libpcap0.8-dev
```

Should fix you up. Btw, I assume you're using this tool for legitimate purposes ;)

---

### Post by cwisham on 2007-12-11
Thank you very much for the reply. I am using the tool for good. I am a security analyst by trade and new to ubuntu. I have installed this tool in my fedora days without issue. I installed the pcap package and now get this error stream:

sudo make
cc -pipe -Wall -D_LINUX -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE  -O4 -D_OPENSSL_MD4 -g3 -ggdb ajinject.c -c
In file included from ajinject.c:35:
/usr/include/linux/wireless.h:886: error: ‘IFNAMSIZ’ undeclared here (not in a function)
ajinject.c: In function ‘aj_setmonitor’:
ajinject.c:104: error: storage size of ‘req’ isn’t known
ajinject.c:104: warning: unused variable ‘req’
ajinject.c: In function ‘aj_setmode’:
ajinject.c:138: error: storage size of ‘req’ isn’t known
ajinject.c:138: warning: unused variable ‘req’
ajinject.c: In function ‘aj_setchannel’:
ajinject.c:172: error: storage size of ‘req’ isn’t known
ajinject.c:172: warning: unused variable ‘req’
ajinject.c: In function ‘aj_setessid’:
ajinject.c:206: error: storage size of ‘req’ isn’t known
ajinject.c:224: warning: pointer targets in passing argument 1 of ‘__builtin_strncpy’ differ in signedness
ajinject.c:206: warning: unused variable ‘req’
ajinject.c: In function ‘aj_setmac’:
ajinject.c:240: error: storage size of ‘req’ isn’t known
ajinject.c:240: warning: unused variable ‘req’
ajinject.c: In function ‘aj_ifupdown’:
ajinject.c:366: error: storage size of ‘ifr’ isn’t known
ajinject.c:388: error: ‘IFF_UP’ undeclared (first use in this function)
ajinject.c:388: error: (Each undeclared identifier is reported only once
ajinject.c:388: error: for each function it appears in.)
ajinject.c:366: warning: unused variable ‘ifr’
ajinject.c: In function ‘aj_getsocket’:
ajinject.c:410: error: storage size of ‘req’ isn’t known
ajinject.c:421: error: invalid application of ‘sizeof’ to incomplete type ‘struct ifreq’ 
ajinject.c:410: warning: unused variable ‘req’
make: *** [ajinject.o] Error 1

---

### Post by Dryw Paulic on 2007-12-11
Hi Chris,

Are you running Feisty Fawn? I compiled this on a dapper/gutsy system with no issues. However I just tried compiling on fiesty and this is what I needed to do to get it to work:

Add the following line to /usr/include/linux/wireless.h at the very top: 

```
#include <linux/if.h>
```

Then take care of dependencies:

```
sudo apt-get install libssl-dev
```

```
sudo apt-get install libpcap0.8-dev
```

Hope this works for you!

---

### Post by cwisham on 2007-12-11
SOLVED.

Thank you very much for your help. I am using gutsy. I guess that I was missing the deps. and the code addition.This user community is why I made the switch to ubuntu.

Chris

---

### Post by Dryw Paulic on 2007-12-11
Yeah, not sure why that code snippet is missing from wireless.h. It might be an upstream bug. I'll have to look into it and file a bug report if necessary. I'll file it on my @ home todo list :)

The community here is awesome. I've lurked this forum for a long time and there are not many issues that go unsolved. =D>

-Dryw

---


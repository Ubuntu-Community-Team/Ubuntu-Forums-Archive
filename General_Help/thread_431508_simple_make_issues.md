---
title: "simple make issues"
date: 2007-05-03
forum: General Help
---

### Post by mrchrisblau on 2007-05-03
So i'm trying to install aircrack 2.41 from a tgz file. I extract to the desktop then run

```
sudo make
```

inside the folder i just extracted.

Then it gives me the following errors:

```
chris@greyhat:~/Desktop/aircrack-2.41$ sudo make
Password:
gcc -g -W -Wall -O2 -D_FILE_OFFSET_BITS=64 -D_MAJ=2 -D_MIN=41 linux/airodump.c -o airodump
In file included from linux/airodump.c:29:
/usr/include/linux/wireless.h:882: error: ‘IFNAMSIZ’ undeclared here (not in a function)
linux/airodump.c: In function ‘disable_wep_key’:
linux/airodump.c:1390: error: ‘struct iwreq’ has no member named ‘ifr_name’
linux/airodump.c: In function ‘set_channel’:
linux/airodump.c:1440: error: ‘struct iwreq’ has no member named ‘ifr_name’
linux/airodump.c: In function ‘set_monitor’:
linux/airodump.c:1484: error: ‘struct iwreq’ has no member named ‘ifr_name’
linux/airodump.c: In function ‘main’:
linux/airodump.c:1556: error: storage size of ‘ifr’ isn’t known
linux/airodump.c:1670: error: ‘IFF_UP’ undeclared (first use in this function)
linux/airodump.c:1670: error: (Each undeclared identifier is reported only once
linux/airodump.c:1670: error: for each function it appears in.)
linux/airodump.c:1670: error: ‘IFF_BROADCAST’ undeclared (first use in this function)
linux/airodump.c:1670: error: ‘IFF_RUNNING’ undeclared (first use in this function)
linux/airodump.c:1556: warning: unused variable ‘ifr’
make: *** [airodump] Error 1

```

I installed build-essential (as per somebody else's recommendation). 

What do I need to do to be able to install it?

---

### Post by jfinkels on 2007-05-03
Typically, you don't need to run "make" as root. Your typical config and compile should look something like this:
```

./configure --prefix=/usr
make
sudo checkinstall

```
(I highly recommend installing checkinstall, it's in the repos. It'll make a .deb for you)

Also, you could try installing from Synaptic :D

---


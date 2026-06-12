---
title: "Regretting upgrading to Hardy!"
date: 2008-04-23
forum: General Help
---

### Post by dave333 on 2008-04-23
Today I upgraded my work PC to Hardy, and have had a number of problems.

First off, X decided to give me a virtual resolution higher than my monitor resolution, so I had to scroll the entire screen to see all of it. A quick change to Xorg.conf and it was back to normal.

Next, PHP will no longer connect to the local MySQL server using mysql_connect("localhost","username","password). Replacing localhost with 127.0.0.1 works fine - not sure why??

Thirdly, and most annoyingly, Compiz seems to be really screwed. I'm getting huge shadows on windows (just on the title bars, above the windows) and whenever I press a number on the numeric keyboard, I get a segfault and X restarts

```
[ 2684.774653] compiz.real[10456]: segfault at 0572014d eip 08055a80 esp bf995e60 error 4
[ 2684.870573] [fglrx] interrupt source 10000000 successfully disabled!
[ 2684.870578] [fglrx] enable ID = 0x00000000
[ 2684.870581] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000009
[ 2684.870591] [fglrx] interrupt source 20008000 successfully disabled!
[ 2684.870593] [fglrx] enable ID = 0x00000000
[ 2684.870595] [fglrx] Receive disable interrupt message with irqEnableMask: 20008000; dwIRQEnableId: 00000008
[ 2687.398190] [fglrx] PCIe has already been initialized. Reinitializing ...
[ 2687.419283] [fglrx] Reserve Block - 0 offset =  0X1000000 length = 0X5000
[ 2687.419287] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[ 2687.419290] [fglrx] Reserve Block - 2 offset =  0X7fff000 length = 0X1000
[ 2687.419292] [fglrx] Reserve Block - 3 offset =  0X7fbf000 length = 0X40000
[ 2687.457335] [fglrx] interrupt source 20008000 successfully enabled
[ 2687.457344] [fglrx] enable ID = 0x00000008
[ 2687.457358] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[ 2687.457431] [fglrx] interrupt source 10000000 successfully enabled
[ 2687.457437] [fglrx] enable ID = 0x00000009
[ 2687.457442] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000

```

Anyone able to offer any advice on the 2 problems. I really don't want to have to re-install gutsy!

---

### Post by OoooMatron on 2008-04-23
you need to edit /etc/hosts and add 127.0.0.1 as the localhost. should fix that one.

---

### Post by dave333 on 2008-04-24
Thanks but that hasn't done the trick. 

I've fixed the segfault in Compiz. After removing Compiz, I was still getting the same symptoms, but a segfault in Xgl. I re-installed the xgl and all xserver packages that were installed and this seems to have fixed the problem.

---

### Post by PmDematagoda on 2008-04-24
Please understand this, Ubuntu 8.04 has not yet been released, so when you upgraded you actually upgraded to Ubuntu 8.04 RC not the final version.

Please wait until Hardy is released and then try updating again.

---


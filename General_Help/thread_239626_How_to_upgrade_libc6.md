---
title: "How to upgrade libc6"
date: 2006-08-19
forum: General Help
---

### Post by BlackBottle on 2006-08-19
Ok, so I need to upgrade libc6 from 2.3.6 to 2.4 and what a stupid problem am I running into..

anything i try to upgrade it, it finds something that depends on old version 2.3.6 and refuses to go further.



~> sudo dpkg -i libc6-pic_2.4-1ubuntu9_i386.deb
(Reading database ... 96758 files and directories currently installed.)
Preparing to replace libc6-pic 2.4-1ubuntu9 (using libc6-pic_2.4-1ubuntu9_i386.deb) ...
Unpacking replacement libc6-pic ...
dpkg: dependency problems prevent configuration of libc6-pic:
 libc6-pic depends on libc6 (= 2.4-1ubuntu9); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
dpkg: error processing libc6-pic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6-pic


Stupid! Of course current version of libc6 is NOT 2.4, thats why I'm upgrading it.

i tried several cycles of -f install and remove but nothing came forward! for example this is my history:
   186  12:00   dpkg -i libc6-pic_2.4-1ubuntu9_i386.deb
   187  12:00   sudo dpkg -i libc6-pic_2.4-1ubuntu9_i386.deb
   188  12:02   sudo apt-get install libc6-pic
   189  12:02   sudo apt-get -f install
   190  12:02   sudo apt-get -f install
   191  12:02   sudo apt-get install libc6-pic
   192  12:02   sudo dpkg -i libc6-pic_2.4-1ubuntu9_i386.deb
   193  12:02   sudo apt-get -f install
   194  12:02   sudo apt-get -f install
   195  12:02   sudo dpkg -i libc6-pic_2.4-1ubuntu9_i386.deb
   196  12:03   sudo apt-get install libc6-pic
   197  12:03   sudo apt-get install libc6-pic
   198  12:03   sudo apt-get -f install
   199  12:03   sudo dpkg -i libc6-pic_2.4-1ubuntu9_i386.d


do you know whats going on? i am actually new to ubuntu and can't believe this should be such a big problem.. 

am i missing something??

thanks a lot..

---

### Post by Perfect Storm on 2006-08-19
What's the reason you want to upgrade it?

---

### Post by BlackBottle on 2006-08-19
i am trying to install xboing which requires newer version.. i can live without the game but to me (i am new to ubuntu) it looks incredebly complicated to upgrade a packet! may be i am missing something,

---

### Post by Anduu on 2006-08-19
You do not want to upgrade libc6...trust me.

Just about every app that runs under Ubuntu depends on the version you have. That is why it won't let you upgrade.

libc6 is locked for Ubuntu...you would have to add Debian repos to be able to upgrade and would most likely hose your system.

---

### Post by BlackBottle on 2006-08-19
ok thanks.. i can live without xboing..

good to know the specifics of the problem.. i was getting scared upgdrading a packet would be that complicated on ubuntu!

thanks..

---

### Post by Anduu on 2006-08-19
No problem :)

---

### Post by mlind on 2006-08-19
If something needs different (newer) version of libc6, it means package is not for your distribution and was compiled with different toolchain, I think. 

Edgy and Dapper are not "binary compatible" because Edgy's gcc is 4.1.x and Dapper's is 4.0.x. Same goes for different Debian and Ubuntu distributions. 
If you really need that package, fetch the source package and recompile it with your own system.

---


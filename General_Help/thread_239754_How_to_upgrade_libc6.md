---
title: "How to upgrade libc6"
date: 2006-08-19
forum: General Help
---

### Post by BlackBottle on 2006-08-19
I have been trying to upgrade libc6 from 2.3.6 to 2.4. however its running into dependency issues.. i tried -f install but to no avail.

~> sudo dpkg -i libc6-pic_2.4-1ubuntu9_i386.deb
(Reading database ... 96758 files and directories currently installed.)
Preparing to replace libc6-pic 2.3.6-0ubuntu20 (using libc6-pic_2.4-1ubuntu9_i386.deb) ...
Unpacking replacement libc6-pic ...
dpkg: dependency problems prevent configuration of libc6-pic:
 libc6-pic depends on libc6 (= 2.4-1ubuntu9); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
dpkg: error processing libc6-pic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6-pic


stupid says new version libc6-pic of needs new version of libc6 which is not present! of course its not, thats why i want to upgrade :) 

do you have any suggestion?

here is my history of commands i have tried.
  191  12:02   sudo apt-get install libc6-pic
   192  12:02   sudo dpkg -i libc6-pic_2.4-1ubuntu9_i386.deb
   193  12:02   sudo apt-get -f install
   194  12:02   sudo apt-get -f install
   195  12:02   sudo dpkg -i libc6-pic_2.4-1ubuntu9_i386.deb
   196  12:03   sudo apt-get install libc6-pic
   197  12:03   sudo apt-get install libc6-pic
   198  12:03   sudo apt-get -f install
   199  12:03   sudo dpkg -i libc6-pic_2.4-1ubuntu9_i386.deb


please help.. thanks a lot!

---

### Post by john_galt on 2008-06-17
even I am facing a similar situation.. i have libc6 with version 2.6.1 and i need a version >=2.7 to install some other package which is dependent on this one.. I have checked in the repositories and the desired version is not available..
please help me out too

---


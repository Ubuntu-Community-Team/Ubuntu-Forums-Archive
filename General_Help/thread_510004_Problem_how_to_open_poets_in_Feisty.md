---
title: "Problem: how to open poets in Feisty ?"
date: 2007-07-26
forum: General Help
---

### Post by gy_ro on 2007-07-26
I installed Feisty Fawn (7.04) and added Samba,proftpd,Apache, PHP5 and shorewall to it. I configured shorewall to accept everything from the net through port 21, 22, 80, 12000 and 16001 with rules like these :

ACCEPT   net   fw   tcp   21
ACCEPT   net   fw   tcp   22
ACCEPT   net   fw   tcp   80
ACCEPT   net   fw   tcp   12000
ACCEPT   net   fw   tcp   16001

I know I configured shorewall like it should be (have done it on Dapper Drake with no errors)
I can surf the net and play with ftp without problems, but if I want to update a php-script from the outside via the web-browser, the script keps telling me it can't access port 16001 to update. ( I know the script is ok, once again tested on Dapper Drake) Which differences could exist between Feisty and Dapper concerning opened/closed ports ?

---


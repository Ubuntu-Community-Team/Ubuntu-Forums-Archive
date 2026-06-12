---
title: "Atomic precision of time and date"
date: 2015-08-17
forum: General Help
---

### Post by Erik Kaiser on 2015-08-17
Linux Ubuntu
 

 Time and date

 

 Hi !
 

 This is the question if an automatic adjustment of the time is possible whenever we go online.

 

 It has been found that the Ubuntu clock on my laptop screen is not in accordance with atomic time if you compare it to the world time, the time you can click on the top right of the screen in Ubuntu. Does a software protocol allow to adjust the internal computer time automatically ?

 

 

 Have a nice day
 

 Erik Kaiser

---

### Post by howefield on 2015-08-17
The default setting is to check the time Automatically from the Internet. 

Do you need something different ?

---

### Post by tgalati4 on 2015-08-17
If you want continuous (hourly) time correction, then install *ntp*.  At bootup, your system clock is syncronized--with *ntpdate* I believe.  If your system has been up for several days, then you can get clock drift which will not be corrected without the *ntpd* daemon running to fix it hourly.

---


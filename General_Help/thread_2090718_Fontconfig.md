---
title: "Fontconfig"
date: 2012-12-03
forum: General Help
---

### Post by DoctorVell on 2012-12-03
Hi there, how do I fix this error...it 

Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum-eco.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum-eco.conf", line 18: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum-eco.conf", line 28: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum-eco.conf", line 38: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum-eco.conf", line 48: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum-gothic-light.conf", line 8: Having multiple values in <test> isn't supported and may not works as expected

I get this error message when I try and load emesene AND I also see it when I do a shutdown.  I am assuming it shows up sometime during my logon OR as I am logged in.

I am just wondering how to edit it so I can delete the multiple values in those lines OR a fix so it doesn't do that.  Thanks

---

### Post by ibjsb4 on 2012-12-03
Looks like a bug

[http://ubuntuforums.org/showthread.php?t=2046558](http://ubuntuforums.org/showthread.php?t=2046558)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=90-fonts-nanum&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=90-fonts-nanum&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by DoctorVell on 2012-12-07
I still have the error message after doing what the first link has stated...going to check out the second link now.  Plus it is with other programs not just emesene.

Just did that and I looked in some of those links in the second link and it said it was one of the fonts, so I decided to uninstall the fonts in question and see if that works.

---

### Post by DoctorVell on 2012-12-11
> **DoctorVell said:**
> I still have the error message after doing what the first link has stated...going to check out the second link now.  Plus it is with other programs not just emesene.

Just did that and I looked in some of those links in the second link and it said it was one of the fonts, so I decided to uninstall the fonts in question and see if that works.

That is what worked the best, the fonts have been removed

---


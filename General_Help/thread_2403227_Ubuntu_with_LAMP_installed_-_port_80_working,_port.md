---
title: "Ubuntu with LAMP installed - port 80 working, port 443 not working"
date: 2018-10-08
forum: General Help
---

### Post by FoolInTheRain on 2018-10-08
Hello,
I have Ubuntu 18.04 installed and I also installed LAMP and everything's working EXCEPT I can't get HTTPS pages to serve up properly.
I'm using several virtual hosts
I have several websites setup under /etc/apache2/sites-available with the proper Symlinks

SSL IS working.

But when I try to open a local website I've installed using port 80 it opens just fine.  But when I try to open it using port 443 it will only open the Apache2 Ubuntu Default ("It works") Page.

I had a similar problem with port 80 originally but I deleted the 000-default.conf files and it started working.  Unfortunately, there is no default SSL conf file to delete.

So SSL IS WORKING......but 443 requests re not getting to the right place

I'm certain it's something simple...but I just can't find it.

Thanks for your help

---

### Post by FoolInTheRain on 2018-10-10
Yep...it was something simple.....usually is

---

### Post by QIII on 2018-10-10
Hello!

Would you care to detail the solution so that the entire community can benefit?  The Ubuntu Forums is a community resource, not an individual one.

If your share the solution, others will not have to repeat your struggle.

Thanks.

---


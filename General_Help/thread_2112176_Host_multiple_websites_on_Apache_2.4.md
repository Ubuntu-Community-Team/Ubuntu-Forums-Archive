---
title: "Host multiple websites on Apache 2.4"
date: 2013-02-04
forum: General Help
---

### Post by hovrashko on 2013-02-04
Can anyone suggest a good tutorial on how to host multiple websites on Apache 2.4? Specifically for Linux (if possible Ubuntu 12.10 x64) 

I have tried a bunch for other older version but can get it to work with 2.4

Currently I'm hosting 7 websites on the wamp, with no problems. 

Thanks :)

---

### Post by omeomi on 2013-02-04
Are you looking for something like [VirtualHosts]("http://httpd.apache.org/docs/2.4/vhosts/examples.html") ?

---

### Post by hovrashko on 2013-02-04
> **omeomi said:**
> Are you looking for something like [VirtualHosts]("http://httpd.apache.org/docs/2.4/vhosts/examples.html") ?

Thank you, I could find any of that on Google, I will try it and will post back.
:)

---

### Post by hovrashko on 2013-02-09
Ok, that didn't work, but I combined several resources and was able to get it to work.

sudo  gedit /etc/apache2/apache2.conf
add or uncomment:

NameVirtualHost *


And the rest is this tutorial [http://wiki.gandi.net/en/hosting/using-linux/tutorials/ubuntu/virtualhosts](http://wiki.gandi.net/en/hosting/using-linux/tutorials/ubuntu/virtualhosts)

Hope this helps :)

---


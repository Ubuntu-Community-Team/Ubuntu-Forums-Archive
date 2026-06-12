---
title: "restrict website apache2"
date: 2014-05-17
forum: General Help
---

### Post by nathanhawthorne12 on 2014-05-17
Evening guys, pretty new to the web hosting bit.  Just done a brand new install of ubuntu 14 set-up SSH and installed Apache2.  Sticking with the test page it seems i can access the site from my main internet IP. i would like too restrict this too 2 internal ip's 192.168.*.*.  How would i go about doing this?

---

### Post by pqwoerituytrueiwoq on 2014-05-17
what version of apache2?
this if for prior to v2.4
[http://www.cyberciti.biz/faq/apache-restrict-access-based-on-ip-address-to-selected-directories/](http://www.cyberciti.biz/faq/apache-restrict-access-based-on-ip-address-to-selected-directories/)
change the file path at the start to /etc/apache2/apache2.conf
Opps seems you are using 14.04, that had version 2.4
based on the manual: [http://httpd.apache.org/docs/current/mod/mod_authz_host.html](http://httpd.apache.org/docs/current/mod/mod_authz_host.html)
you need to only add one line to a section that is similar the the part in the same file 
```
Require ip 192.168
```
BTW that section will start with this:
```
<Directory /var/www/html/>
```

---

### Post by nathanhawthorne12 on 2014-05-18
Ah, thank you very much it was indeed what I needed.  I don't know how i missed that as require all granted should have gave it away.  Cheers again

---


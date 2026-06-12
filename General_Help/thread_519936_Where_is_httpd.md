---
title: "Where is httpd?"
date: 2007-08-07
forum: General Help
---

### Post by FrankBlourtango on 2007-08-07
I have Apache installed and running.

Here is my question.  In ubuntu 7.06 where is the httpd exectutive file?  I've tried search, find, locate, which...   I cannot find httpd.

---

### Post by eggdeng on 2007-08-07
Not sure what you mean by the 'executive file'. Do```
sudo updatedb
``` and then try again with ```
locate httpd
``` On both Dapper and Edgy, I get
```
locate httpd
/etc/apache2/httpd.conf
/usr/lib/apache2/modules/httpd.exp
/usr/share/doc/apache2/examples/httpd-std.conf
```

---

### Post by FrankBlourtango on 2007-08-08
I found it.  It's apache  not httpd on ubuntu

---


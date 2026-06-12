---
title: "Apache is no working ok"
date: 2007-01-18
forum: General Help
---

### Post by OOzypal on 2007-01-18
I installed Apache then I moved my http.conf and hosts to my kubuntu from my backup. Then ran
```

apachectl configtest
```

I am getting this warning. I edited my http.conf and could not find any trace to /mirror/debian
```

Warning: DocumentRoot [/mirrors/debian] does not exist
Syntax OK
```

---

### Post by tronica on 2007-01-18
that just it, /mirrors/debian does not exist.  You need to see if its there. The document root is where apache serves files.

---

### Post by OOzypal on 2007-01-18
Yes I know but where can I change the document root?

---

### Post by JamieC on 2007-01-18
In your httpd.conf file...

---

### Post by OOzypal on 2007-01-18
here is what I have in the http.conf

DocumentRoot /home/hab/www/

---

### Post by tronica on 2007-01-18
well, just make it where ever you have your files for your site.

---

### Post by JamieC on 2007-01-18
Hm, try specifying the location of the configuration file, here's what I'd do on CentOS:
```

/usr/sbin/httpd -f /etc/httpd/conf/httpd.conf

```

---


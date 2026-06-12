---
title: "lighttpd upload problem"
date: 2008-05-28
forum: General Help
---

### Post by ikkubus on 2008-05-28
hi!

im having trouble with lighttpd. Uploading 1-20+ mb file works. but when i upload 50mb+ files it doesnt work. i already set upload max size to 100 and max post size to 100 in php.ini 

i also noticed this in lighttpd /tmp:

```

-rw------- 1 www-data www-data 1.0M 2008-05-28 10:33 lighttpd-upload-1gOAQ6
-rw------- 1 www-data www-data 1.0M 2008-05-28 10:27 lighttpd-upload-8bMJG1
-rw------- 1 www-data www-data 1.0M 2008-05-28 10:35 lighttpd-upload-8Zah9w
-rw------- 1 www-data www-data 1.0M 2008-05-28 10:28 lighttpd-upload-9QYF37
-rw------- 1 www-data www-data 800K 2008-05-28 10:36 lighttpd-upload-bv86rT
-rw------- 1 www-data www-data 1.1M 2008-05-28 10:26 lighttpd-upload-CIZeP1
-rw------- 1 www-data www-data 1.0M 2008-05-28 10:32 lighttpd-upload-d29nt3
-rw------- 1 www-data www-data 1.0M 2008-05-28 10:29 lighttpd-upload-p13E7t
-rw------- 1 www-data www-data 1.0M 2008-05-28 10:31 lighttpd-upload-rsian4
-rw------- 1 www-data www-data 1.0M 2008-05-28 10:34 lighttpd-upload-w5MbJe
-rw------- 1 www-data www-data 1.0M 2008-05-28 10:30 lighttpd-upload-xLYxWb


```

im using:
ubuntu hardy,php5,mysql and lighttpd-1.4.19
 

anyone know how to fix this? thanks in advance

---

### Post by ikkubus on 2008-05-28
anyone? please...

---

### Post by ikkubus on 2008-05-28
this is lighttpd error.log

```

2008-05-28 12:34:48: (network_write.c.112) write failed:  Broken pipe
2008-05-28 12:34:48: (connections.c.615) connection closed: write failed on fd 9

```

---

### Post by bodhi.zazen on 2009-06-08
post your php.ini

Try:

```
memory_limit = 128M
post_max_size = 128M
upload_max_filesize = 128M

upload_tmp_dir = /var/tmp
```

make sure /var/tmp is writable by lighttpd (www-data)

---


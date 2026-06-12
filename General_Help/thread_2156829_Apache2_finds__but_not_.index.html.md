---
title: "Apache2 finds / but not /.index.html"
date: 2013-06-23
forum: General Help
---

### Post by cipe53 on 2013-06-23
I have installed Apache2 on 12.04 server and made no configuration changes. If I browse to 127.0.0.1/ I see the file /var/www/index.html. If, however, I browse to 127.0.0.1/index.html, I get a file not found error. The same is true via the external interface. The same behaviour occurrs for, say, 127.0.0.1/test and 127.0.0.1/test/index.html.

What mistake am I making?

I have tried Google, but results concern finding the default file via a "directory url", rather than the converse situation that I am in.

---

### Post by sanderj on 2013-06-23
what's the output of

```
ls -al /var/www/
```

and inspect the files in /var/log/apache2/

---

### Post by cipe53 on 2013-06-23
The output of ls -al /var/www/ is

drwxr-xr-x 2    root root 4096  date .
drwxr-xr-x 13  root root 4096  date ..
-rw-r--r--    1    root root 42     date index.html

Both error.log and access.log are empty.

In the configuration file the log level is at WARN.

Note that I can browse and see the file /var/www/index.html provide I browse to [http://127.0.0.1/](http://127.0.0.1/) but not if I browse to [http://127.0.0.1/index.html](http://127.0.0.1/index.html)

Thanks.

---

### Post by 2Stoned on 2013-06-23
You may need to change the DirectoryIndex part. If it is set to /var/www/index.html change it to index.html. Let us know if it worked.

---

### Post by cipe53 on 2013-06-23
**cat **/etc/apache2/mods-enabled/dir.conf

<IfModule mod_dir.c>

          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm

</IfModule>


As expected.

Note that my problem is the **converse** situation: 127.0.0.1/ yields /var/www/index.html while 127.0.0.1/index.html yields file not found. Further, I have **no way** of fetching /var/www/test.html.

No configuration changes have been made to Apache2 since installation.

Thanks

---

### Post by sanderj on 2013-06-23
And when you change the contents of index.html, does it show in your browser?

What is the output of "netstat -apon | grep -i listen | grep 80"?

---

### Post by cipe53 on 2013-06-23
:oops: tntnet is bound! Not sure why! But that is my problem.

Thanks.

---


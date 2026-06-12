---
title: "apache/php charset problems on ubuntu server edition"
date: 2007-02-27
forum: General Help
---

### Post by VipArt on 2007-02-27
I have apache2 and php5 working on ubuntu server 6.06 (AMD 64 bit).

When I access the web site on my server, the browser can't determine the correct charset. It always recognizes UTF-8 event if the META charset tag in the HTML HEAD is set to ISO-8859-13 (for example) or other...

I checked /etc/apache2/apache2.conf file. **AddDedaultCharset** is commented. So it shouldn't always determine UTF-8, but it does. PHP configuration file also have similar property like **default_charset**, but it is also commented.

Where could be the problem? 

Thanks in advance,
Antanas Vipartas

---

### Post by scorphus on 2007-03-01
I was facing the very same problem and an article helped me to understand the thing. You can read it at:

[http://beranger.org/index.php?fullarticle=1344](http://beranger.org/index.php?fullarticle=1344)

After reading it, I just commented the following line in /etc/apache2/conf.d/charset

```
AddDefaultCharset UTF-8
```

I hope it helps you too.

-- Scorphus

---

### Post by VipArt on 2007-03-05
Thanks, scorphus, you solved the problem!

The thing that helped me was to comment the line (as follows)

```
#AddDefaultCharset UTF-8
```

in file **/etc/apache2/conf.d/charset**.

Thanks for the help :)

---

### Post by scorphus on 2007-03-07
Cool!
You are welcome!

Glad to help,
Scorphus

---


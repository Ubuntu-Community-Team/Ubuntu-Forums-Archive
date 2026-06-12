---
title: "virtual hosting at ubuntu (apache2) - using multiple domains for the same folder"
date: 2017-10-18
forum: General Help
---

### Post by marchello_lippi2 on 2017-10-18
Hi all, 
Not sure which forum branch suits the best.. 
I got virtual hosting at ubuntu 14.04 (apache2). 
How do I use multiple domains to point to the same physical folder?
Of course, I can schedule cp to copy the content from one folder to another (the content is mostly static), though there should be more intelligent solution. 
Thanks ahead.

---

### Post by SeijiSensei on 2017-10-18
There are two possible answers to this question.  If every domain is supposed to serve the same content, the easiest thing to do is to add each virtual host as an alias to the primary site.

```

<VirtualHost *:80>
ServerName     www.example.com
ServerAlias    www.example2.com mail.example.com mail.example2.com 
[stuff]
</VirtualHost>

```

If you point the DNS records for all four of those names at your server, they will all be treated as identical, and Apache will serve up the same page.

If you have separate files in /etc/apache2/sites-available/ for each virtual domain, just point the DocumentRoot directive in each such file to the same location in the filesystem like /var/www/html.

---

### Post by marchello_lippi2 on 2017-10-19
**SeijiSensei**
> [COLOR=#000000]If you have separate files in /etc/apache2/sites-available/ for each virtual domain, just point the DocumentRoot directive in each such file to the same location in the filesystem like /var/www/html.[/COLOR]
Works great, thx.

---


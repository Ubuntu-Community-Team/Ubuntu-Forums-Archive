---
title: "[SOLVED] Apache: Need help rewriting URLs"
date: 2008-05-16
forum: General Help
---

### Post by x1a4 on 2008-05-16
Hi,

I need help rewriting URLs in Apache. I want the 'www.' to be stripped while preserving the directory structure. For example: If a user types 'www.hex1a4.net/mirror/openoffice/' the URL should be rewritten as 'hex1a4.net/mirror/openoffice/'.

I'm having a really hard time coming up with the correct rewrite conditions. So far I was able to come up with the following:
```

RewriteCond %{HTTP_HOST} ^www.hex1a4.net$
RewriteRule ^(.*)$ http://hex1a4.net/ [R=301,L]

```
but this doesn't doesn't take into account the directory structure, and regardless of the path specified, if the address is prefixed with 'www.' the home page will always be displayed.

Please note that I am not the admin of the system and don't have access to Apache's configuration files. I can only use .htaccess.  The Apache version is 1.3.37

Thank you.

---

### Post by x1a4 on 2008-05-20
Well I've been reading up on rewriting URLs creating some easier ones, and it turns out this is just as easy.  Here's how I did it:
```

RewriteCond %{HTTP_HOST} ^www\.hex1a4\.net(.*)$
RewriteRule ^(.*)$ http://hex1a4.net/$1 [R=301,L]

```

---


---
title: "RewriteBase /"
date: 2008-04-07
forum: General Help
---

### Post by tefflox on 2008-04-07
How do I change url **localhost/12/dir/** to **localhost/12/dir** ?

Here is the .htaccess code I'm working with ---

[SIZE=1][B]RewriteBase /

RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^([^/]+)/([^/]+)/([^/]+)/?$[/B][/SIZE]

---


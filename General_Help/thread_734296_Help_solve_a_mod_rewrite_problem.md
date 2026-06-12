---
title: "Help solve a mod_rewrite problem"
date: 2008-03-24
forum: General Help
---

### Post by tefflox on 2008-03-24
[SIZE=3]I've got a fresh install of gutsy w/ apache / php.  Simply, I want to rewrite all url's from such **~/15/artist/** to **~/15/artist**

Here's what I've got so far.
[B]
httpd.conf[/B]

```
# AllowOverride controls what directives may be placed in .htaccess files.
# It can be "All", "None", or any combination of the keywords:
#   Options FileInfo AuthConfig Limit
#
    AllowOverride All


#
# AccessFileName: The name of the file to look for in each directory
# for access control information.  See also the AllowOverride directive.
#
AccessFileName .htaccess
```**.htaccess**

```
RewriteEngine on
RewriteBase /

RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^([^/]+)/([^/]+)/([^/]+)/?$ /index.php?x=$1&y=$2&z=$3 [L,QSA]
```The .htaccess code was a "for example" from a friend.  I'm not sure if it's what I need, but he's got it working on his site...

[COLOR=Orange]** Thanks for your continued support.**[/COLOR][/SIZE]

---


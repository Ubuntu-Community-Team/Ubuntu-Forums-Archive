---
title: "Apache Virtual Hosts"
date: 2006-10-15
forum: General Help
---

### Post by chocolatetoothpaste on 2006-10-15
Hey everyone,
  I am having a strange problem occuring.  I searched the archives and couldn't find anything similar.  My problem is this:

I have an Apache/PHP/Mysql setup running Apache 1.3.34.  The other program versions are not relevant to this problem.  I am trying to setup up a couple local servers.  We'll call them "example" and "testing".  Well, when I make a new virtual host declaration, instead of going to the specified document root, it replaces "example" or "testing" with "example.com" or "testing.com" respectively.  Or sometimes it will do a google search for these domains.  On top of that, when I have these vhosts declared, localhost no longer works.  But if I delete the entries then restart the server, localhost works fine.  Can anyone tell me what I am doing wrong?  These are my virtual host definitions:
```

NameVirtualHost *:80
<VirtualHost *:80>
    ServerName    example
    DocumentRoot    /home/user/www/example
    DirectoryIndex    index.php
</VirtualHost>

```Also:
```

NameVirtualHost *:80
<VirtualHost *:80>
    ServerName   testing
    DocumentRoot    /home/user/www/testing
    DirectoryIndex    index.php
</VirtualHost>

```

---

### Post by kidders on 2006-10-15
Hi there,

Seems like your computer can't resolve "example", so your browser guesses that you might have meant "example.com". If you're running a DNS server, you should add a CNAME for "example", so your machines know where to find it.

Hope that helps.

Incidentally, you only need one NameVirtualHost directive. Including two will probably cause odd behaviour.

---

### Post by l.tambiah on 2006-10-15
This guide will be of use to you:

[http://www.onlamp.com/pub/a/apache/2003/07/24/vhosts.html?page=1](http://www.onlamp.com/pub/a/apache/2003/07/24/vhosts.html?page=1)

---


---
title: "redirect in Apache"
date: 2015-07-14
forum: General Help
---

### Post by ELMIT on 2015-07-14
I had a node.js web site on port 8888 besides my apache setup.

I want to use the port 8888 now in apache and redirect to a new site:

[http://abc.foo.com:8888](http://abc.foo.com:8888) => [http://abc.new.com](http://abc.new.com)

[http://abc.new.com](http://abc.new.com) is already working
[http://abc.foo.com:8888](http://abc.foo.com:8888) I have already disabled in node.js

I put a conf file in /etc/apache2/sites-available with following content:

<VirtualHost *:8888>
    ServerAdmin [email]me@here.com[/email]
    ServerName abc.foo.com
    Redirect 301 / [http://abc.new.com](http://abc.new.com)

</VirtualHost>


pointing my browser to [http://abc.foo.com:8888](http://abc.foo.com:8888)   gives me an error (unable to connect)

What am I missing?

---

### Post by ELMIT on 2015-07-14
solved by adding Listen directive in /etc/apache2/ports.conf

---


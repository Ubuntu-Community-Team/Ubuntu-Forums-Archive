---
title: "mod_php and apache not working"
date: 2005-08-16
forum: General Help
---

### Post by mxc on 2005-08-16
Hi all,

I have apache2 mpm-prefork installed and also selected libapache2-mod_php4 installed. However I cannot get the web server to display php pages. Each time I try and access a php pages I get asked if I want to dowload it.

How do I get mod_php working with apache2?

thanks

---

### Post by jostein on 2007-10-28
Hi, 

I just had the exact same problem. I solved it by adding the following to /etc/apache2/sites-availible/default (near the top, but I don't think the order matters much...):

<Location />
	AddType text/html .php .phps
	AddHandler application/x-httpd-php .php
	AddHandler application/x-httpd-php-source .phps
</Location>

You will probably have to do the same thing for all the files in /etc/apache2/sites-availible/ if you're using more than one virtual host.

I found the solution here: [http://www.devside.net/articles/php](http://www.devside.net/articles/php) . If you need any technical explanations, just check that page, it looked thorough to me.

Good luck!

Jostein.

---


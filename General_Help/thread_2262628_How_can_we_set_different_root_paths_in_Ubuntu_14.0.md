---
title: "How can we set different root paths in Ubuntu 14.04"
date: 2015-01-26
forum: General Help
---

### Post by Ahmed_Ibrahim on 2015-01-26
How can we set different root paths in Ubuntu 14.04 


I am having two different domain names:


I need [www.domain01.com](www.domain01.com) root to be /var/www/html

and 
The second domain [www.domain02.com](www.domain02.com) root to be /var/www/html/sub01/sub02


How can we do this?

---

### Post by TheFu on 2015-01-26
It would be better to have each domain outside each other's subdirectory. Don't nest.
/var/www/virt/sub01 - sub01.com
/var/www/virt/sub02 - sub02.com

Say out of the /var/www/html/ area - which is where the default stuff goes.

Just create 2 virtual hosts in the way your web server requires. Each web server is a little different, so need to know what you are using and the version used.
[https://httpd.apache.org/](https://httpd.apache.org/) is probably what you are using.  If it is version 2.4 ... [https://httpd.apache.org/docs/2.4/vhosts/](https://httpd.apache.org/docs/2.4/vhosts/)

---

### Post by SeijiSensei on 2015-01-26
The [DocumentRoot]("http://httpd.apache.org/docs/current/mod/core.html#documentroot") directive in Apache is used to identify each virtual host's root directory.  Just point each virtual host to its corresponding directory.

---

### Post by Ahmed_Ibrahim on 2015-01-28
Great;
Thank you all
I followed your instructions and I did the task by setting two different Apache Virtual Hosts


The following link is really good
[https://www.digitalocean.com/communi...untu-14-04-lts](https://www.digitalocean.com/communi...untu-14-04-lts)

---


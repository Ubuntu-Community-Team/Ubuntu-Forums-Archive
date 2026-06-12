---
title: "Rename Virtual Host"
date: 2013-03-13
forum: General Help
---

### Post by ptmuldoon on 2013-03-13
I just recently setup a linode VPS to host a few BS websites, and help me learn more on Ubuntu and CLI, etc.

Following the Linode guides, I was successful in setting up 4 websites with virtual host naming.

Now I learned that when I visit the IP address of the VPS, it will get the first site listed alphabetically.

What is the best way to have the IP address to point to a different site?   I think I need to rename the sites-enabled/mysite.com to sites-enabled/00.mysite.com?

when I do that and reload apache, it throws an error (will have to retry and copy it here if interested).

Am I on the right track?

---

### Post by SeijiSensei on 2013-03-13
Create a separate configuration file for each virtual host in /etc/apache2/sites-available and use a2ensite to create the needed symlinks to each file in /etc/apache2/sites-enabled.  Each site's configuration needs to have a unique "ServerName" directive so that Apache can tell which configuration to use in response to a request.  [More details here](http://httpd.apache.org/docs/2.2/vhosts/name-based.html).

---

### Post by ptmuldoon on 2013-03-13
> **SeijiSensei said:**
> Create a separate configuration file for each virtual host in /etc/apache2/sites-available and use a2ensite to create the needed symlinks to each file in /etc/apache2/sites-enabled.  Each site's configuration needs to have a unique "ServerName" directive so that Apache can tell which configuration to use in response to a request.  [More details here](http://httpd.apache.org/docs/2.2/vhosts/name-based.html).

Thats exactly what I did following the guides from Linode as well.  And I have the DNS setup for all them and it works well.

But now I learned that when I point my actual IP address, it points site mysite01,  when I want it retrieve mysite04.  I learned this because its alphabetical.

someone mentioned just renaming the config file in sites-available/mysite04 to 00-mysite04.  But than when I reload apache, it gives an error of not finding sites/enabled/mysite04

I think I need to unlink mysite04 and relink to 00-mysite04?


EDIT::

Yes..  It worked by running 

sudo a2dissite mysite04

and than

sudo a2ensite 00-mysite04

---

### Post by SeijiSensei on 2013-03-13
If you connect to the server via IP address, you'll get the default host, which is determined by alphabetical order.  To make mysite04 be the default host, change the name of that file to something like "0mysite04" so it loads first alphabetically, then restart Apache.

---


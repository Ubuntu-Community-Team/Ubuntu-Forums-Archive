---
title: "Apache, redirect"
date: 2013-04-19
forum: General Help
---

### Post by clvrfsh on 2013-04-19
I'm messing around with Apache and I was wondering how to redirect Apache from it's Index.html file to another file temporarily. I want to be able to go to 127.0.0.1 (or localhost) on my browser and for it to take me to a file I created called Index2.html (Also in /var/www). I then want to be able to delete the Index2.html file and have it go back to Index.html without making excess changes to Index.html other than to redirect it.

---

### Post by midnightramen on 2013-04-20
i'm going to say that is the DirectoryIndex parameter in the httpd.conf file. I don't recall exactly where ubuntu stores it (/etc/httpd/conf, most likely, but it could be under /etc/apache2). Anyway, more info here: [http://www.cyberciti.biz/faq/apache-display-or-change-a-default-page-other-than-indexhtml/](http://www.cyberciti.biz/faq/apache-display-or-change-a-default-page-other-than-indexhtml/)

---

### Post by Novastorm on 2013-04-20
If you want to redirect whenever the 'index2.html' file is present, for example while performing maintenance on your site, then you could use a rewrite rule like this (put it in your apache config file):

```
RewriteEngine On
RewriteCond %{DOCUMENT_ROOT}/index2.html -f
RewriteRule ^/index.html$ /index2.html [R]
```

What these lines do is:
1. Enable the rewrite engine
2. Determine if index2.html exists in the document root (usually /var/www/html), if it does exist, then process the rewrite rules below
3. Rewrite requests for /index.html to /index2.html, and the R bit at the end says to do this using a redirect

---

### Post by clvrfsh on 2013-04-22
Thank you for responding and I'm sorry it took me so long to respond. Where in my apache.conf file do I put the rewrite code?

---

### Post by Lars Noodén on 2013-04-22
The rewrite rules can go almost anywhere per vhost in <VirtualHost> or per directory in <Directory> etc.  

You do need to have the module turned on first before it will work.

```

sudo a2enmod rewrite

```

See the [rewrite guide](https://httpd.apache.org/docs/2.2/rewrite/) for full details.

---

### Post by SeijiSensei on 2013-04-22
I think it's a lot easier to create symlinks, e.g., "ln -s index2.html index.html".  Just make sure you have "[Options]("http://httpd.apache.org/docs/current/mod/core.html#options") FollowSymLinks" included in the <Directory> stanza for that directory.

Of course, you realize that you can access index2.html directly by using the URL [http://localhost/index2.html](http://localhost/index2.html), right?

---

### Post by CharlesA on 2013-04-22
> **SeijiSensei said:**
> I think it's a lot easier to create symlinks, e.g., "ln -s index2.html index.html".  Just make sure you have "[Options]("http://httpd.apache.org/docs/current/mod/core.html#options") FollowSymLinks" included in the <Directory> stanza for that directory.

Of course, you realize that you can access index2.html directly by using the URL [http://localhost/index2.html](http://localhost/index2.html), right?

I would have to agree, but if you symlink index.html to index2.html, what's the point of having index2.html instead of just using index.html ?

---

### Post by SeijiSensei on 2013-04-22
Sometimes I'll have two different versions of the file, in my case, say index1.php and index2.php.  It makes it easy to switch from one to the other if I use a symlink to index.php.

The OP wanted an easy way to switch from one index file to another.  As I said, I'd just avoid the problem by using the appropriate URL and accessing the correct file directly.

---

### Post by CharlesA on 2013-04-22
Ah, that makes sense. Thanks!

---

### Post by clvrfsh on 2013-04-23
It still does not work. I have enabled mod rewrite and posted the rewrite rules into the apache.conf file in different locations. I restart apache after each change I make and when I go to my browser and type in 127.0.0.1 it still takes me to the index.html page instead of the index2.html

---

### Post by Lars Noodén on 2013-04-24
Nothing should go in /etc/apache2/apache2.conf  and apache.conf shouldn't exist at all.  All your configurations changes need to go in the configuration file for that particular virtual host.  If you have not added any, then make the changes in the default vhost.  The configuration file for that is /etc/apache2/sites-enabled/000-default

Once you've added the rewrite rules to the appropriate <VirtualHost> or <Directory> you can then test the syntax of what you have done with [apache2ctl](http://manpages.ubuntu.com/manpages/raring/en/man8/apache2ctl.8.html).

```

/usr/sbin/apache2ctl configtest

```

---


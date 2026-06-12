---
title: "apache2 doesn't work"
date: 2008-02-04
forum: General Help
---

### Post by lusis89 on 2008-02-04
Hello,
I've installed apache2 and php on my ubuntu gutsy box, but
when i try to visit a static page, a text file, an image, and so on, the result is a blank page (0 bytes); this does not happens with dynamic php pages.

Any idea?
Thanks

---

### Post by OffAxis on 2008-02-04
you may have disabled apache's ability to display those file types.
check your apache2.conf file and any .htaccess files you may have implemented. There's a filetype section that you might have commented out.

Were you initially able to reach the default apache2 index.html file and have it display properly?
[http://localhost/](http://localhost/)

your document root also may be pointing to the wrong directory if you tried to redirect from it from the default.

Do the file names show up when you're trying to view them from the browser or is it just blank?

Could also be an ownership problem.

---

### Post by lusis89 on 2008-02-04
Thanks for the reply,

the DocumentRoot is set to /www/ (but also /var/www didn't work), all files in that directory belongs to www-data with global read,write,execute permissions.

There is no .htaccess in any directory, and I've never edited the apache2.conf. 
I can't find the file types section in any of the configuration files in /etc/apache2.

I've reinstalled (purged) apache2, but didn't change.

```
ubuntu@ubuntu:~$ dpkg -l | grep apache2
ii  apache2-mpm-prefork                        2.2.4-3build1           Traditional model for Apache HTTPD
ii  apache2-utils                              2.2.4-3build1           utility programs for webservers
ii  apache2.2-common                           2.2.4-3build1           Next generation, scalable, extendable web se
ii  libapache2-mod-php5                        5.2.3-1ubuntu6.2        server-side, HTML-embedded scripting languag

```

I've attacched two screenshots.
**EDIT:** Note that the first (php) page does not have images and style...

---

### Post by OffAxis on 2008-02-04
> Note that the first (php) page does not have images and style...
Is it just your php pages that can't access the files?
If that's the case it's a permissions or path problem.

What I'm still a little confused on, is...
The initial page that pops up when apache2 finishes the install, the 'You made it!' or whatever it says; does it make it that far?
Does it pop up with a blank screen?
Or does nothing happen?
Can you manually navigate there locally? [http://localhost/](http://localhost/)

---

### Post by OffAxis on 2008-02-04
The second screenshot there has a path going to /www
was this pre or post re-install (as you noted, the default path being /var/www)

There's an option in the apache2.conf (/etc/apache2/apache2.conf) for setting the document root, and there's also the option for setting the document root in the 'default' sites available section, as well.
I'm guessing that's where your incongruity is.

/etc/apache2/sites-available/default

usually when doing multiple hosting you'll have a separate .conf file for each, but you can do it for just one, too. You can modify the 'default' file or create your own .conf file.
So you put your mysite.conf file in the sites-available folder and use **a2dissite **to turn off the default file and **a2ensite **to turn on your mysite.conf file.
Then restart the server.
```
sudo /etc/init.d/apache2 restart
```

If you're just modifying the default file then you just need to restart the server.

---

### Post by lusis89 on 2008-02-04
Any static page, picture, etc... shows up as a blank page, either if it's accessed directly and if it's accessed from a php script.

I've changed the DocumentRoot to /www/, but the default /var/www/ didn't work as well.

Something even more strange: only static files under 5KB show up correctly...

the *same* version of Apache2, the *same* version of the website and the *same* 'sites-enabled' config file works correctly under the others machines.

I think this is not a permission problem...
Could this be caused by another program/library? (eg glibc, ...)

---


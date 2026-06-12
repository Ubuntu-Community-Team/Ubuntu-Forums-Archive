---
title: "Editing /etc/apache2/apache2.conf with shell script"
date: 2013-12-26
forum: General Help
---

### Post by frogwarrior on 2013-12-26
I'm making a shell script which automatically sets up a lamp server with PHPMyAdmin and to do this I need to add this line:
Include /etc/phpmyadmin/apache.conf
to apache2.conf. I tried this:
[B]sudo echo "Include /etc/phpmyadmin/apache.conf" >> /etc/apache2/apache2.conf
[/B]but it tells me permission denied. I found this thread:
[http://ubuntuforums.org/showthread.php?t=1845306](http://ubuntuforums.org/showthread.php?t=1845306)
which says that if you run sudo bash first, then you won't get the permission denied problem. I tried that and no permission denied problem but the script isn't editing the apache2.conf file. In fact, all the commands after sudo bash don't seem to get executed. For example, I change the script to:
```
sudo bash
echo "Now running as root"
sudo echo "Include /etc/phpmyadmin/apache.conf" >> /etc/apache2/apache2.conf
```
but it doesn't print "Now running as root" and it doesn't edit the .conf file. What do I need to do to make this shell script edit apache2.conf?

---

### Post by Lars Noodén on 2013-12-26
If you're using the stock Apache2 configuration, your default virtual host is in  /etc/apache2/sites-available/000-default.conf  For the most parts all your settings for that vhost should be made in that file instead of apache2.conf

About sudo, it only affects the program it runs.  Any redirects are done as the original user.

So you need to launch the redirect inside its own shell.

```

sudo sh -c 'date >> /tmp/x.txt'
ls -lh /tmp/x.txt

```

---

### Post by frogwarrior on 2013-12-26
Thanks a lot, using bash with the -c parameter worked, it edits the apache2.conf file now. I'm gonna look into what you said about virtual hosts though and change the way I do things.  I don't actually know what a virtual host is, so I suppose I need to learn more about apache.

---

### Post by Lars Noodén on 2013-12-26
A single web server can publish multiple web sites, each site maintained separately as a [virtual host](http://httpd.apache.org/docs/2.4/vhosts/) within Apache2.

[http://httpd.apache.org/docs/2.4/vhosts/examples.html](http://httpd.apache.org/docs/2.4/vhosts/examples.html)

The Apache2 configuration for Ubuntu is set up to facilitate managing several sites easily with separate  configfuration files.  The old Apache 1.3.x had everything in one file, but now things are split out one (or more) files per web site.  

There are a lot of tutorials and HowTos around but the the above links, even if a little abstract, are the authoritative sources of information on the topic.

---


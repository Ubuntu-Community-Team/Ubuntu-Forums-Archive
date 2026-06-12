---
title: "Error installing Wordpress"
date: 2013-02-03
forum: General Help
---

### Post by jrohde on 2013-02-03
Hi

I am following [this]("https://help.ubuntu.com/community/WordPress")guide to install Wordpress on a newly installed Ubuntu Server 12.10.

I get this error:

**bash: /usr/share/doc/wordpress/examples/setup-mysql: No such file or directory**

When executing this command:

[FONT="Courier New"]sudo bash /usr/share/doc/wordpress/examples/setup-mysql -n wordpress localhost[/FONT]

I am pretty sure I have followed the guide coorectly, so I guess there is an error in the guide.

The file setup-mysql.gz does exist:

[FONT="Courier New"]jakob@server:~$ ls -al /usr/share/doc/wordpress/examples
total 16
drwxr-xr-x 2 root root 4096 Feb  3 10:58 .
drwxr-xr-x 3 root root 4096 Feb  3 10:58 ..
-rw-r--r-- 1 root root 2076 Sep 12 14:52 apache.conf
-rw-r--r-- 1 root root 2311 Sep 12 14:52 setup-mysql.gz[/FONT]


How do I fix this?

Thanks
Jakob

---

### Post by bhattigurjot on 2013-06-16
This error is occuring because your file is zipped. It has to be unzipped first. You need to enter following code
sudo gunzip /usr/share/doc/wordpress/examples/setup-mysql.gz

After that run
sudo bash /usr/share/doc/wordpress/examples/setup-mysql -n wordpress localhost

And you are done!

---

### Post by lovevn on 2013-08-31
I also have an error when I install wordpress. I installed apache2, mysql, phpmyadmin... successfully. I extracted wordpress.zip and copied the wordpress folder to var/www.
I opened my browser and type URL: localhost/wordpress, then go step-by-step, but when I filled in databasename, username and password, then clicked Submit, it prompted an annoucement like this:
[http://upanh.com/slider/?e=malihu&s=upload&start=avp29c1oeqg](http://upanh.com/slider/?e=malihu&s=upload&start=avp29c1oeqg)
I tried to **open wp-config-sample.php in a text editor, fill in my information, and save it as wp-config.php, **but it didn't work! I also tried to created a new wp-config.php file, but it's impossible. What do I have to do now? 
Thanks!

---

### Post by SeijiSensei on 2013-08-31
I cannot see that image you posted, so I don't know what the error is. 

Did you create the database and database user prior to running WP?  Having just installed another WP instance yesterday, I had to create the database and user, then modify wp-config-sample.php with that information to create wp-config.php.

---

### Post by Habitual on 2013-08-31
cp -p wp-config-sample.php wp-config.php
nano (or vi) wp-config.php with your information

---

### Post by lovevn on 2013-09-01
> **SeijiSensei said:**
> I cannot see that image you posted, so I don't know what the error is. 

Did you create the database and database user prior to running WP?  Having just installed another WP instance yesterday, I had to create the database and user, then modify wp-config-sample.php with that information to create wp-config.php.
sorry, but I still see my image posted. 
> **Habitual said:**
> cp -p wp-config-sample.php wp-config.php
nano (or vi) wp-config.php with your information
Well, I have done it. It worked!
Thanks for replying me, SeijiSensei and Habitual. :)

---

### Post by Habitual on 2013-09-01
Glad it worked out.

---


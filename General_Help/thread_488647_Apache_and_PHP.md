---
title: "Apache and PHP"
date: 2007-06-30
forum: General Help
---

### Post by carpetn on 2007-06-30
I've installed PHP and Apache using the Ubuntu downloads. When I type "localhost" into my Firefox browser I get an index page that includes this information: "Apache/2.2.3 (Ubuntu) PHP/5.2.1 Server at localhost Port 80."

When I enter "file:////var/www/apache2-default/index.html" I get a page that says "It Works!"

But when I try to enter this, "file:////var/www/apache2-default/test.php," I get this message rather than a page:

"You have chosen to open test.php, which is a PHP script from://var/www/apache2-default. What should Firefox do with this file? "

What do I need to do? I'm guessing from my _Dummies_ book that I need to configure Apache somehow. The instructions there say I need to know the directory where PHP is installed, but when I do " sudo find / -name "php*" " I find stuff with PHP in many different directories. How do I know which on is the directory in which the program is actually installed?

Thanks.

carpetn

---

### Post by mpeters on 2007-06-30
Do you have the files php5.conf and php5.load present under your /etc/apache2/mods-enabled/ directory? To find out run:

 [INDENT][FONT="Fixedsys"]ls /etc/apache2/mods-enabled/php*[/FONT][/INDENT]

If not, you should copy them from /etc/apache2/mods-available:

[INDENT][FONT="Fixedsys"]cp /etc/apache2/mods-available/php* /etc/apache2/mods-enabled/[/FONT][/INDENT]

and restart apache:

[INDENT][FONT="Fixedsys"]/etc/init.d/apache2 restart[/FONT][/INDENT]

---

### Post by carpetn on 2007-06-30
Both those files were there:

eric@lenovo-1:~$ ls /etc/apache2/mods-enabled/php*
/etc/apache2/mods-enabled/php5.conf  /etc/apache2/mods-enabled/php5.load


These are the seemingly relevant processes from ps -aux:

root      5676  0.0  0.5  20024  6004 ?        Ss   18:18   0:00 /usr/sbin/apach
www-data  5756  0.0  0.3  20024  3208 ?        S    18:18   0:00 /usr/sbin/apach
www-data  5757  0.0  0.3  20024  3208 ?        S    18:18   0:00 /usr/sbin/apach
www-data  5758  0.0  0.3  20024  3208 ?        S    18:18   0:00 /usr/sbin/apach
www-data  5759  0.0  0.3  20024  3208 ?        S    18:18   0:00 /usr/sbin/apach

I still get the same response when I try to run the PHP page.

Thanks.

---

### Post by mpeters on 2007-06-30
You could try re-installing the Apache php module:

[INDENT]sudo apt-get install libapache2-mod-php5[/INDENT]

and just to be sure:

[INDENT]sudo a2enmod php5[/INDENT]

finally restart apache:

[INDENT]sudo /etc/init.d/apache2 restart[/INDENT]

---

### Post by carpetn on 2007-06-30
I just tried that. It doesn't seem to have helped. 

eric@lenovo-1:~$ sudo a2enmod php5
Module php5 installed; run /etc/init.d/apache2 force-reload to enable.
eric@lenovo-1:~$ sudo /etc/init.d/apache2 force-reload
 * Forcing reload of web server (apache2)...                                    apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
eric@lenovo-1:~$ sudo /etc/init.d/apache2 restart
 * Forcing reload of web server (apache2)...                                    apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

"sudo ps -aux" shows the same 5 apache processes, so the restart seems to have worked.

I also used the Synaptic Package Manager to uninstall and reinstall what seemed to be the key PHP programs: libapache2-mod-php5, php5, php5-common, and php5-mysql. I did this because I had installed apache after installing php5 and thought maybe the order of installing was important.

My _Dummies_ book says that there needs to be some appropriate lines about php in the httpd.conf file. My http.conf file is blank. Should I enter the material they suggest? To do that, I need to know the directory where php is installed. Here's what the command "find" give me. How can I tell which is the php installation and which are auxilliary files? I'm guessing it's one that ends with a simple "php" rather than a more complex name, but there are several of those. (Unfortunately the Synaptic Package Manager doesn't tell me where it is installing things or give me a choice.)

eric@lenovo-1:/$ sudo find / -name "php*"
/usr/lib/php5
/usr/share/php5
/usr/share/php5/php.ini-dist
/usr/share/php5/php.ini-dist.cli
/usr/share/lintian/overrides/php5-common
/usr/share/gedit-2/plugins/snippets/php.xml
/usr/share/services/searchproviders/php.desktop
/usr/share/doc/php5
/usr/share/doc/php5-mysql
/usr/share/doc/php5-common
/usr/share/doc/php5-common/examples/php.ini-recommended
/usr/share/doc/php5-common/examples/php.ini-dist
/usr/share/doc/php5-common/examples/php.ini-paranoid
/usr/share/gtksourceview-1.0/language-specs/php.lang
/usr/share/linda/overrides/php5-common
/usr/share/icons/mono/scalable/apps/phppg.svgz
/usr/share/icons/mono/scalable/mimetypes/php.svgz
/usr/share/icons/crystalsvg/32x32/apps/phppg.png
/usr/share/icons/crystalsvg/16x16/apps/phppg.png
/usr/share/icons/crystalsvg/128x128/apps/phppg.png
/usr/share/icons/crystalsvg/64x64/apps/phppg.png
/usr/share/icons/crystalsvg/48x48/apps/phppg.png
/usr/share/apps/quanta/templates/scripts/php
/usr/share/apps/quanta/templates/pages/php
/usr/share/apps/quanta/doc/php.docrc
/usr/share/apps/quanta/doc/php
/usr/share/apps/quanta/dtep/php
/usr/share/apps/katepart/syntax/php.xml
/usr/share/apps/kafkapart/pics/php.png
/etc/php5
/etc/php5/apache2/php.ini
/etc/cron.d/php5
/etc/apache2/mods-enabled/php5.conf
/etc/apache2/mods-enabled/php5.load
/etc/apache2/mods-available/php5.conf
/etc/apache2/mods-available/php5.load
/var/lib/php5
/var/lib/dpkg/info/php5-mysql.list
/var/lib/dpkg/info/php5-common.md5sums
/var/lib/dpkg/info/php5-common.postrm
/var/lib/dpkg/info/php5-common.list
/var/lib/dpkg/info/php5.list
/var/lib/dpkg/info/php5-common.conffiles
/var/lib/dpkg/info/php5-mysql.conffiles
/var/lib/dpkg/info/php5-mysql.md5sums
/var/lib/dpkg/info/php5-mysql.postinst
/var/cache/apt/archives/php5_5.2.1-0ubuntu1.2_all.deb
/var/cache/apt/archives/php5-common_5.2.1-0ubuntu1.2_i386.deb
/var/cache/apt/archives/php5-mysql_5.2.1-0ubuntu1.2_i386.deb


Thanks.

---

### Post by carpetn on 2007-06-30
I just edited my httpd.conf file following the _PHP & MySQL for Dummies_ book (2004), as follows. I still can't get my test.php file to run. It's saved in the same directory as the file that came with apache, file:////var/www/apache2-default/index.html, which runs. Is this the correct "web space" aka "Document Root"? 

Thanks

---

### Post by carpetn on 2007-06-30
Sorry, I forgot to paste in what I put in the httpd.conf file.

I just edited my httpd.conf file following the _PHP & MySQL for Dummies_ book (2004), as follows. 

#by EHB per _PHP & MySQL for Dummies_ (2004)
ScriptAlias /php/ /etc/php
Action application/x-httpd-php /php/php-cgi-exe
AddType application/x-httpd-php .php


I still can't get my test.php file to run. It's saved in the same directory as the file that came with apache, file:////var/www/apache2-default/index.html, which runs. Is this the correct "web space" aka "Document Root"?

Thanks

---

### Post by Milambar on 2007-06-30
I might be wrong here...

Doesnt a file://// URI access the file directly, without going through the webserver at all? Therefore, he will be prompted for what to do with the .php file...

In order to get the php file to execute, he needs to request it from the webserver with a http:// URI

Im probably wrong though.

---

### Post by carpetn on 2007-06-30
Thanks for the suggestion. However, I get the same result if I use File-Open and click on the file. File-Open works for other (html) files OK.

---

### Post by Milambar on 2007-07-01
*sigh*

File->open is exactly the same as typing file:////. Yes it works for other html files because they are not dependant on server side parsing of the code. 

php files are PROGRAMS which need to be interpeted, which is similar to being executed, by apache. Firefox doesn't understand php code. Nor should it. The code HAS to be processed by apache, and file->open and file://// both bypass apache.

Try pointing a web browser to [http://127.0.0.1/your.php.file](http://127.0.0.1/your.php.file) or [http://localhost/your.php.file](http://localhost/your.php.file).

Of course, thats assuming apache is up and running, listening on the right port, has the right modules enabled, and that the docroot is set up correctly.

---

### Post by carpetn on 2007-07-01
Trying both "localhost/test.php" and "192.0.0.1/test.php" results in:

    "Firefox can't establish a connection to the server at 127.0.0.1."

Milanbar wrote: "Of course, thats assuming apache is up and running, listening on the right port, has the right modules enabled, and that the docroot is set up correctly."

I've been hoping someone familiar with Ubuntu's versions of Apache and PHP could help me determine whether in fact I have them set up right, since I'm using Ubuntu versions of both. 

As noted in my previous posts, it appears that php5.conf and php5.load are installed and, if I am interpreting the ps -aux results right, that apache is up and running. I have not seen anything that tells me what "docroot" is or how to set it up correctly.

Thanks.

---

### Post by mpeters on 2007-07-01
> **carpetn said:**
> Sorry, I forgot to paste in what I put in the httpd.conf file.

I just edited my httpd.conf file following the _PHP & MySQL for Dummies_ book (2004), as follows. 

#by EHB per _PHP & MySQL for Dummies_ (2004)
ScriptAlias /php/ /etc/php
Action application/x-httpd-php /php/php-cgi-exe
AddType application/x-httpd-php .php


This is basically what /etc/apache2/mods-enabled/php5.conf provides.

> 
I still can't get my test.php file to run. It's saved in the same directory as the file that came with apache, file:////var/www/apache2-default/index.html, which runs. Is this the correct "web space" aka "Document Root"?

Thanks

As Milambar correctly said, you should be accessing this file by via [http://localhost/test.php](http://localhost/test.php). HTML files will display OK accessing them via File->Open but not php scripts.

---

### Post by mpeters on 2007-07-01
> **carpetn said:**
> Trying both "localhost/test.php" and "192.0.0.1/test.php" results in:

    "Firefox can't establish a connection to the server at 127.0.0.1."

Milanbar wrote: "Of course, thats assuming apache is up and running, listening on the right port, has the right modules enabled, and that the docroot is set up correctly."

I've been hoping someone familiar with Ubuntu's versions of Apache and PHP could help me determine whether in fact I have them set up right, since I'm using Ubuntu versions of both. 

As noted in my previous posts, it appears that php5.conf and php5.load are installed and, if I am interpreting the ps -aux results right, that apache is up and running. I have not seen anything that tells me what "docroot" is or how to set it up correctly.

Thanks.

Sorry, didn't see this post before I sent my last reply. What does:

[INDENT]sudo netstat -atnp | grep apache2[/INDENT]

show. Do you have a firewall running?

Do you have any files under /etc/apache2/sites-enabled/? If so, make sure "Document root" is set correctly there. If not, copy or link the file /etc/apache2/sites-available/default to /etc/apache2/sites-enabled and make sure "Document root" is set correctly in that file. Once again restart apache after making any changes.

---

### Post by carpetn on 2007-07-01
Thanks, mpeters. 

Here's what I get;

eric@lenovo-1:~$ sudo netstat -atnp | grep apache2
Password:
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     5672/apache2   

Document Root is set for /var/www, which seems to be right. 

I don't think I have a firewall set--does feisty fawn set one automatically? I don't see anything about firewall or security under Applications or System. My router has a firewall, but I would think that localhost access would not be affected by that. I'm able top ping localhost OK.

I commented out (#) the changes I made to httpd.conf.

When I try:
[http://localhost/test.php](http://localhost/test.php)

I get:
"Not Found

The requested URL /test.php was not found on this server.
Apache/2.2.3 (Ubuntu) PHP/5.2.1 Server at localhost Port 80"

---

### Post by carpetn on 2007-07-01
eric@lenovo-1:~$ sudo /etc/init.d/apache2 restart
Password:
 * Forcing reload of web server (apache2)...                                                    apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

This results in the following processes, acc to ps -aux:
root      7983  0.0  0.5  20024  6004 ?        Ss   08:28   0:00 /usr/sbin/apache2 -k start
www-data  7987  0.0  0.3  20024  3716 ?        S    08:28   0:00 /usr/sbin/apache2 -k start
www-data  7988  0.0  0.3  20024  3208 ?        S    08:28   0:00 /usr/sbin/apache2 -k start
www-data  7989  0.0  0.3  20024  3208 ?        S    08:28   0:00 /usr/sbin/apache2 -k start
www-data  7990  0.0  0.3  20024  3208 ?        S    08:28   0:00 /usr/sbin/apache2 -k start
www-data  7991  0.0  0.3  20024  3208 ?        S    08:28   0:00 /usr/sbin/apache2 -k start
www-data  8012  0.0  0.3  20024  3208 ?        S    08:29   0:00 /usr/sbin/apache2 -k start

Does anything look wrong here?

---

### Post by mpeters on 2007-07-01
> **carpetn said:**
> Thanks, mpeters. 

Here's what I get;

eric@lenovo-1:~$ sudo netstat -atnp | grep apache2
Password:
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     5672/apache2   

Document Root is set for /var/www, which seems to be right. 

I don't think I have a firewall set--does feisty fawn set one automatically? I don't see anything about firewall or security under Applications or System. My router has a firewall, but I would think that localhost access would not be affected by that. I'm able top ping localhost OK.

I commented out (#) the changes I made to httpd.conf.

When I try:
[http://localhost/test.php](http://localhost/test.php)

I get:
"Not Found

The requested URL /test.php was not found on this server.
Apache/2.2.3 (Ubuntu) PHP/5.2.1 Server at localhost Port 80"

OK. That shows us you are accessing the webserver correctly and that PHP is running. It's just that the file is not being found. Is your test.php script located in /var/www/test.php? If so what are the permissions on the file:

[INDENT]ls -l /var/www/test.php[/INDENT]

The file should be world readable or owned by the user which your apache process is running as, probably *www-data*

---

### Post by carpetn on 2007-07-01
Oops.

Directory root should be /var/www/apache2-default. I'll make that change.

---

### Post by carpetn on 2007-07-01
That did it--after restarting.
Thanks for the help and patience. Curious that the apache installation created the subdirectory /var/www/apache2-default but was inconsistent then when it defined the Directory root.

Thanks again.

---

### Post by Milambar on 2007-07-01
Next learn how to define apache vhosts...

*hides*

Well done, glad you got it sorted.

---


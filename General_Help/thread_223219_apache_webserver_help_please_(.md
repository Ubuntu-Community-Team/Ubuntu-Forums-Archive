---
title: "apache webserver help please :("
date: 2006-07-26
forum: General Help
---

### Post by Xzallion on 2006-07-26
I have never messed with servers before, and want to play around with a *simple* webserver on my desktop pc running ubuntu 6.06 Dapper Drake.

I just spent over three hours googling and searching the ubuntu forums for a tutorial on how to set up the webserver after apache is installed.  I haven't been able to find one.  I did find out everything else though (Like dynamic dns stuff and port forwarding through my router).

Anyways, I installed apache2 through synaptic package manager, and told it to start the server by clicking System> Administration> Services and clicking apache, but I have no clue what to do from here.  Any help and/or advice would be appreciated. Thanks in advance :)

---

### Post by MonkeyNet on 2006-07-26
Your configuration files are located in the /etc/apache2 directory. If you edit any of the files, they are pretty self explanitory with heaps of comments made throughout the file.

By default, the directory to place html files is /var/www

In your web browser, you should be able to type in localhost and see the default page for apache which lets you know that it is working.

Start putting your HTML files into /var/www and away you go :)

Cheers,

Andrew

---

### Post by Xzallion on 2006-07-26
When I type in [http://localhost/](http://localhost/) I get an error page, not the default page.

Also, the only thing in /var/www/ is a folder called apache2-default
inside that folder is a bunch of index pages, is that where I'm supposed to put web pages, or should I put them straight into /var/www/ ?

Do I need to edit any of the files in /etc/apache2/ to get apache to work?

---

### Post by MonkeyNet on 2006-07-26
> **Xzallion said:**
> When I type in [http://localhost/](http://localhost/) I get an error page, not the default page.

Also, the only thing in /var/www/ is a folder called apache2-default
inside that folder is a bunch of index pages, is that where I'm supposed to put web pages, or should I put them straight into /var/www/ ?

Do I need to edit any of the files in /etc/apache2/ to get apache to work?

If you edit /etc/apache2/apache2.conf you will see a line called

ServerRoot

This line points to the directory of the default site. Try that and see how you go

---

### Post by Xzallion on 2006-07-26
I edited /etc/apache2/apache2.conf, set the server root to the right directory ( /var/www/ ) and I still get nothing but an error page from [http://localhost/](http://localhost/)

---

### Post by clarkth on 2006-07-26
If you haven't done so (or it is not set up), look at the ports.conf file in /etc/apache2/

Make sure it is set to the http port.

Listen 80

Save, and restart apache with /etc/init.d/apache2 restart

You should be able to use [http://127.0.0.1](http://127.0.0.1) and see the apache default index.html file that is in /var/www/

---

### Post by Xzallion on 2006-07-26
I just checked the ports.conf file, it says "Listen 80".  I did the restart command and tried [http://127.0.0.1/](http://127.0.0.1/) , I still get an error :(

---

### Post by az on 2006-07-26
[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

You do not need to start apache.  It starts every time you boot and only stops if you stop it.

Do you remember what you did to configure apache2?  Because it works out-of-the-box.

After you run

sudo apt-get install apache2
you should be able to browse localhost and see your default site.

You can always remove the apache2 directory in /etc and the reinstall apache2

sudo apt-get install --reinstall apache2 apache2-common apache2-mpm-worker apache2-utils libapr0 ssl-cert

---

### Post by nihilocrat on 2006-07-26
hee hee.

First of all, ServerRoot sets the directory where apache looks for config files. DocumentRoot is the one you want to point to /var/www/.

Secondly, as of ... whenver ago... apache2 started using the sites-available / sites-enabled vhosting scheme as default. You will find the vhost for the default apache page in /etc/apache2/sites-available and symlinked in /etc/apache2/sites-enabled. Dumping stuff in /var/www/ as of "whenver ago" will do absolutely nothing.

If you just want to play around without having to learn what a vhost is and everything, just replace index.html in /var/www/apache-default with an index.* of your choosing. If you want to start using PHP or something like that off the bat, then you'll need to install libapache2-php5 or something like that.

---

### Post by Xzallion on 2006-07-26
> **azz said:**
> [https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

You do not need to start apache.  It starts every time you boot and only stops if you stop it.

Do you remember what you did to configure apache2?  Because it works out-of-the-box.

After you run

sudo apt-get install apache2
you should be able to browse localhost and see your default site.

You can always remove the apache2 directory in /etc and the reinstall apache2

sudo apt-get install --reinstall apache2 apache2-common apache2-mpm-worker apache2-utils libapr0 ssl-cert

I didn't do anything to configure apache2 besides click System> Administration> Services and check the box that says apache2.  Then I did what MonkeyNet and Clarkth said.  But I removed /etc/apache2, reinstalled everything, and have not done any configuration. In other words back to square one.

but somehow that fixed everything cause [http://localhost/](http://localhost/) works now.  thanks alot! :D

---


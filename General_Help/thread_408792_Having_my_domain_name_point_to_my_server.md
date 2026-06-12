---
title: "Having my domain name point to my server"
date: 2007-04-13
forum: General Help
---

### Post by justin on 2007-04-13
I have recently set up Apache on my computer, [http://68.46.79.22/]("http://68.46.79.22/") and everything seems to be working ok, at least enough for a basic web site.

I also have registered a domain at GoDaddy.com, how can I get the domain to point to my server. It works using the forward feature, but that immediately exposes my ip in the navigation bar. What's the real way to set this up?

[http://www.justinplummer.com]("http://www.justinplummer.com")

---

### Post by bernied on 2007-04-13
Is it the ServerName directive?
```
cat /etc/apache2/apache2.conf | grep ServerName
```
It should have the full name and port number, so:
ServerName [www.justinplummer.com:80](www.justinplummer.com:80)

---

### Post by justin on 2007-04-13
What do I do on the godaddy end though?

---

### Post by bernied on 2007-04-13
I was assuming you had a standard ubuntu install of apache2. If so, you should have an /etc/apache2 directory, and in it there should be a file called apache2.conf

If you have this file, then you could try editing it and adding the directive to it.

[Here](http://httpd.apache.org/docs/2.0/mod/core.html#servername) is the description in the apache manual.

---

### Post by jeffathehutt on 2007-04-13
What you need to do is find a place that will manage the dns for you.  Try [www.zoneedit.com](www.zoneedit.com)

As far as I know, they are still free.  I used their site in the past and it couldn't be any easier.  All you do is go to the managed dns section, then enter your domain name as well as your IP address.  They will then give you nameservers to use.  Go to godaddy and edit the name servers for your domain to match what zoneedit told you.  After a few days (maybe even sooner) your domain should be working:)

---

### Post by justin on 2007-04-13
I'll see if it works, thanks for the info!

---

### Post by az on 2007-04-13
> **justin said:**
> I have recently set up Apache on my computer, [http://68.46.79.22/]("http://68.46.79.22/") and everything seems to be working ok, at least enough for a basic web site.

I also have registered a domain at GoDaddy.com, how can I get the domain to point to my server. It works using the forward feature, but that immediately exposes my ip in the navigation bar. What's the real way to set this up?

[http://www.justinplummer.com]("http://www.justinplummer.com")

You need to set your domain record to point to your IP address.  Your domain hosting provider should help you with that.   It will usually take 24-48 hours for DNS propagation to happen, after that.

Your server will work out-of-the box, If only one site is being hosted on your box, you don't even need to specify the ServerName.

---

### Post by kraymore on 2007-12-04
i used [www.dnsexit.com](www.dnsexit.com) as an alternative to the website used to manage domain dns to my home ip address.
what is a free managed dns service for web and mail hosting, preferably one that does mail backup for free (or very cheap), and with the ability to update ip address through an ubuntu daemon ?

also when i visit my self hosted domain i am dropped to 

Index of /
[ICO]	Name	Last modified	Size	Description
[DIR]	apache2-default/	20-Nov-2004 14:16 	


this is my sites-enabled file 
# NameVirtualHost *
<VirtualHost *>
        ServerAdmin [email]admin@mydomain.com[/email]
        ServerName [www.mydomain.com:80](www.mydomain.com:80)
        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # RedirectMatch ^/$ /apache2-default/
        </Directory>


however i am using apache2 and in my /etc/apache2/sites-available/domain file 
which has been activated by sudo a2ensite domain when i edit the */sites-enabled/mydomain file 
i have checked and unchecked RedirectMismatch yielding the same results.  i've also restarted the apache2 webserver as well inbetween checking as well as clearing the cache.

---

### Post by kraymore on 2007-12-04
> **bernied said:**
> Is it the ServerName directive?
```
cat /etc/apache2/apache2.conf | grep ServerName
```
It should have the full name and port number, so:
ServerName [www.justinplummer.com:80](www.justinplummer.com:80)

if you are hosting multiple sites how do you change the apache2.conf to reflect them ?  i used a a2ensite command to load the settings of my first website however it would not launch until i did what you did to apache2.conf.  i however dont know what would happen if i were to host more sites.

---


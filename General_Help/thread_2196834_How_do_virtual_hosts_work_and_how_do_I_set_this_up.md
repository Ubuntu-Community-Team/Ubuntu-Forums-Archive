---
title: "How do virtual hosts work and how do I set this up for an locally hosted Wordpress"
date: 2013-12-31
forum: General Help
---

### Post by greavette on 2013-12-31
Hello,

I've successfully installed WordPress on Ubuntu 12.04 on our home server (in a Virtual Machine). I can access this site using our internal IP address.

I have our Untangle router installed that acts as our DHCP and DNS server. This gateway allows me to use Namecheap for dynamic DNS. Our Home network does not have a static IP address.

I've bought a domain name (for this post I will use a dummy name of ourfamily.ca as our domain name) from Namecheap and I've successfully setup Namecheap for our dynamic dns. Using our recently purchased domain name I can access our Untangle Router Login from outside our network so I know that our dynamic dns account is working properly.

(I've changed the following from the actual names, but I want to give a sense to you all on how I've set this up)

I've installed WordPress in /var/www/familysite
I can access our WordPress site internally using:
10.100.105.110/familysite

On our Untangle Router I've added a portforward rule using port 80 to our WordPress Server. This is where I'm having trouble. I don't think I've done this correctly because when I try to connect to our WordPress site from outside and not use the WordPress site Name like so:
[http://ourfamily.ca](http://ourfamily.ca)

I receive the "It Works!" page so I am getting to my Apache site.

But when I try to access the WordPress site using:
[http://ourfamily.ca/familysite](http://ourfamily.ca/familysite)

I receive "Service Temporarily Unavailable" error message.  But what's strange is in my address bar I don't see [http://ourfamily.ca/familysite/wp-login.php](http://ourfamily.ca/familysite/wp-login.php) like I would expect...But I see instead 10.100.105.110/familysite/wp-login.php? 

I've asked on the Wordpress forum and they say the problem is with my Dynamic DNS provider. I checked with Namecheap and they say it's my internal webserver problem. I'm not sure where the problem is. I've checked with Untangle Support and received the reply that the problem is most likely that I'm not using Virtual Hosts on my Apache Server.  I've read up a bit on virtual hosts now and it looks like this would be used to run more than one domain off a single IP address.  I'm not using more than one domain here...just a single domain "ourfamily.ca".  

I'm at a loss as to what to look up next?  Any advice you can give me on how to fix this would be greatly appreciated.  

Thank you.

---

### Post by TheFuzz4 on 2013-12-31
So in /etc/apache2 there are two directories
sites-available and sites-enabled

In your sites-available you're going to want to have a file named something like ourfamily.ca.conf
The contents of this file should look something like this
```

<VirtualHost *:80>
ServerAdmin webmaster@ourfamily.ca
ServerName ourfamily.ca
ServerAlias ourfamily.ca
DocumentRoot " /var/www/familysite"
<Directory " /var/www/familysite">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

```

Once you have that then cd /etc/apache2/sites-enabled
sudo ln -s /etc/apache2/sites-available/ourfamily.ca.conf .
sudo service apache2 reload

This is a virtual server config that tells apache to listen for all http requests coming from ourfamily.ca and handle them.  I use these all the time for subdomains of my domain i.e. photos.mydomain.com blog.mydomain.com etc.  Let me know if I can be of any more assistance to you.  Thanks.

---

### Post by greavette on 2013-12-31
Awesome!  Thanks very much for the assistance Fuzz!

question for you...does the line:
ServerAdmin [email]webmaster@ourfamily.ca[/email]

Need to use webmaster or does it use the user id of my server?

Thanks again...I'll give this a try. 

Happy New Year!

---

### Post by greavette on 2013-12-31
That's weird. I added these changes just as you suggested but upon reloading apache2 service I received this error:

Warning: Document Root [/etc/apache2/ /var/www/familysite] does not exist.

Yet I've checked at that this is the corrent name in /var/www/ so I don't know why it says it doesn't exist?  Any ideas what I've done wrong?

---

### Post by SeijiSensei on 2014-01-01
Remove the leading spaces in " /var/www/..." and see if that helps.

Concerning your broader question about DNS resolution, you might be encountering a problem with some routers where they cannot send outbound traffic to the inbound interface.  You would need to have machines on the local LAN resolve the website hostname to the local 10.100.105.110 address.  You can do that by running a local DNS server or by using "[hosts]("http://en.wikipedia.org/wiki/Hosts_%28file%29#Location_in_the_file_system")" files on the local clients.

---

### Post by greavette on 2014-01-01
Thanks!  That got me a bit further...but still not working quite properly.

By removing the leading spaces I'm not seeing the does not exist error now when I reload apache2.  But when I try to get to ourfamily.ca, I can now see that the addressbar changes to the following:

10.100.105.110/familysite/wp-login.php

With a 'Service Temporarily Unavailable' message instead of my login page.

This can't be that hard?  I'm sure many others are setting up a local install of some website and using a domain they bought with dynamic dns and when people go to that domain they come to the local website instead.  What am I doing wrong?

So in /etc/apache2/sites-enabled I have a file called ourfamily.ca.conf.  The contents of this file are:

```
<VirtualHost *:80>
Alias /ashley /var/www/familysite
ServerAdmin webmaster@ourfamily.ca
ServerName ourfamily.ca
ServerAlias ourfamily.ca
DocumentRoot "/var/www/familysite"
<Directory "/var/www/familysite">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

```

How do I get this to work so the following happens:
#1:  When people type in [http://ourfamily.ca/familysite](http://ourfamily.ca/familysite) they are sent to my local install of Wordpress in /var/www/familysite and they can login and don't see the IP address in the addressbar?

#2:  If I wanted to add another subdirectory to /var/www for another Wordpress site for say example:  [http://ourfamily.ca/familysite2](http://ourfamily.ca/familysite2) they are sent to another local install of Wordpress in /var/www/familysite2 and they can login and don't see the IP address in the addressbar?

If my expectation of how this should work is completely wrong, then I ask that someone please set me straight on how this should work for me.

Thanks!

---

### Post by SeijiSensei on 2014-01-02
I'd start by reading the [Server Guide](https://help.ubuntu.com/12.04/serverguide/httpd.html), but as I said before, you need to fix your name resolution to get rid of the IP address issue.  I only host sites on publicly-visible servers from [Linode]("http://linode.com/") where I can control the DNS and IP addressing and ensure both forward and reverse name resolution works properly. Trying to host sites on a residential server with dynamic DNS and port forwarding can be more problematic, but there are people who do this.  Perhaps one of them will pitch in.

---


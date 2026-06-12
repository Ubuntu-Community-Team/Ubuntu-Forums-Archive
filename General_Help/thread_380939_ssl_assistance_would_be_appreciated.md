---
title: "ssl assistance would be appreciated"
date: 2007-03-10
forum: General Help
---

### Post by Biggus on 2007-03-10
Hi chaps.

I've recently been messing around with stuff I don't know much about, and have managed to get myself an Apache server up and running.

I thought it would be quite cool if I could have some sort of secure connection thing going on, so I spent ages trying to install it from the openssl site, before I realised I already had it installed from the Synaptic Package Manager.

Anyhow, I've been following the instructions on another thread [here]("http://www.ubuntuforums.org/showpost.php?p=19832&postcount=4") .

The problem is that when I attempt to access my server at [https://myyip](https://myyip) , it is throwing up an error message, namely > "myip has sent an incorrect or unexpected message. Error code -12263"

I also noticed that when I restart my Apache service, I am now getting a couple of error messages, 

> sudo /etc/init.d/apache2 restart

 * Forcing reload of apache 2.0 web server...
 apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sat Mar 10 14:54:01 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sat Mar 10 14:54:03 2007] [warn] NameVirtualHost *:0 has no VirtualHosts

Simply typing the ip into firefox does still bring up the index page of the server, so it's not critical that I get it fixed, but it would be nice to have a groovy little padlock appear somewhere in my browser.

Perhaps some brighter spark who has a higher level of caffeine in their bloodstream than I is able to spot some obvious error of my ways?

---

### Post by x1a4 on 2007-03-10
Hi, 

The error you get is generated because, apparently, you don't have a fully qualified domain name.  You need to register a domain name with an authorized domain registrar then update your Apache configuration.  

You also need Apache's SSL module for SSL to work.

---

### Post by Biggus on 2007-03-10
Really? Wow that's pretty far out dude.

I never knew that a domain name was required, I do have a few which I've registered through GoDaddy, and which are currently 'parked', so I might well have a little mess around with that and see if I can come up with anything.

The Apache SSL module thing will have to wait until my Linux boffin friend comes over, 

Anything which downloads as source code is still sorcery as far as I'm concerned. :)

---

### Post by x1a4 on 2007-03-12
> **Biggus said:**
> Really? Wow that's pretty far out dude.

I never knew that a domain name was required, 

Be sure to read the Apache documentation, it's all there.  
The url is [http://localhost/manual/](http://localhost/manual/)


> The Apache SSL module thing will have to wait until my Linux boffin friend comes over, 

To enable Apache's SSL module create these symlinks

/etc/apache2/mods-enabled/ssl.conf
/etc/apache2/mods-enabled/ssl.load

pointing to 

/etc/apache2/mods-available/ssl.conf
/etc/apache2/mods-available/ssl.load

Do it like this: 

[I]sudo ln -s /etc/apache2/mods-available/ssl.conf /etc/apache2/mods-enabled/ssl.conf

sudo ln -s /etc/apache2/mods-available/ssl.load /etc/apache2/mods-enabled/ssl.load[/I]

Modify _/etc/apache2/httpd.conf_ to include this line: 

**LoadModule mod_ssl /usr/lib/apache2/modules/mod_ssl.so**

now restart Apache 

*sudo apache2ctl restart*


Look in Apache's documentation about how to configure SSL
[http://localhost/manual/mod/mod_ssl.html](http://localhost/manual/mod/mod_ssl.html)

You should also install [OpenSSL](http://www.openssl.org/), it's in the repositories.  Just run: 

*sudo apt-get install openssl*

---


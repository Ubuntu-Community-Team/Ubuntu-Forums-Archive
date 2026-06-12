---
title: "Creating Virtual Hosts in Ubuntu 13.10"
date: 2014-01-26
forum: General Help
---

### Post by N3RVE on 2014-01-26
Hello There,

I'm new to server management in Ubuntu. I have a VPS at Linode powered by Ubuntu 13.10 Server edition. I run Ubuntu 13.10 Desktop edition on my laptop and I have a LAMP stack setup with a web directory that works out of an assigned folder in my home folder.

I'm trying to achieve this setup:

A new Virtual host setup with an IP address different from the localhost or 127.0.0.1, I tried using **128.0.5.1**. So under /etc/apache2/sites-available, I created **128.0.5.1.conf** and this is the content of the file:
```
<VirtualHost *:80>
	# The ServerName directive sets the request scheme, hostname and port that
	# the server uses to identify itself. This is used when creating
	# redirection URLs. In the context of virtual hosts, the ServerName
	# specifies what hostname must appear in the request's Host: header to
	# match this virtual host. For the default virtual host (this file) this
	# value is not decisive as it is used as a last resort host regardless.
	# However, you must set it for any further virtual host explicitly.
	
	ServerName 128.0.5.1

	ServerAdmin webmaster@localhost
	DocumentRoot /home/n3rve/www2

	# Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
	# error, crit, alert, emerg.
	# It is also possible to configure the loglevel for particular
	# modules, e.g.
	#LogLevel info ssl:warn

	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined

	# For most configuration files from conf-available/, which are
	# enabled or disabled at a global level, it is possible to
	# include a line for only one particular virtual host. For example the
	# following line enables the CGI configuration for this host only
	# after it has been globally disabled with "a2disconf".
	#Include conf-available/serve-cgi-bin.conf

<Directory "/home/n3rve/www2">
   Order allow,deny
   Allow from all
   AllowOverride FileInfo
   # New directive needed in Apache 2.4.3: 
   Require all granted
</Directory>
</VirtualHost>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
```

I edited the /etc/**hosts** file as follows:
```

127.0.0.1	localhost
127.0.1.1	B-613
128.0.5.1	localhost
128.0.5.1	B-613
128.0.5.1	127.0.0.1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

127.0.0.1 productsearch.ubuntu.com
```

Then in a terminal window, I ran **a2ensite 128.0.5.1.conf** and it asked me to run **service apache2 reload** which I did. Now when I try to run a2ensite 128.0.5.1, it says Site **128.0.5.1 already enabled**.

When I try to visit [http://128.0.5.1](http://128.0.5.1), it doesn't work. Looking at the above setup, what have I or haven't I done, and how can I get it working?
I appreciate any help.

---

### Post by TheFu on 2014-01-26
To begin, you cannot use just any IP that you want. 128.0.5.1 is part of Romania's address space and unless you are actually on that subnet with THAT specific IP assigned by the provider, nothing good will happen.

127.0.0.1 is the localhost for every computing device in the world. 127.0.1.1 is another - this may be what you want, provided traffic never needs to leave the machine.  If you want to run on a different IP, usually the best choice is one from your LAN address space.  Usually something like 192.168.0.x or 192.168.1.x.  It isn't clear to me whether this is running in the VPS or on your home LAN at this point. I'm easily confused.

If you run **ifconfig** and **route** commands and post those back here, we can help.

Please put the /etc/hosts file back the way it was originally for now.  Networking is not hard, but it is not very forgiving of mistakes either.  If you really want to get started understanding IPv4 networking, might I suggest episode 25+ of the Security Now podcast?   grc.com/sn will get you close to the link.

---

### Post by CharlesA on 2014-01-26
They have a VPS at Linode. :) The Linode control panel should give them the IP address of their box.

As far as the virtual host config, ServerName is usually a domain or subdomain, not an IP address.

Keep in mind that you can't use just any domain name, you have to have purchased one in order to use it.

If you replace the ServerName directive with: ServerName somedomain.tld and restart apache, it should work.

If you have not updated DNS, you can test it by adding the IP of the server and the host/domain name you want to test to /etc/hosts as TheFu suggested.

---

### Post by N3RVE on 2014-01-26
Thank you for your replies, TheFu & CharlesA.

> **TheFu said:**
> To begin, you cannot use just any IP that you want. 128.0.5.1 is part of Romania's address space and unless you are actually on that subnet with THAT specific IP assigned by the provider, nothing good will happen.

Yes, I understand this. I was trying to MAP IP addresses, and discovered this wasn't possible using the hosts file so I've resolved to using IP Tables for this and I can confirm this works as the redirection happens as expected. 

> **TheFu said:**
> 127.0.0.1 is the localhost for every computing device in the world. 127.0.1.1 is another - this may be what you want, provided traffic never needs to leave the machine.  If you want to run on a different IP, usually the best choice is one from your LAN address space.  Usually something like 192.168.0.x or 192.168.1.x.  It isn't clear to me whether this is running in the VPS or on your home LAN at this point. I'm easily confused.

Yes, I know 127.0.0.1 is home on any device. Actually 127.0.1.1 along with a bunch of others, 127/8 (127.0.0.0 => 127.255.255.255) are all reserved for loopback purposes. And to clarify, this is running locally, not on my VPS.

---

### Post by CharlesA on 2014-01-26
If you are running locally, you'd have to use a local IP instead of the public IP, otherwise it won't work.

---


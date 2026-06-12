---
title: "Subdomain / Loalhost"
date: 2008-02-19
forum: General Help
---

### Post by Quads on 2008-02-19
After reading several threads on setting up a subdomain on my local ubuntu server (basic LAMP install / 7.10) I've followed this document [https://help.ubuntu.com/community/LocalhostSubdomain](https://help.ubuntu.com/community/LocalhostSubdomain) which walks through a pretty basic set of steps to create essentially the virtual server, which is pointing to the subdomain folder in my /var/www directory. Those steps worked, worked well in fact, but possibly "too" well. 

When I open my browser (FF) on the server to test it, and I enter [http://localhost](http://localhost) I get forwarded to the subdomain. If I type in [http://my_subdomain_name.localhost](http://my_subdomain_name.localhost) I go to the specified folder I set up. 

So, it's like it took control over all traffic and doesn't allow me to access the rest of the folders / directories under var/www/ 

From another machine on my local network, obviously localhost won't resolve to my ubuntu server, so I type in the IP address. Interestingly, it shows the entire web contents (all my other folders and such) and doesn't 'jail' me in the subdamain. 

Any ideas? Did I miss a step? (or misunderstand something in the process?) 

TIA-

---

### Post by SpaceTeddy on 2008-02-19
nice gotcha. your problem is that apache distinguishes HOW you connect to it... i.e. it makes a difference if you use the ip or the name.

Explanation:
when you access the webserver from the same machine it is running on, you use the name to access it. In the configuration, you set the virtual host to respond to the name of the computer. which all works well. it responds to your virtual host, since that is (from the howto) set to respond [http://my_subdomain_name.localhost](http://my_subdomain_name.localhost) . 

now, when you access from other computers, you do NOT use the name you specified in the virtual host, you use the IP. to the virtual host will not kick in and you will end up in the default page (check /etc/apache/sites-available/default) that responds to anything apache does not have a specific virtual host for.

On the server itself, you can always use the ip instead of the name and you will get the same result as on any other computer in the network.

hope this makes sense...

---

### Post by Quads on 2008-02-19
Thanks Teddy. 
I'll never use the machine itself to access the development area on it in which I use it for. So, I'll never use [http://localhost](http://localhost) or subdomain/loaclhost. 

I'll always access the machine via the network, and through the IP address. 

What I'm trying to get to is to be able to use dyndns, and point all of that traffic to the subdomain. 

So, internally, I do my development via the IP, and I have / see all of the folders in the root of /var/www/ and others who access the machine (from the intarwebs) use the address (for example) [http://subdomain.myname.dyndns.org](http://subdomain.myname.dyndns.org) and they are pointed to *only* the subdomain on my server and don't see everything else in /var/wwww/ (the only see what's in www/subdomain.

Does that make sense?

---

### Post by SpaceTeddy on 2008-02-19
yep, makes sense... i don't know if this is a safe way to do it, but you can do it like that...

what you want to do is swap the default and the virtual host... you want the server to always reply with the restricted section, except when you address it with it's internal ip address (since nobody else on the net should be able to do that, right ?)

you got pretty much everything setup for now... if you want further help, paste the default and the virtual host config along with your internal ip address of the server and i can fix them up for you so you can see what it should look like.

i know it works because i have several dynamic hostnames pointing to a machine :)

---

### Post by Quads on 2008-02-19
I'll dig up the config files and post them for your input. 

Thanks!

---

### Post by Quads on 2008-02-19
The internal IP address of the machine is 
192.168.15.50 
Under network setup for "hosts" I have both localhost and public.localhost bound to 127.0.0.1 

Default apache2 Host Config: 

```

NameVirtualHost *
<VirtualHost *>

	ServerAdmin webmaster@localhost
	
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
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

And the second virtual server I was creating to use / point to the subdomain: 

```

<VirtualHost public.localhost>
DocumentRoot /var/www/public/
ServerName public.localhost

<Directory "/var/www/public/">
                Options Indexes FollowSymLinks MultiViews +Includes
                AllowOverride None
                Order allow,deny
                allow from all
</Directory>
</VirtualHost>

```

And my dyndns config file: 
(my host pointer at dyndns is set to quads.dyndsn.org, which Ideally, I'd update that entry to public.quads.dyndns.org and route that traffic to the var/www/public/ folder. ) 

```

# Basic configuration file for ddclient
#
# /etc/ddclient.conf

daemon=600
cache=/tmp/ddclient.cache
pid=/var/run/ddclient.pid
use=web, web=checkip.dyndns.com/, web-skip='IP Address'
login=my_username
password=my_password
protocol=dyndns2
server=members.dyndns.org
wildcard=YES
quads.dyndns.org
custom=yes, example.com

```

Let me know what else I can provide. 

I'll try and write a tourorial after this is done, and hopefully this will be of assistance to others. 

Much thanks-

---

### Post by SpaceTeddy on 2008-02-20
ok, here are the config files that (hopefully) work the way you want them to. i've deleted some stuff i have never used, but if you need the docs or the CGI's then just put them back in... for me, they were always... overhead i never use...

ok, here they come

default> ####################
#  default config  #
####################
NameVirtualHost *
<VirtualHost *>
  DocumentRoot /var/www/public/


  <Directory "/var/www/public/">
    Options Indexes FollowSymLinks MultiViews +Includes
    AllowOverride None
    Order allow,deny
    allow from all
  </Directory>

 	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On
</VirtualHost>

and the config for the internal access (ONLY via ip, if you want a name, you will need to setup an internal dns aswell)

> ###################
# internal config #
###################

<VirtualHost *>
  ServerName 192.168.15.50
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from 192.168.15.0/24
	</Directory>

</VirtualHost>

bacup your old ones, copy these in, restart the apache and it should work. btw, you can create more of internal hostnames (by copying the file) for different hostnames you assign to yourself. so if you have more than one dyndns name, just create a config for each of them if you want them to be handeled differently

i really hope this works (since i cannot test ist) and that it helps you :)

Oh, one last thing... for the virtual hosts, if you want your server to answer on every network device, ALWAYS specify the * in the VirutalHost, otherwise it will only respond on the given ip address. Also, you can define more (!) than one ServerName in a config if you don't want multiple configs where just the ServerName differes.
The Allow from is (at the moment) set to your internal subnet. This is not really neccessary, but i thought i might put it in anyway so you can see how it woks.

Also, this is not the most secure of all setups, but it will work for now.
Enjoy

---

### Post by Quads on 2008-02-20
Awesome Teddy-

I'll play with these today and update the thread with some more info. 

Much thanks again.

---

### Post by Quads on 2008-02-20
Works like a charm. 

Internally, accessing the server via IP address, I have full view of the www/root 

Externally, (via dyndns) I have access to only the www/public/ folder and its contents. 

If others would find use in this, I'd be happy to create a short toutorial. 

LMK if you think that would be helpful. I'll put something together and post it.

---

### Post by SpaceTeddy on 2008-02-20
nice to know that it works... 
a short tutorial might not be bad - might even combine it with the setup of dyndns and post it as a howto so other can do what you have just done.

congratulations to your new webserver :)

---


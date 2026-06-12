---
title: "Help please, Apache and Vhost"
date: 2006-07-31
forum: General Help
---

### Post by savo on 2006-07-31
I have been trying for days to get this to work with no luck what so ever.

I have tried severl manuals but still i end up with the same problem.

I have set my /etc/hosts/ file like this

127.0.0.1 localhost jarsl.co.uk
127.0.0.1 jarsl.co.uk.co.uk jarsl.co.uk
127.0.0.1 mesh.jarsl.co.uk

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I have 2 files in /etc/apache2/sites-available and the enabled folder

default 

NameVirtualHost *
<VirtualHost *>
ServerName jarsl.co.uk
	ServerAdmin webmaster@localhost
	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# Uncomment this directive is you want to see apache2's
		# default start page (in /apache2-default) when you go to /
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

and the one i created

mesh

NameVirtualHost *:80
<VirtualHost *:80>
ServerName mesh.jarsl.co.uk
DocumentRoot /var/www/mesh/main
</VirtualHost>


Which as far as i can tell is all i need? The problem is i always end up in the mesh/main folder.

I am new to Linux so im bound to be missing something silly. 

Any ideas on what it is?

Sav

---

### Post by adamkane on 2006-07-31
The problem is probably with trying to configure with ipv6.

---

### Post by savo on 2006-07-31
I havent touched any of the IPv6 settings. I dont have any need for it atm should i just remove it from the hosts file ?

Thanks

Sav

---

### Post by adamkane on 2006-07-31
Oops, never mind. See:
[http://www.ubuntuforums.org/showthread.php?t=225009](http://www.ubuntuforums.org/showthread.php?t=225009)
[http://www.ubuntuforums.org/showthread.php?t=205724](http://www.ubuntuforums.org/showthread.php?t=205724)

---

### Post by savo on 2006-07-31
Looking at both the links you gave the first one is a problem where one of the sites is not enabled i duble checked and both of mine are running.

The only diffrence i can see with the other setup is that one is using site1 and site 2 and i am using default and site 2. 

I wouldnt have thought that this would matter but for some reason only site2 is being displayed.

---


---
title: "Apache2 Alias Issue"
date: 2012-10-17
forum: General Help
---

### Post by OldManRiver on 2012-10-17
All,

I have defined my aliases of:

```
<VirtualHost *:80>
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
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

	# Declare the Aliases here!
	Alias /davisoft/ "/var/www/Projects/Comp-WebSites/davisoft/"
	<Directory "/var/www/Projects/Comp-WebSites/davisoft/">
		Options Indexes MultiViews FollowSymLinks
		AllowOverride None
		Order allow,deny
		Allow from all
	</Directory>

	Alias /ads/ "/home/files/Dropbox/ads-n-cl/Ad Campaigns/"
	<Directory "/home/files/Dropbox/ads-n-cl/Ad Campaigns/">
		Options Indexes MultiViews FollowSymLinks
		AllowOverride None
		Order allow,deny
		Allow from all
	</Directory>

	Alias /dc-tech/ "/var/www/Projects/Comp-WebSites/dc-tech/"
	<Directory "/var/www/Projects/Comp-WebSites/dc-tech/">
		Options Indexes MultiViews FollowSymLinks
		AllowOverride None
		Order allow,deny
		Allow from all
	</Directory>

	Alias /doc/ "/usr/share/doc/"
	<Directory "/usr/share/doc/">
		Options Indexes MultiViews FollowSymLinks
		AllowOverride None
		Order deny,allow
		Deny from all
		Allow from 127.0.0.0/255.0.0.0 ::1/128
	</Directory>

	Alias /frameworks/ "/var/www/Frameworks/"
	<Directory "/var/www/Frameworks/">
		Options Indexes MultiViews FollowSymLinks
		AllowOverride None
		Order allow,deny
		Allow from all
	</Directory>

	Alias /functions/ "/var/www/functions/"
	<Directory "/var/www/functions/">
		Options Indexes MultiViews FollowSymLinks
		AllowOverride None
		Order allow,deny
		Allow from all
	</Directory>

	Alias /help/ "/var/www/helpdocs/"
	<Directory "/var/www/helpdocs/">
		Options Indexes MultiViews FollowSymLinks
		AllowOverride None
		Order allow,deny
		Allow from all
	</Directory>

	Alias /lists/ "/var/www/OS-Packages/PHPList/public_html/lists/"
	<Directory "/var/www/OS-Packages/PHPList/public_html/lists/">
		Options Indexes MultiViews FollowSymLinks
		AllowOverride None
		Order allow,deny
		Allow from all
	</Directory>

	Alias /marketing/ "/var/www/Marketing/"
	<Directory "/var/www/Marketing/">
		Options Indexes MultiViews FollowSymLinks
		AllowOverride None
		Order allow,deny
		Allow from all
	</Directory>

	Alias /metrix/ "/var/www/Projects/Comp-WebSites/metrix/"
	<Directory "/var/www/Projects/Comp-WebSites/metrix/">
		Options Indexes MultiViews FollowSymLinks
		AllowOverride None
		Order allow,deny
		Allow from all
	</Directory>

	Alias /packages/ "/var/www/OS-packages/"
	<Directory "/var/www/OS-packages/">
		Options Indexes MultiViews FollowSymLinks
		AllowOverride None
		Order allow,deny
		Allow from all
	</Directory>

	Alias /projects/ "/var/www/Projects/"
	<Directory "/var/www/Projects/">
		Options Indexes MultiViews FollowSymLinks
		AllowOverride None
		Order allow,deny
		Allow from all
	</Directory>

	Alias /refurbproducts/ "/var/www/Projects/Comp-WebSites/refurbproducts/"
	<Directory "/var/www/Projects/Comp-WebSites/refurbproducts/">
		Options Indexes MultiViews FollowSymLinks
		AllowOverride None
		Order allow,deny
		Allow from all
	</Directory>

	Alias /total-connect/ "/var/www/Projects/Comp-WebSites/total-connect/"
	<Directory "/var/www/Projects/Comp-WebSites/total-connect/">
		Options Indexes MultiViews FollowSymLinks
		AllowOverride None
		Order allow,deny
		Allow from all
	</Directory>

	Alias /work/ "/var/www/Work/"
	<Directory "/var/www/Work/">
		Options Indexes MultiViews FollowSymLinks
		AllowOverride None
		Order allow,deny
		Allow from all
	</Directory>
</VirtualHost>
```

But not all the aliases are working.  The localhost/ads/ and localhost/lists/ are not working, and wondering why as syntax is same for both of these.

OMR

---

### Post by greenpeace on 2012-10-29
hi,

not sure if you got this one solved already, but the alias for /ads/ has a space in the directory name, between "Ad" and "Campaigns"

```
Alias /ads/ "/home/files/Dropbox/ads-n-cl/Ad Campaigns/"
  <Directory "/home/files/Dropbox/ads-n-cl/Ad Campaigns/">
  Options Indexes MultiViews FollowSymLinks
  AllowOverride None
  Order allow,deny
  Allow from all
</Directory>
```

Could that be the cause?  Also, does the apache user have access to the Dropbox folder?


Finally, the [docs on Apache's site]("http://httpd.apache.org/docs/2.2/mod/mod_alias.html#alias") confirm behaviour of the aliases in the presence of slashes:

> Note that if you include a trailing / on the URL-path then the server will require a trailing / in order to expand the alias. That is, if you use

Alias /icons/ /usr/local/apache/icons/
then the URL /icons will not be aliased, as it lacks that trailing /. Likewise, if you omit the slash on the URL-path then you must also omit it from the file-path.

just check that this is what you want!  

cheers

---

### Post by OldManRiver on 2012-11-02
> **greenpeace said:**
> hi,

not sure if you got this one solved already, but the alias for /ads/ has a space in the directory name, between "Ad" and "Campaigns"

```
Alias /ads/ "/home/files/Dropbox/ads-n-cl/Ad Campaigns/"
  <Directory "/home/files/Dropbox/ads-n-cl/Ad Campaigns/">
  Options Indexes MultiViews FollowSymLinks
  AllowOverride None
  Order allow,deny
  Allow from all
</Directory>
```

Could that be the cause?  Also, does the apache user have access to the Dropbox folder?


Finally, the [docs on Apache's site]("http://httpd.apache.org/docs/2.2/mod/mod_alias.html#alias") confirm behaviour of the aliases in the presence of slashes:



just check that this is what you want!  

cheers

GP,

No the quotes fix anything not linux standard naming convention.

I have everything working except for the "/lists/" alias.

I've tried both these combinations:
```

	Alias /lists/ "/var/www/OS-Packages/PHPList/public_html/lists/"
	<Directory "/var/www/OS-Packages/PHPList/public_html/lists/">
and
	Alias /lists/ "/var/www/OS-Packages/lists/"
	<Directory "/var/www/OS-Packages/lists/">

```
As I posted the code in both places on the server, but neither work.  I first thought maybe there was a .htaccess file keeping it from working, but in searching found no file, so really puzzled why this does not work.

Maybe I need to add a .htaccess file with the right permissions to get this working but the error is a 404, not a 403 permissions error.

Open to suggestions here.

Cheers!

OMR

---

### Post by OldManRiver on 2012-11-25
All,

Can I get some help here?

Cheers!

OMR

---

### Post by pkadeel on 2012-11-25
> **OldManRiver said:**
> All,

Can I get some help here?

Cheers!

OMR
Check the file permission of your "index.html" (or what ever DirectoryIndex file is) in the Aliases which are giving 404 error. Most probably those will be set at -rw-r----- (0640)

---

### Post by OldManRiver on 2013-07-02
> **pkadeel said:**
> Check the file permission of your "index.html" (or what ever DirectoryIndex file is) in the Aliases which are giving 404 error. Most probably those will be set at -rw-r----- (0640)
P,

Not getting and 404 errors, just does not display file listing as it should.  I'm mostly using command line to process.

I make sure there is no index.anything files in the dirs, so I can test, and use symlinks to the starting process files when I finally want to call via browser.

Funny thing have exact same alias file on multiple machines, with differing results on each machine.

Cheers!

OMR

---


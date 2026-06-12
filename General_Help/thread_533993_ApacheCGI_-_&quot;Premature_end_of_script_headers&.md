---
title: "Apache/CGI - &quot;Premature end of script headers&quot;"
date: 2007-08-24
forum: General Help
---

### Post by blip2 on 2007-08-24
When trying to run a CGI:IRC script i still get this even after going through all the Apache how-to's and multiple google searches:

```
Server error!

The server encountered an internal error and was unable to complete your request.

Error message:
Premature end of script headers: irc.cgi

If you think this is a server error, please contact the webmaster.
Error 500
irc.dogmatix.net
Fri Aug 24 22:04:33 2007
Apache/2.0.55 (Ubuntu) DAV/2 mod_mono/1.1.10 mod_python/3.1.4 Python/2.4.3 PHP/5.1.2 mod_ruby/1.2.5 Ruby/1.8.4(2005-12-24) mod_perl/2.0.2 Perl/v5.8.7 
```

Log File:
```
[Fri Aug 24 22:04:33 2007] [error] [client 87.127.186.150] (2)No such file or directory: exec of '/web/live/irc/irc.cgi' failed
[Fri Aug 24 22:04:33 2007] [error] [client 87.127.186.150] Premature end of script headers: irc.cgi
```

Relevant sections from apache2.conf
```
<Directory /web/live>
	Options FollowSymLinks MultiViews
	AllowOverride All
	Order allow,deny
	allow from all
</Directory>

<VirtualHost *:80>
	ServerAdmin webmaster@dogmatix.net
	Servername irc.dogmatix.net	
	DocumentRoot /web/live/irc
      <Directory "/web/live/irc/">
        Order deny,allow
      </Directory>
</VirtualHost>
```

.htaccess in /web/live/irc
```
AuthType Basic
AuthName "Restricted Files"
AuthUserFile /web/users
Require user ben

Options  FollowSymLinks MultiViews +ExecCGI

<Files cgiirc.config>
   <Limit GET POST>
   deny from all
   </Limit>
</Files>
```

File permissions are set to 755

Fairly fresh install of Ubuntu 6.06

Whatever I've tried still doesn't work (the script is valid and even a simple hello world causes the same error) and yes the headers are actually written when I run the script in command line it produces this:

```
Set-cookie: cgiircauth=j1dabecn3qh5;path=/
Content-type: text/html
Pragma: no-cache
Cache-control: must-revalidate, no-cache
Expires: -1

<!-- This is part of CGI:IRC 0.5
  == http://cgiirc.sourceforge.net/
  == Copyright (C) 2000-2006 David Leadbeater <cgiirc@dgl.cx>
  == Released under the GNU GPL
  -->

<html>
<head>
...etc
```

Any idea on what is wrong or how this can be fixed?

---


---
title: "2 sites on Apache 2, but only one works"
date: 2007-11-30
forum: General Help
---

### Post by qwert231 on 2007-11-30
I just upgraded from 6.10 to 7.4. Before the upgrade my two sites, [http://mark.phillk.net](http://mark.phillk.net) and [http://www.greatwhitedata.com](http://www.greatwhitedata.com) were working.

Now, when apache2 starts, I get this:
mark@linux800:/etc/apache2/mods-enabled$ sudo /etc/init.d/apache2 restart
 * Forcing reload of web server (apache2)...                                                             apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Fri Nov 30 13:04:27 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
httpd (no pid file) not running
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Fri Nov 30 13:04:37 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
                                                                                                  [ OK ]


and only [http://mark.phillk.net](http://mark.phillk.net) works.

---

### Post by lightstream on 2007-12-01
So you are running your own web server with the DNS settings for each site pointing to your own static IP?

Cooool ...

When I click the problematic link, I get a 404 not found error, I presume this is the issue you're referring to?

Have you set up your .htaccess to redirect requests for this URL to the correct location?

Edited to add: the only thing which looks unusual in the Apache output is that it is saying 'using 127.0.1.1 for Server name', when I believe it is usually 127.0.0.1 - could be related?

The other thing I was going to ask was if the web site works properly if you go directly to the subfolder it's housed in from the server using a URL like **127.0.1.1/mywebfolder**?

---

### Post by mysticrider92 on 2007-12-01
I am not that experienced with this, but have you checked the VirtualHosts configuration file? It could have been overwritten in the upgrade, and the path for your buisness website was changed.

It looks like from your error that httpd is not running. I think that is an importent part of the VirtualHost setup.

---

### Post by qwert231 on 2007-12-07
I haven't looked at the VirtualHost file. What I had been using, when it worked, was sites-enabled, and a file for each site in there.

Yes, perhaps a file got over writtion somewhere, but I'm not sure where.

---

### Post by qwert231 on 2007-12-07
Here's what's in my logs for today:
[Thu Dec 06 23:56:38 2007] [error] [client 66.249.72.169] Attempt to serve directory: /web/GreatWhite/
[Fri Dec 07 04:22:06 2007] [error] [client 38.114.104.15] File does not exist: /web/GreatWhite/robots.txt
[Fri Dec 07 04:22:07 2007] [error] [client 38.114.104.53] Attempt to serve directory: /web/GreatWhite/
[Fri Dec 07 06:33:52 2007] [error] [client 66.249.72.169] File does not exist: /web/GreatWhite/robots.txt
[Fri Dec 07 06:33:52 2007] [error] [client 66.249.72.169] Attempt to serve directory: /web/GreatWhite/
[Fri Dec 07 07:45:10 2007] [error] [client 208.96.54.90] File does not exist: /web/GreatWhite/robots.txt
[Fri Dec 07 07:45:10 2007] [error] [client 208.96.54.90] Attempt to serve directory: /web/GreatWhite/
[Fri Dec 07 08:17:44 2007] [error] [client 91.64.109.178] File does not exist: /web/GreatWhite/robots.txt, refe
rer: [http://www.greatwhitedata.com/](http://www.greatwhitedata.com/)
[Fri Dec 07 10:15:16 2007] [error] [client 199.26.230.102] Attempt to serve directory: /web/GreatWhite/
[Fri Dec 07 10:57:26 2007] [error] [client 66.249.72.169] Attempt to serve directory: /web/GreatWhite/
[Fri Dec 07 13:20:02 2007] [error] [client 67.98.221.192] File does not exist: /web/GreatWhite/favicon.ico

---


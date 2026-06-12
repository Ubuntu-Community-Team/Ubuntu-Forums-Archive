---
title: "Reverse Proxy - images missing"
date: 2007-11-06
forum: General Help
---

### Post by awreneau on 2007-11-06
I've setup a reverseproxy using 6.06 and successfully proxied a few websites.  However I'm not pulling the images down each time.

A bit of info:

Ubuntu 6.06
Apache2
Modules enabled
[LIST]
[*]cgid.conf
[*]cgid.load
[*]proxy.conf
[*]proxy_html.load
[*]proxy.load
[*]ssl.conf
[*]ssl.load
[*]userdir.conf
[*]userdir.load
[/LIST]

I can pull from some sites all the images, but others i cannot.  I've pasted my virtual site below:

NamevirtualHost *:80

<VirtualHost *:80>

        # This secures the server from becoming a third party server
        ProxyRequests Off        

        DocumentRoot /var/www/

        ServerName test.local

        ProxyPass / [http://someplace.com](http://someplace.com)
        ProxyPassReverse / [http://someplace.com](http://someplace.com)
</VirtualHost>


It's a very simple host, and as I stated earlier it works for some sites not others.  Anybody have any ideas as to why?

Viewing the properties of the "missing image" the path is rewritten to test.local/path_to_image/imgage.gif.

---

### Post by awreneau on 2007-11-07
The key was a trailing slash on 

ProxyPass / [http://someplace.com](http://someplace.com)
ProxyPassReverse / [http://someplace.com](http://someplace.com)

should have been

ProxyPass / [http://someplace.com/](http://someplace.com/)
ProxyPassReverse / [http://someplace.com/](http://someplace.com/)


apache error log read as 

 proxy: DNS lookup failure for: [www.someplace.comwp-content](www.someplace.comwp-content) 

No slash between the .com and wp-content

.com/wp-content

---


---
title: "How do you confiure a URL for LAMP Installation with Coppermine Example?"
date: 2012-10-16
forum: General Help
---

### Post by Randy Schilling on 2012-10-16
I followed the instructions in the Linux Bible, 2007 Edition, 
to install LAMP, Apache2 + MySQL + PHP5.
I tested my installation with a file /var/www/info.php containing 
just one line: <?php phpinfo(); ?>.  Firefox responds with an
information page when you enter this url:  [http://localhost/info.php](http://localhost/info.php).

Why does Firefox responds to [http://localhost/info.php?](http://localhost/info.php?) 
I cannot find the directive ServerName localhost anywhere.

I get the following message: 
"Could not reliably determine the server's fully qualified domain name, 
    using 127.0.1.1 for ServerName..."
when I restart Apache2 with sudo /etc/init.d/apache2 restart?
Should I be concerned with this?

I came upon [https://help.ubuntu.com/11.04/serverguide/httpd.html](https://help.ubuntu.com/11.04/serverguide/httpd.html). 
This reference was most helpful but questions persist.
My main question concerns urls.  The Ubuntu reference contains this statement:

The ServerName directive is optional and specifies what FQDN your site should answer to. The default virtual host has no ServerName directive specified, so it will respond to all requests that do not match a ServerName directive in another virtual host. If you have just acquired the domain name ubunturocks.com and wish to host it on your Ubuntu server, the value of the ServerName directive in your virtual host configuration file should be ubunturocks.com. Add this directive to the new virtual host file you created earlier (/etc/apache2/sites-available/mynewsite). 

For now, I'm concerned with getting just one site up and running,
a simple Coppermine Photo Gallery for family photos.
Should I create a new virtual host for this site or should I set it up under the
system supplied default site?

I have to acquire a domain name.  Is this done through a company like GoDaddy.com?

Suppose I have acquired a domain name, say rjs.com (which is in use).  
Would I then add the directive: ServerName rjs.com 
to the file /etc/apache2/sites-available/mynewsite and then link this file 
/etc/apache2/sites-enabled/000-mynewsite? (This 000 syntax is used for
the default virtual host; /etc/apache2/sites-enabled/000-defualt is linked to
/etc/apache2/sites-available/default on my system's installation.)

/var/www/ is called my web directory and I plan to place the files of my
Coppermine installation in a subdirectory, say /var/www/galleria.
If this is correct then I would add also the appropriate  ServerAlias directive
and visitors would access my site using the url [http://www.rjs.com/galleria](http://www.rjs.com/galleria).
Is this correct?


My other option is to use the existing default virtual host.
Would I then add the directive: ServerName rjs.com to
my existing file /etc/apache2/sites-available/default?
Is this a viable option?  Which do you suggest?

I'm grateful to have this forum to resort to for help.  
Many thanks and kind regards - Randy

---


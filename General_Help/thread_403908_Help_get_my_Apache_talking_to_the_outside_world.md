---
title: "Help get my Apache talking to the outside world"
date: 2007-04-07
forum: General Help
---

### Post by hansoffate on 2007-04-07
Hi Guys,

   Right now my apache works in network, however, it doens't work out of network.  I have the box that it is running on set to DMZ (all ports available).  I also have the listen port set to 8081 (non standard so isp won't block).  I can't find where to bind my webaddress.  Right now when I restart my apache I get this.

```
hansoffate@mythlinux:/etc/apache2$ sudo /etc/init.d/apache2 restart
 * Forcing reload of web server (apache2)... are free software;
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName /usr/share/doc/*/copyright.
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerNameBSOLUTELY NO WARRANTY, to the extent permitted by
   ...done.law.
``` 

How do I set this to my registered dyndns address (hans.dnsdojo.com)?  Where do I edit this?  Also, if it isn't too hard, is there a way for it to ask for authentication before letting people in?  I am setting this up so I can connect to my mythweb away from home and schedule recordings.

This is what my file structure looks like.

```
hansoffate@mythlinux:/etc/apache2$ ls
apache2.conf  envvars     mods-available  ports.conf       sites-enabled
conf.d        httpd.conf  mods-enabled    sites-available
```

Thanks for the help
Hans

---

### Post by orlox on 2007-04-07
I don't know how to bind it to an adress, but I access my çcomputer with the ip adress:

[http://myip/](http://myip/)

wich shows what i have on the /var/www folder....

---

### Post by PurplePenguin on 2007-04-07
I can see your index at hans.dnsdojo.com:8081

If you're using Dyndns and you want to get rid of the 8081 (that is, make it so people don't need to add the port number onto the end), I believe you'll need to upgrade your Dyndns service.

EDIT: You're looking for the WebHop service from DynDns.  I just scanned the info, but it looks like it's free for up to five domains.  [Here's the FAQ.]("http://www.dyndns.com/services/webredirect/webhop/faq.html")

PS: You might want to put an index.html into your /var/www/ directory... as it is, your mythweb stuff is open to the world!  Cool stuff, I'm jealous. :)

---

### Post by llamakc on 2007-04-07
Right now, folks can delete your programs. You may wanna do something about that.

---

### Post by hansoffate on 2007-04-08
Yeah.  How do I lock it up?  Probably something with .htaccess right?  I'll try to do some reading to find out what I can do.  If I find anything, i'll post back.  If anyone knows what to do, can they post back?

Thank you for the help,
Hans

---


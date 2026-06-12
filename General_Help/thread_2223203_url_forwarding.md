---
title: "url forwarding"
date: 2014-05-09
forum: General Help
---

### Post by adamjedgar on 2014-05-09
Is there anything specific I need to do on my vps (self hosted on static ip) when i purchase a domain name and then, on the registrars nameserver admin panel, forward it to my ip?

I am having problems with an existing wordpress multi site after doing this. If I go back to using static ip address (on the vps clone backup) everything is running fine

---

### Post by TheFu on 2014-05-10
Exactly what have you done? 
What is the DNS settings for the domain? 
What, if any, virtualhosts are being attempted?  Are you trying to use name-based virtual hosts?

I don't know anything about WP setup, sorry, but I do KNOW how to run load balanced websites across many different machines in different parts of the world. We just aren't allowed to use php.

---

### Post by SeijiSensei on 2014-05-10
On the registrar's management page, create an "A" record for the hostname "www".  Then point that record at your server's IP address.  

On the server, if you're using Apache, you'll need to make sure that the [VirtualHost]("https://httpd.apache.org/docs/2.2/vhosts/name-based.html") for this application has a "ServerName" directive with [www.yourdomain.com](www.yourdomain.com) as the hostname.

Once this is set up properly, [www.yourdomain.com](www.yourdomain.com) will deliver the index page of the directory defined as the virtual host's DocumentRoot.  Usually that will be a "wordpress/" directory somewhere on the server.

---


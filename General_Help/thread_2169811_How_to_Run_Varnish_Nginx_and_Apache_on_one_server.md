---
title: "How to Run Varnish Nginx and Apache on one server?"
date: 2013-08-23
forum: General Help
---

### Post by heavymark on 2013-08-23
I have a single server running Ubuntu 13.04 with php-fpm.

I know how to setup the server to do CloudFlare > Varnish > Nginx > APC / WordPress. I also know how to do CloudFlare > Varnish > Nginx Reverse Proxy > Apache > APC / WordPress.

However, I do not know how to do both those setups on one server.

That is for example I'd like example1.com and example2.com to use (CloudFlare > Varnish > Nginx > APC / WordPress) but for example3.com and example4.com to use (CloudFlare > Varnish > Nginx Reverse Proxy > Apache > APC / WordPress).

Presumably Varnish would accept all traffic on port 80. And while I can give apache a custom port to listen to on localhost and give nginx a custom port to listen to on nginx, in Varnish how would I tell it to send some domains to nginx and some to apache?

If I can't figure it out, I suppose I could take Varnish out of the mix for either the Apache or the Nginx stack and buy an extra IP for the server. In that case I'd need to know if Varnish would be more beneficial with Apache or with Nginx.

---

### Post by Habitual on 2013-08-23
> **heavymark said:**
> Presumably Varnish would accept all traffic on port 80. And while I can give apache a custom port to listen to on localhost and give nginx a custom port to listen to on nginx, in Varnish how would I tell it to send some domains to nginx and some to apache?

If I can't figure it out, I suppose I could take Varnish out of the mix for either the Apache or the Nginx stack and buy an extra IP for the server. In that case I'd need to know if Varnish would be more beneficial with Apache or with Nginx.

There are only Two files you need to be concerned with:

Check out 
[COLOR=#ff0000]/etc/default/varnish[/COLOR] and it should have a -f option showing the vcl file being used.
Check out [COLOR=#ff0000]/etc/varnish/default.vcl[/COLOR] or whatever is there.
Here's a minimal working /etc/default/varnish file:
```
START=yes
NFILES=131072
MEMLOCK=82000
DAEMON_OPTS="-a :80 \ # yes, backslashes included!
             -T 0.0.0.0:6082 \ 
             -f /etc/varnish/default.vcl \ 
             -S /etc/varnish/secret \
             -s malloc,256m"
```
My suggestion is let Varnish have port :80 as defined in /etc/default/varnish
Use another port for the Apache host.
Use still another for nginx and configure them in **/etc/varnish/default.vcl **like so:
```

backend apache {
   .host = "domain.com";
   .port = "8080";
}
backend nginx {
   .host = "domain2.com";
   .port = "8088";
}

```
(This assumes your Virtualhosts are defined to listen on port:8080 for Apache/httpd)
Configure nginx  hosts for port:8088... I don't know squat about that webserver software, sorry.
save the file (you made a backup, *yes*? Good!)
```
service varnish restart
```

That should get you started and keep you from scratching your eyes out.
I was amazed at how simple Varnish was to put in front of something.
And I **never had to touch the apache** anything. Varnish just did it's thing.


```
netstat -pntl | grep -E "apache2|varnish"
``` or similar to see if the ports are in fact open.

Subscribed with interest...

Edit:
I would utilize what I call a "poor man's dns" by editing /etc/hosts with entries for 
<IP> <tab> domain.com
<IP> <tab> domain2.com
where IP is your local IP address.
Please don't do anything 'rash' like format and re-install please. I spent a fair amount of time on you already. :)

I saw but didn't answer your post at [AskUbuntu]("http://askubuntu.com/questions/336338/how-setup-varnish-nginx-and-apache-and-apc")

---


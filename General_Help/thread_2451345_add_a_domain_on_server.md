---
title: "add a domain on server"
date: 2020-10-02
forum: General Help
---

### Post by raduenea on 2020-10-02
Hello,

I am new in Ubuntu and I want to know how to add a domain to ubuntu server.

I have a domain registered on regisrar and i want hosting on my Ubuntu Server.
I add php, apache , mysql on server. Now what I need to do in order when i open my domain on browser to acces website from my server ?

Thanks

---

### Post by TheFu on 2020-10-02
"domain" is a generic term.  If you are just talking about DNS TLD, then there isn't something you do except in the web server settings.

For apache, the "servername" config setting controls this.  The hostname doesn't need to know anything about that name.
Suppose you have a nextcloud server and want to make it available over the internet without HTTPS (bad idea). Anyway, in the /etc/apache2/sites-enabled/ directory, you should make a file with the name of the full domain (for your sanity later).conf.  For example, nc.example.com.conf.  It can be named anything you want, provided it ends in .conf - that's an apache thing added in the last 8 yrs sometime.
Inside that file, would be the normal lines needed. My nextcloud.conf file is 40 lines.

```
<VirtualHost *:80>
     ServerAdmin [email]webmaster@example.com[/email]
     [COLOR="#FF0000"]ServerName nc.example.com[/COLOR]

.....
</VirtualHost>
```
That 1 line, is what makes this server answer to nc.example.com when traffic comes on port 80/tcp from anywhere.
The other 36 lines are left as an exercise and will be different from what I use.  I block most of the world from access to my nextcloud server and only enable specific internet subnets based on the public IPs when I'm traveling. I don't use HTTPS **on** the Apache machine. I handle that with an upstream server called a reverse proxy which terminates all SSL traffic for about 20-25 domains.

BTW, that machine is:
```
$ hostname
nextcloud
```
and the /etc/hosts looks like this:

```
$ more /etc/hosts
# Ansible managed

127.0.0.1 localhost
127.0.1.1 nextcloud.example.com nextcloud
```

External, public DNS knows how to find nc.example.com, but internal DNS also answers with the IP for my reverse proxy so HTTPS works for both external and internal clients. If you don't do SSL, then your internal DNS would point to nextcloud and internal LAN-only IPs.

Clear as mud?

---

### Post by raduenea on 2020-10-02
Ok, but how my server will know that accesing mydomain "webdev.co.ro" will access files from it (like /var/www/html/myfiles) ?

---

### Post by TheFu on 2020-10-02
/etc/apache2/sites-enabled/  config files is how apache does that.

```
DocumentRoot /var/www/html
   <Directory /var/www/html/>
....
   </Directory>
```

is part of the same file ... inside those 40 lines mentioned above.  There are lots and lots of examples online for this. Different versions of apache have slightly different requirements.  Using php changes things a little too. I don't do php stuff and haven't really touched apache since 2007-ish, so I just followed instructions posted online in a how-to guide for nextcloud.  We switched to nginx a long time ago.

[https://httpd.apache.org/docs/](https://httpd.apache.org/docs/) is the official apache documentation.
You can find ubuntu versions at help.ubuntu.com, but apache is apache is apache and works the same across all distros. I'd be surprised if a distro didn't work the way that the official apache docs say. I've not seen that.

---

### Post by TheFu on 2020-10-02
webdev.co.ro isn't resolving here, BTW.  

[https://blog.jdpfu.com/2009/08/18/internet-hosting-setup](https://blog.jdpfu.com/2009/08/18/internet-hosting-setup) explains how  the registrar, DNS, and hosting are connected. You **must** have all three.  They can be from different providers.  I have them split with 3 different companies and host many domains on my business servers under my physical control.  This is getting harder for home users as ISPs block more and more ports inbound to residential addresses.

---

### Post by HermanAB on 2020-10-03
Typically, you need a business account with your ISP, as they will likely block incoming http requests to your IP address if it is a Home account.

---

### Post by dragonfly41 on 2020-10-03
By coincidence I have just installed [ngrok]("https://ngrok.com/") to my home based development PC to demonstrate some workflows.
That works nicely. I just have a normal account and I can change the port.

---

### Post by TheFu on 2020-10-03
> **dragonfly41 said:**
> By coincidence I have just installed [ngrok]("https://ngrok.com/") to my home based development PC to demonstrate some workflows.
That works nicely. I just have a normal account and I can change the port.

Is setting up a reverse proxy, managed by someone else, into a home LAN, something desirable?

---

### Post by dragonfly41 on 2020-10-03
The idea is to run demos (briefly) on a dedicated external dockable SSD with just slim Ubuntu installed.

Alternatively launch Heroku free dyno.

---


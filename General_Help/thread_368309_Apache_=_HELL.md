---
title: "Apache = HELL"
date: 2007-02-23
forum: General Help
---

### Post by nick.inspiron6400 on 2007-02-23
I have been trying to get Apache to work for the past week, and i am now fed up. I switched to Linux as i need a web server.

Hardware:

Dell Inspiron 6400 Ubuntu 6.10 (the server)
AMD Duron 750 desktop (SUSE 10.1)
D-Link Di-524 Cable/DSL router.

I have tried everything, i have set port 80 to forward to MY IP address. I have re-installed Apache 2, NOTHING.

What can i do?

Thanks,

Nick.

---

### Post by kidders on 2007-02-23
Hi there,

What do you mean by "Nothing" exactly? Could you describe your network configuration, and what you'd like to achieve? Perhaps you could post some config file or system log excerpts that might help identify your problem.

---

### Post by nick.inspiron6400 on 2007-02-23
I registered a public DNS with dynDNS. And i was expecting to be able to view these files on a remote location e.g work desktop.

I can not get to see my web server on a remote location. 

What do you need me to post?

Thanks,

Nick.

EDIT

I have Virgin Media, (ntl) broadband.

---

### Post by kidders on 2007-02-23
Hey again,

That leaves an awful lot of places to look for problems! :-( I suppose, if we think about things from the outside in, a few issues worth checking would be...

[LIST]
[*]Does your ISP permit incoming traffic on port 80?
[*]Is your dynamic DNS service pointing your domain name at the right IP?
[*]Is anything between your web server and your ISP running a firewall?
[*]Is everything between your web server and your ISP configured to forward incoming traffic to the right place?
[*]Is your web server running?
[*]Is the server listening on an externally accessible interface?
[/LIST]

Hopefully we can identify what your problem is from how far down the list you can get.

**Edit:** I'm still not completely sure what the actual problem is though... When you say nothing happens, what do you mean? What errors do you receive client-side?

---

### Post by nick.inspiron6400 on 2007-02-23
I can view the web server on my desktop (same network, running Windows) but i cant see anything on a different computer.

1. I think Virgin blocks port 80
2. The DNS is pointing my remote IP address to the domain
3. No firewall on the laptop, ZoneAlarm on the desktop.

The problem is i cant see my web server on a different computer.

Nick

---

### Post by kidders on 2007-02-23
> **nick.inspiron6400 said:**
> As normal the problem is in Linux.:confused: If your ISP is blocking incoming HTTP traffic, your web server won't be externally accessible on port 80, no matter which operating system you run it off.

Have you tried using a different port?

---

### Post by nick.inspiron6400 on 2007-02-23
What other ports could i use???

Nick.

---

### Post by kidders on 2007-02-23
That depends on what your ISP will allow. Anything relatively high should be acceptable, I'd say.

---

### Post by nick.inspiron6400 on 2007-02-23
Okay what about port 120?

Nick,

---

### Post by kidders on 2007-02-23
Anything in the region 6000-7000 should be okay. Technically, I suppose most common reserved port numbers are below 1024 though.

**Edit:** I tried to persuade Virgin's website to tell me what your traffic restrictions might be ... their customer support pages don't reveal much!

---

### Post by nick.inspiron6400 on 2007-02-23
Okay i will try 6500.

Thanks for all your help.

---

### Post by nick.inspiron6400 on 2007-02-23
How do i change it? 

I created HTTP1 put my IP address and set it to forward to port 6500. Is that correct? Then when i go to [www.nickcastilla.dnsdojo.net](www.nickcastilla.dnsdojo.net), it tells me it is on port 80???

Help!

Nick.

---

### Post by laitem on 2007-02-23
> **nick.inspiron6400 said:**
> How do i change it? 

I created HTTP1 put my IP address and set it to forward to port 6500. Is that correct? Then when i go to [www.nickcastilla.dnsdojo.net](www.nickcastilla.dnsdojo.net), it tells me it is on port 80???

Help!

Nick.
No,

You will need to forward all incoming requests on port 6500 to your internal ip on port 80. So you don't have to change anything in your webserver configuration. Only in your router settings.

The only problem is that people who want to visit your webserver will need to access it trough [http://www.nickcastilla.dnsdojo.net:6500](http://www.nickcastilla.dnsdojo.net:6500).

---

### Post by reclusivemonkey on 2007-02-23
I'm not sure how you have set this up, but I use DynDNS myself and I have to set this up in the router.

See my webpage in my signature.

The problem here is most certainly *not* Linux; I wouldn't advise you bad-mouthing Linux without knowing specifically what the problem is or you may deter people from helping you.

---

### Post by nick.inspiron6400 on 2007-02-23
I will try that address. Also i think it has something to do with my ISP.

---

### Post by punx45 on 2007-02-23
in /etc/apache2/sites-available/sitename
'NameVirtualHost' needs to match the domain name right?

---

### Post by nick.inspiron6400 on 2007-02-24
Punx45,

in /etc/apache2/sites-available/sitename
'NameVirtualHost' needs to match the domain name right?

How do i do that?

Thanks,

Nicolas

---

### Post by punx45 on 2007-02-26
open the file with any text editor

you might want to check out the[ apache docs here.]("http://httpd.apache.org/")

---

### Post by stokedfish on 2007-02-26
Well, it's not that hard, really...

apache.conf

```
ServerName localhost

NameVirtualHost *:80

<VirtualHost *:80>
    ServerName mydyndns.dyndns.org
    ServerAlias mydyndns.dyndns.org
    DocumentRoot /var/www/yourwebsitedirectory
    HostnameLookups On
    UseCanonicalName On
</VirtualHost>
```
Now forward port 80 and that's it.

And don't forget to /etc/init.d/apache restart!  ;)

---

### Post by stokedfish on 2007-02-26
Oh, and of course you have to enable the loopback interface of your router if you want to see your website on the net AT HOME (which doesn't really make sense anyway) - I just open mine with [http://192.168.1.3/](http://192.168.1.3/) instead of my dyndns when I'm in my flat...

---

### Post by stokedfish on 2007-02-28
Sooo...did it work?

---


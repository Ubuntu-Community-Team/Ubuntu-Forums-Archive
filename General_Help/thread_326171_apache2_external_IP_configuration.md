---
title: "apache2 external IP configuration?"
date: 2006-12-27
forum: General Help
---

### Post by a.d.gardiner on 2006-12-27
Hey all,

I have a couple of hopefully simple questions regarding my apache2 configuration. Please bare with me, I've been through the manual, but I'm new and still a little confused.

At present I am running xubuntu 6.10 locally on my network. I have apache2 up and running with php5 & mysql. I got a phpBB running on there too.

The machine has a static IP address of 192.168.1.39 and I can connect to web pages hosted in /var/www/ locally by typing this into a browser on any machine in the network. I can also get to them from outside because I have port forwarded my router's static IP 81.149.22.40 to 192.168.1.39

What I want to do now is point my apache2 at my broadbands static IP 81.149.22.40, and modify my hosts file to get all internal clients to just route directy to my box. I don't have a domain name either, I'm just using the IP at present. I believe the example code below needs dropping in somewhere, but I'm confused which files to edit and where?

can anybody help? 8) 

```

<VirtualHost 10.1.2.3>
ServerAdmin webmaster@host.foo.com
DocumentRoot /www/docs/host.foo.com
ServerName host.foo.com
ErrorLog logs/host.foo.com-error_log
TransferLog logs/host.foo.com-access_log
</VirtualHost>

```

---

### Post by evilghost on 2006-12-27
You're going about this the wrong way.  I doubt your router will port-forward 80 on the internal interface to your 192.168.1.39 address.

You can:

1) Install BIND9 and create a zone for your domain (if you're going to register one) to use the local 192.168.1.39 address

2) Modify the HOSTS file on each machine to point the domain name to the local address of 192.168.1.39

I opted for method #2.  Most DSL/Cable routers will only port-forward traffic originating from the external interface.

---

### Post by a.d.gardiner on 2006-12-27
Okay, cool. Sorry if I seem abit vague. I don't think I explained myself too good :)

I think what I meant is external users can see the site at 81.149.22.40 because the router forwards external traffic to the internal 192.168.1.39 address. (pretty much as you said in number two).

I wanted to make the apache listen on 81.149.22.40 but I don't know what files to modify?

Not sure if im making sense here. lol

---

### Post by Swab on 2006-12-27
> **a.d.gardiner said:**
> Okay, cool. Sorry if I seem abit vague. I don't think I explained myself too good :)

I think what I meant is external users can see the site at 81.149.22.40 because the router forwards external traffic to the internal 192.168.1.39 address. (pretty much as you said in number two).

I wanted to make the apache listen on 81.149.22.40 but I don't know what files to modify?

Not sure if im making sense here. lol

Apache can't listen on an IP address other that its own.  It only really listens on the port number it has been configured with.  You have your router setup to forward to the apache server, so what is the problem?

---

### Post by a.d.gardiner on 2006-12-27
Good point. I forgot to mention the other bit of the problem.

Access from inside the network is fine. Users simply type 192.168.1.39 and you can login to phpBB no problem.

Access externally across the internet is a different matter. Users gaining access with 81.149.22.40 are port forwarded to 192.168.1.39 and get the page, but they can't login to the board because the login cookie located inside the network (or so i had it explained to me on the phpBB community...

This is what somebody else wrote about the problem..

> 
The problem is that you are accessing the board from inside using an internal address, so that is what is in the sserver and cookie domain fields.

When you try to access it from outside, it is using those same internal names, which are of course not accessible from the outside.


Hence me posting about a ton of stuff im struggling to understand :) (everybodies help is really nice to have btw, many thanks)

---

### Post by evilghost on 2006-12-27
If you register a domain name you'll likely resolve these issues since the cookie domain will be bound to a FQDN instead of an IP Address which is different for internal/external users...

---

### Post by a.d.gardiner on 2006-12-27
The cookie domain is indeed set to 192.168.1.39 :confused:

---

### Post by a.d.gardiner on 2006-12-27
Just any old cheap domain from lycos or somewhere? £1.99 job?

Sorry if I seem a little ignorant, I'm kinda new.

---

### Post by evilghost on 2006-12-27
Any domain would work really.  I use [http://www.simpleurl.com](http://www.simpleurl.com) since they're only $12 USD/year for a .com/.net/.org TLD.  They also provide free DNS hosting as well.

Other than that you may want to look at another product instead of phpBB, I'm not sure if vbulletin needs a cookie domain, AFAIK it uses sessions.

---

### Post by a.d.gardiner on 2006-12-27
Your a gent, thanks for the information. Will have a crack with that.

---

### Post by evilghost on 2006-12-27
> **a.d.gardiner said:**
> Your a gent, thanks for the information. Will have a crack with that.

Thanks, always glad to help.  Since you're running PHP5 with phpBB (fairly bleak/insecure record) check out:

[http://advosys.ca/viewpoints/2006/11/hardening-php-servers-with-suhosin/](http://advosys.ca/viewpoints/2006/11/hardening-php-servers-with-suhosin/)

---


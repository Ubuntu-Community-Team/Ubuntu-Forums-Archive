---
title: "changing website names in ubuntu"
date: 2008-05-15
forum: General Help
---

### Post by mebuntu on 2008-05-15
****Hi, am running a website on ubuntu server 7.10 with .co.uk
address. have been asked to change this to a .com address. 

would appreciate any advice/assistance in acheiving this ?

thanks

---

### Post by rubicon on 2008-05-15
Better ask people who have sold you that domain name

---

### Post by mebuntu on 2008-05-15
i'm a bit confused as whether i need to change the host name, domain name and edit the httpd/conf file.

---

### Post by talz13 on 2008-05-15
> **mebuntu said:**
> i'm a bit confused as whether i need to change the host name, domain name and edit the httpd/conf file.

You need to change the domain name by buying the .com address first.

---

### Post by fyo on 2008-05-15
OK, this sounds very strange on the face of it... thinking about it, though, I think I understand what you mean:

You have a webserver running a website which can be accessed at the .co.uk domain. This needs to be changed to a different domain (which just happens to be a .com domain, but that's irrelevant here).

(I'm assuming ownership over the domain names is not an issue...)

You need to make a few changes in order for everything to work properly:

-> The new domain name needs to point at the IP address of your server. (name server)

-> Your server needs to be aware of the name. Exactly how this is achieved depends on your server setup (multiple virtual hosts? which web server? etc)

---

### Post by mebuntu on 2008-05-15
apologies for not giving a full explanation but FYO is correct. 

we have a single webserver running the .co.uk website. we also own a .com address. (no virtual hosts)

the powers that be want users to access our website via the .com domain. so we need make a name change on the webserver so it resolves to its IP address. 

just wanted a few pointers on how to achieve this.

---

### Post by fyo on 2008-05-15
> **mebuntu said:**
> the powers that be want users to access our website via the .com domain. so we need make a name change on the webserver so it resolves to its IP address. 

just wanted a few pointers on how to achieve this.

As I said, the change needs to be made in two places:

1) The name server.
2) The web server.

Usually, small companies don't own either, instead relying on hosting.

You say you have the web server, but I don't know if you also have a name server.

If you want to find out what name servers you are using, you could just do a "whois" on your domain. There are plenty of free services that provide this type of service or it could be through your ISP... or even a different server in your company.

As for how to tell apache what your domain name is... well, that's when you edit httpd.conf.

---


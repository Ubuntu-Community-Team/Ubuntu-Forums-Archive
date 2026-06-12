---
title: "Setting up a web server/host"
date: 2007-01-27
forum: General Help
---

### Post by v8YKxgHe on 2007-01-27
Hey,

I've just brought a Shuttle XPC from eBay and would like to turn it into a small webserver/host. Now, I know how to install Apache, PHP and MySQL to get a working LAMP server but how would I go about setting it up as like a web host, with quota and a web control panel etc? So I can just make a new user which they can then FTP into and upload files etc to make a website. 

I probably wont be hosting any websites on it, I just wanna learn how it's done etc. What's needed to do this?

---

### Post by pod25 on 2007-01-27
You need ISPconfig installed.
I have it installed on my server comp, it works like a charm and acts just like the pro's

---

### Post by v8YKxgHe on 2007-01-27
Yeah I've heard about ISPConfig, but it needs Quota installed. I found this guide, [The Perfect Setup]("http://www.howtoforge.com/perfect_setup_ubuntu_6.10") but when I come install Quota I get errors like "Do not have permission" when I come to do:

```
quotacheck -avugm
```

even though I am using sudo as well.

Another question, why do I need to install a DNS Server (BIND)? What exactly does it do?

---

### Post by Duffy on 2007-01-27
If you want something easier to set-up, I would like to suggest you look at Sambar Server - sambar.com

Graphic web interface and free for basic - $99 for full which includes web, mail, IM, FTP, Blogging, etc.

Duffy

---

### Post by pod25 on 2007-01-27
> **AlexC_ said:**
> Yeah I've heard about ISPConfig, but it needs Quota installed. I found this guide, [The Perfect Setup]("http://www.howtoforge.com/perfect_setup_ubuntu_6.10") but when I come install Quota I get errors like "Do not have permission" when I come to do:

```
quotacheck -avugm
```

even though I am using sudo as well.

Another question, why do I need to install a DNS Server (BIND)? What exactly does it do?

Are you using SUDO ? ..  Oops, I should of continued reading before I hit REPLY.

And I can not fully explain how DNS works, but it is needed to run a proper web hosting server, 
I think at this point you might want to stop and do some more reading before going any further.

---

### Post by v8YKxgHe on 2007-01-31
weird, I never got any email notification back!

pod25, I know how a DNS works - it's like a telephone directory that converts say [www.google.co.uk](www.google.co.uk) to an IP address of the physical machine.

Do I have to buy another domain name in order to set up a real, test server? Because in the examples/guides I see the DNS set to like "server1.example.com" - well if I don't own a domain name which I can use for this test server, how else can I create the "server1.example.com" ?

---

### Post by pod25 on 2007-02-01
> **AlexC_ said:**
> 
Do I have to buy another domain name in order to set up a real, test server? Because in the examples/guides I see the DNS set to like "server1.example.com" - well if I don't own a domain name which I can use for this test server, how else can I create the "server1.example.com" ?

No.
Just use localhost or your comps name minus the .com

---


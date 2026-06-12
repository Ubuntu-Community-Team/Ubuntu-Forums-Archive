---
title: "Accessing my server via public IP"
date: 2006-11-19
forum: General Help
---

### Post by themikeflynn on 2006-11-19
Today I setup my first home server (Ubuntu 6.10 Server). Everything went well, and I suppose I'm just finishing up now. Last thing I need to know is how I can access it outside of my house. I can get to it via its local IP (192.168.1.180) but I'm not sure how to access it from the public one. 

Do I need to do something with DNS? Not really sure what to do next.

---

### Post by dcstar on 2006-11-20
> **themikeflynn said:**
> Today I setup my first home server (Ubuntu 6.10 Server). Everything went well, and I suppose I'm just finishing up now. Last thing I need to know is how I can access it outside of my house. I can get to it via its local IP (192.168.1.180) but I'm not sure how to access it from the public one. 

Do I need to do something with DNS? Not really sure what to do next.

No, how you do it depends on your Internet setup.

If you use NAT (like most of us...), do a forum search of the topic or an Internet search on NAT forwarding.

Beware that there are serious security risks involved in providing any sort of access from the Internet.

---

### Post by themikeflynn on 2006-11-20
I forwarded port 80 on the server and now I'm able to access it easily. 

What kind of security risks should I worry about?

---

### Post by dcstar on 2006-11-20
> **themikeflynn said:**
> I forwarded port 80 on the server and now I'm able to access it easily. 

What kind of security risks should I worry about?

Making sure that the software now accessible via port 80 is kept up to date so any vulnerabilities are not exploited!

---

### Post by fragos on 2006-11-20
Check out changip.com to see how to set up a dynamic dns.  Chances are you don't have a static IP.  Changeip will help set up a dynamic IP and a domain name.  When you boot up and your ISP assigns you an IP address and a startup routine in your box will register that IP with the dynamic DSN providers.  There's a little more to it depending on what you use to connect to the Internet but this will give you a domain name to be found by DNS servers.

---

### Post by koenn on 2006-11-20
> **themikeflynn said:**
> I forwarded port 80 on the server and now I'm able to access it easily. 

What kind of security risks should I worry about?

As you can easily access the server on port 80, so can anybody else on the internet. 
That's probably the point (since it is a webserver - judging from the port)
The pont to worry about is : any flaw in the webserver (a bug, a sloppy configuration, a small mistake in any server-side scripts for your web server, ...) may give others more that just the opportunity to view web pages, eg access to your filesystem, shell, ... 

Make sure you read the documentation of your web server (Apache ?), especially the chapters about securing it.

---


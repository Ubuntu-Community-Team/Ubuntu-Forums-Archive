---
title: "Domain Problem"
date: 2008-01-13
forum: General Help
---

### Post by .Shaun on 2008-01-13
Hello. I host my own domain on my Ubuntu 7.10 server. But for some reason, you can only access my site from [www.example.com](www.example.com), and not example.com. Why is this? 

~Shaun

---

### Post by TwoWordz on 2008-01-13
Do you mean your webserver?

On your registrar, you should see [www.example.com](www.example.com) pointing to your server's IP address. Look around there should also be a *.example.com, this will send all hosts with now A record to your website. 

Im not sure but if you use apache2 the right way, you should also have the line 

Serveralias example.com

In your site-enabled configuration.

Hope I got your problem right.

TW

---


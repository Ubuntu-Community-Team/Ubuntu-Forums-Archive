---
title: "Is nginx a legitimate program?"
date: 2014-12-29
forum: General Help
---

### Post by Ralph L on 2014-12-29
I just got this message on Firefox when I tried to access a web site:
```
Welcome to nginx!

If you see this page, the nginx web server is successfully installed and working. Further configuration is required.

For online documentation and support please refer to nginx.org.
Commercial support is available at nginx.com.

Thank you for using nginx
```
I don't know what is nginx nor how it got installed.  Is it something I should be concerned about, or is it a legitimate program that I should configure as it requests?  I am running Ubuntu 12.04 and Firefox 27.0.1.  I know Firefox should be updated and I will do so as soon as I get a chance.

---

### Post by lisati on 2014-12-29
It's a valid program, and is used as a web server. The web page you saw appears to be the default home page, i.e. the admin of the website you're visiting might not have put any content on the website yet.

---

### Post by deadflowr on 2014-12-29
nginx is an alternative web server to the more well-known Apache.
Totally legit.

But as to why you have that message, or how it seems to have been installed, I do not know.
Have you installed anything new recently?

---

### Post by buzzingrobot on 2014-12-29
> **Ralph L said:**
> I just got this message on Firefox when I tried to access a web site:
```
Welcome to nginx!

If you see this page, the nginx web server is successfully installed and working. Further configuration is required.

For online documentation and support please refer to nginx.org.
Commercial support is available at nginx.com.

Thank you for using nginx
```


It's not a message from anything executed on your system.  It's the default web page returned by nginx after it's been installed, documenting that it works.  Either that site is misconfigured, or there's no other content on it.

---

### Post by Lars Noodén on 2014-12-29
If you look at [Netcraft's December 2014 Web Server Survey](http://news.netcraft.com/archives/2014/12/18/december-2014-web-server-survey.html) in the section "Market share of the top million busiest sites" it is number two, after Apache.  Same for other measures like "active sites"

---

### Post by Ralph L on 2014-12-29
Thank you for your responses.  They were very helpful.

---


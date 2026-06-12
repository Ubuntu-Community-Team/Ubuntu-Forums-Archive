---
title: "Friendly URLs for web apps on Ubuntu Servers"
date: 2015-07-09
forum: General Help
---

### Post by andrew245 on 2015-07-09
I've been working on setting up a small home network consisting of a WebServer (Ubuntu Server 15.04 on a MacMini) and a media server (Ubuntu Server 15.04) with a few web based apps like Webmin and Transmission. The apps are all working well but I was wondering if it's possible to setup URL redirects (or using other technology if redirects aren't the answer) that would map a friendly URL to the apps.

Just so things are easy let's assume:

[LIST]
[*]I have setup a domain "domain.com" that points to my network
[*]The web server's IP is 192.168.0.100
[*]The media server's IP is 192.168.0.101
[/LIST]

My end goal is to have it so that the URL "media.domain.com/webmin" redirects to the media server's instance of Webmin (192.168.0.101:10000) and "web.domain.com/webmin" redirects to the web server's Webmin instance.

My guess would be I need to use Apache with proxy/redirect and rewrite rules but I'm not sure exactly how to achieve this. Any help or suggestions would be greatly appreciated.

---

### Post by TheFu on 2015-07-09
Support for 15.04 ends in January. If I were going to the effort to setup servers, I'd use an LTS - 14.04. 6-9months of support just isn't worth it, IMHO.

To redirect like you want, just use a reverse proxy.  apache, nginx, pound, htproxy and others exist.  I use nginx and find it easiest to setup.  Used pound for about 5 yrs before, but needed some features that only nginx could provide.  Apache just as a reverse proxy is kinda heavy.
[https://help.ubuntu.com/community/Pound](https://help.ubuntu.com/community/Pound) is really easy to setup.

webmin isn't well supported on Ubuntu. Cannot recommend it. 

Oh - and "web/domain.com/webmin" isn't possible. I suspect it is a typo.

---

### Post by andrew245 on 2015-07-09
> **TheFu said:**
> Support for 15.04 ends in January. If I were going to the effort to setup servers, I'd use an LTS - 14.04. 6-9months of support just isn't worth it, IMHO.

Didn't know that, thanks! I only used 15.04 because 14.04 seems to have issues installing on something without an optical drive. I'll look into 14.04 again.

> **TheFu said:**
> To redirect like you want, just use a reverse proxy.  apache, nginx, pound, htproxy and others exist.  I use nginx and find it easiest to setup.  Used pound for about 5 yrs before, but needed some features that only nginx could provide.  Apache just as a reverse proxy is kinda heavy.
[https://help.ubuntu.com/community/Pound](https://help.ubuntu.com/community/Pound) is really easy to setup.

Awesome, I'll take a look at those. I appreciate the information (bit of a noob so I don't know many of the alternatives in regards to using apache)

> **TheFu said:**
> webmin isn't well supported on Ubuntu. Cannot recommend it.

What would you suggest? Again, bit of a noob and not familiar with a lot of tools out there.

> **TheFu said:**
> Oh - and "web/domain.com/webmin" isn't possible. I suspect it is a typo.
Should have proofread....
[IMG]http://i.lvme.me/g4q9a75.jpg[/IMG]

---

### Post by TheFu on 2015-07-09
So if you are just starting out, know that there aren't any short-cuts.  You need to learn the shell, period. It will take time. Don't use GUI tools until you've mastered the cli version. That goes for webmin and phpmyadmin and cpanel and ... 
Become a power-user before a sysadmin.  GUI tools usually do not provide the full power that the cli versions have. Some only have 15% of the capabilities. Most introduce security issues too.

[http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) - there is a free PDF file there that I think you will like.
[http://blog.jdpfu.com/2010/10/29/linux-training-and-documentation-resources](http://blog.jdpfu.com/2010/10/29/linux-training-and-documentation-resources)

---


---
title: "Firefox will not run CF admin offline"
date: 2008-06-26
forum: General Help
---

### Post by Kelrizzo on 2008-06-26
Well, I wasn't sure where else to post this, so I'll stick it here and ask forgiveness.

I'm running the latest Unbuntu build, Firefox 3.0 on an HP Pavillion with wireless internet capabilities.

I've installed Coldfusion Developer edition, mySQL, and Eclipse.

My problem is that I can't access the coldfusion administrator when I have no internet connection.

I use path [http://localhost:8500/CFIDE/administrator](http://localhost:8500/CFIDE/administrator) and I will also substitute 127.0.0.1 in for local host.

I've verified that coldfusion sever is indeed running.  I've tried it with the wifi disabled, and ensured that Firefox does indeed show that I'm working offline (File<work offlie)

Here's the kicker: when I'm connected to the internet, I can access CF admin just fine.

I've pretty much exhausted anything I can think of.  Any thoughts? :)

---

### Post by Kelrizzo on 2008-06-27
Blah, I'm a moron, figured it out :p

It defaults to use offline.  Since CF is your webserver, it wouldn't do to work offline.

---


---
title: "webserver setup.."
date: 2005-09-12
forum: General Help
---

### Post by billy314159 on 2005-09-12
Im behind a router, dynamic ip (it changes) and I want the website to be viewable from any computer, specifically outside the network.  I would like detailed instructions on how to configure apache2 so that I can use a domain name, not using virtual server on my router.

If anyone can help, id be really happy!!!

---

### Post by KingBahamut on 2005-09-12
[QUOTE=billy314159]Im behind a router, dynamic ip (it changes) and I want the website to be viewable from any computer, specifically outside the network.  I would like detailed instructions on how to configure apache2 so that I can use a domain name, not using virtual server on my router.

If anyone can help, id be really happy!!![/QUOTE]
 apt-get install apache2 

read 

[http://httpd.apache.org/docs/2.0/](http://httpd.apache.org/docs/2.0/)

Youll probably want to use something to the affect of Name Based Virtual hosting within Apache( Rather than IP based because you only have 1 ip , or so Im assuming) , there are extensive docs in there about that specifically. 

There really isnt a quick way to do this, so if thats what your looking for, your not going to find that there, get ready to roll your sleves up and sweat the brow a little.

---

### Post by billy314159 on 2005-09-12
cool, thanks

---


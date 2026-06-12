---
title: "Installing Torrentflux on Ubuntu"
date: 2008-06-19
forum: General Help
---

### Post by gamingneeds on 2008-06-19
Hey guys,

I need to install Torrentflux onto my new ubuntu 7.04 Feisty server.

I have 2 IP's currently, and want one install on each. Does anyone know how I can do this?

Thanks.

---

### Post by justleen on 2008-06-19
simply extract torrentflux in the www dir of your webserver (or, in the case of two ip's in the correct virtual hosts www folder)


after that run the mysql import to generate the DB..

---

### Post by gamingneeds on 2008-06-19
I don't know how to setup the Virtual Hosts. :(

And what is MySQL Import?

---

### Post by depele on 2008-06-19
the mysql import is a script which generates the database which is needed for torrentflux.

For the 2 ip's I think you just have to edit the conf file.

I believe you can also apt-get torrentflux.

```
sudo apt-get install torrentflux
```

this is a good howto to.

[http://my.opera.com/albuemil/blog/2007/01/09/server-install-torrentflux](http://my.opera.com/albuemil/blog/2007/01/09/server-install-torrentflux)

[http://ubuntuforums.org/showthread.php?t=268985](http://ubuntuforums.org/showthread.php?t=268985)


==> and many more to find on google.com

---


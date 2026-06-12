---
title: "Which packages exactly for Apache2+php4+mysql"
date: 2005-08-02
forum: General Help
---

### Post by eeried on 2005-08-02
Hello,

I've read quite a few thread on the subject of one or other of these apps but I need the three to work together. I don't use my box as a web server just to build a website locally, using a CMS that requires the three apps to work together.

Okay, Apache2 is easy I've got it : 3 packages are installed after you type apt-get install apache2

Now mysql offers quite a lot of packages. Can someone confirm I only need mysql-server -- or is it mysql-server-4.1? (no -client, no -common?)

- One thread recommends llibapache2-mod-php4 while the Unofficial Ubuntu Guide recommends ibapache2-mod-auth-mysql. The first one would seem more appropriate. can someone confirm this?

- php4-mysql is required too.

- php4 is required too of course

- phpmyadmin is quite useful too.

All very confusing!

---

### Post by revs on 2005-08-02
[QUOTE=eeried]Hello,

I've read quite a few thread on the subject of one or other of these apps but I need the three to work together. I don't use my box as a web server just to build a website locally, using a CMS that requires the three apps to work together.

Okay, Apache2 is easy I've got it : 3 packages are installed after you type apt-get install apache2

Now mysql offers quite a lot of packages. Can someone confirm I only need mysql-server -- or is it mysql-server-4.1? (no -client, no -common?)

- One thread recommends llibapache2-mod-php4 while the Unofficial Ubuntu Guide recommends ibapache2-mod-auth-mysql. The first one would seem more appropriate. can someone confirm this?

- php4-mysql is required too.

- php4 is required too of course

- phpmyadmin is quite useful too.

All very confusing![/QUOTE]
 [http://ubuntuguide.org/#apachehttpserver](http://ubuntuguide.org/#apachehttpserver)

read the FAQ... read the FAQ again, then post :D

---

### Post by eeried on 2005-08-02
Sorry, revs, I forgot to clearly state I first read the unofficial guide but it sometimes clashes with what I've read on this forum, namely concerning the libapache* package.

 :-?

---

### Post by eeried on 2005-08-02
Okay, what I did was reinstall ubuntu because I had too many problems with dependcies and locales impossibilities.

Tthis reinstalltion proved again how excellent Partman is, and ubuntu does a great job indeed: I was able to reinstall without destroying /home or /opt. 

What I did then was to follow the wiki on apache+php+Mysql blindly, like a good ubuntu girl, after adding some repositories as the ubuntu unoffcial guide says. [https://wiki.ubuntu.com/ApachePHPMySQL?actihttps://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28apache%29on=show](https://wiki.ubuntu.com/ApachePHPMySQL?actihttps://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28apache%29on=show)

I've learnt my lesson: with ubuntu follow ubuntu without asking questions, and it'll be all right unless you're a real exper. Well, it takes some getting used to, that's all.

So I would  recommend the wiki page rather than the Ubuntu unofficial guide. Don't ask yourself any question. Do as you're told and you'll be fine. All my silly questions were answered just by typing what I was told to and gaping at the screen output.

All's well that ends well. Works like a charm...

Many thanks, Ubuntu team  ;-)

---


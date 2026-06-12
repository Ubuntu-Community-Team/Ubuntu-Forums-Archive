---
title: "ubuntu for servers, which?"
date: 2006-07-27
forum: General Help
---

### Post by Dan C on 2006-07-27
Hey,

I've got an ubuntu ( desktop, x86 ) CD I ordered an age ago, it's a couple of versions old. I'm looking to set up a local development and file server, and was wondering...

Is there any benefit to using the ubuntu 'server version' you offer now, over installing from the CD I have, with the 'server' flag set and then upgrading to the latest version with apt-get?  I'll be installing PHP, MySQL, PGSQL, etc. from source anyway.  Would I be losing out in any way at all by **not **using the server version?

Thanks!

- Dan

---

### Post by GuitarHero on 2006-07-27
If you install an older version of the server install and upgrade it will be the same.

---

### Post by az on 2006-07-27
> **Dan C said:**
> Is there any benefit to using the ubuntu 'server version' you offer now, over installing from the CD I have, with the 'server' flag set and then upgrading to the latest version with apt-get?  

How hard is it for you to download and brun the server iso?  It would be simpler to just use that.  You can dist-upgrade from one release to the next, but if your cd is old, that would mean dist-upgrading from, say, Warty to Hoary, then to Breezy and then to Dapper.  That's the reccommended way to do with using the desktop, I'm not sure if the same holds true for the base system.

If you have some time on your hands, you can find out.

Also, don't foget to istall the server kernel to get optimised performance.  You won't get that from earlier versions of Ubuntu (or the alternate cd or desktop cd for the current version)

sudo apt-get install linux-server


> **Dan C said:**
> 
I'll be installing PHP, MySQL, PGSQL, etc. from source anyway.  Would I be losing out in any way at all by **not **using the server version?

Why install PHP and mysql from source?

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

will install php5, mysql5.0 and apache2.

---


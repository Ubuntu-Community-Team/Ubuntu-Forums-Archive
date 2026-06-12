---
title: "Please help me get TorrentFlux working!"
date: 2008-01-17
forum: General Help
---

### Post by 449 on 2008-01-17
I've been trying for a while now to get Torrentflux working in Ubuntu 7.10. I've tried using the guide here ,but with no success. So let's just say I have everything installed, how would I run TorrentFlux? 

Thanks.

---

### Post by gvartser on 2008-01-18
Prerequsite's:
* MYSQL
* PHP
* APACHE2

1) Install Torrentflux
   #)[COLOR="DarkGreen"] sudo apt-get install torrentflux[/COLOR]

2) Check that you have a link in your /etc/apache2/conf.d dir:
   -  torrentflux.conf -> /etc/torrentflux/apache.conf

  IF not, then create it.
  #) [COLOR="DarkGreen"]cd /etc/apache2/conf.d[/COLOR]
  #)[COLOR="DarkGreen"] sudo ln -s /etc/torrentflux/apache.conf torrentflux.conf[/COLOR]

3) Restart Apache

  #)[COLOR="DarkGreen"] sudo /etc/init.d/apache2 restart[/COLOR]

4) Point you web browser to
  - [http://yourdomain.com/torrentflux](http://yourdomain.com/torrentflux)

Best regz,
/g:

---

### Post by njparton on 2008-01-18
Point your browser at:

[http://localhost/torrentflux/login.php](http://localhost/torrentflux/login.php)

to see it's running.  Also try:

[http://localhost/torrentflux](http://localhost/torrentflux)

if the first option wasn't successful.

Also remember that apache and mysql must be started (set them to start as services).

---

### Post by 449 on 2008-01-18
> **njparton said:**
> Point your browser at:

[http://localhost/torrentflux/login.php](http://localhost/torrentflux/login.php)

to see it's running.  Also try:

[http://localhost/torrentflux](http://localhost/torrentflux)

if the first option wasn't successful.

Also remember that apache and mysql must be started (set them to start as services).

I don't know how to start apache, and when I try to start mysql I get this:

erik@erik-desktop:~$ sudo mysql
[sudo] password for erik:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

---

### Post by njparton on 2008-01-18
It should be done automatically for you to be honest.  Did you install torrentflux from via synaptic?

That should instsll php, mysql and apache for you and start them up as well.  If you install using this method it will automatically ask you a few questions about mysql including creating passwords to the database.

It sounds like you need to uninstall and try again.  I'd uninstall mysql, apache and torrentflux.  php should be OK.

---

### Post by 449 on 2008-01-18
I did complete removals and then installed everything. Then it asked me if I wanted to restart apache2 and I did. Now I get this. 

Not Found

The requested URL /torrentflux/login/php was not found on this server.
Apache/2.2.4 (Ubuntu) Server at 192.168.1.5 Port 80

I wish there were some more clear directions on how to get torrentflux working. :confused:

---

### Post by h0me5k1n on 2008-01-18
I never had a problem installing torrentflux myself although I never used the repository version.

I use b4rts version.  It has lots of mods that the original torrentflux doesn't come with and it has a web installation routine that's easy to follow.  IIRC the hardest part when I first started was getting it to connect to the database. The b4rt version also comes with full installation instructions too.

You can find it [here]("http://tf-b4rt.berlios.de/").

---

### Post by kidford on 2008-01-18
I just installed torrentflux myself.  I guess you got Apache up and running?  Did you get your mysql problem sorted?
Is that error message verbatim (copy&paste)?  Because the address should be /torrentflux/login.php   not /torrentflux/login/php 
 > Not Found

The requested URL /torrentflux/login/php was not found on this server.
Apache/2.2.4 (Ubuntu) Server at 192.168.1.5 Port 80

---


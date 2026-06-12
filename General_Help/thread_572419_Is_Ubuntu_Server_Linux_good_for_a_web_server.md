---
title: "Is Ubuntu Server Linux good for a web server?"
date: 2007-10-10
forum: General Help
---

### Post by vstmlinux on 2007-10-10
Is Ubuntu Server Linux good for a web server?
Is it easy to use?
I never used a server before for a web server, i always used 1and1.com but now im sick of the inconvience of web hosts.

---

### Post by maybeway36 on 2007-10-10
It has no GUI, but you could install a desktop system on it too and it would probably be a bit easier. Be prepared to edit some files.

---

### Post by #Reistlehr- on 2007-10-10
yeah i think it's nice and stable.

I have DNS, DHCP running on one instance, and apache, mysql, ftp, svn, cvs on another. works great!

better than fedora i think

---

### Post by phillips321 on 2007-10-10
what a silly question to ask at an ubuntu forum.

Ubutnu server works fine for webserving,

I use ubuntu server for ww, ftp, dns and smtp. Doesn't have a gui and there's plenty of help available from
[ubuntuguide.org]("http://ubuntuguide.org")

---

### Post by naazgull on 2007-10-10
Hi,

Yes, ubuntu is good enough for hosting a web server. Actually, any linux distribution (Debian, Ubuntu, Fedora, Suse, etc) is good enough for hosting a website. Apache and Linux are almost siamese twins. 

Have in mind that may be better to edit some files in text mode that install a desktop environment you are going to use only a few times. My web/mail/multimedia host is only text-based and my interaction with it is basically updating it.

On the other hand, if you really don't like text-mode, install some web-based application to manage your server, like *Webmin*. 

Cheers,

---

### Post by vstmlinux on 2007-10-10
No GUI means it runs like DOS?

---

### Post by phillips321 on 2007-10-10
No gui means it will install by default like DOS, but to get a gui on it all you have to type is
```
sudo apt-get install kubuntu-desktop
```
If your asking if no gui means like DOS then your probably better off starting by using the standard ubuntu 7.04 cd then installing apache, php, etc.. afterwards

---

### Post by AZzKikR on 2007-10-10
I've been running a box of Ubuntu for over 1,5 years now as a webserver. Runs fine and dandy if you ask me :D

---

### Post by az on 2007-10-10
> **vstmlinux said:**
> No GUI means it runs like DOS?

Not DOS.  It's Unix.  Unix was around long before DOS...

See this:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

and

[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

---

### Post by _samba_ on 2007-10-10
web,ftp,mail,ntp,mysql,shorewall
:~# uptime 13:59:43 up 88 days,  3:28, (and I've seen a lot more)

---


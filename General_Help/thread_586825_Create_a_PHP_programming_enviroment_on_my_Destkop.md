---
title: "Create a PHP programming enviroment on my Destkop?"
date: 2007-10-22
forum: General Help
---

### Post by thenetduck on 2007-10-22
Hi

 I would like to somehow create an environment on my desktop PC (using Gusty) that I can program PHP/CSS/MySQL in. 

I was thinking the best solution would be to do a ubuntu-server install on my desktop but wanted to see if there would be a "best" solution. Thanks for the help guys

The Net Duck

---

### Post by Ek0nomik on 2007-10-22
> **thenetduck said:**
> Hi

 I would like to somehow create an environment on my desktop PC (using Gusty) that I can program PHP/CSS/MySQL in. 

I was thinking the best solution would be to do a ubuntu-server install on my desktop but wanted to see if there would be a "best" solution. Thanks for the help guys

The Net Duck

I am by no means a "programmer" although I have dipped into HTML, PHP, CSS, and Visual Basic .NET.

If you wanted to install the Ubuntu Server edition, it should be known that you don't get a graphical environment by default.  Although it's easy to install if you do want it.

This can help you on your journey with Ubuntu Server 7.10:  [http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

If you want the "Ubuntu" goodies you can simply run

```
sudo apt-get install ubuntu-desktop
```

after you install the server if you wish.  Or you could install the server tools after a regular Ubuntu install.

I don't know if you're an IDE guy or not, but I know Eclipse now has PHP support with a plug-in.  You could also try Aptana which is another PHP IDE.  Both are still "unstable", but they get the job done.

Cheers!

---

### Post by KCPokes on 2007-10-22
Sounds like you are just looking for a LAMP environment (Linux Apache MySQL PHP).  I'd suggest taking a look at [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) .  You don't necessarily need a server build if you just want a development environment.  If you are going to truly host sites from that machine, though, I would recommend a server install and forgo a lot of the GUI administration.

---

### Post by leg on 2007-10-22
I have pretty much as the above poster stated. I have installed Apache, mysql and PHP onto my machine. When I want to develop a site I turn the apache and mysql servers on and then build my sites using Bluefish. When I am finished developing I then transfer the files to the final server. There are plenty of other editors if you don't fancy Bluefish such as NVU, Kompressor, Quanta. Just set your projects up so that they are managed in the webroot of Apache so you can easily browse them.

---


---
title: "Web, samba server"
date: 2014-10-07
forum: General Help
---

### Post by scrufulufugu517 on 2014-10-07
I have so many problems:

My main goals are to host an apache web server, get my website running with my own domain name, and host a samba picture share server.

Q's:

I want to install ubuntu 12 desktop on my server.

When I update the kernel I can no longer view the "Its working" page but webmin still works

I get a constant error of "no talloc stackframe at ../source3/param/loadparam.c:4864, leaking memory"


P.S.
I have reinstalled ubuntu several times.

---

### Post by Doug S on 2014-10-08
> **scrufulufugu517 said:**
> When I update the kernel I can no longer view the "Its working" page but webmin still worksThe default DocumentRoot location changed, but that shouldn't be your problem because it isn't kernel related and was on 14.04. Does the /var/log/apache2/error.log file give you any insight?> **scrufulufugu517 said:**
> I get a constant error of "no talloc stackframe at ../source3/param/loadparam.c:4864, leaking memory"The bug report for that one is [here]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1257186"). I ignore that message now.

---

### Post by mastablasta on 2014-10-08
> **scrufulufugu517 said:**
> 
Q's:

I want to install ubuntu 12 desktop on my server.
.

consider using a lighter desktop environment if you are running a (headless) server. webmin should do all you need to do.

other interfaces than work on Ubuntu to explore and consider that might be easier on the eyes than webmin:
Zentyal
Ajenti

you can admin the server with webgui, no need for deksotp on it. if you really want desktop install lubuntu or maybe just a windows manager would be enough such as icewm.

---

### Post by scrufulufugu517 on 2014-10-08
> **Doug S said:**
> Does the /var/log/apache2/error.log file give you any insight?
A bunch of php config's but nothing else.

---


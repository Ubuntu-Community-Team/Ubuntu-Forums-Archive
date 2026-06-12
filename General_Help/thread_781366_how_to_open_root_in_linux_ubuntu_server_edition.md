---
title: "how to open root in linux ubuntu server edition"
date: 2008-05-04
forum: General Help
---

### Post by taimur on 2008-05-04
how to open root in linux ubuntu server edition?

---

### Post by tvtech on 2008-05-04
is gksu or sudo not enough for your application?

if not [go here]("http://www.netadmintools.com/art512.html")  [or here]("http://www.ubuntux.org/how-to-change-the-root-password-in-ubuntu")

it's a simple way to assign a root password and log in as root.  

I will warn you though while being logged in as root your server is very vulnerable to server side attacks.  malicious people ip and port surfing to see if there are unprotected servers in specific ip ranges. usually just stick to using gksu or sudo this gives you user level privledges and leases root for the time you need to install applications or configure most server software and then closes root access down, much more secure.

---


---
title: "freeipa installation"
date: 2020-12-17
forum: General Help
---

### Post by sniper8752 on 2020-12-17
I am trying to install freeipa on my ubuntu 20 server.  Here is the command that I run: sudo apt-get install freeipa-server -yThis is the response that I get:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package freeipa-server
```

How can I install this?

---

### Post by #&amp;thj^% on 2020-12-17
See if this helps: [https://computingforgeeks.com/install-and-configure-freeipa-server-on-ubuntu/](https://computingforgeeks.com/install-and-configure-freeipa-server-on-ubuntu/)

---

### Post by TheFu on 2020-12-17
```
sudo apt search freeipa
```
doesn't show that package, though it does show client-side packages.  

You'll need to find a PPA or some other method to get, install, and maintain the freeipa-server on Ubuntu.  That tells me that Ubuntu isn't a primary target for the FreeIPA development team, so I'd be afraid to run the server on Ubuntu.

I'd probably lean towards running it in an LXD container with a minimal CentOS8 OS running inside. I'd know this would need to be updated to some fork of CentOS soonish.  Seems FreeIPA and LXD have some infrastructure challenges due to userid mapping done in LXD, so this may not work. The article I found was a few years old.

---

### Post by #&amp;thj^% on 2020-12-17
+1 for TheFu's advice.
freeipa-server is a standard module to be installed in the 16.04 LTS version "only" without any additional PPA's! 
As far as I can see: [https://launchpad.net/freeipa](https://launchpad.net/freeipa) are the only sources supported. (I use that term loosely)

---

### Post by sniper8752 on 2020-12-19
any good alternatives to freeipa?

---

### Post by #&amp;thj^% on 2020-12-19
Well have a look at few, not sure on your needs though: [https://www.saasworthy.com/product-alternative/6003/freeipa](https://www.saasworthy.com/product-alternative/6003/freeipa)

---

### Post by sniper8752 on 2020-12-19
I just need to manage user logins from different boxes.

---

### Post by #&amp;thj^% on 2020-12-20
Seems the majority of those shown in my link will do the trick.

---

### Post by TheFu on 2020-12-20
Or use:
[LIST]
[*]NIS
[*]NIS+ 
[*]openLDAP
[/LIST]
NIS+ server is only available for Solaris, unfortunately.
NIS has security issues so places that care about that moved off it around 2000.
openLDAP is what all LDAP Linux solutions are built around. Modifications are handled via LDIF files in batch.  There are a few bloated desktop LDAP browsers, and a webapp that leaves me worried about security.  In the end, hooked up our LDAP clients to a Zimbra LDAP server. I wouldn't do this again and wouldn't recommend it, but to each their own.  Every Zimbra upgrade required removing the POSIX schema - doing the upgrade - then re-adding the POSIX schema back.

If you just need something quick for 5 systems and 20 users or less, NIS is easy.  NIS uses the yp-commands.  yppasswd, stuff like that. Any key-value DB can be used.

---

### Post by sniper8752 on 2020-12-20
I am going to try keycloak.

---

### Post by #&amp;thj^% on 2020-12-20
sponsored by RedHat, (certainly not a bad thing) lets us know will ya?

---


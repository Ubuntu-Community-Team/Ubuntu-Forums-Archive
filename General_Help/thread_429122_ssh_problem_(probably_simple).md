---
title: "ssh problem (probably simple)"
date: 2007-04-30
forum: General Help
---

### Post by srhlefty on 2007-04-30
Hello,
When I execute ```
ssh localhost
``` I get back ```
ssh: connect to host localhost port 22: Connection refused
```.

I've got the 'openssh-client' package installed.  I haven't installed openssh-server, because apt-get tells me the package doesn't exist.  Why is my ssh broken?  If I need to install openssh-server, why isn't it in the repositories? (maybe I don't have the right ones enabled?)

Thanks!
(This on Feisty)

---

### Post by jfinkels on 2007-04-30
> **srhlefty said:**
> Hello,
When I execute ```
ssh localhost
``` I get back ```
ssh: connect to host localhost port 22: Connection refused
```.

I've got the 'openssh-client' package installed.  I haven't installed openssh-server, because apt-get tells me the package doesn't exist.  Why is my ssh broken?  If I need to install openssh-server, why isn't it in the repositories? (maybe I don't have the right ones enabled?)

Thanks!
(This on Feisty)

If you want to ssh to localhost, you will need to have both the client and the server installed! I don't know why openssh-server can't be installed. If you want to enable the universe repository, go to "System > Administration > Software Sources" and check the universe repo.  To install openssh-server, type ```
sudo aptitude install openssh-server
```

---

### Post by WW on 2007-04-30
openssh-server is in the main repository, so you shouldn't have to enable any extra repositories to get it. 

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=openssh-server&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=openssh-server&searchon=names&subword=1&version=all&release=all)

---

### Post by srhlefty on 2007-04-30
Problem solved.  For some reason that package was not showing up in Synaptic or apt-cache search, but now for some reason it does.  The universe repo was already enabled, but the source code repo had a minus in the checkbox, so I changed it to a full check.  That's all I changed!  Strange...

Anyway now it works.  Thanks for your help!

---


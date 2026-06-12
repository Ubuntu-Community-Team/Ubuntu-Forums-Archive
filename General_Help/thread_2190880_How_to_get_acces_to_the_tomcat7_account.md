---
title: "How to get acces to the tomcat7 account"
date: 2013-11-29
forum: General Help
---

### Post by Empire-Phoenix on 2013-11-29
Hi,

Well I installed tomcat7 via apt-get and put a jenkins on it via the manager. So far so good.
Now I want to set up a public private key authentification for the tomcat user to one test server. For this I need to login to the tomcat7 user. However I find no way to make this possible.

I tried, to sudo passwd tomcat7 a password. This allows me to open a connection via ssh, that is instantly killed after the welcome stuff.
I tried in the /etc/init.d/tomcat7 to change the user to my user account. It is just ignored and starts with the tomcat7 user anyway. 

So far I see no errors in the var/log/tomcat7 it is just completly ignored

If i try to sudo su tomcat7 just nothing happend, I just stay at the account I'm with.

I don't know what to do anymore except killing the machine, and installing a tomcat manually, but this cannot be the only solution ?

Any help would be very much appreciated.

---

### Post by wbloos on 2014-03-17
Hi, did you solve this?
I would like to be able to su to tomcat7 too.

cheers,

WBL

---


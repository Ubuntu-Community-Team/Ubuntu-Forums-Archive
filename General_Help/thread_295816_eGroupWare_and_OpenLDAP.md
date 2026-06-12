---
title: "eGroupWare and OpenLDAP"
date: 2006-11-08
forum: General Help
---

### Post by mikcsabee on 2006-11-08
Hello everybody!

I have a problem with setup my OpenLdap clients whid my OpenLdap server.
First I setup my OpenLdap server like here: [https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)
Then I setup my eGroupWare like here: [http://mikcsabee.uw.hu/dokumentumok/ldap/ldap.png](http://mikcsabee.uw.hu/dokumentumok/ldap/ldap.png)
That is working.
But I want to setup some Ubuntu client. I try to setup like here: 
[https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication) and
[http://mikcsabee.uw.hu/dokumentumok/ldap/02.png](http://mikcsabee.uw.hu/dokumentumok/ldap/02.png) and
[http://mikcsabee.uw.hu/dokumentumok/ldap/03.png](http://mikcsabee.uw.hu/dokumentumok/ldap/03.png)

Something is wrong :(
Can someone help me?

---

### Post by backu on 2007-01-28
Don't require database login. Anonymous login will allow for retrieval of information. If login is required, then pam.d needs to know how to login.

Last time I had eGroupWare installed using OpenLDAP w/ Client/User Authentication, it was a bit of a hassle to get everything working right as the schema's don't mesh up properly and information is skewed.

---


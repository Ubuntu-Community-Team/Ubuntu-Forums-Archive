---
title: "LDAP – installation on web server – possible?"
date: 2007-12-06
forum: General Help
---

### Post by Berduchwal on 2007-12-06
I have my own website which is hosted on shared commercial sever and I wanted to find out if it is possible to install/set up LDAP server there. 
I have access to use ftp and php5.
I basically just want to have address book on the server that Thunderbird at home and MS Outlook at work can connect to.
How can I check if this is possible or try to do it?

---

### Post by opportunity on 2008-05-02
sure it is. u just have to install openldap using any guide like 
[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

u do have to expose / open the 389 ldap port.

setting up clients for the openldap also isnt a cake walk and requires reading. Damn qualified names...

---


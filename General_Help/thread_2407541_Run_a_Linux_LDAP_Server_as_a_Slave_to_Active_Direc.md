---
title: "Run a Linux LDAP Server as a Slave to Active Directory"
date: 2018-12-05
forum: General Help
---

### Post by mglau72 on 2018-12-05
I have a client that is _**currently **_using LDAP for user authentication.   They run 4 Slave LDAP UBUNTU servers on premise.  There are a total of 4 more Slaves running at 2 other offices.  The Slaves replicate to a Master UBUNTU LDAP server.  The LDAP slaves are being used to provide access to specific services like Apache.  There is a Samba server in the mix that serves as the domain controller.  Users login to the Samba DC for general domain services.  I hope that makes sense.  

They need to change their current environment.  **Their Goal is as follows**; They want to run the 8 UBUNTU servers as Slaves to Active Directory.  They want to continue to run LDAP, but want to point at AD and become Read Only Copies of AD.  Their goal would then be to remove the Master LDAP server as well as the Samba Server.  The Users would login to AD for general Domain Use, but still need the ability to login to the LDAP Servers for Linux Services.  

So- the current situation changes by losing the Master LDAP servers and the Samba server that is used as the DC.  Added to this- is the LDAP servers become slaves to Active Directory.  

I've found related information out there, but nothing pointing in this specific direction.

---


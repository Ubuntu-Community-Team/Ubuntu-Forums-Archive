---
title: "Equivalent to Active Directory for Ubuntu clients and server"
date: 2014-08-06
forum: General Help
---

### Post by vmalep on 2014-08-06
Dear all,

we are installing Lubuntu in a school in Addis. One nice feature that I never saw in the Ubuntu world is the equivalent to the Active Directory, meaning that the students can login on any Lubuntu client and get their files and configuration back from the server.

I know we can configure such kind of server with Samba and there is maybe a way to configure Lubuntu as client for this, but I guess there should be a better way, more integrated to the Linux system (as there will be no Windows client anyway).

For sure, NFS for the files and the server can get the home folder of all the client. Then what? LDAP? (I have 0 experience in this solution actually)...

Thanks for your support and suggesstions!
Pierre

---

### Post by cj13579 on 2014-08-06
You could use OpenLDAP to achieve this. [This]("https://www.digitalocean.com/community/tutorials/how-to-authenticate-client-computers-using-ldap-on-an-ubuntu-12-04-vps") is a really good guide on configuring an OpenLDAP server and configuring the clients to talk to it.

---

### Post by wyliecoyoteuk on 2014-08-06
Active Directory is just the Microsoft version of LDAP.

You can also use a Samba server as a domain controller, and use LDAP for authentication with Samba clients.

---


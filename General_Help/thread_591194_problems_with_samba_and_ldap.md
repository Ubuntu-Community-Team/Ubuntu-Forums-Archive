---
title: "problems with samba and ldap"
date: 2007-10-25
forum: General Help
---

### Post by grev1 on 2007-10-25
Hi all linux people, my first post here:-)

I have configured a server with Samba as a PDC, and i seemed to work well. I managed to join the domain with windows computers, and shares worked fine. 

Then i would try to get Samba and Ldap to work together, and red som turtorials on the net, and added these lines in the global section of mye smb.conf

passdb backend = ldapsam:ldap://127.0.0.1
ldap passwd sync = Yes
ldap suffix = dc=tklab,dc=local
ldap admin dn = cn=admin,dc=tklab,dc=local
ldap ssl = start tls
ldap user suffix = ou=People
ldap machine suffix = ou=Computers
ldap idmap suffix = ou=People
add user script = /usr/sbin/smbldap-useradd -m "%u"
ldap delete dn = Yes
add machine script = /usr/sbin/smbldap-useradd -w "%u"

Then I restarted the Samba server, and tried to join a computer to the domain. I got this error message:
-------------------------------------------------------------
The following error occurred when DNS was queried for the service location (SRV) resource record used to locate a domain controller for domain tklab.:

The error was: "DNS name does not exist."
(error code 0x0000232B RCODE_NAME_ERROR)

The query was for the SRV record for _ldap._tcp.dc._msdcs.tklab.

Common causes of this error include the following:

- The DNS SRV record is not registered in DNS.

- One or more of the following zones do not include delegation to its child zone:

tklab.
. (the root zone)
---------------------------------------------------------
I changed the zonefile, and added the srv record, and tried again, but got this error:
----------------------------------------------------------
The domain name tklab might be a NetBIOS domain name. If this is the case, verify that the domain name is properly registered with WINS.

If you are certain that the name is not a NetBIOS domain name, then the following information can help you troubleshoot your DNS configuration.

DNS was successfully queried for the service location (SRV) resource record used to locate a domain controller for domain tklab:

The query was for the SRV record for _ldap._tcp.dc._msdcs.tklab

The following domain controllers were identified by the query:

nasse.tklab.local

Common causes of this error include:

- Host (A) records that map the name of the domain controller to its IP addresses are missing or contain incorrect addresses.

- Domain controllers registered in DNS are not connected to the network or are not running.
-------------------------------------------------------------------------
Everything worked perfect before i made these changes, and I only did the ldap changes in smb.conf. 

I tried to comment out all the ldap lines in smb.conf, and then restart the Samba server, but i still got the same error.

I still got permission to linux-shares from the windows computer.

Any idea what have happened?

Thanks for any good solution of this.

Ps: I am a bit noob when it comes to linux
Ps2: Sorry for my bad English :-P

Best regards

---

### Post by grev1 on 2007-10-26
bump

---

### Post by grev1 on 2007-10-28
Solved :-)

---

### Post by thechitowncubs on 2008-02-23
how did you solve this? I am getting the same problem

---


---
title: "ldapsearch TLS 1.2 error"
date: 2015-08-26
forum: General Help
---

### Post by Muhammad_Arif on 2015-08-26
Hello. I'm new here and this is my first post. I'm trying to troubleshoot a problem with ldapsearch with Active Directory. I've set up a lab environment and reproduced the problem as follows:

 Ubuntu 14.04.3
 Old domain controller running Windows 2008 R2
 New domain controller running Windows 2012 R2
 Active Directory domain in 2008 R2 functional level

 I can run ldapsearch -H [ldaps://oldserver.foobar.com:636](ldaps://oldserver.foobar.com:636) -D [EMAIL="myid@mydomain"]myid@mydomain[/EMAIL] -W -b "dc=foobar,dc=com" -s sub -x -d 1 and it works fine.

 If I try the exact same command but use the new server with 2012 R2, I get an error: TLS: can't connect: A TLS packet with unexpected length was received.

 If I turn off TLS 1.1 and 1.2 on the new server, this command works. So, this has something to do with TLS 1.2 

 I have tried a few things I found by searching but haven't been able to fix the problem. I can't turn off TLS 1.2 on the new domain controller because many other non-Unix clients are using it.
 Any suggestions? Thanks in advance.

---

### Post by Hilitec on 2015-12-28
Hello,

GnuTLS and SChannel (Microsoft) implementations are not (yet) compatible for TLS 1.2 negotiation during AD/LDAPS binding.

The trick is to disable TLS1.2 for OpenLDAP like this:
export LDAPTLS_CIPHER_SUITE=NORMAL:!VERS-TLS1.2

If you are binding AD/LDAP from PHP, you can do something like that:
putenv(‘LDAPTLS_CIPHER_SUITE=NORMAL:!VERS-TLS1.2’);

Hope it helps

Best regards,

Andre


> **Muhammad_Arif said:**
> Hello. I'm new here and this is my first post. I'm trying to troubleshoot a problem with ldapsearch with Active Directory. I've set up a lab environment and reproduced the problem as follows:

 Ubuntu 14.04.3
 Old domain controller running Windows 2008 R2
 New domain controller running Windows 2012 R2
 Active Directory domain in 2008 R2 functional level

 I can run ldapsearch -H [ldaps://oldserver.foobar.com:636](ldaps://oldserver.foobar.com:636) -D myid@mydomain -W -b "dc=foobar,dc=com" -s sub -x -d 1 and it works fine.

 If I try the exact same command but use the new server with 2012 R2, I get an error: TLS: can't connect: A TLS packet with unexpected length was received.

 If I turn off TLS 1.1 and 1.2 on the new server, this command works. So, this has something to do with TLS 1.2 

 I have tried a few things I found by searching but haven't been able to fix the problem. I can't turn off TLS 1.2 on the new domain controller because many other non-Unix clients are using it.
 Any suggestions? Thanks in advance.

---


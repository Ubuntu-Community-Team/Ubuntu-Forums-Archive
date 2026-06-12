---
title: "Evolution giving SSL cert error for ATT/Yahoo email"
date: 2013-02-11
forum: General Help
---

### Post by genterminl on 2013-02-11
For the past few weeks, Evolution is giving me an error trying to fetch pop3 email from AT&T/Yahoo (sbcglobal.net address)
> SSL Certificate check for inbound.att.net:

Issuer:            CN=VeriSign Class 3 Secure Server CA - G3,OU=Terms of use at [https://www.verisign.com/rpa](https://www.verisign.com/rpa) (c)10,OU=VeriSign Trust Network,O="VeriSign, Inc.",C=US
Subject:           CN=inbound.att.net,OU=att.net Mail,O="AT&T Services, Inc.",L=Southfield,ST=Michigan,C=US
Fingerprint:       3e:13:32:42:87:cb:12:f7:2b:84:bd:a7:56:27:3c:8c
Signature:         BAD

Do you wish to accept?
Initially, I figured that AT&T/Yahoo had changed something, but after a bunch more searching, I'm not sure.  

I've seen a number of posts regarding Evolution issues with nss.  I do see a file with the name of the above fingerprint in ~/.camel_certs, dated about a month ago, although most of the other files in that directory are older.  However, several posts I've seen seem to indicate that ~/.camel_certs is old and no longer used.  

Other posts point to ~/.pki/nssdb - and particularly claim there should be an file (or symlink?) in it named libnssckbi.so.  However, creating a symlink there to /usr/lib/i386-linux-gnu/nss/libnssckbi.so did not eliminate the error.  More interestingly, doing an strace on evolution includes the line:
> open("sql:/home/me/.pki/nssdb/libnssckbi.so", O_RDONLY) = -1 ENOENT (No such file or directory)I'd love to know whether I'm actually missing a file.  Also, what is the "sql:" at the beginning of the pathname for?

I suppose I'll just end up accepting the cert, but I don't really want to do that without actally understanding why I'm getting the error now?

Evolution 3.2.2, Ubuntu 11.10

Thanks for any suggestions.

---


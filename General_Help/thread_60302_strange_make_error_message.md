---
title: "strange make error message"
date: 2005-08-27
forum: General Help
---

### Post by roots on 2005-08-27
hi everybody,

i just tried to install thc_hydra on ubuntu hoary...configure went fine but make brought the following output:

```

gcc -I. -Wall -O2 -lm -o hydra hydra-vnc.o hydra-pcnfs.o hydra-rexec.o hydra-nntp.o hydra-socks5.o hydra-telnet.o hydra-cisco.o hydra-http.o hydra-ftp.o hydra-imap.o hydra-pop3.o hydra-smb.o hydra-icq.o hydra-cisco-enable.o hydra-ldap.o hydra-mysql.o hydra-http-proxy.o hydra-smbnt.o hydra-mssql.o hydra-snmp.o hydra-cvs.o hydra-smtpauth.o hydra-sapr3.o hydra-ssh2.o hydra-teamspeak.o hydra-postgres.o hydra-rsh.o hydra-rlogin.o crc32.o d3des.o md4.o hydra-mod.o hydra.o -lm -lpq -L/usr/lib -L/usr/local/lib -L/lib -L/usr/lib
/usr/bin/ld: cannot find -lpq
collect2: ld returned 1 exit status
make: *** [hydra] Error 1

``` 

as i'm pretty n00b to that kind of stuff - can anyone tell me what the problem with ld is and how to solve it?

cheers,
.roots :-)

---


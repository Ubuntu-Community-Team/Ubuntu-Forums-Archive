---
title: "Compiling package: error 1"
date: 2008-01-13
forum: General Help
---

### Post by dzuari on 2008-01-13
im trying to compile a package for hydra-5.4-src the directions are:
```
HOW TO COMPILE
--------------
Type "./configure" and then "make" and "make install".
If you have CYGWIN, you have to follow the instructions "./configure" prints
after running.
For PalmPilot, run "./configure-palm".
For ARM processor mobiles, run "./configure-arm".
```

but when i get to the comand "make" this is wat happens:
```
NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES
=======================================================================
ARM/PalmPilot users: please run ./configure-arm or ./configure-palm respectivly

now type "make"
root@jahood:/home/jahood/Desktop/Documents/blank/THC/hydra/hydra-5.4-src# make
gcc -I. -Wall -O2 -o pw-inspector pw-inspector.c
gcc -I. -Wall -O2 -c hydra-vnc.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-pcnfs.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-rexec.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-nntp.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-socks5.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-telnet.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-cisco.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-http.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-ftp.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-imap.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-pop3.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-smb.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-icq.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-cisco-enable.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-ldap.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-mysql.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-http-proxy.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-smbnt.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-mssql.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-snmp.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-cvs.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-smtpauth.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-sapr3.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-ssh2.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-teamspeak.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-postgres.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-rsh.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-rlogin.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-oracle-listener.c -DLIBPOSTGRES 
hydra-oracle-listener.c:10:2: warning: #warning "The Oracle Listener module does not work yet"
gcc -I. -Wall -O2 -c hydra-svn.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-pcanywhere.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-sip.c -DLIBPOSTGRES 
hydra-sip.c:4:25: error: openssl/ssl.h: No such file or directory
hydra-sip.c:5:25: error: openssl/err.h: No such file or directory
hydra-sip.c:6:25: error: openssl/md5.h: No such file or directory
hydra-sip.c: In function ‘md5_crypt’:
hydra-sip.c:24: error: ‘MD5_DIGEST_LENGTH’ undeclared (first use in this function)
hydra-sip.c:24: error: (Each undeclared identifier is reported only once
hydra-sip.c:24: error: for each function it appears in.)
hydra-sip.c:26: error: ‘MD5_CTX’ undeclared (first use in this function)
hydra-sip.c:26: error: expected ‘;’ before ‘c’
hydra-sip.c:31: warning: implicit declaration of function ‘MD5_Init’
hydra-sip.c:31: error: ‘c’ undeclared (first use in this function)
hydra-sip.c:32: warning: implicit declaration of function ‘MD5_Update’
hydra-sip.c:33: warning: implicit declaration of function ‘MD5_Final’
hydra-sip.c:24: warning: unused variable ‘md5_raw’
hydra-sip.c: In function ‘sip_register’:
hydra-sip.c:60: error: ‘MD5_DIGEST_LENGTH’ undeclared (first use in this function)
hydra-sip.c:61: warning: unused variable ‘resp’
hydra-sip.c:61: warning: unused variable ‘mu’
hydra-sip.c:60: warning: unused variable ‘urp’
make: *** [hydra-sip.o] Error 1
root@jahood:/home/jahood/Desktop/Documents/blank/THC/hydra/hydra-5.4-src# 

```

can someone tell me wats wrong and why i cant compile these?

---

### Post by dzuari on 2008-01-13
bump

---

### Post by dzuari on 2008-01-13
bump

---

### Post by geraldm on 2008-01-14
hydra-sip.c:4:25: error: openssl/ssl.h: No such file or directory
hydra-sip.c:5:25: error: openssl/err.h: No such file or directory
hydra-sip.c:6:25: error: openssl/md5.h: No such file or directory

It did not find the openssl headers, which sometimes install to /usr/local/include
You will either need to install them, which would be in *-dev package OR perhaps set configure options to try without the openssl package.

Gerald

---


---
title: "Installing Hydra 5.4 help"
date: 2007-12-10
forum: General Help
---

### Post by slowz3r on 2007-12-10
Im having trouble getting Hydra/HydraGTK to compile and install properly here are the steps im using and the output from these steps.

andy@slowz3r:~/Desktop/hydra-5.4-src$ sudo ./configure

> Starting hydra auto configuration ...

Checking for openssl (libssl/ssl.h) ...
                                    ... NOT found, SSL support disabled
Get it from [http://www.openssl.org](http://www.openssl.org)
Checking for Postgres (libpq) ...
                              ... found
Checking for SVN (ibsvn_client-1 libapr-0.so libaprutil-0.so) ...
                              ... found
Checking for SAP/R3 (librfc/saprfc.h) ...
                                      ... NOT found, module sapr3 disabled
Get it from [http://www.sap.com/solutions/netweaver/linux/eval/index.asp](http://www.sap.com/solutions/netweaver/linux/eval/index.asp)
Checking for libssh (libssh/libssh.h) ...
                                      ... NOT found, module ssh2 disabled
Get it from [http://0xbadc0de.be/](http://0xbadc0de.be/) - use v0.11!

Hydra will be installed into .../bin of: /usr/local
  (change this by running ./configure --prefix=path)

Writing Makefile.in ...

NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES
=======================================================================
ARM/PalmPilot users: please run ./configure-arm or ./configure-palm respectivly

now type "make"
andy@slowz3r:~/Desktop/hydra-5.4-src$ sudo ./configure

Starting hydra auto configuration ...

Checking for openssl (libssl/ssl.h) ...
                                    ... NOT found, SSL support disabled
Get it from [http://www.openssl.org](http://www.openssl.org)
Checking for Postgres (libpq) ...
                              ... found
Checking for SVN (ibsvn_client-1 libapr-0.so libaprutil-0.so) ...
                              ... found
Checking for SAP/R3 (librfc/saprfc.h) ...
                                      ... NOT found, module sapr3 disabled
Get it from [http://www.sap.com/solutions/netweaver/linux/eval/index.asp](http://www.sap.com/solutions/netweaver/linux/eval/index.asp)
Checking for libssh (libssh/libssh.h) ...
                                      ... NOT found, module ssh2 disabled
Get it from [http://0xbadc0de.be/](http://0xbadc0de.be/) - use v0.11!

Hydra will be installed into .../bin of: /usr/local
  (change this by running ./configure --prefix=path)

Writing Makefile.in ...

NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES
=======================================================================
ARM/PalmPilot users: please run ./configure-arm or ./configure-palm respectivly

now type "make"


andy@slowz3r:~/Desktop/hydra-5.4-src$ sudo make

> gcc -I. -Wall -O2 -c hydra-sip.c -DLIBPOSTGRES 
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

andy@slowz3r:~/Desktop/hydra-5.4-src$ sudo make install
> gcc -I. -Wall -O2 -c hydra-sip.c -DLIBPOSTGRES 
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


I know thats allot of stuff, i noticed allot of warnings after the make and make install commands, i just dont know how to fix those

Any help would be much appreciated

---

### Post by cisforcojo on 2007-12-17
Ok I'm actually doing this right now as well but I've gotten it installed. I'm working on adding protocols to it. First you should look at the ./configure part and make sure that everything that is NOT FOUND is stuff that you don't care about. Personally, I need it for SSH so I had to solve that SSH problem. That part is easy, just go to the badc0de site it lists in configure, download v0.11 and install it. 

Now some advice for installing,
1) Find libssl and libssl-dev in synaptic and install it. You need it. That's what the first few errors are in 'make'
2) NEVER EVER EVER type 'make install'. It's really messy and you need to keep the source if you ever want to uninstall. Instead do a 'sudo apt-get install checkinstall' and then INSTEAD of 'sudo make install' type 'sudo checkinstall'. That will make a .deb file and install that so if you want to ever remove it, you can just do a sudo apt-get remove packagename. It's very difficult to remove files from a 'sudo make install'

So first do these 2 things (I'd strongly suggest installing everything so that when you type ./configure everything is found. Why not just do it right now and have more for later?)

Get back to me if you're still having problems.

EDIT: I'd also recommend to use
```

./configure --prefix=/usr

```

---


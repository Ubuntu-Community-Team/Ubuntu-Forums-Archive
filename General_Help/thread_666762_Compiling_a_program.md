---
title: "Compiling a program"
date: 2008-01-13
forum: General Help
---

### Post by dzuari on 2008-01-13
im currently trying to compile Hydra5.4 and in its read me it says to:

```
/HOW TO COMPILE
--------------
Type "./configure" and then "make" and "make install".
If you have CYGWIN, you have to follow the instructions "./configure" prints
after running.
For PalmPilot, run "./configure-palm".
For ARM processor mobiles, run "./configure-arm".

```

but when i open up a terminal and type /configure i get this

```
root@jahood:/home/jahood# /configure
bash: /configure: No such file or directory
root@jahood:/home/jahood# 
root@jahood:/home/jahood# 

```

can anyone explain to me? there is a file inside the Hydra  name "configure" but when i click it the terminal pops up and goes away to fast for me to read it...

---

### Post by SOULRiDER on 2008-01-13
You missed the dot.
its **.**/configure not just /configure

---

### Post by holihue on 2008-01-13
> **dzuari said:**
> 
```
root@jahood:/home/jahood# /configure
bash: /configure: No such file or directory
root@jahood:/home/jahood# 
root@jahood:/home/jahood# 

```



try: "./configure" (when you are inside the folder with the source)

What you did wrong was "/configure", and what you need to run is "./configure"

---

### Post by KingWilliam on 2008-01-13
Your readme is telling you exactly what tot do :)
```

CD "the directory where the configure file is located"
./configure
make
make install

```

---

### Post by SOULRiDER on 2008-01-13
I forgot to tell you. Remember youre gonna need packages in order to compile. Run these commands to install the necessary packages.
```
sudo aptitude install build-essential checkinstall
```

When compiling dont use the ```
make install
``` command, instead do ```
sudo checkinstall
```

---

### Post by dzuari on 2008-01-13
iv tried ./configure and it still doesnt work, do i have to change my directory to where my Hydra files are? my terminal starts in
 ```
root@jahood:/home/jahood# 

``` 
and my hydra directory is
```
/home/jahood/Desktop/Documents/blank/THC/hydra/hydra-5.4-src
```

and is changing dir like it is on DOS?
 ```
/cd
```
??

---

### Post by dzuari on 2008-01-13
bump

---

### Post by dzuari on 2008-01-13
k i figured out that i had to change the dir, but now after i type ./configure and then type /make, i get an error:
```
Installing with make install...

========================= Installation results ===========================
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

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

help?

---

### Post by ZapalacX on 2008-01-13
yes, just

```
cd Desktop/Documents/blank/THC/hydra/hydra-5.4-src
```

---

### Post by sumguy231 on 2008-01-13
Did ./configure throw any errors or mention missing dependencies? It sounds like you're missing some other software that Hydra depends on.

---

### Post by dzuari on 2008-01-13
wat do u mean by throw any errors? im new to all this, just started today:D, heres exactly wat i typed to get this starting at the /cd command 

```
root@jahood:/home/jahood# cd /home/jahood/Desktop/Documents/blank/THC/hydra/hydra-5.4-src
root@jahood:/home/jahood/Desktop/Documents/blank/THC/hydra/hydra-5.4-src# ./configure

Starting hydra auto configuration ...

Checking for openssl (libssl/ssl.h) ...
                                    ... NOT found, SSL support disabled
Get it from http://www.openssl.org
Checking for Postgres (libpq) ...
                              ... found
Checking for SVN (ibsvn_client-1 libapr-0.so libaprutil-0.so) ...
                              ... NOT found, module svn disabled
Checking for SAP/R3 (librfc/saprfc.h) ...
                                      ... NOT found, module sapr3 disabled
Get it from http://www.sap.com/solutions/netweaver/linux/eval/index.asp
Checking for libssh (libssh/libssh.h) ...
                                      ... NOT found, module ssh2 disabled
Get it from http://0xbadc0de.be/ - use v0.11!

Hydra will be installed into .../bin of: /usr/local
  (change this by running ./configure --prefix=path)

Writing Makefile.in ...

NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES
=======================================================================
ARM/PalmPilot users: please run ./configure-arm or ./configure-palm respectivly

now type "make"
root@jahood:/home/jahood/Desktop/Documents/blank/THC/hydra/hydra-5.4-src# make
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

---

### Post by sumguy231 on 2008-01-13
It apparently still wants OpenSSL to be installed even though it said it was just going to disable support for it and move on. As far as I can see there isn't any way to disable it at configuration either. Maybe someone with experience compiling it can help you instead.

I should add that searching for "hydra ubuntu" might turn up some useful material. If you're willing to trust this random stranger, then here's someone who has precompiled packages:
[http://blog.goukihq.org/2006/07/28/the-hackers-choice-hydra-on-ubuntu/](http://blog.goukihq.org/2006/07/28/the-hackers-choice-hydra-on-ubuntu/)
Use at your own risk, of course.

---

### Post by KingWilliam on 2008-01-15
```

Checking for openssl (libssl/ssl.h) ...
                                    ... NOT found, SSL support disabled
Get it from http://www.openssl.org

Checking for SVN (ibsvn_client-1 libapr-0.so libaprutil-0.so) ...
                              ... NOT found, module svn disabled

Checking for SAP/R3 (librfc/saprfc.h) ...
                                      ... NOT found, module sapr3 disabled
Get it from http://www.sap.com/solutions/netweaver/linux/eval/index.asp

Checking for libssh (libssh/libssh.h) ...
                                      ... NOT found, module ssh2 disabled
Get it from http://0xbadc0de.be/ - use v0.11!

```

running ./configure is meant to check wheter you have all the programs required to install/run your new program and detect your system specs. If configure fails, you wont be able to "make" or compile the program. Your configure threw 4 errors. I copied them above. If you want to be able to install your program, you MUST install these 4 programs first.

---

### Post by maiux on 2008-01-22
I tried installing THC HYDRA and get the same error message. If you've found the missing components post the URL or better yet the direct file source so people don't have to search the site for hours looking for it. Thanks.

---

### Post by ellgor on 2008-01-23
Hi,

Configure is looking for a program called openssl, which is in the repositries, it might show up as installed but there could be a dev package which you might need, there's also a lot of openssl packages? hope this helps.

Regards, Ellgor.

---

### Post by jakx on 2008-02-03
```
========================= Installation results ===========================
gcc -I. -Wall -O2 -c hydra-sip.c -DLIBPOSTGRES 
hydra-sip.c:4:25: error: openssl/ssl.h: No such file or directory
hydra-sip.c:5:25: error: openssl/err.h: No such file or directory
hydra-sip.c:6:25: error: openssl/md5.h: No such file or directory
hydra-sip.c: In function &#8216;md5_crypt&#8217;:
hydra-sip.c:24: error: &#8216;MD5_DIGEST_LENGTH&#8217; undeclared (first use in this function)
hydra-sip.c:24: error: (Each undeclared identifier is reported only once
hydra-sip.c:24: error: for each function it appears in.)
hydra-sip.c:26: error: &#8216;MD5_CTX&#8217; undeclared (first use in this function)
hydra-sip.c:26: error: expected &#8216;;&#8217; before &#8216;c&#8217;
hydra-sip.c:31: warning: implicit declaration of function &#8216;MD5_Init&#8217;
hydra-sip.c:31: error: &#8216;c&#8217; undeclared (first use in this function)
hydra-sip.c:32: warning: implicit declaration of function &#8216;MD5_Update&#8217;
hydra-sip.c:33: warning: implicit declaration of function &#8216;MD5_Final&#8217;
hydra-sip.c:24: warning: unused variable &#8216;md5_raw&#8217;
hydra-sip.c: In function &#8216;sip_register&#8217;:
hydra-sip.c:60: error: &#8216;MD5_DIGEST_LENGTH&#8217; undeclared (first use in this function)
hydra-sip.c:61: warning: unused variable &#8216;resp&#8217;
hydra-sip.c:61: warning: unused variable &#8216;mu&#8217;
hydra-sip.c:60: warning: unused variable &#8216;urp&#8217;
make: *** [hydra-sip.o] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```whats the problem???

---


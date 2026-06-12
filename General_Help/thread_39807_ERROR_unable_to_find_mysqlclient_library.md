---
title: "ERROR: unable to find mysqlclient library"
date: 2005-06-06
forum: General Help
---

### Post by SilverCloak on 2005-06-06
Hi,

I'm trying to compile Barnyard because I want to use Sguil  and I always
receive this message during  ./configure command :


.
.
.
checking for strerror... (cached) yes
checking for /usr/local/include/mysql/mysql.h... yes
checking for mysql_real_connect in -lmysqlclient... no

**********************************************
  ERROR: unable to find mysqlclient library
  checked in the following places
        /usr/lib/
**********************************************

I insatlled libmysqlclient12-dev  but I still get the error...

Anyone can help ?

Andre Noel

---

### Post by xao on 2005-06-06
Is the library actually in /usr/lib?

It may be possible that you have it installed but it is not in the place the config script is looking....

---

### Post by SilverCloak on 2005-06-07
Yes I did verify that  here is what I see:

/usr/lib/libmysqlclient.a
/usr/lib/libmysqlclient.la
/usr/lib/libmysqlclient_r.a
/usr/lib/libmysqlclient_r.la
/usr/lib/libmysqlclient_r.so -> libmysqlclient_r.so.12
/usr/lib/libmysqlclient_r.so.12 -> libmysqlclient_r.so.12.0.0
/usr/lib/libmysqlclient_r.so.12.0.0
/usr/lib/libmysqlclient.so -> libmysqlclient.so.12
/usr/lib/libmysqlclient.so.12 -> libmysqlclient.so.12.0.0
/usr/lib/libmysqlclient.so.12.0.0
/usr/lib/libmysqld.a

Andre

---

### Post by xao on 2005-06-07
I did some poking around. It seems that you are very much NOT in the minority on this problem. I found the following fix:

.....It appears the files needed are in place. This error demonstrates the second weakness of installing software from source. Sometimes it does not work as expected, and administrators must tweak installation files to accommodate their systems.

The resolution to this problem surfaces by doing a Google search. If we modify the configure script as shown, it fixes the problem:

original configure script:

  LIBS="${LIBS} -lz -lssl -lmysqlclient"

modified configure script:

  LIBS="${LIBS} -lz -lssl -lcrypto -lmysqlclient"


Let me know what happens, but it seems like this has worked for many people.




xao

---

### Post by SilverCloak on 2005-06-07
I had already found that fix on google and I tried it without any
success.

---

### Post by xao on 2005-06-07
ok ok. i downloaded barnyard and all the other stuff in hopes of reproducing the error. well, as with you the same error was being thrown when i configured it. 

remember the line:
 LIBS="${LIBS} -lz -lssl -lmysqlclient"  ???

per the suggestion of research, i tried removing the -lz -lssl from the line making it:

LIBS="${LIBS} -lmysqlclient"   

(on line 2556)

and lo and behold it configured and compiled.


hope this helps....


xao

---

### Post by SilverCloak on 2005-06-08
I tried what you suggested but got the same error.

What version of mysql client have you installed  ? For me it's version 1.2

Is there a debian package already done for barnyard ?

---

### Post by SilverCloak on 2005-06-08
I tried again with your suggestion removing  the -lz -lssl  parameters but this time issuing the command:

./configure --with-mysql-libraries=/usr/lib/ --enable-mysql

and it looks that it worked.

---

### Post by xao on 2005-06-08
horay!!!

---

### Post by SilverCloak on 2005-06-08
Thank you very much xao, really appreciated.

---

### Post by xao on 2005-06-08
no problem at all. glad i could do something constructive with my time. summer school at university requires remarkably little of it..

---


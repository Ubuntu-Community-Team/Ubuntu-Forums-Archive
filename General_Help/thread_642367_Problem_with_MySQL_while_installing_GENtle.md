---
title: "Problem with MySQL while installing GENtle"
date: 2007-12-16
forum: General Help
---

### Post by Biochem on 2007-12-16
I'm trying to install GENtle for a friend but I'm having proble with some dependencies. In Edgy it only required to untar the program and run the executable, but now it doesn´t work.

At first I got :
```
~/GENtle$ ./GENtle
./GENtle: error while loading shared libraries: libmysqlclient.so.14: cannot open shared object file: No such file or directory

```

So I did:
```
$ sudo ln -s /usr/lib/libmysqlclient.so.15 /usr/lib/libmysqlclient.so.14
```

And now I'm stuck with:
```
$ ./GENtle
./GENtle: /usr/lib/libmysqlclient.so.14: version `MYSQL_4.1' not found (required by ./GENtle)
```

Anybody has an idea what I'm doing wrong?

Thanks.

---

### Post by Biochem on 2007-12-19
Any suggestion would be appreciated?

Thanks

---

### Post by Biochem on 2007-12-27
bump

---

### Post by kalon33 on 2008-02-25
I have the same problem with it. I'm trying to compile it from sources but encounters problems. When they will be closed, I would send it my results !

But it seems that your problem is due to very close dependency on a version of the mysqlclient... I've no solution for it except that you've already done, or to recompile it.

---

### Post by Biochem on 2008-02-25
Hello kalon33,
Thanks for your input. I did try to compile it from source but had nerver manage to do it. seems to be beyond my capabilities of typing:

./configure
make
make install

If you succeed in your compilation please post back your results.

Biochem

---

### Post by Berneri on 2008-04-22
Hi,
So GENtle needs libmysqlclient14, which is only present in Dapper and Edgy. From Feisty on, it is replaced by libmysqlclient15. As the binary you got is compiled for libmysqlclient14, it can't work on your machines. One solution is to get the libmysqlclient.so.14 and copy it to /usr/libs/ folder. Another solution might be (but it comes close to the limits of my linux knowlegde) to create in /usr/libs/ a libmysqlclient.so.14 file that would actually point to libmysqlclient.so.15 so that GENtle believes that the former is here.
Best solution of all: compile it with the libmysqlclient15. I tried but to date did not manage to get it.

Anyway, in case you just want something like clone manager or gene construction kit, there is ApE in Tcl/Tk. Not really beautiful, but to my opinion, far better clone manager for example (but i'm sure you already heard about it).

Bye, and good luck. If i manage to get a package, i'll let you know.

---

### Post by Berneri on 2008-04-22
Hi, it's me again, to get the libraries I mentionned, you can follow this link:[GENtle_libraries]("http://http://downloads.sourceforge.net/gentle-m/GENtle_libraries.tar.bz2?modtime=1121161355&big_mirror=0") to untar the libraries and deal with it as described in my precedent post.

---

### Post by shoponline on 2008-04-22
Hello! welcome to our website; [http://www.newnike-shoes.com](http://www.newnike-shoes.com)
we can supply low price with high quality products.You can view our website for the details. 
Thanks for your reading , pls email us if u have any questions about business . We hope that will make a long&great business with you in future.
Your satisfactions,Our pursuit!
Please Email me to get discount!!
website: [http://newnike-shoes.com](http://newnike-shoes.com)
MSN: [email]newnike-shoes@hotmail.com[/email] 
YAHOO: [email]newnike-shoes@yahoo.com.cn[/email]  
or E-mail:newnike.shoes100@gmail.com
Best regards

---


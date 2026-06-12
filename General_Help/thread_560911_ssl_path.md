---
title: "ssl path"
date: 2007-09-26
forum: General Help
---

### Post by ryanfx on 2007-09-26
Hey guys,


I'm new to linux and I still don't quite understand the concept of paths and environment variables, hopefully someone can help me.

I tried to update my SSL and I came across a little problem 

```

OpenSSL> version
OpenSSL 0.9.8c 05 Sep 2006
OpenSSL> 
ryan@ryan-desktop:/usr/local/ssl/bin$ ./openssl 
OpenSSL> version
OpenSSL 0.9.8e 23 Feb 2007
OpenSSL> 
ryan@ryan-desktop:/usr/local/ssl/bin$ which openssl
/usr/local/bin/openssl
ryan@ryan-desktop:/usr/local/ssl/bin$ 

```

When I execute the openssl (which is a global) command it prints out revision c, but if I browse to where the new version of ssl was installed and call the openssl bin file in that directory it boots up to the e version.  Could someone tell me how to fix this so the correct version of openssl is called, and some documentation to my problem?  The problem is I don't  even know enough to ask the right question!

as you can see the old version is at 
/usr/local/bin/openssl
and the new version is at 
/usr/local/ssl/bin

Thanks a lot!

---

### Post by gautada on 2007-09-27
To find out which application you are running type
 ```
%> which openssl
```
 To find your path type
```
%> set | grep "^PATH"
```
If you pre-pend the new application path to the PATH variable it will be found first
```
%> export PATH=/usr/local/ssl/bin:$PATH
```
 To check that it worked type
```
%> which openssl
```
This should be the new path.

Adam Gautier

---


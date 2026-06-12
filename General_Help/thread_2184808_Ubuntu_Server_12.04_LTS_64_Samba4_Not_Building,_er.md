---
title: "Ubuntu Server 12.04 LTS 64 Samba4 Not Building, error in heimdal"
date: 2013-10-30
forum: General Help
---

### Post by DantePasquale on 2013-10-30
Hi, I'm trying to get Samba 4 to compile on a server running 12.04 LTS as part of installing and testing OpenChange. I'm following the instructions from: [http://iabsis.com/EN/article/35-3/Samba4-installation]("http://iabsis.com/EN/article/35-3/Samba4-installation")

So, I have samba4-4.0.0~alpha18.dfsg1 and when I run configure, it configures OK - here are the relevant Heimdal entreis:

```
grep heimdal configure.log
Using in-tree heimdal kerberos defines
Checking for program krb5-config.heimdal                                                        : /usr/bin/krb5-config.heimdal 
```

However, when I run make (or make install) I get a failure from Heimdal about missing rfc3454.txt file:


```
root@openchangedev:~/Samba4/samba4-4.0.0~alpha18.dfsg1# make
WAF_MAKE=1 ./buildtools/bin/waf build
Waf: Entering directory `/root/Samba4/samba4-4.0.0~alpha18.dfsg1/bin'
Waf: Leaving directory `/root/Samba4/samba4-4.0.0~alpha18.dfsg1/bin'
input file '../heimdal/lib/wind/rfc3454.txt' could not be found ('/root/Samba4/samba4-4.0.0~alpha18.dfsg1/source4/heimdal_build')
make: *** [all] Error 1
```

In that directory, though, there is an rfc3454.py file, so maybe I need to do something python to the heimdal part before running make???

```
root@openchangedev:~/Samba4/samba4-4.0.0~alpha18.dfsg1# ls -l /root/Samba4/samba4-4.0.0~alpha18.dfsg1/source4/heimdal/lib/wind/
total 124
-rw-r--r-- 1 root root  2879 Jun 11  2010 bidi.c
-rw-r--r-- 1 root root  2328 Jun 11  2010 combining.c
-rw-r--r-- 1 root root  2610 Nov  9  2011 errorlist.c
-rw-r--r-- 1 root root  3257 Jun 11  2010 gen-bidi.py
-rw-r--r-- 1 root root  3062 Jun 11  2010 gen-combining.py
-rw-r--r-- 1 root root  3171 Jun 11  2010 generate.py
-rw-r--r-- 1 root root  3615 Jun 11  2010 gen-errorlist.py
-rw-r--r-- 1 root root  4339 Jun 11  2010 gen-map.py
-rw-r--r-- 1 root root  5755 Jun 11  2010 gen-normalize.py
-rw-r--r-- 1 root root  2747 Dec 12  2011 ldap.c
-rw-r--r-- 1 root root  2748 Jun 11  2010 map.c
-rw-r--r-- 1 root root  7489 Dec 12  2011 normalize.c
**-rw-r--r-- 1 root root  2296 Jun 11  2010 rfc3454.py**
-rw-r--r-- 1 root root  5603 Jun 11  2010 rfc4518.py
-rw-r--r-- 1 root root  4120 Dec 12  2011 stringprep.c
-rw-r--r-- 1 root root  3447 Nov  9  2011 stringprep.py
-rw-r--r-- 1 root root  2167 Jun 11  2010 UnicodeData.py
-rw-r--r-- 1 root root 12754 Jan 31  2012 utf8.c
-rw-r--r-- 1 root root  1978 Jun 11  2010 util.py
-rw-r--r-- 1 root root   547 Jan 31  2012 version-script.map
-rw-r--r-- 1 root root   695 Jun 11  2010 wind_err.et
-rw-r--r-- 1 root root  3167 Nov  9  2011 wind.h
-rw-r--r-- 1 root root  2394 Jun 11  2010 windlocl.h
```

I'm stumped - any suggestions????

---


---
title: "iked (shrewsoft vpn) Falied to attach to key daemon"
date: 2016-02-15
forum: General Help
---

### Post by 3-gary-0 on 2016-02-15
Hi,

I am running into a issues trying to get shrewsoft vpn client on ubuntu 15.10 on a new skylake machine. It runs fine on 15.10 on an older machine. I have tried installing from source and from the package and get the same result.

The GUI will show... "failed to attach to key daemon"  I believe this is telling me the iked process can't start...

When I start it "sudo iked" I get...
iked: pthread_mutex_unlock.c:87: __pthread_mutex_unlock_usercnt: Assertion `type == PTHREAD_MUTEX_ERRORCHECK_NP' failed.

Doing some digging I found a couple of interesting Debian bugs. That seem to refer to a bug in glibc when used with skylake or broadwell processors.. 

[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=756316](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=756316)
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=810322](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=810322)

I was wondering if anyone could confirm this and/or if there will be an update coming for ubuntu glibc to address the issue... Or if anyone has a work around that would be great as well..

Thanks in advance!

---

### Post by sandyd on 2016-02-15
Have you tried the fix at the bottom of the bug.

i.e.
```

diff -r -u ike-orig/source/libith/libith.cpp ike/source/libith/libith.cpp
--- ike-orig/source/libith/libith.cpp   2012-02-10 08:05:36.000000000 +0100
+++ ike/source/libith/libith.cpp        2016-01-08 11:42:32.000000000 +0100
@@ -94,7 +94,7 @@
 {
        memset( obj_name, 0, 20 );
        pthread_mutexattr_init( &attr );
-       pthread_mutexattr_settype( &attr, PTHREAD_MUTEX_ERRORCHECK );
+       pthread_mutexattr_settype( &attr, PTHREAD_MUTEX_NORMAL );
        pthread_mutex_init( &mutex, &attr );
 }

```

Go into libith/libith.cpp in the ike source code, replace
```

pthread_mutexattr_settype( &attr, PTHREAD_MUTEX_ERRORCHECK );
```
with
```

pthread_mutexattr_settype( &attr, PTHREAD_MUTEX_NORMAL );
```

---

### Post by 3-gary-0 on 2016-02-15
Hi Sandyd,

Yes it did indeed!  Thank you for the clear direction, that is what I needed. Now just need to get my tunnel to configure...  

Thanks again!

---


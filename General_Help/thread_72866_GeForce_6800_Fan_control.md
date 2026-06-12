---
title: "GeForce 6800 Fan control"
date: 2005-10-07
forum: General Help
---

### Post by serzz on 2005-10-07
So I'm asking is there similar software to SmartDoctor for linux or another vga card fan control program?

---

### Post by serzz on 2005-10-09
Alright I've found solution it asusfan what I was looking for. But now I have hard times to compile it. When I run ./configure it doesn't give me any errors after that I'm trying to run make and it gives me following:
```

serzz@pk5-b-31-1:~/asusfan-0.1$ make
make  all-recursive
make[1]: Entering directory `/home/serzz/asusfan-0.1'
Making all in libasus
make[2]: Entering directory `/home/serzz/asusfan-0.1/libasus'
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -MT i2c.lo -MD -MP -MF ".deps/i2c.Tpo" -c -o i2c.lo i2c.c; \
then mv -f ".deps/i2c.Tpo" ".deps/i2c.Plo"; else rm -f ".deps/i2c.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -g -O2 -MT i2c.lo -MD -MP -MF .deps/i2c.Tpo -c i2c.c  -fPIC -DPIC -o .libs/i2c.o
In file included from xf86i2c.h:10,
                 from i2c.c:70:
xfree.h:10:23: error: X11/Xdefs.h: No such file or directory
In file included from xf86i2c.h:10,
                 from i2c.c:70:
xfree.h:33: error: syntax error before 'pointer'
xfree.h:33: warning: no semicolon at end of struct or union
xfree.h:36: error: syntax error before '*' token
xfree.h:36: error: 'pointer' declared as function returning a function
xfree.h:36: warning: data definition has no type or storage class
xfree.h:37: error: syntax error before '}' token
xfree.h:37: warning: data definition has no type or storage class
In file included from i2c.c:70:
xf86i2c.h:31: error: syntax error before 'Bool'
xf86i2c.h:31: warning: no semicolon at end of struct or union
xf86i2c.h:33: error: syntax error before '*' token
xf86i2c.h:33: error: 'Bool' declared as function returning a function
xf86i2c.h:33: warning: data definition has no type or storage class
xf86i2c.h:34: error: syntax error before '*' token
xf86i2c.h:34: error: syntax error before 'Bool'
xf86i2c.h:34: error: 'Bool' declared as function returning a function
xf86i2c.h:34: warning: data definition has no type or storage class
xf86i2c.h:36: error: syntax error before 'DriverPrivate'
xf86i2c.h:36: warning: data definition has no type or storage class
xf86i2c.h:48: error: syntax error before '}' token
xf86i2c.h:48: warning: data definition has no type or storage class
xf86i2c.h:51: error: syntax error before 'Bool'
xf86i2c.h:52: error: syntax error before 'xf86I2CBusInit'
xf86i2c.h:52: warning: data definition has no type or storage class
xf86i2c.h:71: error: syntax error before 'Bool'
xf86i2c.h:72: error: syntax error before 'xf86I2CDevInit'
xf86i2c.h:72: warning: data definition has no type or storage class
xf86i2c.h:77: error: syntax error before 'xf86I2CProbeAddress'
xf86i2c.h:77: warning: data definition has no type or storage class
xf86i2c.h:78: error: syntax error before 'xf86I2CWriteRead'
xf86i2c.h:79: warning: data definition has no type or storage class
xf86i2c.h:81: error: syntax error before 'xf86I2CReadStatus'
xf86i2c.h:81: warning: data definition has no type or storage class
xf86i2c.h:82: error: syntax error before 'xf86I2CReadByte'
xf86i2c.h:82: warning: data definition has no type or storage class
xf86i2c.h:83: error: syntax error before 'xf86I2CReadBytes'
xf86i2c.h:83: warning: data definition has no type or storage class
xf86i2c.h:84: error: syntax error before 'xf86I2CReadWord'
xf86i2c.h:84: warning: data definition has no type or storage class
xf86i2c.h:86: error: syntax error before 'xf86I2CWriteByte'
xf86i2c.h:86: warning: data definition has no type or storage class
xf86i2c.h:87: error: syntax error before 'xf86I2CWriteBytes'
xf86i2c.h:87: warning: data definition has no type or storage class
xf86i2c.h:88: error: syntax error before 'xf86I2CWriteWord'
xf86i2c.h:88: warning: data definition has no type or storage class
xf86i2c.h:89: error: syntax error before 'xf86I2CWriteVec'
xf86i2c.h:89: warning: data definition has no type or storage class
i2c.c:98: error: syntax error before 'I2CAddress'
i2c.c:98: warning: data definition has no type or storage class
i2c.c: In function 'NV_I2CGetBits':
i2c.c:112: error: dereferencing pointer to incomplete type
i2c.c: In function 'NV_I2CPutBits':
i2c.c:126: error: dereferencing pointer to incomplete type
i2c.c: At top level:
i2c.c:151: error: syntax error before 'Bool'
i2c.c: In function 'ProbeCard':
i2c.c:158: error: 'nbus' undeclared (first use in this function)
i2c.c:158: error: (Each undeclared identifier is reported only once
i2c.c:158: error: for each function it appears in.)
i2c.c:160: error: dereferencing pointer to incomplete type
i2c.c: In function 'I2cCreateBusPtr':
i2c.c:259: error: dereferencing pointer to incomplete type
i2c.c:260: error: dereferencing pointer to incomplete type
i2c.c:261: error: dereferencing pointer to incomplete type
i2c.c:262: error: dereferencing pointer to incomplete type
i2c.c:263: error: dereferencing pointer to incomplete type
i2c.c:264: error: dereferencing pointer to incomplete type
i2c.c:265: error: dereferencing pointer to incomplete type
make[2]: *** [i2c.lo] Error 1
make[2]: Leaving directory `/home/serzz/asusfan-0.1/libasus'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/serzz/asusfan-0.1'
make: *** [all] Error 2


```

Can anyone advice me what should be done?

---

### Post by serzz on 2005-10-09
Found solution, installed kdelibs and kdelibs4-dev

---


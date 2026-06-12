---
title: "problem installing ZThread-2.3.2"
date: 2008-03-19
forum: General Help
---

### Post by jmartrican on 2008-03-19
Hello,

I am have a problem installing ZThread-2.3.2, I do not have a previous version installed.  I am running Ubuntu 7.1, using g++ version 4.2.  The steps for installing are ./configure, then make, make install... similar to other applications.  

The ./configure went through OK, I think.  Here are the last few outputs of ./configure (didnt want to post the whole thing cause it's very long.

> configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating share/zthread-config
config.status: creating share/zthread.spec
config.status: creating src/config.h
config.status: src/config.h is unchanged
config.status: executing depfiles commands
jose@jmart1:~/ZThread-2.3.2$
jose@jmart1:~/ZThread-2.3.2$
  

When I ran make here is what I got, I cant decipher what it means.

> make[2]: Entering directory `/home/jose/ZThread-2.3.2/src'
if /bin/bash ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I. -I../include   -g -O2 -Wall -DNDEBUG  -g -O2 -Wall -DNDEBUG -MT AtomicCount.lo -MD -MP -MF ".deps/AtomicCount.Tpo" \
          -c -o AtomicCount.lo `test -f 'AtomicCount.cxx' || echo './'`AtomicCount.cxx; \
        then mv -f ".deps/AtomicCount.Tpo" ".deps/AtomicCount.Plo"; \
        else rm -f ".deps/AtomicCount.Tpo"; exit 1; \
        fi
 g++ -DHAVE_CONFIG_H -I. -I. -I. -I../include -g -O2 -Wall -DNDEBUG -g -O2 -Wall -DNDEBUG -MT AtomicCount.lo -MD -MP -MF .deps/AtomicCount.Tpo -c AtomicCount.cxx  -fPIC -DPIC -o .libs/AtomicCount.o
In file included from vanilla/SimpleAtomicCount.cxx:26,
                 from AtomicCount.cxx:55:
../include/zthread/Guard.h: In destructor 'ZThread::Guard<LockType, LockingPolicy>::~Guard()':
../include/zthread/Guard.h:494: error: there are no arguments to 'isDisabled' that depend on a template parameter, so a declaration of 'isDisabled' must be available
../include/zthread/Guard.h:494: error: (if you use '-fpermissive', G++ will accept your code, but allowing the use of an undeclared name is deprecated)
make[2]: *** [AtomicCount.lo] Error 1
make[2]: Leaving directory `/home/jose/ZThread-2.3.2/src'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/jose/ZThread-2.3.2/src'
make: *** [install-recursive] Error 1


I noticed that it's using a directory called '../src/vanilla', I tried to get it to use '../src/linux' instead by changing two variables in ./configure.  I set these two variables to the values displayed.

>   --enable-atomic-linux   use linux atomic instructions default=yes
  --enable-vanilla        Select vanilla implementation default=no


But it had no affect (same results).  I noticed a configure.ac file that might be setting the variables back to 'no' and 'autodetect', respectively....who knows.

Any help would be greatly appreciated.

---

### Post by jmartrican on 2008-03-19
Figured it out.  Had to set an environment variable that is used to tell the compiler to  enable fpermissive.

> export CXXFLAGS="-fpermissive"

thanks

---


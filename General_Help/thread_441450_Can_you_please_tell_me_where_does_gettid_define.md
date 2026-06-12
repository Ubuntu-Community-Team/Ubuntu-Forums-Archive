---
title: "Can you please tell me where does gettid define?"
date: 2007-05-12
forum: General Help
---

### Post by yinglcs2 on 2007-05-12
I try to build a software in ubuntu, but it said 'gettid' has not  been declared.
Can you please tell me where does it defined?

Thank you.

make copy
g++ -pipe -Wall -Wreturn-type -Wno-non-virtual-dtor -fno-exceptions --permissive -fno-rtti -Wno-ctor-dtor-privacy -Winline -Wdisabled-optimization -Wno-unused-parameter -Wno-reorder -fmessage-length=0  -march=i686 -O0 -g -DDEBUG -D_DEBUG  -I../../common/runtime/pub -I/usr/X11R6/include -I../include -I../runtime/pub -I../system/pub -I../fileio/pub -I../util/pub -Ipub/platform/default -I./pub -I. -include dbg/common_dbgtool_ribodefs.h -fPIC -DPIC -o dbg/obj/servertrace.o -c servertrace.cpp
servertrace.cpp:70: error: ‘gettid’ has not been declared
servertrace.cpp:71: error: expected constructor, destructor, or type conversion before ‘pid_t’
servertrace.cpp: In static member function ‘static void ServerTrace::PrintThreadId()’:
servertrace.cpp:128: error: ‘gettid’ was not declared in this scope
make: *** [dbg/obj/servertrace.o] Error 1
Time used: 0.10 seconds
ERROR: UNIXCompile(common/dbgtool) ERROR: Make failed.

--- Build System Error ------------------------------------
Make failed.

---

### Post by kidders on 2007-05-13
Hi there,

> **yinglcs2 said:**
> Can you please tell me where does it defined?It could be absolutely anywhere! You should check that you have fulfilled all dependencies for whatever you're compiling.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---


---
title: "unable to compile and run c++ programmes please help"
date: 2008-03-25
forum: General Help
---

### Post by lookforlohith on 2008-03-25
//lohi.cc
#include<iostream>

main()
{

printf("lohi");

}

i wrote this and try to compile

$cc lohi.cc
/tmp/cc0YAzPm.o: In function `__static_initialization_and_destruction_0(int, int)':
lohi.cc:(.text+0x23): undefined reference to `std::ios_base::Init::Init()'
/tmp/cc0YAzPm.o: In function `__tcf_0':
lohi.cc:(.text+0x6c): undefined reference to `std::ios_base::Init::~Init()'
/tmp/cc0YAzPm.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
lohi@look:~$ 

so its not getting compiled , but c programmes r compiling (lohi.c),,,,,,,,, please help

---

### Post by provisional_idiot on 2008-03-25
well printf() is part of the c standard library...not c++


what you want, instead of, printf, is:

```
#include <iostream>
int main()
{
       cout << "lohi";
    return 0;
}

```

---

### Post by lloyd_b on 2008-03-25
When compiling C++ code, use "g++" rather than "cc" (or "gcc").  It makes a difference...

Lloyd B.

---

### Post by lookforlohith on 2008-03-25
In file included from /usr/include/c++/4.1.3/backward/iostream.h:31,
                 from lohi.cc:1:
/usr/include/c++/4.1.3/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.


this is the warning its showing , i gave g+ to compile it worked, but y this warning

---

### Post by lloyd_b on 2008-03-25
Did you change the "#include <iostream>" to "#include <iostream.h>"?  If so, change it back.

Lloyd B.

---


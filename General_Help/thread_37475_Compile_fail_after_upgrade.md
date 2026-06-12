---
title: "Compile fail after upgrade"
date: 2005-05-27
forum: General Help
---

### Post by jsemczyk on 2005-05-27
Hi,

I got an automatic upgrade this morning and now I cannot link anymore (It was able to link yesterday). I get :

```
gcc -O3 -Wall  -DTHREADSAFE -DLinux -DMAXFD=1024 -c test.cpp
gcc -o test test.o -lstdc++ -lpthread
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../crt1.o: file not recognized: File format not recognized
collect2: ld returned 1 exit status
make: *** [test] Error 1

```

I copied the sources on another debian box and it linked well...

This can help, I tried 
On the ubuntu box :
```
$ ld /usr/lib/crt1.o
/usr/lib/crt1.o: file not recognized: File format not recognized
```

On the debian box :
```
$ ld /usr/lib/crt1.o
/usr/lib/crt1.o(.text+0xc): In function `_start':
../sysdeps/i386/elf/start.S:92: undefined reference to `__libc_csu_fini'
/usr/lib/crt1.o(.text+0x11):../sysdeps/i386/elf/start.S:93: undefined reference to `__libc_csu_init'
/usr/lib/crt1.o(.text+0x18):../sysdeps/i386/elf/start.S:98: undefined reference to `main'
/usr/lib/crt1.o(.text+0x1d):../sysdeps/i386/elf/start.S:102: undefined reference to `__libc_start_main'
```


Seems like my linker is broken ... I tried to reinstall binutils but it did not work.

Any ideas ?


JoN


Ubuntu box :
gcc (GCC) 3.3.5 (Debian 1:3.3.5-8ubuntu2)
GNU ld version 2.15

Debian box :
gcc (GCC) 3.3.4 (Debian 1:3.3.4-6sarge1)
GNU ld version 2.15

test code :
```
#include <iostream>

using namespace std;

int main(int argc, char ** argv)
{
	cout << "hello" << endl;
	return 0;
}
``` 

detailed output :
```
gcc -v -o test test.o -lstdc++ -lpthread
Reading specs from /usr/lib/gcc-lib/i486-linux/3.3.5/specs
Configured with: ../src/configure -v --enable-languages=c,c++,java,f77,pascal,objc,ada,treelang --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --with-gxx-include-dir=/usr/include/c++/3.3 --enable-shared --with-system-zlib --enable-nls --without-included-gettext --enable-__cxa_atexit --enable-clocale=gnu --enable-debug --enable-java-gc=boehm --enable-java-awt=xlib --enable-objc-gc i486-linux
Thread model: posix
gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)
 /usr/lib/gcc-lib/i486-linux/3.3.5/collect2 --eh-frame-hdr -m elf_i386 -dynamic-linker /lib/ld-linux.so.2 -o test /usr/lib/gcc-lib/i486-linux/3.3.5/../../../crt1.o /usr/lib/gcc-lib/i486-linux/3.3.5/../../../crti.o /usr/lib/gcc-lib/i486-linux/3.3.5/crtbegin.o -L/usr/lib/gcc-lib/i486-linux/3.3.5 -L/usr/lib/gcc-lib/i486-linux/3.3.5/../../.. test.o -lstdc++ -lpthread -lgcc --as-needed -lgcc_s --no-as-needed -lc -lgcc --as-needed -lgcc_s --no-as-needed /usr/lib/gcc-lib/i486-linux/3.3.5/crtend.o /usr/lib/gcc-lib/i486-linux/3.3.5/../../../crtn.o
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../crt1.o: file not recognized: File format not recognized
collect2: ld returned 1 exit status
make: *** [test] Error 1


```


And here the detailed output for the debian box. This one is a bit different and works, I see some more link flags but I don't think it is the issue, ld cannot even read crt1.o :
```
gcc -O3 -Wall  -DTHREADSAFE -DLinux -DMAXFD=1024 -c test.cpp
gcc -v -o test test.o -lstdc++ -lpthread
Lecture des spécification à partir de /usr/lib/gcc-lib/i486-linux/3.3.4/specs
Configuré avec: ../src/configure -v --enable-languages=c,c++,java,f77,pascal,objc,ada,treelang --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --with-gxx-include-dir=/usr/include/c++/3.3 --enable-shared --with-system-zlib --enable-nls --without-included-gettext --enable-__cxa_atexit --enable-clocale=gnu --enable-debug --enable-java-gc=boehm --enable-java-awt=xlib --enable-objc-gc i486-linux
Modèle de thread: posix
version gcc 3.3.4 (Debian 1:3.3.4-6sarge1)
 /usr/lib/gcc-lib/i486-linux/3.3.4/collect2 --eh-frame-hdr -m elf_i386 -dynamic-linker /lib/ld-linux.so.2 -o test /usr/lib/gcc-lib/i486-linux/3.3.4/../../../crt1.o /usr/lib/gcc-lib/i486-linux/3.3.4/../../../crti.o /usr/lib/gcc-lib/i486-linux/3.3.4/crtbegin.o -L/usr/lib/gcc-lib/i486-linux/3.3.4 -L/usr/lib/gcc-lib/i486-linux/3.3.4/../../.. test.o -lstdc++ -lpthread -lgcc -lgcc_eh -lc -lgcc -lgcc_eh /usr/lib/gcc-lib/i486-linux/3.3.4/crtend.o /usr/lib/gcc-lib/i486-linux/3.3.4/../../../crtn.o

```

---

### Post by Xian on 2005-05-27
[QUOTE=jsemczyk]Seems like my linker is broken ... I tried to reinstall binutils but it did not work.[/QUOTE]
Instead of re-installing you might want to downgrade:

```
$ sudo aptitude install <pkgname>=<version>
```

---


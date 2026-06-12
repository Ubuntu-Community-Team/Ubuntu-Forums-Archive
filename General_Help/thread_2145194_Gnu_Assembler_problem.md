---
title: "Gnu Assembler problem"
date: 2013-05-14
forum: General Help
---

### Post by Mathematica on 2013-05-14
edit:
problem was the x86 libs for development
I downloaded and fixed it


I'm running ubuntu 13.04 x64 bit


when I ran my test.out
shell returns this error:
> Accessing a corrupted shared library
I think it returns because I m using 64 bit os



```


.code32

.section .data
par1:
.int 33
msg:
.asciz "%d\n"
.section .text
.globl _start
_start:
pushl $par1
pushl $msg
call printf



cikis:
movl $1,%eax
movl $1,%ebx
int $0x80


```

ldd test.out
```

ldd test.out
    linux-vdso.so.1 =>  (0x00007fff615fe000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fbfb56f8000)
    /lib32/libc.so.6 => /lib64/ld-linux-x86-64.so.2 (0x00007fbfb5ae0000)

```

makefile
```

as test.s -o test.o
ld -dynamic-linker /lib/ld-linux.so.2 -lc test.o -o test.out



// I also tried 


ld -dynamic-linker /lib32/ld-linux.so.2 -lc test.o -o test.out

```



and sorry for my english

---


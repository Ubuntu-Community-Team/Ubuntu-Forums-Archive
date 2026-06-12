---
title: "Nasm/cant execute"
date: 2007-02-23
forum: General Help
---

### Post by Hatty on 2007-02-23
so I wrote a cat clone in asm, but i cant execute it.
Using Ubuntu 6.10 Edgy,
GNU ld version 2.17 Debian GNU/Linux
NASM version 0.98.38 compiled on Jun 27 2005
```

hatty@chimera:~/devel/nasm/cat$ ls
build.sh  mycat.asm
hatty@chimera:~/devel/nasm/cat$ ./build.sh 
hatty@chimera:~/devel/nasm/cat$ ls
build.sh  mycat  mycat.asm  mycat.o
hatty@chimera:~/devel/nasm/cat$ ./mycat
bash: ./mycat: No such file or directory
hatty@chimera:~/devel/nasm/cat$ 

```
mycat.asm:
```

section .data:
    filename db 'cat.asm', 0 ;filename to open
    filePtr  db 0            ;pointer to fd
    fileMode db 'r',0        ;file mode = read

section .text:
    extern fopen    ;fopen from libc
    extern fclose   ;fclose from libc
    extern putchar  ;fputc from libc
    extern fgetc    ;fgetc from libc
    global _start   ;start

_start:
    mov ebx, fileMode  ;file mode (read)
    mov eax, filename  ;filename
    call fopen         ;open file, store fd in eax
    mov [filePtr], eax ;move fd into filePtr

readloop:
    mov eax, [filePtr]  ;move fd into eax
    call fgetc         ;get char, store in eax

    cmp eax, -1        ;if eax 
    je end             ;== 0
                       ;jump to end
    call putchar       ;print the char (eax)

    jmp readloop       ;again

end:
    mov eax, [filePtr] ;move filePtr into eax
    call fclose        ;close file
    mov eax, 10
    call putchar       ;print 
    mov eax, 1         ;sys_exit
    mov ebx, 0        ;exit code 
    int 80h            ;call kernel

```

build.sh
```
#!/bin/bash
nasm -f elf -o mycat.o mycat.asm
ld -o ./mycat -lc mycat.o

```

---

### Post by taurus on 2007-02-23
```
ls -la ~/devel/nasm/cat
```

---

### Post by po0f on 2007-02-23
Hatty,

Have you tried:

```
[font="Courier New"]$ ls -l ./mycat[/font]
```

Is the binary executable?  I don't see why it wouldn't be, but you might want to double-check.

---

### Post by Hatty on 2007-02-23
```
hatty@chimera:~/devel/nasm/cat$ ls -la ./mycat
-rwxr-xr-x 1 hatty hatty 2411 2007-02-23 18:06 ./mycat
```

---

### Post by po0f on 2007-02-23
Hatty,

Sorry, I don't have any experience compiling ASM, just reaching for a solution.

Maybe try `file ./mycat` to see what kind of file your computer thinks it is.

---

### Post by Hatty on 2007-02-23
```
hatty@chimera:~/devel/nasm/cat$ file ./mycat
./mycat: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), not stripped

```

---

### Post by Hatty on 2007-02-24
It seems to be ld. If I link to libc, I can't run it, but if I don't, I can.
Also, if I link with gcc it works, so I guess I'll just do that.

---

### Post by MaindotC on 2007-11-14
I'm currently using MASM 6.15 and I'd like to switch to NASM.  Looking at your code, it seems that the syntax is different.  Do you have any tutorials or documentation on using NASM with assemblies written for MASM 6.15?  Thanks!

---


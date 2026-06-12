---
title: "please help -- shellcoding problem"
date: 2006-11-18
forum: General Help
---

### Post by Ellias on 2006-11-18
Hello everyone, I'm going to out on a limb here and post this up because I am completely baffled here and it may be able to help others in the future...

I am trying to learn shellcode using ubuntu edgy eft. I have written a small vulnerable program in C (vuln.c) that is vulnerable to a buffer overflow.

```

int main(int argc, char **argv, char **envp) {

        char buf[50];
        strcpy(buf, argv[1]);
        return 0;
}

```

I have compiled it by typing
```

gcc -ggdb -fno-stack-protector -o $1 $2

```

In order to get rid of the stack overflow protection mechanism that is now part of gcc. I have also used the command 

```
kernel.randomize_va_space = 0
```

to disable the randomized buffer feature ubuntu has.

In theory my program should be vulnerable to a buffer overflow attack of input greater than 50 characters. So an execution of ./vuln `perl -e 'print "A"x50 . "BBBB" . "CCCC"'` should overflow the stack and overwrite the eip value to 0X43434343. For some reason unknown to me this is not happening. Here is what I get when I use gdb to examine the memory stack...

```
jason@pitchblack:~/code$ **gdb vuln**
GNU gdb 6.4.90-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".

**(gdb) run `perl -e 'print "A"x50 . "BBBB" . "CCCC"'`**
Starting program: /home/jason/code/vuln `perl -e 'print "A"x50 . "BBBB" . "CCCC"'`

[B]Program received signal SIGSEGV, Segmentation fault.
0x08048389 in main (argc=Cannot access memory at address 0x42424242
) at vuln.c:6
6       }[/B]
(gdb) info reg
eax            0x0      0
ecx            0x42424242       1111638594
edx            0xbffff9fc       -1073743364
ebx            0xb7fd6ff4       -1208127500
[B]esp            0x4242423e       0x4242423e
ebp            0x43434343       0x43434343[/B]
esi            0xb8000ce0       -1207956256
edi            0x0      0
**eip            0x8048389        0x8048389 <main+53>**
eflags         0x210286 [ PF SF IF RF ID ]
cs             0x73     115
ss             0x7b     123
ds             0x7b     123
es             0x7b     123
fs             0x0      0
gs             0x33     51
(gdb) 

```

As you can see, for some reason the eip value (the value used to point to different locations in memory) is not being manipulated by the buffer overflow. The eip remains untouched no matter how many characters I overflow the buffer with. Every tutorial I have looked says that it should be. Is there some security feature built in that I am not aware of? I tried googleing but came up with nothing. I would really appreciate some help, thanks!

---

### Post by loell on 2006-11-18
perhaps its already been fixed in ubuntu specific kernel

---

### Post by Ellias on 2006-11-18
hello loell, thanks for your response.

I tested this with Fedora Core 4, and I got the same issue. I would really like to know why exactly this is happening. :confused:

---

### Post by loell on 2006-11-19
though i'm not fund of shellcode exploits, i think its a hit or miss, imho
how about other shellcodes?

---

### Post by Ellias on 2006-11-19
While I agree with you that shellcode is very much a hit or miss procedure, all I am trying to do is overwrite the eip (i dont even care if the address in the eip points to a valid memory block). For example:

( char buf[50] 50 bytes)(EBP frame pointer 4 bytes)(EIP return address 4 bytes)

The buffer contents after the overflow should look like this...

(*50 A characters)(BBBB)(CCCC)

but instead the eip is remaining untouched. ](*,)

---

### Post by Ellias on 2006-11-20
Hello again all,

I have found the solution to this issue I was having. It seems that the vulnerable program that I had created was not executing the instructions in the order that I had expected them to. I borrowed someone elses sample code from... 

[http://www.addict3d.org/index.php?page=viewarticle&type=security&ID=6962&title=Simple%20Buffer%20Overflow%20Tutorial](http://www.addict3d.org/index.php?page=viewarticle&type=security&ID=6962&title=Simple%20Buffer%20Overflow%20Tutorial)

```

#include <stdlib.h>
#include <stdio.h>
#include <string.h>

int bof(char *string) {

char buffer[1024];

strcpy(buffer, string);

return 1;
}

int main(int argc, char *argv[]) {

bof(argv[1]);
printf("Done..\n");

return 1;
}

```

To be perfectly honest, I am not sure 'why' this vulnerable code overwrites the eip (instruction pointer) in memory when its buffer is overrun, and other similar ones do not. It seems like there could be many reasons which I will investigate later. Anyway, here is the resulting output after using gdb...

```
jason@pitchblack:~/code$ gdb vuln2
GNU gdb 6.4.90-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".

**(gdb) run `perl -e 'print "A"x1040'`**
Starting program: /home/jason/code/vuln2 `perl -e 'print "A"x1040'`

Program received signal SIGSEGV, Segmentation fault.
0x41414141 in ?? ()
(gdb) i r
eax            0x1      1
ecx            0xfffffa38       -1480
edx            0xbffffba1       -1073742943
ebx            0xb7fd6ff4       -1208127500
esp            0xbffff5d0       0xbffff5d0
**ebp            0x41414141       0x41414141**
esi            0xb8000ce0       -1207956256
edi            0x0      0
**eip            0x41414141       0x41414141**
eflags         0x10246  [ PF ZF IF RF ]
cs             0x73     115
ss             0x7b     123
ds             0x7b     123
es             0x7b     123
fs             0x0      0
gs             0x33     51

```

Notice now in this example, the eip is now overwritten with A's hexidecmial equivalent of x41. Hope this thread helps anyone that is trying to learn assembly/how buffer overflows work. 8)

---

### Post by marco.zunino on 2007-12-10
Dear Ellias, i think I can help you to understand what's wrong with your first code. When you call a function in main, the system insert in the stack a new stack frame, at the top of witch  the vars of the current scope (for example buffer of the function bof()), under it the frame pointer and after this the return adress. When you use an overflowing input, the excess chars overwrite the return adress, and the program flow can be alterated. Your first code didn't work because there isn't an external function and a call in the main, the instruction were in the main.

Perhaps I said a lot of junkes, but I think this is the reason. Ah.. sorry for my bad english

---


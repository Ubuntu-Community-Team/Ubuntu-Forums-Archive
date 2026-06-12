---
title: "How to compile an X86 assembly file ?"
date: 2007-11-22
forum: General Help
---

### Post by sshahir on 2007-11-22
Hi all,

I need to know how to compile  assembly program files under ubuntu v6.06. I have tried to compile an assembly language using "gcc" compiler but I ran into some errors. 

I have tried to compile the following simple assembly program called  "Assem_Test1.s":

> .MODEL SMALL
.CODE

MOV AH,2
MOV DL,5A
INT 21
INT 20

I have tried the following there commands to generate the .obj file using C compiler as the X86 assembler:

[LIST]
[*]gcc Assem_Test1.s

[*]gcc -assembler Assem_Test1.s

[*]g++ -assembler-with-cpp Assem_Test1.s m_Test1.s
[/LIST]

when I try to compile the file using gcc compiler the following  error messages are thrown:

> [COLOR="Red"]Assem_Test1.s:1: Error: unknown pseudo-op: `.model'
Assem_Test1.s:2: Error: unknown pseudo-op: `.code'
Assem_Test1.s:4: Error: too many memory references for `mov'
Assem_Test1.s:5: Error: too many memory references for `mov'
Assem_Test1.s:6: Error: suffix or operands invalid for `int'
Assem_Test1.s:7: Error: suffix or operands invalid for `int'
a[/COLOR]

I am wondering whether I can use the gcc or g++ compiler to compile assembly files. if so, please let me know what is the right syntax. Otherwise, please let me know how I can compile assembly files.

I appreciate for any comments or suggestions.

Regards,
sshahir

---

### Post by harshask on 2007-11-22
Dude is tht 8086 pgms??

---

### Post by sshahir on 2007-11-22
> **harshask said:**
> Dude is tht 8086 pgms??

Yes, it is Intel assembly. In windows, I can use ml.exe to genrate the .obj file from an assembly file, but I don't know how to compile Intel assembly files in Ubuntu.

---

### Post by harshask on 2007-11-22
According to my knowledge ....all assembly language prms are saved with .asm extensions..........for executing the assembly language pgms(8086) u need to download tis

[http://www.esnips.com/doc/6a245c81-1e47-46db-b26b-393f0086ced4/MASM-5.1](http://www.esnips.com/doc/6a245c81-1e47-46db-b26b-393f0086ced4/MASM-5.1)

extract tis file (.rar) n paste it in your home folder...

thn type tis in terminal

sudo apt-get install dosemu dosemu-freedos

after installing  type these instructions 

dosmu(u wil get a black screen after typing this) 
d: 

now your are ready for assembly language programming .... 

edit filename.asm

after you have typed the program exit from it .Type 
masm/zi filename.asm;
link/co filename.obj;
filename (to see the direct output) OR cv/p filename.exe after this u wil enter a screen ..press F5 to see the o/p :guitar:

one more thing ..dont forget the semicolons in the above instructions :)

---

### Post by harshask on 2007-11-22
According to my knowledge ....all assembly language prms are saved with .asm extensions..........for executing the assembly language pgms(8086) u need to download tis

[http://www.esnips.com/doc/6a245c81-1...6ced4/MASM-5.1](http://www.esnips.com/doc/6a245c81-1...6ced4/MASM-5.1)

extract tis file (.rar) n paste it in your home folder...

thn type tis in terminal

sudo apt-get install dosemu dosemu-freedos

after installing type these instructions

dosmu(u wil get a black screen after typing this)
d:

now your are ready for assembly language programming ....

edit filename.asm

after you have typed the program exit from it .Type
masm/zi filename.asm;
link/co filename.obj;
filename (to see the direct output) OR cv/p filename.exe after this u wil enter a screen ..press F5 to see the o/p

one more thing ..dont forget the semicolons in the above instructions

---

### Post by sshahir on 2007-11-22
> **harshask said:**
> .....after you have typed the program exit from it .Type 
**masm**/zi filename.asm;
**link**/co filename.obj;
filename (to see the direct output) OR cv/p filename.exe after this u wil enter a screen ..press F5 to see the o/p :guitar:

one more thing ..dont forget the semicolons in the above instructions :)

Do you mean  the **masm** and **link** commands can be used to compile assembly  files under both MS Windows and Linux platforms?

---

### Post by harshask on 2007-11-22
yes ......u wil switch to dos mode after u hav installed dosemu..[:D]...
search for adityakavoor's  posts for more details :D

---

### Post by harshask on 2007-11-22
Follow those instructions dude ...It is more than enough...if stuck reply back!..

---

### Post by maxesanu on 2007-11-24
How about AMD64 assembler? If I am using a 64 bit Ubuntu and follow the above instructions, will I be able to compile 64 bit assembly code? Thank you.

---

### Post by sliverman69 on 2008-01-14
amd is compatible with intel architechture, so you will be able to compile and run it with a 64 bit processor.  We just discussed this in my Assembly class a few minutes ago.

---

### Post by peabody on 2008-01-14
NASM also should work.  It's fairly compatible with MASM/intel style assembly.

sudo aptitude install nasm.

---


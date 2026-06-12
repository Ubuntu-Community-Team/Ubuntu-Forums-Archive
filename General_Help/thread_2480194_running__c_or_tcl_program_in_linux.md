---
title: "running  c or tcl program in linux"
date: 2022-10-22
forum: General Help
---

### Post by lich444 on 2022-10-22
i have ubuntu 20 ... with lot of application installed 
How do i compile and run a program in c or c++ 
i also installed tcl 8.6
and  cant run nothing 
lich

---

### Post by QIII on 2022-10-22
Moved to General Help.

You originally placed your query in the Resolution Centre.  The RC is not a technical help sub-forum.  The tagline(s) read(s):

> Account queries following change to SSO login
Please read this sticky BEFORE posting your request in the Resolution Centre.

Username change requests
Please read this sticky BEFORE posting your request in the Resolution Centre.

---

### Post by Impavidus on 2022-10-22
You need a compiler (I suggest you install gcc from the repositories), the libraries your program needs (maybe those are already installed) and the header files. You can get the header files for all libaries that are in the repositories from the repositories too. Usually, you take the name of the package with the library, then add the -dev suffix. Further, the make tool may be handy. That should be all you need to compile C or C++ on Ubuntu. Then run the program from command line. You need execute permission, but when gcc creates an executable, it adds the execute permission automatically.

Run gcc from the command line. Few people use IDEs on Linux.

---

### Post by TheFu on 2022-10-22
> **lich444 said:**
> i have ubuntu 20 ... with lot of application installed 
How do i compile and run a program in c or c++ 
i also installed tcl 8.6
and  cant run nothing 
lich

Google found these instructions: [https://www3.cs.stonybrook.edu/~cse230/hw/instructionsV1.1.htm](https://www3.cs.stonybrook.edu/~cse230/hw/instructionsV1.1.htm)
They are reasonable for C or C++.

The .c file needs to be compiled into an "object file", .o.  Then the linker takes the resulting .o files and libraries to "link" all of them into an executeable program file.  On Unix/Linux, there isn't any extension required for a program to be executable, just that it have the correct permissions with the execute flag and obviously, that it is compiled for the correct machine architecture.  So if you have an x86-64 CPU, then you want to compile and link an x86-64 machine program, not an ARM64 or MIPS or SPARC or PA RISC machine architecture program.  The default compile and link will be for the current machine architecture, so this really isn't something to worry about, but it does mean that a compiled program for 1 type of machine cannot be copied to a different machine architecture (say ARM to Intel) and be expected to run.

As for TCL, that's a scripting language, so you'd need to create a TCL script that is compatible with the TCL version you installed and feed that script into the TCL interpreter to be run.  Most of the time, we use Tk/TCL together (or TCL/Tk), but it is possible to use nearly any scripting language with TCL.  I cannot say that I've seen any TCL-only program before. [https://wiki.tcl-lang.org/page/An+Introduction+to+Tcl+Scripting](https://wiki.tcl-lang.org/page/An+Introduction+to+Tcl+Scripting)

+1 on using the OS as the IDE for all programming.  [https://blog.sanctum.geek.nz/series/unix-as-ide/](https://blog.sanctum.geek.nz/series/unix-as-ide/) explains more.

---

